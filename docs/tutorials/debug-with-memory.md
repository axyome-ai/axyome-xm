# Debug with memory

**Track:** Coder · **Level:** Junior · **Time:** 30 min · **Before this:** VS Code and Copilot basics; Axyome XM installed and recording ([first tutorial, Step 1](vibe-coding-with-copilot.md#step-1-install-axyome-xm-and-choose-what-it-records))

**You will end with** the request tracker under git, two fixed bugs, and the habit of asking
"have I seen this before?" before you start debugging.

Most bugs you hit are bugs you have hit before. Axyome XM records the errors VS Code shows in the
**Problems** panel, your commits and your file changes. Together they tell you when you saw an error
and what you changed to fix it.

**How it fits together:** the same as in the [first tutorial](vibe-coding-with-copilot.md#how-it-fits-together).

---

## Before you start

- [ ] [Git](https://git-scm.com/downloads) installed. VS Code uses it for the **Source Control** view.
- [ ] In the Axyome XM capture settings, **Problems** and **Git** are on (Command Palette >
      **Axyome XM: Review Capture Settings**). **Recommended** turns both on.

---

## Step 1: Get the project

Use the `request-tracker` folder from the business track, or create it now: make an empty folder
`request-tracker`, open it in VS Code, open the **Chat view** in **Agent** mode (`Ctrl+Shift+I`,
`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux) and send:

```text
Build a single page index.html called "Request tracker". A form adds a request with a title, requester, date and a status of New, In progress or Done. Show the requests in a table below the form, newest first, and keep them in the browser so they survive a page reload. Use navy #1F3A5F and orange #F28C28. Do not use anything I need to install.
```

Then move the code into its own file, so VS Code checks it:

```text
Move the JavaScript from index.html into app.js and load it from index.html. Change nothing else.
```

Click **Keep** and open `index.html` in the browser to check it still works.

---

## Step 2: Put it under git

1. Open the **Source Control** view (`Ctrl+Shift+G`, `Ctrl+Shift+G` on a Mac too) and click **Initialize Repository**.
2. Type the message `Request tracker: first version` and click **Commit** (choose **Yes** to stage all files).

Axyome XM records every commit from now on. If you work in a project that already had commits, run
**Axyome XM: Import Git History** once: it reads your own commits of the last 90 days.

---

## Step 3: First bug, and its fix

Break the code on purpose. In `app.js`, delete the last closing brace `}` of any function and save.

Open the **Problems** panel (`Ctrl+Shift+M`, `Cmd+Shift+M` on a Mac). VS Code reports an error such as
`'}' expected.` Axyome XM has just recorded it: the message, the file, the time.

Now fix it with Copilot:

```text
Fix the error in app.js that the Problems panel shows.
```

**Keep** the fix, then commit it with a message that says what the fix was:

```text
Fix: missing closing brace in app.js
```

A commit message that names the fix is what makes the next step work.

---

## Step 4: Second bug, from memory

Days later, a similar error. Try it now: delete a different closing brace in `app.js` and save.

**Before** you ask for a fix, ask your history:

```text
Have I seen this error before: '}' expected
```

Copilot runs `axm_find_similar_errors` and finds the earlier error: when it happened and in which
file. Then connect it to what you did about it:

```text
What did I change in app.js, and what did I commit, right after that earlier error?
```

Copilot reads your file changes and commits (`axm_recall_activity`) and finds your
`Fix: missing closing brace` commit. Now you know the cause and the fix before you start, and you
can ask for exactly that:

```text
Same problem as my "Fix: missing closing brace" commit. Fix it the same way.
```

Commit again, with a message that names the fix.

---

## Step 5: See it in the dashboard

Open the Axyome XM dashboard (`Ctrl+Shift+Alt+M`, `Cmd+Shift+Alt+M` on a Mac):

- **Activity > History** shows your saves and commits on a timeline.
- **Replay > Time Machine**, today, **Errors**: the two errors, each at the moment it appeared.

---

## Your data and privacy

What is recorded and where is described in the [first tutorial](vibe-coding-with-copilot.md#your-data-and-privacy)
and the [privacy policy](../privacy.md). New here: with **Problems** on, Axyome XM stores the error
messages VS Code shows for files in your open folder, and with **Git** on, your commit messages.

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| "Have I seen this error before?" finds nothing | The error must have appeared in the **Problems** panel for a file inside the open folder. Errors in `node_modules`, `dist`, `out` and `.git` are not recorded. |
| Copilot answers without running an `axm_` tool | Add "Use Axyome XM" to the question. |
| Copilot finds the error but not the fix | Your commit messages are the memory of your fixes. Name the fix in each one: "Fix: …". |
| The Problems panel shows nothing for `app.js` | Save the file. VS Code checks JavaScript in `.js` files, not inside `index.html`. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Check an error against my history | "Have I seen this error before: *message from the Problems panel*" |
| Find what fixed it last time | "What did I change in *file*, and what did I commit, right after that earlier error?" |
| Open the Problems panel | `Ctrl+Shift+M` (`Cmd+Shift+M` on a Mac) |
| Import an existing project's commits | Command Palette > **Axyome XM: Import Git History** |

---

## Next

[A feature across three days](feature-across-three-days.md): build a tested feature over several
sessions without losing the thread.
