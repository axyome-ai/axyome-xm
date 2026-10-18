# Uninstall and data removal

Axyome XM keeps everything it records on your computer. This guide shows what is stored, how to take a
copy, how to delete it from inside VS Code, and how to remove the extension and its folder completely.

Uninstalling the extension does not delete your data. VS Code removes the extension itself and leaves its
storage folder behind. Delete your data first (section 2), then uninstall (section 3).

## 1. Take a copy first (optional)

Open the Command Palette (`Ctrl+Shift+P`, or `Cmd+Shift+P` on macOS) and run
**Axyome XM: Export All My Data**.

1. Pick a folder. Axyome XM creates a new folder inside it named `axyome-xm-export-<date and time>`.
2. Every table that has rows is written twice:
   - `<table>.json`: a JSON array, one row per line, every value in full. Binary values are written as
     `{"$base64": "..."}`.
   - `<table>.md`: the same rows as a Markdown table that you can read in any editor. Cells longer than
     2,000 characters are cut in the Markdown file only, and the cell says where the full value is.
3. Tables with no rows are skipped.

The export is read-only: it opens the database separately, reads it in small pages (so a database of a
gigabyte or more does not need that much memory), and changes nothing. It exports all your history, not
just the window your plan shows in the dashboard.

## 2. Delete all my data

Run **Axyome XM: Delete All My Data**. Axyome XM asks you to type `DELETE` (capital letters). Anything
else, or closing the box, cancels and removes nothing.

What it does, in order:

1. Stops the Axyome XM MCP server, so that nothing else is using the database. It is offered to VS Code
   again when the delete ends, whatever the result.
2. Drops queued events that were waiting to be saved.
3. Deletes every row of every table: captured events, chat and session copies, observations, decisions,
   patterns, goals, statistics, profile and licence state. Only `migrations`, which records the database
   version, is kept. Search indexes are emptied too.
4. Compacts the database file, so the deleted content is not left behind inside it.
5. Removes the database backups, the pre-upgrade copies of the database, the queue files (pending,
   processed and failed), the wiki pages and the archive folder.

What it does not touch:

- Your code, your workspaces and your VS Code settings.
- Anything outside the Axyome XM storage folder (section 4). Every delete is checked against that folder
  first; a path that resolves anywhere else is refused.
- Your account and any data synced to the cloud on Team & Enterprise plans. Those are managed at
  [app.axyome.ai](https://app.axyome.ai).
- Files that Axyome XM wrote into a workspace when you chose to configure it (see section 3).

After it finishes, VS Code offers **Reload Window**. Reload to start from a clean slate: the database file
is still there, empty, and the extension keeps recording unless you turn capture off in the settings
(`Axyome XM: Stop Capture`). Your plan and sign-in are re-read the next time you sign in or the extension
syncs.

If the notification says the file could not be compacted, another program (a second VS Code window, or an
AI tool that runs the Axyome XM server) had the database open. Close it and run the command again.

A delete removes the data from the database and from disk the way any file deletion does. It is not a
secure erase of the disk itself. For that, use your operating system's disk-wipe tools.

## 3. Uninstall the extension

1. Delete your data (section 2). Optional, but recommended before step 2.
2. In VS Code open Extensions, find **Axyome XM**, and choose **Uninstall**. Reload when asked.
3. Remove the workspace files if you created them. Only workspaces where you ran
   **Axyome XM: Configure Workspace for AI Memory** have them:
   - the `axyome-xm` server entry in `.vscode/mcp.json`
   - the Axyome XM section in `AGENTS.md`, and `.github/agents/memory.md`
   - the three Axyome XM settings in `.vscode/settings.json`
4. Remove the storage folder (section 4) if you want nothing left.

## 4. Where the data lives

Axyome XM stores its data in the extension's global storage folder:

| System | Folder |
|---|---|
| Windows | `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\` |
| macOS | `~/Library/Application Support/Code/User/globalStorage/axyome.axyome-xm/` |
| Linux | `~/.config/Code/User/globalStorage/axyome.axyome-xm/` |

For VS Code Insiders, VSCodium and other builds, replace `Code` with that build's folder name
(for example `Code - Insiders`).

| Item | What it is |
|---|---|
| `axyome-xm.db`, `axyome-xm.db-wal`, `axyome-xm.db-shm` | the database and its write-ahead log |
| `axyome-xm.db.backup-*` | copies made before the database was upgraded |
| `backups/` | database backups |
| `queues/` | events waiting to be saved, and the ones just saved |
| `wiki/`, `archive/` | wiki pages and archived data, if you used them |
| `db-transactions.log` | the database log, only if you turned it on |
| `.extension-version`, `axyome-xm.db.version` | version markers |

To remove everything by hand, close VS Code (all windows), then delete that folder. The extension folder
itself (`~/.vscode/extensions/axyome.axyome-xm-<version>`) is removed by the uninstall.

Older versions also kept a daily chat copy under `~/.memory-agent/` in your home folder. If that folder
exists on your computer, delete it the same way.

## 5. Where are the commands?

| Command | Command ID |
|---|---|
| Axyome XM: Export All My Data | `axyome-xm.exportAllData` |
| Axyome XM: Delete All My Data | `axyome-xm.deleteAllData` |
| Axyome XM: Clear Captured Events | `axyome-xm.clearEvents` (clears captured file, git, terminal, editor and imported-session events only) |
