# A small tool built over a week

**Track:** Business · **Level:** Intermediate · **Time:** 3 sessions of 30 min · **Before this:** [Vibe coding with Copilot and Axyome XM](vibe-coding-with-copilot.md)

**You will end with** a request tracker for your team that opens in the browser, built over three
sessions, plus a playbook of what you learned that you can reuse on the next project.

Real tools are not built in one sitting. In this tutorial you stop and come back three times.
Each time, Copilot picks up where you left off from Axyome XM, not from your notes.

**How it fits together:** the same as in the [first tutorial](vibe-coding-with-copilot.md#how-it-fits-together).

---

## Before you start

- [ ] Axyome XM installed and recording ([first tutorial, Step 1](vibe-coding-with-copilot.md#step-1-install-axyome-xm-and-choose-what-it-records)).
- [ ] The brand rule saved in the [first tutorial, Step 5](vibe-coding-with-copilot.md#step-5-teach-it-your-decisions).
      Skipped it? Send that "Remember:" prompt now.
- [ ] Ideally a day between sessions. A break of an hour works too.

---

## Session 1, Step 1: Start a new project from what you already decided

1. Create a new empty folder, `Documents/request-tracker`, and open it with **File > Open Folder...**.
2. Open the **Chat view** in **Agent** mode: `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux).
3. Ask about the rule you saved in the other project:

```text
What did we decide about chart colours and currency?
```

Copilot finds the rule with `axm_search_decisions`, even though you saved it in a different folder.
Decisions belong to you, not to one project.

---

## Session 1, Step 2: Build the tracker in small steps

Send one prompt at a time and try the page after each one (double-click `index.html`).

```text
Create index.html called "Request tracker" with a form to add a request: a title, a requester, a date and a status of New, In progress or Done. Use our brand colours. Do not use anything I need to install.
```

```text
Show the requests in a table below the form, newest first.
```

```text
Keep the requests in the browser so they are still there after I reload the page.
```

Then save what a request is, so later sessions and later projects use the same words:

```text
Remember: in the request tracker, a request has a title, a requester, a date and a status of New, In progress or Done.
```

Stop here for today.

---

## Session 2, Step 3: Pick up where you stopped

Open the `request-tracker` folder again and start a **new** chat. Do not explain anything; ask:

```text
Where did I stop on the request tracker, and what is left to do?
```

Copilot reads your last session from Axyome XM: the files you changed, when, and how long you worked.
Check its answer against the page in your browser.

Now add two features:

```text
Add a filter above the table to show only one status, or all.
```

```text
Show the number of requests per status above the table.
```

---

## Session 2, Step 4: Recover from a bad change

Sooner or later a change breaks something that worked, and you notice only after you clicked
**Keep** and moved on. Try it on purpose:

```text
Let me edit a request by clicking its row.
```

If the table or the filter stops working, do not guess. First find out what changed:

```text
What changed in index.html today, and when?
```

Then look at the day yourself: open the Axyome XM dashboard (`Ctrl+Shift+Alt+M`, `Cmd+Shift+Alt+M` on a Mac)
and go to **Replay > Time Machine**. Pick today. **Chapters** shows your session step by step, so you can see
which change came just before the problem.

Now you can ask for exactly what you want:

```text
The filter worked before the edit feature. Keep the edit feature, but make the filter work again.
```

Describing what worked *before* a change is the fastest way to get it back.

---

## Session 3, Step 5: Build your playbook

Axyome XM writes **XM Wiki** pages from your sessions automatically when VS Code is idle. To write them now, open the **Command Palette** (`Ctrl+Shift+P`, `Cmd+Shift+P` on a Mac)
and run **XM Wiki: Ingest Latest Session**.

Then search them: Command Palette > **XM Wiki: Search…**, type `request tracker`. You can also browse
the pages in the dashboard under **Replay > Wiki**.

Now ask Copilot to turn your experience into rules for next time:

```text
What did I learn building the request tracker that I should reuse on my next project? Give me three short rules.
```

Save the rules you agree with, one "Remember:" prompt each, for example:

```text
Remember: when I build a form, I ask for the table and the saving in separate prompts and test after each one.
```

Your next project starts with these rules already known.

---

## Your data and privacy

Nothing new is recorded in this tutorial. Everything stays on your computer, as described in the
[first tutorial](vibe-coding-with-copilot.md#your-data-and-privacy) and the [privacy policy](../privacy.md).

---

## Tips and troubleshooting

| What you see | What to do |
| --- | --- |
| Copilot does not know the rule from the other project | Ask "Use Axyome XM: what did we decide about chart colours?" Check that the rule was saved: Copilot showed `axm_log_decision` when you sent it. |
| "Where did I stop?" describes the wrong project | Name the project and folder: "on the request tracker in Documents/request-tracker". |
| The requests disappear after a reload | Say exactly that: "The requests disappear when I reload the page." |
| **XM Wiki: Search…** finds nothing | Run **XM Wiki: Ingest Latest Session** first, then search again. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Pick up a project | New chat: "Where did I stop on *project*, and what is left to do?" |
| Find what changed today | "What changed in *file* today, and when?" or **Replay > Time Machine** |
| Get back what worked | "*Feature* worked before *change*. Keep *change*, but make *feature* work again." |
| Write Wiki pages now | Command Palette > **XM Wiki: Ingest Latest Session** |
| Search my playbook | Command Palette > **XM Wiki: Search…** |

---

## Next

[Hand your prototype to developers](handover-to-developers.md): turn the request tracker and its
history into a handover pack.
