<div align="center">
  <h1>Axyome XM</h1>
  <p><strong>The black box flight recorder for AI-assisted coding.</strong></p>

  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey" alt="Platform" />
  <img src="https://img.shields.io/badge/MCP%20Tools-54-brightgreen" alt="MCP Tools" />
  <img src="https://img.shields.io/badge/privacy-local--first-success" alt="Privacy" />
  <img src="https://img.shields.io/badge/license-Proprietary-red" alt="License" />
</div>

---

## What is Axyome XM?

Axyome XM is a **black box flight recorder for AI-assisted coding**. Every session is captured as a full forensic trail of the files touched, prompts given, errors hit, commands run and commits made. That gives you traceability from your code back to where it came from: you can see which session changed a file, which assistant (Copilot or Claude Code) made the change, and the prompts behind it. Time Machine replays any past coding day chapter by chapter. Hybrid semantic and keyword search pulls back any moment on demand, and the auto-generated XM Wiki turns your history into a searchable knowledge base.

Axyome XM also **looks after the developer**. Session analytics and the productivity heatmap show your working rhythm: when you reach flow state, how long your sessions run, and when late nights or marathon stretches start adding up. Achievement badges mark your milestones and streaks. There are 54 MCP tools, and Axyome XM is **local-first**: your activity is recorded and stored on your own machine.

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
| **Forensic Trail** | Every session captured: the files touched, prompts given, errors hit, commands run and commits made |
| **Traceability** | See which session changed a file, which assistant (Copilot or Claude Code) made the change, and the prompts behind it |
| **Time Machine** | Replay any past coding day chapter by chapter |
| **Hybrid Search** | Semantic + keyword search pulls back any moment on demand |
| **XM Wiki** | Auto-generated from your sessions: your history as a searchable knowledge base |
| **Developer Wellness** | Session analytics and a productivity heatmap show your rhythm: flow state, session length, late nights and marathon stretches |
| **Achievement Badges** | 12 badges mark your milestones and streaks: Flow State, Week Streak, Prompt Master and more |
| **54 MCP Tools** | Full `axm_*` tool suite - your AI assistant can search, recall and log for you |
| **Local-first** | Your activity is recorded and stored on your own machine |

---

## Install

Axyome XM is **not listed on the VS Code Marketplace** at the time of writing
(checked 2026-09-26). Install the VSIX for your platform:

```bash
code --install-extension axyome-xm-win32-x64-<version>.vsix --force
```

-> [Detailed install guide with platform notes](docs/install.md)

---

## Quick Start

After installing, Axyome XM activates automatically:

1. Look for the **Axyome XM** icon in the Activity Bar (left sidebar)
2. Click it to open the Dashboard (or press `Ctrl+Shift+Alt+M`)
3. Run **Axyome: Start Onboarding** from the Command Palette for a 3-step quick tour
4. Ask Copilot: **"What did I work on today?"** - it now knows!

-> [Complete onboarding guide](docs/onboarding.md)

---

## Dashboard

![Axyome XM dashboard - Home tab](docs/images/dashboard-home.png)

8 tabs: Home, Activity, AI, Quality, Intel, Wellness, Replay and System.

-> [Dashboard tour with screenshots of every tab](docs/dashboard.md)

---

## Requirements

| Requirement | Minimum |
|-------------|---------|
| VS Code | 1.100.0+ |
| GitHub Copilot | Any (for MCP tool use) |
| Node.js | Not required - binary is embedded |

---

## Platform Support

| Platform | VSIX Size |
|----------|-----------|
| Windows (win32-x64) | ~31 MB |
| Linux (linux-x64) | ~45 MB |
| macOS (darwin-x64) | ~36 MB |

Sizes measured on the 0.2.824 build.

---

## MCP Tool Suite

Axyome XM ships with **54 MCP tools** (`axm_*`) served by an embedded MCP
server, so GitHub Copilot can use them without manual setup.

**What it writes into your workspace.** On first install it configures the open
workspace without asking: `.vscode/mcp.json` (the MCP server entry),
`AGENTS.md`, `.github/agents/memory.md` and recommended VS Code settings. In
other workspaces it asks first (Configure All / Choose... / Skip / Don't Ask
Again). Dismissing that prompt still creates `.vscode/mcp.json`.

```
axm_recall_activity        - Search past work by query, file, or date
axm_search_sessions        - Semantic search through chat history
axm_get_session_summary    - Summarize what you worked on
axm_log_decision           - Remember a decision or preference
axm_find_similar_errors    - Check if you've seen this bug before
axm_wiki_query             - Search your personal knowledge wiki
axm_get_developer_intelligence - Full DIP score and recommendations
... and 47 more
```

-> [Full MCP tool reference](docs/mcp-tools-reference.md)

---

## Privacy

- Local-first: data is stored at `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\`
- No third-party analytics. Cloud sync only on Team & Enterprise plans.
- Terminal, chat and Claude Code capture are **on by default**, with automatic secret redaction for terminal commands. Turn any source off in settings.
- Clear all data anytime: **Axyome XM: Clear Captured Events**

-> [Full privacy policy](docs/privacy.md)

---

## Documentation

| Doc | Description |
|-----|-------------|
| [Install](docs/install.md) | Installation, platform notes, troubleshooting |
| [Onboarding](docs/onboarding.md) | Your first 10 minutes |
| [Dashboard Tour](docs/dashboard.md) | Every tab, with screenshots |
| [MCP Tools Reference](docs/mcp-tools-reference.md) | All 54 `axm_*` tools |
| [Tips & Tricks](docs/tips.md) | Power-user workflows |
| [FAQ](docs/faq.md) | Common questions answered |
| [Privacy](docs/privacy.md) | What is (and isn't) collected |
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
See [LICENSE](LICENSE) for details.
