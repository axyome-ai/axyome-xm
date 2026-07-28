# Privacy & Data Policy

## TL;DR

Axyome XM is **100% local**. Your data never leaves your machine. There are no servers, no telemetry, and no analytics transmitted anywhere.

---

## What We Collect (Locally, On Your Machine)

| Data Type | Stored locally | Transmitted | Opt-in required |
|-----------|:--------------:|:-----------:|:---------------:|
| File paths (not contents) | ✅ | ❌ Never | No (automatic) |
| Error messages | ✅ | ❌ Never | No (automatic) |
| Git commit messages | ✅ | ❌ Never | No (automatic) |
| Terminal commands | ✅ | ❌ Never | **Yes (opt-in)** |
| Copilot tool invocations | ✅ | ❌ Never | No (automatic) |
| File **contents** | ❌ Never stored | ❌ Never | — |
| Clipboard contents | ❌ Never stored | ❌ Never | — |
| Keystrokes | ❌ Never stored | ❌ Never | — |
| Passwords / secrets | ❌ Redacted | ❌ Never | — |

---

## Terminal Capture & Secret Redaction

Terminal capture is **opt-in** (disabled by default). When enabled:

Axyome XM automatically redacts values matching:
- Environment variables: `*_TOKEN`, `*_KEY`, `*_SECRET`, `*_PASSWORD`, `*_PASS`
- AWS credentials: `AKIA*`, `AWS_*`
- Connection strings: `postgresql://*:*@`, `mysql://*:*@`
- Bearer tokens: `Authorization: Bearer *`
- SSH private key patterns

Redacted values are replaced with `[REDACTED]` **before** storage. The original value is never written to disk.

To enable terminal capture:
1. `Ctrl+,` → Search `axyome terminal`
2. Enable **Axyome XM: Terminal Capture**

---

## Data Location

All data is stored in VS Code's extension globalStorage:

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

**Files in this directory:**

| File | Contents |
|------|----------|
| `memory-agent-events.db` | Main SQLite database — all captured events |
| `memory-agent-events.db-wal` | SQLite WAL journal (normal — handled automatically) |
| `backups/` | Up to 5 rolling automatic backups |

---

## Network Activity

The Axyome XM extension and its embedded MCP server make **zero outbound network requests** during normal operation.

The only network activity is:
- VS Code Marketplace: checking for extension updates (standard VS Code behavior, not initiated by Axyome XM)
- Semantic embeddings: computed locally using bundled WASM (`@huggingface/transformers` + bge-small-en-v1.5) — no API calls

You can verify this with a network monitor: the process `mcp-server-win-x64.exe` (or equivalent) makes no connections.

---

## Data Retention & Deletion

You are in full control of your data:

**Clear all events:**
```
Ctrl+Shift+P → Axyome XM: Clear Captured Events
```

**Manual full deletion:**
Delete the `memory-agent-events.db` file. A fresh database is created on next VS Code start.

**Backup:**
```
Ctrl+Shift+P → Axyome XM: Backup Database
```

**Restore from backup:**
```
Ctrl+Shift+P → Axyome XM: Restore Database Backup
```

---

## Third-Party Bundled Libraries

The extension bundles the following libraries. None make network requests:

| Library | Purpose | Network |
|---------|---------|---------|
| `better-sqlite3` | Local SQLite engine | ❌ None |
| `@huggingface/transformers` | Local WASM ML inference | ❌ None |
| `sql.js-fts5` | FTS5-enabled SQLite WASM | ❌ None |
| `@modelcontextprotocol/sdk` | MCP stdio communication | ❌ None (local stdio only) |

---

## MCP Server Security

The MCP server binary:
- Runs as a **local stdio process** — no open network ports
- Communicates only through VS Code's stdio pipe
- Reads/writes only within the extension's globalStorage directory
- Is embedded in the VSIX and **hash-validated** during build to prevent tampering
- Has no shell execution capabilities

---

## Vulnerability Disclosure

Found a privacy or security issue? Please report it responsibly.

**Do not file public issues for security vulnerabilities.**

Email: security@axyome.ai

See [SECURITY.md](../SECURITY.md) for the full disclosure policy.
