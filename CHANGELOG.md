# Changelog

All notable changes to the Axyome XM VS Code Extension are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [0.2.746] — 2026-07-27

### 🚀 Initial Public Release — Axyome XM

**Publisher**: `axyome` | **Website**: https://axyome.ai

#### Core Features
- **AI Memory Engine** — Persistent local memory for GitHub Copilot and MCP-compatible AI assistants. Recalls files edited, commands run, git commits, and development patterns across sessions
- **45 MCP Tools** — Full suite of `axm_*` tools: recall, search, decisions, feedback, observations, session summaries, skill tracking, wiki, achievements, and more
- **XM Wiki** — Persistent knowledge base that synthesises patterns, decisions, and errors from session data into searchable wiki pages (`axm_wiki_*` tools)
- **FTS5 Full-Text Search** — Fast keyword search across all memory tables using custom sql.js-fts5 WASM build
- **Semantic Search** — Vector embeddings via `@huggingface/transformers` (bge-small-en-v1.5, 384 dimensions) for meaning-based memory search
- **Hybrid Search** — Combined semantic + keyword search weighted scoring (vector 60%, text 25%, recency 15%)
- **Session Analytics** — ATI (AI Tool Index) metrics, productivity heatmap, tool usage breakdown
- **Achievement System** — 12 unlockable badges: Prompt Master, Flow State, Bug Slayer, Wiki Builder, Speed Coder, and more
- **Developer Intelligence** — DIP score, error forensics, file hotspot analysis, anti-pattern detection
- **Time Machine** — Replay any past coding session broken into chapters (Build, Test, Commit, Debug, Code)
- **Onboarding Dashboard** — Interactive 4-mission tutorial for first-time setup
- **Auto Memory Enhancement** — Automatic memory enrichment on session start, error detection, and session close

#### Platform Support
- Windows (win32-x64): ~38 MB VSIX
- Linux (linux-x64): ~38 MB VSIX  
- macOS (darwin-x64): ~36 MB VSIX

#### Privacy
- 100% local — no cloud, no telemetry, no external servers
- Terminal capture opt-in with automatic redaction of secrets
- All data stored in SQLite at `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\`

#### MCP Integration
- Auto-configured for VS Code 1.100+ (no manual `mcp.json` required)
- MCP server binary embedded in VSIX — no separate installation
- Compatible with GitHub Copilot and any MCP-enabled AI assistant

---

*For the full development changelog, see the [bx-iag repository](https://github.com/BI-Expertise/bx-iag).*
