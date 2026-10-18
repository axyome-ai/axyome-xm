# Privacy & Data Policy

## Summary

- **Local-first.** Axyome XM persists your development activity locally on your machine.
- **Nothing is recorded until you choose.** On first run a panel lists every capture source with one
  line saying what it stores. **Recommended** turns them all on, every source has its own switch, and
  nothing is recorded until you press **Start recording**. Change it any time with
  **Axyome XM: Review Capture Settings**.
- **Network.** The extension contacts the network only to:
  1. talk to `api.axyome.ai` while you are **signed in** (sign-in, licence check, device registration);
  2. on **Team & Enterprise** plans only, sync captured events and coding goals to the cloud.

  While you are signed out, it makes no calls to Axyome servers. There are no third-party
  analytics. The embedded MCP server makes no network calls at all.
- **Redaction.** Terminal commands and editor selections pass through automatic secret redaction
  before they are stored.

This page describes version 0.2.868 of the extension.

---

## What Is Recorded (On Your Machine)

| Data type | Stored locally | Sent to the cloud | In "Recommended" |
|-----------|:--------------:|:-----------------:|:----------------:|
| File paths and file events | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureFiles`) |
| Error and warning messages | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureDiagnostics`) |
| Git commits and messages | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureGit`) |
| Your own commits of the last 90 days, read once ([below](#git-history-import)) | Yes | Team & Enterprise sync only | With Git, on a new install |
| Terminal commands (redacted) | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureTerminal`) |
| Editor selections (redacted) | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureSelectedText`) |
| AI chat sessions (Copilot) | Yes | Team & Enterprise sync only | Yes (`axyomeXM.captureChatSessions`) |
| Claude Code prompts and tool calls | Yes | Team & Enterprise sync only | Yes (`axyomeXM.capture.claudeCode.enabled`) |
| File **contents** | Not read from disk by capture. Excerpts are stored when an AI assistant's tool call or chat reply contains them (tool arguments up to 8 KB, tool results up to 512 bytes, chat code blocks) | Team & Enterprise sync only | With the AI capture sources above |
| Clipboard contents | Never read | Never | — |
| Keystrokes | Only counted, never stored | Never | — |
| Passwords / secrets in terminal commands and selections | Redacted before storage | Never | — |

Before you choose, nothing in this table is recorded.

---

## Terminal Capture & Secret Redaction

Terminal capture is part of **Recommended**. Before a command or an editor selection is stored, Axyome
XM replaces values matching its redaction patterns with `[REDACTED]`. The default patterns cover:
- Assignments to names containing `api_key`, `apikey`, `secret`, `password`, `token`,
  `credential` or `auth` (for example `API_KEY=...`, `password: ...`)
- Bearer tokens (`bearer <token>`)
- Cloud and registry variables starting `aws_`, `azure_`, `gcp_`, `github_` or `npm_`

You can add your own patterns with the `axyomeXM.terminalRedactPatterns` setting.

To turn terminal capture off, run **Axyome XM: Review Capture Settings** and switch **Terminal** off,
or `Ctrl+,` -> search `axyome terminal` and uncheck **Axyome XM: Capture Terminal**.

---

## Git History Import

So that memory has something to recall on day one, a **new install** with **Git** on reads your own
commits of the last 90 days once, after you choose what is recorded: hash, message, time, branch and
per-file line counts. Commits by other authors are left out.

- It runs in the background for every repository open in VS Code, and never twice for the same commit.
- Imported commits answer recall questions and fill the commit charts. They never unlock achievements
  and are not counted as work done with AI.
- Set `axyomeXM.history.gitDays` to `0` to skip it, or change the number of days.
  **Axyome XM: Import Git History** runs it on demand.

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

The full list, and how to remove everything, is in the [uninstall and data removal guide](uninstall.md).

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

**Take a copy of everything:**
```
Ctrl+Shift+P - Axyome XM: Export All My Data
```
Every table with rows is written to JSON and Markdown in a folder you choose.

**Delete everything:**
```
Ctrl+Shift+P - Axyome XM: Delete All My Data
```
Type `DELETE` to confirm. It deletes the database contents, backups and queued events on this
computer. Uninstalling the extension alone does not remove them; see the
[uninstall and data removal guide](uninstall.md).

**Clear captured events only** (file, git, terminal, editor and imported-session events):
```
Ctrl+Shift+P - Axyome XM: Clear Captured Events
```

**Backup and restore:**
```
Ctrl+Shift+P - Backup Database
Ctrl+Shift+P - List/Restore Database Backups
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
