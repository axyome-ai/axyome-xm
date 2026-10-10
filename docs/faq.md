# Frequently Asked Questions

## General

### Does Axyome XM send any data to the cloud?

Only in specific cases. Axyome XM is local-first: captured activity is persisted locally on your machine. The extension contacts the network only to talk to `api.axyome.ai` while you are signed in (sign-in, licence check, device registration), and, on Team & Enterprise plans, to sync captured events and coding goals. The embedded MCP server makes no network calls, and there are no third-party analytics. See [Privacy](privacy.md#network-activity).

---

### What data does it collect?

Axyome XM captures development events from VS Code:

| Data | Captured | Notes |
|------|----------|-------|
| File paths and file events | Yes | Language, LOC delta |
| Error messages | Yes | File, line, severity |
| Git commits | Yes | Message, branch, files changed |
| AI chat sessions (Copilot) | Yes | Prompts and replies |
| Claude Code prompts and tool calls | Yes | Tool arguments (up to 8 KB) and a result preview (up to 512 bytes) |
| Terminal commands | Yes (on by default) | With automatic secret redaction |

Capture does not read file contents from disk, the clipboard or keystrokes (keystrokes are only counted). File excerpts are stored when an AI assistant's tool call or chat reply contains them. Every source can be turned off in settings; see [Privacy](privacy.md).

---

### Will it slow down VS Code?

Axyome XM writes captured events through a file-based queue and persists them
locally in the background, so capture does not hold the editor.

---

### Where is my data stored?

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

---

### How do I delete all my data?

**Via Command Palette:** `Ctrl+Shift+P` -> **Axyome XM: Clear Captured Events**

**Manually:** Delete the `memory-agent-events.db` file at the path above. The extension creates a fresh database on next start.

---

### Can I back up my data?

Yes. `Ctrl+Shift+P` -> **Axyome XM: Backup Database** writes a copy to the
`backups/` folder and keeps the 5 most recent. **Axyome XM: List/Restore Database
Backups** lists them and restores one.

Separately, the extension makes an automatic copy next to the database when the
database schema version changes, and keeps up to 10 of those.

---

## MCP Tools

### Do I need to configure anything for Copilot?

Usually not. Axyome XM writes a `.vscode/mcp.json` entry for its MCP server into
your workspace: silently on first install, and after asking in other workspaces
(dismissing the prompt still writes it). The 54 `axm_*` tools then appear in
GitHub Copilot. If you chose **Skip** or **Don't Ask Again**, run
**Axyome XM: Configure Workspace for AI Memory** to create it.

---

### Which AI assistants support `axm_*` tools?

Any MCP-compatible assistant:
- **GitHub Copilot** (VS Code 1.100+) - configured through `.vscode/mcp.json` (see above)
- **Claude Code** and other Claude clients - add the server to their MCP configuration yourself; Axyome XM does not write Claude's MCP config
- Any other tool supporting the [Model Context Protocol](https://modelcontextprotocol.io)

---

### Why does Copilot say it can't find the `axm_*` tools?

1. Ensure VS Code is **1.100 or newer** (`Help - About`)
2. Do a **full restart** of VS Code (close and reopen - not just `Reload Window`)
3. Check the extension is enabled: Extensions panel - search "Axyome XM" - ensure it's not disabled
4. Run `Ctrl+Shift+P` -> **Axyome XM: Show Statistics** to verify the server is running
5. If the server shows an error, check the Output panel: `View - Output - Axyome XM`

---

### How is the MCP server started?

The MCP server is an embedded binary shipped inside the VSIX
(`axyome-xm-mcp-win-<version>.exe` / `axyome-xm-mcp-linux-<version>` /
`axyome-xm-mcp-macos-<version>`). VS Code starts it from the `.vscode/mcp.json`
entry as a local stdio process. It opens no network ports - communication is
entirely through standard input/output.

---

## Storage & Performance

### How large does the database grow?

It depends on how much you code and how many AI chat sessions you run. Imported
chat sessions are usually the largest part: on one heavy user's 621 MB database
they took 397 MB. **System > Overview** in the dashboard shows the current
database size and table count.

Axyome XM does not delete old data automatically, so the database keeps growing
until you remove data yourself.

---

### Can I move my data to a new machine?

Yes. Close VS Code on both machines, then copy `axyome-xm.db` (and its
`axyome-xm.db-wal` file, if present) from the globalStorage path on your old
machine to the same path on your new machine. The extension picks it up on next
start.

---

### Does it work without an internet connection?

Mostly. Capture, search, recall, MCP tools and the dashboard run locally and keep working offline. You need a connection to link an account (required after the 30-day preview), to refresh a paid licence, and for Team & Enterprise cloud sync.

---

## Features

### What is the XM Wiki?

The XM Wiki is a personal, searchable knowledge base auto-generated from your coding sessions. It stores:

- **Entities** - Services, files, tools, packages you interact with
- **Errors** - Documented bugs with proposed resolutions
- **Patterns** - Recurring code patterns
- **Decisions** - Architecture decision records (ADRs)
- **Concepts** - Ideas that recur across sessions
- **Syntheses** - Summaries that combine several pages

Build it by running `@copilot Ingest this session into the wiki.`, the
**XM Wiki: Ingest Latest Session** command, or **Replay > Wiki > Ingest** in the
dashboard.

---

### What are the Achievement Badges?

12 badges you unlock by hitting milestones. See them under **System > Badges**
in the dashboard ([screenshot](dashboard.md#badges)).

| Badge | Unlock Condition |
|-------|----------------|
| Prompt Master | 12+ AI tool calls per prompt (weekly ratio) |
| Flow State | 2+ hours of continuous coding without breaks |
| First-Try | Commit without prior errors |
| Speed Demon | 500+ events in a single hour |
| Clean Coder | Commit with 0 TypeScript errors |
| Early Bird | 10+ events before 8 AM |
| Night Owl | 10+ events after 10 PM |
| AI Whisperer | 100+ AI tool invocations in one day |
| Pattern Finder | Use `axm_search_patterns` 10+ times |
| Decision Logger | Log 5+ decisions in a week |
| Week Streak | 7 consecutive days of activity |
| Memory Champion | 1,000+ events in memory |

---

### What is the DIP Score?

The Developer Intelligence Platform score - a weighted composite of 4 pillars:

| Pillar | Weight | What it measures |
|--------|--------|-----------------|
| **Velocity** | 25% | Build and commit throughput, feature work |
| **Reliability** | 30% | Errors resolved, time-to-fix |
| **Efficiency** | 25% | How effectively AI assistance is used |
| **Learning** | 20% | Patterns matched, skill growth |

The dashboard (**Intel > Score**) calls the second pillar *Reliability*; the
`axm_get_developer_intelligence` tool reports it as *Quality*. Pillars with no
captured data are left out and the score is re-weighted over the rest.

Ask: `@copilot How am I doing this week?`

---

### What is the ATI Score?

**AI Tool Index** - measures how effectively you use AI assistance. It's the ratio of tools-per-prompt: higher means you're getting more value from each AI interaction.

Ask: `@copilot Show my session analytics and ATI score.`

---

### What is the Time Machine?

**Replay > Time Machine** in the dashboard lets you replay any past day (or week),
broken into automatically detected chapters
([screenshot](dashboard.md#time-machine)):

| Chapter Type | Triggered by |
|-------------|-------------|
| CODING | File saves, LOC activity |
| DEBUGGING | Error events, diagnostic activity |
| BUILD_DEPLOY | Build commands, git push |
| TEST_CYCLE | Test runner commands |
| GIT_COMMIT | Commit events |
| DB_INVESTIGATION | Database-related commands |
| REQUIREMENTS | Requirements work |
| DESIGN | Design work |
| MIXED | Mixed activity |

A new chapter starts after a 15-minute inactivity gap. A long chapter is also
split where the dominant activity changes.
