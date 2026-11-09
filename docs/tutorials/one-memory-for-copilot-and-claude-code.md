# One memory for Copilot and Claude Code

**Track:** Coder · **Level:** Senior · **Time:** 45 min · **Before this:** [A feature across three days](feature-across-three-days.md)

**You will end with** Claude Code and Copilot working on the request tracker from one shared memory,
and a refactor whose design decision both assistants can find.

Many developers use two assistants: Copilot in the editor, Claude Code for larger changes. Each one
forgets what the other did. In this tutorial both read and write the same Axyome XM memory on your
computer, so a decision made with one is known to the other.

## How it fits together

```
 +--------------------+                              +--------------------+
 | Copilot Chat       |                              | Claude Code        |
 | Agent mode, in the |                              | in VS Code or in a |
 | editor             |                              | terminal           |
 +--------------------+                              +--------------------+
           |  axm_ tools                                    axm_ tools  |
           v                                                            v
 +----------------------------------------------------------------------------+
 | Axyome XM memory, on your computer                                         |
 | one history and one set of decisions, whichever assistant asks             |
 +----------------------------------------------------------------------------+
```

Both assistants run their AI model in the cloud. Your Axyome XM memory stays on your computer; each
assistant reads from it only through tools whose names start with `axm_`.

---

## Before you start

- [ ] The `request-tracker` project under git, with its tests, from [A feature across three days](feature-across-three-days.md).
- [ ] [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) installed and signed in:
      the Claude Code extension for VS Code, or the `claude` command in a terminal.
- [ ] The **Chat view** in **Agent** mode: `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux).

---

## Step 1: Give Claude Code access to your memory

Open the **Command Palette** (`Ctrl+Shift+P`, `Cmd+Shift+P` on a Mac) and run
**Axyome XM: Review Capture Settings**. Check that **Claude Code memory access** is on (it is part of
**Recommended**), then confirm. Axyome XM adds an `axyome-xm` entry to Claude Code's settings, installs
a plugin with an agent and three memory skills, and keeps them up to date when the extension updates.

To check, open a terminal and run:

```text
claude mcp list
```

You see a line that starts with `axyome-xm:` and ends with **Connected**. If it is missing, run
**Axyome XM: Connect Claude Code** from the Command Palette.

---

## Step 2: Ask Claude Code what you did with Copilot

Open Claude Code in the `request-tracker` folder and ask:

```text
Use the axyome-xm tools: what did I work on in the request-tracker folder this week?
```

When Claude Code asks permission to use an `axyome-xm` tool, allow it. It calls
`axm_recall_activity` and answers from the history recorded while you worked with Copilot: the files
you changed, your commits and the tests you ran.

Then ask for a decision you saved in the first tutorial:

```text
Use the axyome-xm tools: what did we decide about chart colours and currency?
```

Claude Code finds the brand rule with `axm_search_decisions`. You saved it with Copilot, in another
folder.

---

## Step 3: Refactor with Claude Code

Ask Claude Code for the change:

```text
Refactor the request tracker: keep the plain functions in app.js, move all code that reads or changes the page into a new ui.js, and load both from index.html. Do not change what the page does. Run node --test and make sure every test still passes.
```

Review the change, open `index.html` in your browser and check that adding a request still works.
Commit it with a message that names the change, for example `refactor: move page code to ui.js`.

---

## Step 4: Record the design decision

Still in Claude Code:

```text
Use the axyome-xm tools to save this decision: in the request tracker, app.js holds only plain functions that run in Node and are tested; everything that touches the page lives in ui.js.
```

Claude Code saves it with `axm_log_decision`. Name the tools: Claude Code also has its own memory files, and "Remember:" alone may go there. It is now a decision like the brand rule: short, dated,
and found by either assistant.

---

## Step 5: Ask Copilot about the change Claude Code made

Switch to the **Chat view** in **Agent** mode and ask:

```text
What did we decide about how the request tracker's code is split between files?
```

Copilot finds the decision Claude Code saved in Step 4. When Copilot asks to run an `axm_` tool,
choose **Allow**. If it answers without memory, add "Use Axyome XM".

Then ask what happened today:

```text
What did I work on in the request-tracker folder today? Use Axyome XM.
```

The answer includes your `refactor: move page code to ui.js` commit from Step 3. A commit message that names the change is what memory finds.

---

## Your data and privacy

What is recorded and where is described in the [first tutorial](vibe-coding-with-copilot.md#your-data-and-privacy)
and the [privacy section of the README](../../README.md#privacy). New here: Claude Code is a cloud
service too. What it reads from your memory becomes part of its conversation with its AI model.
Axyome XM records Claude Code's prompts and tool calls for the folders open in VS Code, and stores
them only on your computer. Turn **Claude Code** or **Claude Code memory access** off at any time in
**Axyome XM: Review Capture Settings**.

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| `claude mcp list` has no `axyome-xm` line | Run **Axyome XM: Connect Claude Code** from the Command Palette, then run `claude mcp list` again. |
| Axyome XM cannot find Claude Code | Set `axyomeXM.claudeCode.cliPath` to the full path of the `claude` program. |
| Claude Code answers without using memory | Start the prompt with "Use the axyome-xm tools:". |
| Claude Code's work is missing from Copilot's answer | Open the `request-tracker` folder in VS Code: Claude Code's sessions are recorded for folders open there. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Give Claude Code my memory | Command Palette > **Axyome XM: Review Capture Settings** > **Claude Code memory access** on |
| Check the connection | `claude mcp list` shows `axyome-xm` … **Connected** |
| Connect again by hand | Command Palette > **Axyome XM: Connect Claude Code** |
| Ask Claude Code from memory | "Use the axyome-xm tools: *question*" |
| Save a design decision for both assistants | Copilot: "Remember: *decision*" · Claude Code: "Use the axyome-xm tools to save this decision: *decision*" |

---

## Next

Try the business track from the start: [Vibe coding with Copilot and Axyome XM](vibe-coding-with-copilot.md).
