# A feature across three days

**Track:** Coder · **Level:** Intermediate · **Time:** 3 sessions of 30 min · **Before this:** [Debug with memory](debug-with-memory.md)

**You will end with** a tested CSV export in the request tracker, built over three sessions, with
project rules Copilot follows in every chat and a summary you can paste into a pull request.

A feature that spans days fails in the gaps: the rule you set on Monday, the test that broke on
Tuesday. In this tutorial Axyome XM fills the gaps, and you check what it says against git.

**How it fits together:** the same as in the [first tutorial](vibe-coding-with-copilot.md#how-it-fits-together).

---

## Before you start

- [ ] The `request-tracker` project under git, from [Debug with memory](debug-with-memory.md).
- [ ] [Node.js](https://nodejs.org) 18 or newer, for its built-in test runner (`node --test`).
- [ ] The **Chat view** in **Agent** mode: `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux).

---

## Session 1, Step 1: Give the project its rules

Open the **Command Palette** (`Ctrl+Shift+P`, `Cmd+Shift+P` on a Mac) and run
**Axyome XM: Configure Workspace for AI Memory**. Choose **AGENTS.md**. It is a project instruction
file that Copilot reads in every chat; open it and read what it asks Copilot to do. Commit it.

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

Copilot reads your last session (`axm_get_session_summary`) and your commits. Compare its answer with
`git log` in the terminal: it should name `Add toCsv with tests`.

---

## Session 2, Step 4: Look before you touch a file

`app.js` now has history: two bugs from the last tutorial and a new function. Before changing it:

```text
Before you change app.js, get its context from Axyome XM: past errors in it and the decisions that apply.
```

Copilot runs `axm_get_context_snapshot` on the file. It brings back the file's past errors and your
saved rules, in a short answer sized to fit the chat. Now add the button:

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

Copilot reads the recorded test runs and your file changes (`axm_recall_activity`) and narrows the
search to the changes since the last green run. Fix, rerun, and commit: `Add Export CSV button`.

---

## Session 3, Step 6: Review the file's error history

```text
Show the error history of app.js from Axyome XM, and what happened in the chat just before each error.
```

Copilot runs `axm_get_error_forensics`. For each error recorded for that file, it shows when it
appeared and what came just before it in the chat session. Look for a
pattern: did errors follow large prompts that changed several things at once?

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
and the [privacy policy](../privacy.md). New here: `AGENTS.md` is a file in your project, so it is
committed and shared with everyone who clones the project. Read it before you commit it.

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| Copilot ignores the project rules | Check that `AGENTS.md` is in the project root, then ask "What did we decide about tests in the request tracker?" |
| "Where did I stop?" names another project | Name the folder: "in the request-tracker folder". |
| The context snapshot shows no past errors | Errors are recorded only from the **Problems** panel (see [Debug with memory](debug-with-memory.md)). |
| `node --test` finds no tests | Check that the file is `tests/app.test.js` and that you run it from the project root. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Give Copilot project rules | Command Palette > **Axyome XM: Configure Workspace for AI Memory** > **AGENTS.md** |
| Resume a feature | "Where did I stop on *project*, and what is left to do for *feature*?" |
| Check a file before changing it | "Before you change *file*, get its context from Axyome XM." |
| Narrow a failing test | "When did the tests last pass, and what changed in *file* since then?" |
| Review a file's errors | "Show the error history of *file* from Axyome XM." |

---

## Next

The senior tutorial, connecting Claude Code to the same memory, is coming. Until then, the
[MCP tools reference](../mcp-tools-reference.md) lists every `axm_` tool.
