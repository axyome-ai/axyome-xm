# Installation Guide

## Prerequisites

| Requirement | Minimum | Notes |
|-------------|---------|-------|
| VS Code | 1.100.0+ | Required for MCP auto-configuration |
| OS Architecture | 64-bit | Windows, Linux, or macOS |
| Disk space | ~40 MB | For VSIX + SQLite database |
| GitHub Copilot | Any version | Required to use `axm_*` MCP tools |

---

## Option 1 - VS Code Marketplace (Recommended)

1. Open VS Code
2. Press `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (macOS)
3. Search for **Axyome XM**
4. Click **Install**
5. VS Code will prompt to reload - click **Reload**

---

## Option 2 - Command Line

```bash
code --install-extension axyome.axyome-xm
```

---

## Option 3 - VSIX File (Offline / Beta Versions)

Download the platform-specific VSIX from [Releases](https://github.com/BI-Expertise/axyome-xm/releases):

| Platform | File |
|----------|------|
| Windows | `axyome-xm-<version>-win32-x64.vsix` |
| Linux | `axyome-xm-<version>-linux-x64.vsix` |
| macOS | `axyome-xm-<version>-darwin-x64.vsix` |

Install:
```bash
code --install-extension axyome-xm-<version>-<platform>.vsix --force
```

>  **Important:** Install the VSIX that matches your OS. Installing the wrong platform VSIX will cause the native SQLite addon to fail.

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
- Look for the Axyome XM icon in the left sidebar (brain icon)
- Click it - the Dashboard should open

---

## Data Location

All extension data is stored locally. Nothing is sent anywhere.

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |

The primary database is `memory-agent-events.db`  a SQLite file you can back up, inspect, or delete at any time.

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Extension not activating | VS Code < 1.100 | Update VS Code to 1.100+ |
| `axm_*` tools missing in Copilot | Extension not fully loaded | Full restart VS Code (not just reload window) |
| `SQLITE_CANTOPEN` error | AppData folder permissions | Check folder exists and is writable |
| `native addon` load error | Wrong platform VSIX installed | Uninstall and reinstall correct platform VSIX |
| `SQLITE_BUSY` error | VS Code locking DB | This is normal - the extension manages this automatically |
| MCP server shows "Not connected" | Slow startup | Wait 10s after VS Code loads; restart if persistent |

### Full Restart vs Reload

If Copilot tools don't appear after install, use a **full restart**  not just `Ctrl+Shift+P - Reload Window`:

- Windows/Linux: Close VS Code, reopen
- macOS: `Cmd+Q`, reopen

This ensures the MCP server process starts fresh.

---

## Updating

Axyome XM updates automatically via the VS Code marketplace. To update manually:

```bash
code --install-extension axyome.axyome-xm --force
```

After updating, do a full restart of VS Code.

---

## Uninstalling

```bash
code --uninstall-extension axyome.axyome-xm
```

Your data at `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` is **not** removed automatically. Delete that folder manually if you want a clean uninstall.
