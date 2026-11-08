<div align="center">
  <h1>Axyome XM</h1>
  <p><strong>Your AI forgets. Axyome XM remembers.</strong></p>
  <p>The black box flight recorder for AI-assisted coding.</p>

  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey" alt="Platform" />
  <img src="https://img.shields.io/badge/MCP%20Tools-54-brightgreen" alt="MCP Tools" />
  <img src="https://img.shields.io/badge/privacy-local--first-success" alt="Privacy" />
  <img src="https://img.shields.io/badge/license-Proprietary-red" alt="License" />
</div>

---

## What is Axyome XM?

- **Remembers.** The files you edited, the errors you hit, the terminal commands you ran, your commits, and your Copilot and Claude Code sessions. Search it by keyword, or replay any past coding day in Time Machine.
- **Local.** Your activity is recorded and stored on your own machine. No third-party analytics. See [Privacy](#privacy).
- **Works with Copilot and Claude Code.** Copilot recalls your history through the Axyome XM MCP server, which the extension registers in VS Code. Claude Code and other MCP clients can connect to the same server.

---

## Demo

<a href="https://www.youtube.com/watch?v=XEoMJM7y6J8">
  <img src="docs/images/demo-video.png" alt="Watch the 2.5-minute Axyome XM product demo on YouTube" width="720" />
</a>

▶ **[Watch the 2.5-minute product demo](https://www.youtube.com/watch?v=XEoMJM7y6J8)**: live product, real data, recorded in VS Code.

> *"What was that async error I fixed last week?"*

Within seconds, your AI assistant retrieves the exact file, error message, and the fix you applied - without you searching through logs or git blame.

-> [Full demo walkthrough](docs/demo.md)

---

## Key Features

| Feature | What it does |
|---------|-------------|
| **Persistent Memory** | Captures files, errors, commands, and commits across every session |
| **Keyword Search** | FTS5 keyword search over activity, decisions and chat history, ranked by match and recency |
| **XM Wiki** | Auto-generates a searchable knowledge base from your sessions |
| **Session Analytics** | ATI score, productivity heatmap, tool usage breakdown |
| **Achievement System** | 12 badges: Prompt Master, Flow State, Week Streak, and more |
| **54 MCP Tools** | Full `axm_*` tool suite - ask AI to search, recall, and log for you |
| **Time Machine** | Replay any past coding day chapter by chapter |
| **Copilot + Claude Code** | Dashboard compares both assistants side by side |
| **Local-first** | Your data stays on your machine. Nothing is sent anywhere unless you sign in — see [Privacy](#privacy). |

---

## Install

Axyome XM is **not listed on the VS Code Marketplace** or Open VSX yet at the time of writing
(checked 2026-10-18). Install the VSIX for your platform:

```bash
code --install-extension axyome-xm-win32-x64-<version>.vsix --force
```

-> [Detailed install guide with platform notes](docs/install.md)

---

## Quick Start

After installing, Axyome XM activates automatically:

1. **Choose what is recorded.** A panel lists every source with what it stores; nothing is
   recorded until you press **Start recording** ("Recommended" turns them all on).
2. **Follow "Get started with Axyome XM"** (VS Code's Welcome page, or **Welcome: Open
   Walkthrough...**): it checks that Copilot can reach the Axyome XM MCP server and imports your
   own commits of the last 90 days, so memory has something to recall on day one.
3. **Ask Copilot** in Agent mode: **"What did I work on this week?"** The walkthrough's last step
   opens the chat with the question filled in.
4. Open the Dashboard from the **Axyome XM** icon in the Activity Bar (or `Ctrl+Shift+Alt+M`).
   **Axyome: Start Onboarding** offers a quick or full tour of the features.

-> [Complete onboarding guide](docs/onboarding.md)

---

## Tutorials

Step-by-step guides that end with something working.

| Tutorial | For | Time |
|----------|-----|------|
| [Vibe coding with Copilot and Axyome XM](docs/tutorials/vibe-coding-with-copilot.md) | Business users, no coding experience | 30 min |
| [A small tool built over a week](docs/tutorials/tool-over-a-week.md) | Business users who did the first tutorial | 3 × 30 min |
| [Hand your prototype to developers](docs/tutorials/handover-to-developers.md) | Business users with a working prototype | 45 min |
| [Debug with memory](docs/tutorials/debug-with-memory.md) | Junior developers | 30 min |
| [A feature across three days](docs/tutorials/feature-across-three-days.md) | Intermediate developers | 3 × 30 min |
| [One memory for Copilot and Claude Code](docs/tutorials/one-memory-for-copilot-and-claude-code.md) | Senior developers using Claude Code | 45 min |

-> [All tutorials](docs/tutorials/README.md)

---

## Dashboard

![Axyome XM dashboard - Home tab](docs/images/dashboard-home.png)

8 tabs: Home, Activity, AI, Quality, Intel, Wellness, Replay and System.

-> [Dashboard tour with screenshots of every tab](docs/dashboard.md)

---

## Requirements

| Requirement | Minimum |
|-------------|---------|
| VS Code | 1.139.0+ |
| GitHub Copilot | Any (for MCP tool use) |
| Node.js | Not required - binary is embedded |

---

## Platform Support

| Platform | VSIX Size | Notes |
|----------|-----------|-------|
| Windows (win32-x64) | ~24 MB | Native better-sqlite3 |
| Linux (linux-x64) | ~29 MB | Native better-sqlite3 |
| macOS Intel (darwin-x64) | ~26 MB | Native better-sqlite3 |
| macOS Apple Silicon (darwin-arm64) | ~25 MB | Native better-sqlite3; ad-hoc signed MCP server |

Sizes measured on the 0.2.867 build.

---

## MCP Tool Suite

Axyome XM ships with **54 MCP tools** (`axm_*`) served by an embedded MCP
server, so GitHub Copilot can use them without manual setup.

**Tool diet.** To keep every request small, the server lists 11 core tools by
default (recall, session summary, context snapshot, error forensics, similar
errors, decisions, observations, hybrid search, health and tool discovery). Set
`axyomeXM.mcp.toolset` to `all` to list all 54. Tools that are not listed still
run when called by name, and `axm_list_available_tools` names what is hidden.

**What it writes into your workspace.** Nothing without asking. The extension registers its MCP
server with VS Code, so Copilot lists **Axyome XM** without a `.vscode/mcp.json` in your
repository. It then offers to add `AGENTS.md`, `.github/agents/memory.md` and recommended VS Code
settings (Configure All / Choose... / Skip / Don't Ask Again); skipping or dismissing the prompt
writes nothing. **Axyome XM: Configure Workspace for AI Memory** runs the same setup later.

```
axm_recall_activity        - Search past work by query, file, or date
axm_search_sessions        - Keyword search through chat history
axm_get_session_summary    - Summarize what you worked on
axm_log_decision           - Remember a decision or preference
axm_find_similar_errors    - Check if you've seen this bug before
axm_wiki_query             - Search your personal knowledge wiki
axm_get_developer_intelligence - Full DIP score and recommendations
... and 47 more
```

-> [Full MCP tool reference](docs/mcp-tools-reference.md)

---

## Plans

| Plan | Price | History you can see |
|---|---|---|
| Free | $0 | The last 30 days |
| Pro | $9/month | All of it |

Every feature works on every plan, and a plan never deletes your data — it only changes how much
history you can see. Axyome XM runs as a 30-day preview first; after that, a free account is
needed to keep using it. Details: [app.axyome.ai/pricing](https://app.axyome.ai/pricing).

---

## Privacy

- **100% local storage.** On Free and Pro, your activity is stored only on your computer.
- **Nothing is recorded until you choose.** On first run a panel lists every capture source (Claude Code,
  Copilot chat and agent edits, files, git, terminal, editor, selections, problems, debug, tasks, coding
  time) with one line saying what it stores. **Recommended** turns them all on, every source has its own
  switch, and nothing is recorded until you press **Start recording**. Change it any time with
  **Axyome XM: Review Capture Settings**.
- **No account, no network.** Without an account, Axyome XM makes no calls to Axyome servers. There are
  no third-party analytics, and the built-in MCP server makes no network calls at all.
- **Secrets are redacted.** Terminal commands and editor selections pass through automatic secret
  redaction before they are stored.

### What is recorded, on your computer only

| Data | Stored | In "Recommended" |
|------|:------:|:----------------:|
| File paths and file events | Yes | Yes (`axyomeXM.captureFiles`) |
| Error and warning messages from the Problems panel | Yes | Yes (`axyomeXM.captureDiagnostics`) |
| Git commits and messages | Yes | Yes (`axyomeXM.captureGit`) |
| Your own commits of the last 90 days, read once ([below](#git-history-import)) | Yes | With Git, on a new install |
| Terminal commands (redacted) | Yes | Yes (`axyomeXM.captureTerminal`) |
| Editor selections (redacted) | Yes | Yes (`axyomeXM.captureSelectedText`) |
| Copilot chat sessions | Yes | Yes (`axyomeXM.captureChatSessions`) |
| Claude Code prompts and tool calls | Yes | Yes (`axyomeXM.capture.claudeCode.enabled`) |
| File **contents** | Not read from disk, with one exception: once, on a new install, a copy of four project files is saved so your assistant has context from day one (`README.md`, `AGENTS.md`, `.github/copilot-instructions.md`, `package.json`). Excerpts are kept when an AI assistant's tool call or chat reply contains them (tool arguments up to 8 KB, tool results up to 512 bytes, chat code blocks) | The four files: once you press **Start recording**. Excerpts: with the AI sources above |
| Clipboard | Never read | — |
| Keystrokes | Only counted, never stored | — |

Before you choose, nothing in this table is recorded.

### Secret redaction

Before a terminal command or an editor selection is stored, values matching the redaction patterns
are replaced with `[REDACTED]`. The default patterns cover assignments to names containing `api_key`,
`apikey`, `secret`, `password`, `token`, `credential` or `auth` (for example `API_KEY=...`,
`password: ...`), bearer tokens, and variables starting `aws_`, `azure_`, `gcp_`, `github_` or `npm_`.
Add your own with the `axyomeXM.terminalRedactPatterns` setting. To stop terminal capture, switch
**Terminal** off in **Axyome XM: Review Capture Settings**.

### Git history import

So that memory has something to recall on day one, a new install with **Git** on reads your own
commits of the last 90 days once, after you choose what is recorded: hash, message, time, branch and
per-file line counts. Commits by other authors are left out, and imported commits are not counted as
work done with AI. Set `axyomeXM.history.gitDays` to `0` to skip it, or change the number of days;
**Axyome XM: Import Git History** runs it on demand.

### Where your data lives

| OS | Folder |
|----|--------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

It holds the database `axyome-xm.db` (with its journal files) and up to 5 rolling automatic backups.

### Network

| When | Destination | What |
|------|-------------|------|
| You are signed in | `api.axyome.ai` | Sign-in, plan check (about every 4 hours), device registration (its name, platform and version numbers) |
| You click a link | `app.axyome.ai`, in your browser | Sign-in, pricing and billing pages |

Signed out, Axyome XM makes no calls to Axyome servers. VS Code itself may check the Marketplace for
updates; that is VS Code, not Axyome XM.

### Your data, your control

- **Take a copy:** **Axyome XM: Export All My Data** writes every table to JSON and Markdown in a folder
  you choose.
- **Delete everything:** **Axyome XM: Delete All My Data** (type `DELETE` to confirm) deletes the
  database contents, backups and queued events on this computer. Uninstalling the extension alone does
  not remove them; the [uninstall and data removal guide](docs/uninstall.md) lists what is stored and
  where.
- **Clear captured events only:** **Axyome XM: Clear Captured Events**.

### Reporting a security issue

Please do not open a public issue for a security problem. Email **security@axyome.ai** with a
description, the steps to reproduce and the impact.

---

## Documentation

| Doc | Description |
|-----|-------------|
| [Install](docs/install.md) | Installation, platform notes, troubleshooting |
| [Onboarding](docs/onboarding.md) | Your first 10 minutes |
| [Tutorials](docs/tutorials/README.md) | Step-by-step guides, starting with vibe coding for business users |
| [Dashboard Tour](docs/dashboard.md) | Every tab, with screenshots |
| [MCP Tools Reference](docs/mcp-tools-reference.md) | All 54 `axm_*` tools |
| [Tips & Tricks](docs/tips.md) | Power-user workflows |
| [FAQ](docs/faq.md) | Common questions answered |
| [Privacy](#privacy) | What is (and isn't) collected |
| [Uninstall and data removal](docs/uninstall.md) | Export, delete everything, uninstall |
| [Demo Scenarios](docs/demo.md) | Concrete use cases |
| [Changelog](CHANGELOG.md) | Release history |

---

## Support

- [Bug Reports](https://github.com/axyome-ai/axyome-xm/issues/new?template=bug_report.yml)
- [Feature Requests](https://github.com/axyome-ai/axyome-xm/issues/new?template=feature_request.yml)
- [Questions](https://github.com/axyome-ai/axyome-xm/issues/new?template=question.yml)
- [Website](https://axyome.ai)

---

## License

Proprietary (c) [Axyome](https://axyome.ai) - All rights reserved.  
See [LICENSE](LICENSE) for details. Third-party components and their licences are listed in
`THIRD-PARTY-NOTICES.txt`, shipped with the extension.
