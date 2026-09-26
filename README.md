<div align="center">
  <h1>Axyome XM</h1>
  <p><strong>Your AI development memory. Local. Private. Permanent.</strong></p>

  <a href="https://marketplace.visualstudio.com/items?itemName=axyome.axyome-xm">
    <img src="https://img.shields.io/badge/VS%20Code-Marketplace-blue?logo=visualstudiocode" alt="VS Code Marketplace" />
  </a>
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey" alt="Platform" />
  <img src="https://img.shields.io/badge/MCP%20Tools-45-brightgreen" alt="MCP Tools" />
  <img src="https://img.shields.io/badge/privacy-100%25%20local-success" alt="Privacy" />
  <img src="https://img.shields.io/badge/license-Proprietary-red" alt="License" />
</div>

---

## What is Axyome XM?

Axyome XM is a VS Code extension that gives your AI assistant (GitHub Copilot, Claude, or any MCP-compatible tool) **persistent memory of everything you do as a developer** - files you edited, errors you fixed, decisions you made, and patterns you repeat.

Your AI assistant forgets everything between conversations. **Axyome XM remembers.**

> **Nothing leaves your machine.** All data lives in a local SQLite database.

---

## Demo

> *"What was that async error I fixed last week?"*

Within seconds, your AI assistant retrieves the exact file, error message, and the fix you applied - without you searching through logs or git blame.

-> [Full demo walkthrough](docs/demo.md)

---

## Key Features

| Feature | What it does |
|---------|-------------|
| **Persistent Memory** | Captures files, errors, commands, and commits across every session |
| **Hybrid Search** | Combines semantic vector search + FTS5 keyword search for best recall |
| **XM Wiki** | Auto-generates a searchable knowledge base from your sessions |
| **Session Analytics** | ATI score, productivity heatmap, tool usage breakdown |
| **Achievement System** | 12 developer badges: Prompt Master, Flow State, Bug Slayer, and more |
| **45 MCP Tools** | Full `axm_*` tool suite - ask AI to search, recall, and log for you |
| **Time Machine** | Replay any past coding session chapter by chapter |
| **100% Local** | No cloud, no telemetry, no external servers. Ever. |

---

## 30-Second Install

**Option 1 - VS Code Marketplace (recommended)**

1. Open VS Code - Extensions (`Ctrl+Shift+X`)
2. Search **Axyome XM**
3. Click **Install**

**Option 2 - Command line**

```bash
code --install-extension axyome.axyome-xm
```

-> [Detailed install guide with platform notes](docs/install.md)

---

## Quick Start

After installing, Axyome XM activates automatically:

1. Look for the **Axyome XM** icon in the Activity Bar (left sidebar)
2. Click it to open the Dashboard
3. Use the **Onboarding** tab to complete your first 4 missions in ~5 minutes
4. Ask Copilot: **"What did I work on today?"** - it now knows!

-> [Complete onboarding guide](docs/onboarding.md)

---

## Requirements

| Requirement | Minimum |
|-------------|---------|
| VS Code | 1.100.0+ |
| GitHub Copilot | Any (for MCP tool use) |
| Node.js | Not required - binary is embedded |

---

## Platform Support

| Platform | VSIX Size | Notes |
|----------|-----------|-------|
| Windows (win32-x64) | ~38 MB | Native better-sqlite3 |
| Linux (linux-x64) | ~38 MB | Native better-sqlite3 |
| macOS (darwin-x64) | ~36 MB | Native better-sqlite3 |

---

## MCP Tool Suite

Axyome XM ships with **45 MCP tools** (`axm_*`) automatically available in GitHub Copilot (VS Code 1.100+). No manual configuration required.

```
axm_recall_activity        - Search past work by query, file, or date
axm_search_sessions        - Semantic search through chat history
axm_get_session_summary    - Summarize what you worked on
axm_log_decision           - Remember a decision or preference
axm_find_similar_errors    - Check if you've seen this bug before
axm_wiki_query             - Search your personal knowledge wiki
axm_get_developer_intelligence - Full DIP score and recommendations
... and 38 more
```

-> [Full MCP tool reference](docs/mcp-tools-reference.md)

---

## Privacy

- All data stored locally at `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\`
- No network requests. No telemetry. No analytics sent anywhere.
- Terminal capture is **opt-in** with automatic secret redaction
- Clear all data anytime: **Axyome XM: Clear Captured Events**

-> [Full privacy policy](docs/privacy.md)

---

## Documentation

| Doc | Description |
|-----|-------------|
| [Install](docs/install.md) | Installation, platform notes, troubleshooting |
| [Onboarding](docs/onboarding.md) | Your first 10 minutes |
| [MCP Tools Reference](docs/mcp-tools-reference.md) | All 45 `axm_*` tools |
| [Tips & Tricks](docs/tips.md) | Power-user workflows |
| [FAQ](docs/faq.md) | Common questions answered |
| [Privacy](docs/privacy.md) | What is (and isn't) collected |
| [Demo Scenarios](docs/demo.md) | Concrete use cases |
| [Changelog](CHANGELOG.md) | Release history |

---

## Support

- [Bug Reports](https://github.com/BI-Expertise/axyome-xm/issues/new?template=bug_report.yml)
- [Feature Requests](https://github.com/BI-Expertise/axyome-xm/issues/new?template=feature_request.yml)
- [Questions](https://github.com/BI-Expertise/axyome-xm/issues/new?template=question.yml)
- [Discussions](https://github.com/BI-Expertise/axyome-xm/discussions)
- [Website](https://axyome.ai)

---

## License

Proprietary (c) [Axyome](https://axyome.ai) - All rights reserved.  
See [LICENSE](LICENSE) for details.
