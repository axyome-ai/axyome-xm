# Installation Guide

## Prerequisites

| Requirement | Minimum | Notes |
|-------------|---------|-------|
| VS Code | 1.123.0+ | Minimum declared by the extension (`engines.vscode`) |
| OS Architecture | 64-bit | Windows, Linux, or macOS (Intel or Apple Silicon) |
| Disk space | ~25-30 MB + database | The download depends on your platform; the database grows with use |
| GitHub Copilot or Claude Code | Any version | At least one, to use your memory from chat |
| Codex | Any version | Optional: its sessions are recorded and shown in the dashboard |

---

## Install from the VS Code Marketplace

Axyome XM is on the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=axyome-ai.axyome-ai-xm) and on [Open VSX](https://open-vsx.org/extension/axyome-ai/axyome-ai-xm).

1. In VS Code, open the **Extensions** view (`Ctrl+Shift+X`, or `Cmd+Shift+X` on macOS).
2. Search for **Axyome XM** and choose **Install**.

Or run:
```bash
code --install-extension axyome-ai.axyome-ai-xm
```

VS Code picks the build for your platform. Nothing is recorded until you choose what to record on the first-run panel.

### From Open VSX

In an editor that installs extensions from [Open VSX](https://open-vsx.org/extension/axyome-ai/axyome-ai-xm), search
for **Axyome XM** in its Extensions view and install it. The editor must be based on VS Code 1.123 or later. You can
also download the file for your platform from the Open VSX page and install it with **Extensions: Install from VSIX…**.

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

Your activity is stored only on your computer. If you sign in, Axyome XM contacts `api.axyome.ai` for your account and plan; signed out, it makes no calls to Axyome servers.

| OS | Path |
|----|------|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome-ai.axyome-ai-xm\` |
| Linux | `~/.config/Code/User/globalStorage/axyome-ai.axyome-ai-xm/` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome-ai.axyome-ai-xm/` |

Your activity is persisted locally in `axyome-xm.db` - a file you can back up, inspect,
or delete at any time.

Automatic backups are kept in their own folder, outside VS Code's extension storage, so uninstalling or updating
the extension never deletes them:

| OS | Backup folder |
|----|---------------|
| Windows | `%APPDATA%\Code\User\axyome-ai.axyome-xm\backups` |
| Linux | `~/.config/Code/User/axyome-ai.axyome-xm/backups` |
| macOS | `~/Library/Application Support/Code/User/axyome-ai.axyome-xm/backups` |

Run **Axyome XM: Open Backup Folder** to open it.

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Extension not activating | VS Code < 1.123 | Update VS Code to 1.123+ |
| `axm_*` tools missing in Copilot | Extension not fully loaded | Full restart VS Code (not just reload window) |
| "cannot open database" error | AppData folder permissions | Check folder exists and is writable |
| `native addon` load error | Damaged or incomplete install | Uninstall, then install Axyome XM again from the Extensions view |
| "database is locked" error | VS Code locking DB | This is normal - the extension manages this automatically |
| MCP server shows "Not connected" | Slow startup | Wait 10s after VS Code loads; restart if persistent |

### Full Restart vs Reload

If Copilot tools don't appear after install, use a **full restart** - not just `Ctrl+Shift+P - Reload Window`:

- Windows/Linux: Close VS Code, reopen
- macOS: `Cmd+Q`, reopen

This ensures the MCP server process starts fresh.

---

## Updating

VS Code updates Axyome XM automatically, like any Marketplace extension (unless you turned off automatic extension
updates). After an update, do a full restart of VS Code.

---

## Uninstalling

In the Extensions view, find **Axyome XM** and choose **Uninstall**, or run:

```bash
code --uninstall-extension axyome-ai.axyome-ai-xm
```

Uninstalling removes the extension and its database folder. The backups stay in their own folder (see Data
Location) so you can restore them. To remove everything, run **Axyome XM: Delete All My Data** first; see the
[uninstall and data removal guide](uninstall.md).
