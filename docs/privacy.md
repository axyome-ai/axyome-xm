# Privacy & Data Policy

## Summary

- **Local-first.** Axyome XM persists your development activity locally on your machine.
- **Network.** The extension contacts the network only to:
  1. talk to `api.axyome.ai` while you are **signed in** (sign-in, licence check, device registration);
  2. on **Team & Enterprise** plans only, sync captured events and coding goals to the cloud.

  While you are signed out, it makes no calls to Axyome servers. There are no third-party
  analytics. The embedded MCP server makes no network calls at all.
- **Defaults.** File, git, terminal, editor, diagnostics, debug, output, AI chat and Claude Code
  capture are **on by default**. Each source has a setting to turn it off. Terminal commands
  pass through automatic secret redaction before they are stored.

This page describes version 0.2.842 of the extension.

---

## What Is Recorded (On Your Machine)

| Data type | Stored locally | Sent to the cloud | On by default |
|-----------|:--------------:|:-----------------:|:-------------:|
| File paths and file events | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureFiles`) |
| Error and warning messages | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureDiagnostics`) |
| Git commits and messages | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureGit`) |
| Terminal commands (redacted) | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureTerminal`) |
| AI chat sessions (Copilot) | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureChatSessions`) |
| Claude Code prompts and tool calls | Yes | Team & Enterprise sync only | Yes (`axyomeXM.capture.claudeCode.enabled`) |
| File **contents** | Not read from disk by capture. Excerpts are stored when an AI assistant's tool call or chat reply contains them (tool arguments up to 8 KB, tool results up to 512 bytes, chat code blocks) | Team & Enterprise sync only | With the AI capture sources above |
| Clipboard contents | Never read | Never | — |
| Keystrokes | Only counted, never stored | Never | — |
| Passwords / secrets in terminal commands | Redacted before storage | Never | — |

---

## Terminal Capture & Secret Redaction

Terminal capture is **on by default**. Before a command is stored, Axyome XM replaces values
matching its redaction patterns with `[REDACTED]`. The default patterns cover:
- Assignments to names containing `api_key`, `apikey`, `secret`, `password`, `token`,
  `credential` or `auth` (for example `API_KEY=...`, `password: ...`)
- Bearer tokens (`bearer <token>`)
- Cloud and registry variables starting `aws_`, `azure_`, `gcp_`, `github_` or `npm_`

You can add your own patterns with the `axyomeXM.terminalRedactPatterns` setting.

To turn terminal capture off:
1. `Ctrl+,` -> search `axyome terminal`
2. Uncheck **Axyome XM: Capture Terminal**

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
| `axyome-xm.db` | Your activity, persisted locally |
| `axyome-xm.db-wal`, `axyome-xm.db-shm` | Journal files (normal - handled automatically) |
| `backups/` | Up to 5 rolling automatic backups |

---

## Network Activity

| When | Destination | What |
|------|-------------|------|
| Signed in, any plan | `api.axyome.ai` | Sign-in and token refresh, profile and licence check, device registration |
| Team & Enterprise plans | `api.axyome.ai` | Cloud sync of captured events (every 15 minutes) and of coding goals |
| You click a link | `app.axyome.ai` (in your browser) | Sign-in, pricing, billing and contact-sales pages |

Signed out, the extension makes no calls to Axyome servers. There are no third-party analytics.
Search runs locally on keyword indexes. VS Code itself may check the
Marketplace for updates; that is standard VS Code behaviour, not Axyome XM.

---

## Data Retention & Deletion

You are in full control of your data:

**Clear all events:**
```
Ctrl+Shift+P - Axyome XM: Clear Captured Events
```

**Manual full deletion:**
Delete the `axyome-xm.db` file. A fresh database is created on next VS Code start.

**Backup:**
```
Ctrl+Shift+P - Axyome XM: Backup Database
```

**Restore from backup:**
```
Ctrl+Shift+P - Axyome XM: Restore Database Backup
```

---

## Third-Party Bundled Libraries

| Library | Purpose | Network |
|---------|---------|---------|
| `@modelcontextprotocol/sdk` | MCP stdio communication | None (local stdio only) |
| Local storage engine | Persists your activity locally | None |

---

## MCP Server Security

The MCP server binary:
- Runs as a **local stdio process** - no open network ports
- Makes no network calls
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
