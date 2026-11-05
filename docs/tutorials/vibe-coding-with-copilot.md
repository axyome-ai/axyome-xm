# Vibe coding with Copilot and Axyome XM

**Track:** Business · **Level:** Beginner · **Time:** 30 min · **Before this:** nothing

**You will end with** a one-page sales dashboard that opens in your browser, and an Axyome XM history
of how you built it.

In this tutorial you build a small working app by chatting with GitHub Copilot in VS Code, without
writing code yourself. Axyome XM records what you and Copilot did, so the next chat can pick up
where you left off.

**Vibe coding** means you describe what you want in plain words, the AI writes and changes the code,
and you judge the result by trying it. You steer; Copilot types.

---

## How it fits together

```
 +--------------------+  prompt  +--------------------+  edits   +--------------------+
 | You                |--------->| Copilot Chat       |--------->| Your project folder|
 | describe what you  |          | writes and changes |          | the app Copilot    |
 | want; Keep or Undo |          | files; the model   |          | builds             |
 +--------------------+          | runs in the cloud  |          +--------------------+
           ^                     +--------------------+                    |
           | look back                     ^                               | saves, errors
           |                               | axm_ tools                    |
           |                               v                               v
 +--------------------+  shows   +--------------------+  stores  +--------------------+
 | XM dashboard       |<---------| Axyome XM memory   |<---------| Axyome XM recorder |
 | Time Machine,      |          | your history,      |          | notes chats, file  |
 | XM Wiki, AI chats  |          | decisions you saved|          | saves, errors and  |
 +--------------------+          +--------------------+          | commits            |
                                                                 +--------------------+
```

Copilot builds what you ask for; its AI model runs in the cloud. The Axyome XM recorder notes what
happens and stores it on your computer: everything in the bottom row stays there. Copilot reads it back through tools whose names start with `axm_`, and you can browse it
in the dashboard.

---

## Before you start

You need three things, and no coding experience:

- [ ] **VS Code 1.139 or newer.** Free download from [code.visualstudio.com](https://code.visualstudio.com).
      Check your version under **Help > About** (on a Mac: **Code > About Visual Studio Code**).
- [ ] **A GitHub account with Copilot turned on.** Sign in with the **Accounts** icon at the bottom
      left of VS Code. If your company manages Copilot, ask your IT contact which account to use.
- [ ] **The Axyome XM install file (a `.vsix` file) for your computer**, provided by Axyome
      ([install guide](../install.md)). Pick the one whose name matches your machine:

| Your computer | File name contains |
| --- | --- |
| Windows | `win32-x64` |
| Mac with Apple chip (M1 to M4) | `darwin-arm64` |
| Mac with Intel chip | `darwin-x64` |
| Linux | `linux-x64` |

---

## Step 1: Install Axyome XM and choose what it records

Axyome XM installs from the file you received. It records nothing until you press **Start recording**.

1. In VS Code, open the **Extensions** view: the four-squares icon in the **Activity Bar** (the icon
   bar on the far left), or
   `Ctrl+Shift+X` (`Cmd+Shift+X` on a Mac).
2. Click the **...** menu at the top of that view and choose **Install from VSIX...**.
3. Select your `.vsix` file. Wait for the message that the install finished.
4. A panel opens that lists every source Axyome XM can record, with what each one stores: Copilot
   chats, file saves, git commits, terminal commands, errors and more. **Recommended** turns them
   all on. Turn off any source you prefer to keep out, then press **Start recording**.
5. Follow the **Get started with Axyome XM** walkthrough on the Welcome page. It has four short steps:
    1. Choose what Axyome XM records (the panel above).
    2. Check that Copilot can reach your memory. Axyome XM connects itself to Copilot, so there is
       nothing to configure.
    3. Import your git history, if your project has one: your own commits of the last 90 days, read once.
    4. Ask Copilot "What did I work on this week?"

You can change your recording choices at any time. Press `Ctrl+Shift+P` (`Cmd+Shift+P` on a Mac)
to open the **Command Palette**, type **Axyome XM: Review Capture Settings** and press Enter.
A new **Axyome XM** icon now sits in the Activity Bar; it opens the dashboard you will use in Step 6.

---

## Step 2: Open a project folder and Copilot Chat

Copilot works on the files in one folder, so give each project its own folder.

1. Create an empty folder, for example `Documents/sales-dashboard`.
2. In VS Code choose **File > Open Folder...** and select it. If VS Code asks whether you trust the
   authors of the files, choose **Yes**: it is your own folder.
3. Press `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux). The **Chat view** opens on
   the side, in **Agent** mode. You can also click the chat icon at the top of the window.
4. Check that the mode under the message box says **Agent**; change it there if not. In Agent mode, Copilot can create and change
   files and run commands. It asks before it runs a command.

Copilot shows every change it makes. Changed files are marked in the editor, and the chat offers
**Keep** or **Undo** for them. Keep what works and undo what does not: you stay in control.

---

## Step 3: Vibe code a small sales dashboard

You will build a one-page sales dashboard that opens in your web browser. It needs no other
software. Send the prompts below one at a time, and look at the result before you send the next.

**Prompt 1: the data**

```text
Create a file sales.csv with 12 months of made-up sales figures for three regions: North, South and West.
```

**Prompt 2: the page**

```text
Build a single page index.html that shows the data from sales.csv as a bar chart per month, with one colour per region and the yearly total per region above the chart. Put the data inside the page so it opens with a double-click. Do not use anything I need to install.
```

Click **Keep**, then open the folder in your file explorer and double-click `index.html`. Your
dashboard opens in the browser.

**Prompts 3 and 4: make it yours**

```text
Add a dropdown above the chart to show one region or all regions.
```

```text
Use our brand colours for the chart: navy #1F3A5F and orange #F28C28. Make the title "Sales 2026".
```

Refresh the browser page after each change. If you do not like a change, click **Undo** in the chat
and say what you want instead.

**When something breaks, say what you see**

```text
The chart is empty when I open index.html. Fix it.
```

You do not need to understand the error. Describe what you expected and what happened, and Copilot
investigates. Axyome XM records which files changed and when, so you can find this moment again
later (Step 4).

---

## Step 4: Ask Copilot what you did

Copilot on its own forgets everything when you start a new chat. With Axyome XM, it can look up
your real history. Start a new chat with the **+** button at the top of the Chat view, then try:

```text
What did I work on today?
```

```text
Which files changed in the last hour?
```

```text
When did I last change index.html?
```

In the chat you will see Copilot run a tool whose name starts with `axm_`, such as
`axm_recall_activity`. That is Copilot reading your Axyome XM memory. The first time, Copilot may
ask permission to run it: choose **Allow**.

If Copilot answers from general knowledge instead, add "Use Axyome XM" to your question.

---

## Step 5: Teach it your decisions

Tell Copilot a rule once, and every later chat can find it. Start with the word "Remember":

```text
Remember: our charts always use navy #1F3A5F and orange #F28C28, and figures are in euros.
```

Copilot saves this with the tool `axm_log_decision`. Copilot asks your permission before it saves,
unless you told it to always allow this tool.

The next day, in a brand-new chat, ask:

```text
What did we decide about chart colours and currency?
```

Copilot finds the rule with `axm_search_decisions` and applies it. Good things to save as decisions:

- Brand rules: colours, fonts, logo, tone of voice
- Data rules: which file is the source of truth, currency, fiscal year
- Choices you made and why: "we show monthly, not weekly, because finance reports monthly"

---

## Step 6: Look back in the dashboard

The dashboard shows your recorded work without asking Copilot. Open it with the **Axyome XM** icon in
the Activity Bar, or `Ctrl+Shift+Alt+M` (`Cmd+Shift+Alt+M` on a Mac). The five places most useful for
vibe coding:

| Where | What you see | Use it to |
| --- | --- | --- |
| **Home** | Today at a glance: recent sessions, files and AI activity | Pick up where you stopped |
| **Activity** | Your work over time: coding time, history, a heatmap of busy hours | See when and how long you worked on a project |
| **AI** | Your AI assistants: chat sessions, when they ran and the models used | See which chats you had and when |
| **Replay > Time Machine** | Any past day, replayed chapter by chapter: summary, chapters, errors, sessions | Answer "what happened on Tuesday?" |
| **Replay > Wiki** | The XM Wiki: pages written automatically from your sessions | Browse and search what you learned |

A new install shows the most useful tabs first; the others can be turned on later. Everything on
the dashboard comes from your own computer.

Try this: open **Replay > Time Machine**, pick today, and read the chapters of your sales dashboard
session. The [dashboard tour](../dashboard.md) shows every tab.

---

## Your data and privacy

Axyome XM keeps your history on your own computer. Without an Axyome account it makes no network
requests.

- **You choose what is recorded.** Every source has its own switch: **Axyome XM: Review Capture Settings**.
- **Secrets are hidden.** Terminal commands and selected text are stored with passwords, keys and
  tokens removed.
- **If you sign in,** Axyome XM contacts `api.axyome.ai` about every 4 hours to confirm your plan,
  and registers this device (its name and platform). There are no third-party analytics. Cloud sync
  exists only on the Team and Enterprise plans.
- **Take it with you:** **Axyome XM: Export All My Data** writes everything to JSON and Markdown
  files in a folder you choose.
- **Remove it:** **Axyome XM: Delete All My Data** (type `DELETE` to confirm) erases the recorded
  history on this computer. Uninstalling the extension alone does not erase it
  ([uninstall guide](../uninstall.md)).

**Copilot is a cloud service.** Your prompts and the files Copilot reads go to GitHub, under your
company's Copilot terms. When Copilot uses an Axyome XM tool, the answer it reads becomes part of
that chat, just like text you paste in. Follow your company's rules on what data you put into Copilot.

**Plans.** Axyome XM starts as a 30-day preview; after that a free account is needed. Free shows the
last 30 days of history, Pro shows all of it. Every feature works on every plan. Current prices:
[app.axyome.ai/pricing](https://app.axyome.ai/pricing). Full details: [privacy policy](../privacy.md).

---

## Tips and troubleshooting

**Prompts that work**

- **One change per prompt.** "Add a dropdown" works better than five wishes in one message.
- **Say who it is for and what done looks like.** "A page my manager can open by double-clicking,
  showing totals per region."
- **Describe, don't diagnose.** "The total shows 0 for West" beats guessing at the cause.
- **Keep each project in its own folder,** so Copilot and Axyome XM keep the history apart.
- **Check the numbers yourself.** Copilot can be confidently wrong. Compare a few figures with the
  source before you share anything.
- **Start the day with memory:** "What did I do on this project last time, and what was left to do?"

**When something goes wrong**

| What you see | What to do |
| --- | --- |
| Copilot changes files you did not mean it to touch | Click **Undo** in the chat. Then say exactly which file to change. |
| Copilot asks to run a command you do not understand | Ask it first: "What does this command do, and is it safe?" Then choose. |
| Copilot answers "I don't have access to your history" | Add "Use Axyome XM" to the question. Check the chat is in **Agent** mode. |
| No `axm_` tools appear in the chat | Command Palette > **Axyome XM: Validate Installation**. Then restart VS Code. |
| You want to pause recording | Command Palette > **Axyome XM: Stop Capture**. **Axyome XM: Start Capture** resumes it. |
| Anything else | [Ask a question](https://github.com/axyome-ai/axyome-xm/issues/new?template=question.yml): say what you did and what you saw. A screenshot helps. |

---

## Quick reference

| I want to | Do this |
| --- | --- |
| Open the Chat view in Agent mode | `Ctrl+Shift+I` (`Cmd+Shift+I` on a Mac, `Ctrl+Shift+Alt+I` on Linux), or the chat icon at the top of the window |
| Start a fresh chat | **+** at the top of the Chat view |
| Open the Command Palette | `Ctrl+Shift+P` (`Cmd+Shift+P` on a Mac) |
| Open the Axyome XM dashboard | **Axyome XM** icon in the Activity Bar, or `Ctrl+Shift+Alt+M` (`Cmd+Shift+Alt+M` on a Mac) |
| Recall my work | "What did I work on today / this week / on this project?" |
| Find a past error | "Have I seen this error before: *paste the message from the Problems panel*" |
| Save a rule | "Remember: *the rule*" |
| Find a rule | "What did we decide about *topic*?" |
| Replay a past day | Dashboard > **Replay > Time Machine** |
| Change what is recorded | Command Palette > **Axyome XM: Review Capture Settings** |
| Export or delete my history | **Axyome XM: Export All My Data** / **Axyome XM: Delete All My Data** |

---

## Next

See the [Tutorials index](README.md) for the next step in your track, and the
[onboarding guide](../onboarding.md) for the rest of the features.
