# Installation Guide

## Prerequisites

| Requirement | Minimum | Notes |
|-------------|---------|-------|
| VS Code | 1.100.0+ | Minimum declared by the extension (`engines.vscode`) |
| OS Architecture | 64-bit | Windows, Linux, or macOS |
| Disk space | ~24-29 MB + database | VSIX size depends on platform; the database grows with use |
| GitHub Copilot | Any version | Required to use `axm_*` MCP tools |

---

## Availability

Axyome XM is **not listed on the VS Code Marketplace** or Open VSX at the time
of writing (checked 2026-09-26), and this repository has no GitHub Releases yet.
Install from a VSIX file provided by Axyome.

---

## Install from a VSIX File

Use the VSIX built for your platform:

| Platform | File |
|----------|------|
| Windows | `axyome-xm-win32-x64-<version>.vsix` |
| Linux | `axyome-xm-linux-x64-<version>.vsix` |
| macOS | `axyome-xm-darwin-x64-<version>.vsix` |

Install:
```bash
code --install-extension axyome-xm-<platform>-<version>.vsix --force
```

> **Important:** Install the VSIX that matches your OS. Installing the wrong platform VSIX will cause the native storage addon to fail.

---

## Verify Installation

After installing, verify the extension and MCP server are running:

**Method 1 - Command Palette:**
1. Press `Ctrl+Shift+P`
2. Run: **Axyome XM: Show Statistics**
3. A panel should appear showing event counts

**Method 2 - Copilot Chat:**
```
@copilot Is the Axyome XM memory server healthy?
```
Copilot will call `axm_health` and report the status.

**Method 3 - Activity Bar:**
- Look for the Axyome XM icon in the left sidebar (a house inside a circle)
- Click it - the Dashboard should open

**Method 4 - Keyboard:** `Ctrl+Shift+Alt+M` (`Cmd+Shift+Alt+M` on macOS) opens
the dashboard.

---

## Data Location

All extension data is stored locally. Nothing is sent anywhere.

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

Your activity is persisted locally in `axyome-xm.db` - a file you can back up, inspect,
or delete at any time. Installs that still have the older `memory-agent-events.db`
are renamed to `axyome-xm.db` automatically on startup.

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Extension not activating | VS Code < 1.100 | Update VS Code to 1.100+ |
| `axm_*` tools missing in Copilot | Extension not fully loaded | Full restart VS Code (not just reload window) |
| "cannot open database" error | AppData folder permissions | Check folder exists and is writable |
| `native addon` load error | Wrong platform VSIX installed | Uninstall and reinstall correct platform VSIX |
| "database is locked" error | VS Code locking DB | This is normal - the extension manages this automatically |
| MCP server shows "Not connected" | Slow startup | Wait 10s after VS Code loads; restart if persistent |

### Full Restart vs Reload

If Copilot tools don't appear after install, use a **full restart** - not just `Ctrl+Shift+P - Reload Window`:

- Windows/Linux: Close VS Code, reopen
- macOS: `Cmd+Q`, reopen

This ensures the MCP server process starts fresh.

---

## Updating

Because Axyome XM is not on the Marketplace yet, VS Code does not update it
automatically. Install the newer VSIX over the current one:

```bash
code --install-extension axyome-xm-<platform>-<version>.vsix --force
```

After updating, do a full restart of VS Code.

---

## Uninstalling

```bash
code --uninstall-extension axyome.axyome-xm
```

Your data at `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` is **not** removed automatically. Delete that folder manually if you want a clean uninstall.
