# A feature across three days

**Track:** Coder · **Level:** Intermediate · **Time:** 3 sessions of 30 min · **Before this:** [Debug with memory](debug-with-memory.md)

**You will end with** a tested CSV export in the request tracker, built over three sessions, with
project rules saved in Axyome XM that Copilot looks up when you ask, and a summary you can paste into a pull request.

A feature that spans days fails in the gaps: the rule you set on Monday, the test that broke on
Tuesday. In this tutorial Axyome XM fills the gaps, and you check what it says against git.

**How it fits together:** the same as in the [first tutorial](vibe-coding-with-copilot.md#how-it-fits-together).

---

## Before you start

- [ ] The `request-tracker` project under git, from [Debug with memory](debug-with-memory.md).
- [ ] [Node.js](https://nodejs.org) 18 or newer, for its built-in test runner (`node --test`).
- [ ] **Terminal** is on in **Axyome XM: Review Capture Settings** (**Recommended** turns it on), so test runs are recorded.
- [ ] The **Chat view** in **Agent** mode: `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux).

---

## Session 1, Step 1: Give the project its rules

Open the **Command Palette** (`Ctrl+Shift+P`, `Cmd+Shift+P` on a Mac) and run
**Axyome XM: Configure Workspace for AI Memory**. In the list, leave only **Create AGENTS.md** ticked
and press Enter. `AGENTS.md` is a project instruction file for AI assistants; open it and read what it
asks Copilot to do. Commit it.

Then save the project's own rules as decisions:

```text
Remember: in the request tracker, logic lives in app.js as plain functions that also run in Node, and every function has a test in tests/app.test.js using node:test.
```

---

## Session 1, Step 2: Tests first

```text
Add a function toCsv(requests) to app.js that returns the requests as CSV text with a header row: title, requester, date, status. Write its tests first in tests/app.test.js, including a title that contains a comma. Then run node --test.
```

Copilot writes the tests, adds the function and asks to run `node --test` in the terminal: choose
**Allow**. If it puts the code or tests somewhere else, add "Follow our saved decisions for the
request tracker" to the prompt. Axyome XM records each test run and whether it
passed (its exit code).

When the tests pass, commit: `Add toCsv with tests`. Stop for today.

---

## Session 2, Step 3: Resume without notes

Start a **new** chat:

```text
Where did I stop on the request tracker, and what is left to do for the CSV export?
```

Copilot reads a summary of your recent work (`axm_get_session_summary`) and searches your commits
(`axm_recall_activity`). Compare its answer with
`git log` in the terminal: it should name `Add toCsv with tests`.

---

## Session 2, Step 4: Look before you touch a file

`app.js` now has history: two bugs from the last tutorial and a new function. Before changing it:

```text
Before you change app.js, get its context from Axyome XM: its recent errors and the decisions that apply.
```

Copilot runs `axm_get_context_snapshot` on the file. It brings back how many errors the file had this
past week and your recent saved decisions, in a short answer sized to fit the chat. Now add the button:

```text
Add an Export CSV button above the table that downloads the requests as requests.csv using toCsv. Keep the tests passing.
```

---

## Session 2, Step 5: When a test fails

Suppose a test fails after the change (if none does, change the expected header in a test to break
one, and run `node --test`). Before you read the whole diff, ask:

```text
When did the tests last pass, and what changed in app.js since then?
```

Copilot finds the last test run that passed and the times you saved `app.js` after it
(`axm_recall_activity`). Run `git diff` to see what changed since your last commit. Fix, rerun, and commit: `Add Export CSV button`.

---

## Session 3, Step 6: Review the file's error history

```text
Show the error history of app.js from Axyome XM, including errors I already fixed.
```

Copilot runs `axm_get_error_forensics`. For each error, it shows when and where it appeared, the
message, whether you fixed it and how long that took, and how much chat activity came just before it.
Look for a pattern: did errors follow a burst of chat requests?

---

## Session 3, Step 7: Write the pull request text from memory

```text
Summarise what I built this week on the request tracker, for a pull request description: what changed, why, how it was tested. Use Axyome XM and my commits.
```

Check it against `git log` and paste it into your pull request. Then commit and push as your team
usually does.

---

## Your data and privacy

What is recorded and where is described in the [first tutorial](vibe-coding-with-copilot.md#your-data-and-privacy)
and the [privacy section of the README](../../README.md#privacy). New here: `AGENTS.md` is a file in your project, so it is
committed and shared with everyone who clones the project. Read it before you commit it.

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| Copilot ignores the project rules | Check that `AGENTS.md` is in the project root, then ask "What did we decide about tests in the request tracker?" |
| "Where did I stop?" names another project | Name the folder: "in the request-tracker folder". |
| The context snapshot shows no errors | It counts the errors of the past week, recorded only from the **Problems** panel (see [Debug with memory](debug-with-memory.md)). |
| `node --test` finds no tests | Check that the file is `tests/app.test.js` and that you run it from the project root. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Give Copilot project rules | Command Palette > **Axyome XM: Configure Workspace for AI Memory** > only **Create AGENTS.md** ticked |
| Resume a feature | "Where did I stop on *project*, and what is left to do for *feature*?" |
| Check a file before changing it | "Before you change *file*, get its context from Axyome XM." |
| Narrow a failing test | "When did the tests last pass, and what changed in *file* since then?" |
| Review a file's errors | "Show the error history of *file* from Axyome XM." |

---

## Next

Connect Claude Code to the same memory: [One memory for Copilot and Claude Code](one-memory-for-copilot-and-claude-code.md).
