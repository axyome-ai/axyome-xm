# Frequently Asked Questions

## General

### Does Axyome XM send any data to the cloud?

**No.** Axyome XM is 100% local-first. No data ever leaves your machine. There are no network requests, no telemetry, and no external servers involved — the extension and its embedded MCP server are entirely offline.

---

### What data does it collect?

Axyome XM captures development events from VS Code:

| Data | Captured | Notes |
|------|----------|-------|
| File paths (not contents) | ✅ | Language, LOC delta |
| Error messages | ✅ | File, line, severity |
| Git commits | ✅ | Message, branch, files changed |
| Copilot tool invocations | ✅ | Tool name, for analytics |
| Terminal commands | ✅ opt-in | With automatic secret redaction |

It does **not** capture: file contents, clipboard, keystrokes, passwords, or any data outside VS Code's event system.

---

### Will it slow down VS Code?

No. Axyome XM uses an async write queue and in-memory buffering. The SQLite database runs in WAL (Write-Ahead Logging) mode for high throughput without blocking the editor.

Event capture adds less than 2ms latency to file save operations.

---

### Where is my data stored?

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

---

### How do I delete all my data?

**Via Command Palette:** `Ctrl+Shift+P` → **Axyome XM: Clear Captured Events**

**Manually:** Delete the `memory-agent-events.db` file at the path above. The extension creates a fresh database on next start.

---

### Can I back up my data?

Yes. `Ctrl+Shift+P` → **Axyome XM: Backup Database**

The extension also maintains 5 rolling automatic backups triggered on version changes.

---

## MCP Tools

### Do I need to configure anything for Copilot?

No. In VS Code 1.100+, Axyome XM automatically registers its MCP server. The 45 `axm_*` tools appear in GitHub Copilot without any manual `mcp.json` setup.

---

### Which AI assistants support `axm_*` tools?

Any MCP-compatible assistant:
- **GitHub Copilot** (VS Code 1.100+) — no config needed
- **Claude** (via MCP client configuration)
- Any other tool supporting the [Model Context Protocol](https://modelcontextprotocol.io)

---

### Why does Copilot say it can't find the `axm_*` tools?

1. Ensure VS Code is **1.100 or newer** (`Help → About`)
2. Do a **full restart** of VS Code (close and reopen — not just `Reload Window`)
3. Check the extension is enabled: Extensions panel → search "Axyome XM" → ensure it's not disabled
4. Run `Ctrl+Shift+P` → **Axyome XM: Show Statistics** to verify the server is running
5. If the server shows an error, check the Output panel: `View → Output → Axyome XM`

---

### How is the MCP server started?

The MCP server is an embedded binary (`mcp-server-win-x64.exe` / `mcp-server-linux-x64` / `mcp-server-darwin-x64`) that starts as a local stdio process when VS Code launches. It binds to no network ports — communication is entirely through standard input/output.

---

## Storage & Performance

### How large does the database grow?

| Usage Level | Daily events | Monthly DB size |
|------------|-------------|----------------|
| Light (occasional use) | ~200 events | ~10 MB |
| Medium (full workday) | ~2,000 events | ~100 MB |
| Heavy (intensive dev) | ~10,000+ events | ~500 MB |

---

### Can I move my data to a new machine?

Yes. Copy `memory-agent-events.db` from the globalStorage path on your old machine to the same path on your new machine. The extension picks it up on next start.

---

### Does it work without an internet connection?

Yes, entirely. All features — capture, search, recall, MCP tools, semantic embeddings, FTS5 search — work fully offline. There are no cloud dependencies.

---

## Features

### What is the XM Wiki?

The XM Wiki is a personal, searchable knowledge base auto-generated from your coding sessions. It stores:

- **Entities** — Services, files, tools, packages you interact with
- **Errors** — Documented bugs with proposed resolutions
- **Patterns** — Recurring code patterns and architectural decisions
- **Decisions** — Architecture decision records (ADRs)
- **Concepts** — Cross-session synthesized knowledge

Build it by running: `@copilot Ingest this session into the wiki.`

---

### What are the Achievement Badges?

12 developer badges you unlock by hitting milestones:

| Badge | Unlock Condition |
|-------|----------------|
| 🚀 Prompt Master | 50 MCP tool calls |
| 🌊 Flow State | 3-hour uninterrupted coding session |
| 🐛 Bug Slayer | 10 errors resolved |
| 📚 Wiki Builder | 20 wiki pages created |
| ⚡ Speed Coder | 500 LOC written in one day |
| 🔍 Memory Master | 100 recall queries |
| 📝 Decision Maker | 10 decisions logged |
| 🏗️ Architect | 5 ADRs created |
| 🧪 Test Champion | 50 test files modified |
| 🔄 Consistency | 7-day coding streak |
| 🎯 Focus | 5 debugging sessions resolved same day |
| 🌟 All-Rounder | All other badges unlocked |

---

### What is the DIP Score?

The Developer Intelligence Platform score — a composite metric across 4 pillars:

| Pillar | What it measures |
|--------|-----------------|
| **Velocity** | LOC/day, commits/day, session frequency |
| **Quality** | Error rate, bug density, time-to-fix trends |
| **Efficiency** | AI tool usage ratio, pattern reuse rate |
| **Learning** | New patterns discovered, skill growth over time |

Ask: `@copilot How am I doing this week?`

---

### What is the ATI Score?

**AI Tool Index** — measures how effectively you use AI assistance. It's the ratio of tools-per-prompt: higher means you're getting more value from each AI interaction.

Ask: `@copilot Show my session analytics and ATI score.`

---

### What is the Time Machine?

The Time Machine tab lets you replay any past coding session, broken into automatically detected chapters:

| Chapter Type | Triggered by |
|-------------|-------------|
| 🏗️ CODING | File saves, LOC activity |
| 🐛 DEBUGGING | Error events, diagnostic activity |
| 🚀 BUILD_DEPLOY | Build commands, git push |
| 🔬 TEST_CYCLE | Test runner commands |
| 💾 GIT_COMMIT | Commit events |
| 🔍 DB_INVESTIGATION | Database-related commands |
| 🔀 MIXED | Mixed activity |

Chapters are separated by 15-minute inactivity gaps.
