# Hand your prototype to developers

**Track:** Business · **Level:** Advanced · **Time:** 45 min · **Before this:** [A small tool built over a week](tool-over-a-week.md)

**You will end with** a handover pack for the request tracker: the working page plus a `HANDOVER.md`
that tells developers what it does, what you decided and why, and what is left to do.

A prototype is only useful to developers if they know *why* it is the way it is. You do not need to
remember: Axyome XM kept the decisions and the day-by-day history, and Copilot can write them up.

**How it fits together:** the same as in the [first tutorial](vibe-coding-with-copilot.md#how-it-fits-together).

---

## Before you start

- [ ] The `request-tracker` folder from [A small tool built over a week](tool-over-a-week.md), opened in VS Code.
- [ ] The **Chat view** in **Agent** mode: `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux).

---

## Step 1: Collect your decisions

```text
List every decision we saved that applies to the request tracker, with the date of each.
```

Copilot reads them with `axm_search_decisions`. Expect at least the brand rule and what a request
contains. If one is missing, save it now with a "Remember:" prompt: a decision that is not written
down is one the developers will guess.

---

## Step 2: Collect what was built, day by day

```text
Using Axyome XM, summarise what was built on the request tracker on each day I worked on it: the files changed and the features added.
```

Copilot reads each day with `axm_get_session_summary` (how much you changed and how long you worked)
and looks up the files and commits with `axm_recall_activity`. Compare its answer with **Replay > Time Machine**
in the Axyome XM dashboard (`Ctrl+Shift+Alt+M`, `Cmd+Shift+Alt+M` on a Mac): pick each day and read
its **Chapters**. Correct anything Copilot got wrong in the next step.

---

## Step 3: Write the handover file

```text
Create HANDOVER.md in this folder for the developers who will take over the request tracker. Use the decisions and the day-by-day summary from this chat. Sections: What it does; How to open it; Decisions and why; What was built, by day; Known limits; Open questions. Keep it under one page, in plain words.
```

Then read it as if you were the developer, and fix it in plain words:

```text
In Known limits, say that the requests are stored only in this browser on this computer, so two people do not see the same list.
```

```text
Add to Open questions: should requests be shared by the whole team, and who may change a status?
```

---

## Step 4: Check the pack before you send it

Open the folder in your file explorer. It should hold:

| File | What it is |
| --- | --- |
| `index.html` | The working page. A double-click opens it. |
| `HANDOVER.md` | What, why, history, limits, open questions. |

Double-click `index.html` once more and check that it still works. Send the developers the folder,
for example as a zip file, or put it where your team keeps shared files.

The developers can continue with [Debug with memory](debug-with-memory.md), the first coder tutorial,
which starts from this project.

---

## Step 5: Keep your own archive, privately

To keep a copy of everything Axyome XM recorded, open the **Command Palette** (`Ctrl+Shift+P`,
`Cmd+Shift+P` on a Mac) and run **Axyome XM: Export All My Data**. Choose a folder: it receives one
JSON and one Markdown file per kind of record.

**Do not send this export to anyone.** It holds your whole history, from every project: terminal
commands, chat text, file names. The handover pack from Step 4 is what you share.

---

## Your data and privacy

What is recorded and where is described in the [first tutorial](vibe-coding-with-copilot.md#your-data-and-privacy)
and the [privacy section of the README](../../README.md#privacy). New here: the export in Step 5 contains everything, so treat
it like a private diary. `HANDOVER.md` contains only what you read and approved.

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| The day-by-day summary mixes in other projects | Name the folder and ask for its files and commits only: "only the files and commits in Documents/request-tracker, day by day". |
| A decision is missing from the list | Save it now ("Remember: …"), then run Step 1 again. |
| `HANDOVER.md` is too long or too technical | "Make HANDOVER.md shorter and plainer. One page, no code." |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| List my decisions | "List every decision we saved that applies to *project*." |
| Summarise the work by day | "Using Axyome XM, summarise what was built on *project* on each day." |
| Check a day myself | Dashboard > **Replay > Time Machine** > pick the day > **Chapters** |
| Keep a private archive | Command Palette > **Axyome XM: Export All My Data** |

---

## Next

The business track ends here. The coder track starts with [Debug with memory](debug-with-memory.md),
on the same request tracker.
