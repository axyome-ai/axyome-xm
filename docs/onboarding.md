# Getting Started: Your First 10 Minutes

Axyome XM captures development context automatically from the moment it's installed. Here's how to go from zero to productive.

---

## Step 1 - Open the Dashboard (30 seconds)

Click the **Axyome XM icon** in the Activity Bar (left sidebar - a house inside a
circle), or press `Ctrl+Shift+Alt+M`.

You'll see the Dashboard with 8 tabs:

| Tab | What's inside |
|-----|--------------|
| **Home** | Authorship estimate, velocity, quality, builds, commits, lines of code |
| **Activity** | Coding time, history, heatmap, live feed, unified timeline |
| **AI** | Copilot vs Claude Code: sessions, models, time, value, ATI |
| **Quality** | Quality score, errors, hotspots, patterns, DORA metrics |
| **Intel** | Developer Intelligence score, progress, actions, knowledge |
| **Wellness** | Wellness score, flow, trends, recommendations |
| **Replay** | Time Machine, Memory Map, XM Wiki, usage |
| **System** | Pipeline status, tables, sources, badges, account, settings |

-> [Dashboard tour with screenshots](dashboard.md)

---

## Step 2 - Take the Onboarding Tour (3 minutes)

Onboarding runs from the Command Palette (`Ctrl+Shift+P`), not from a dashboard tab.

**Axyome: Start Onboarding** opens a 3-step quick tour:

| Step | What you learn |
|------|---------------|
| **Your First Memory Query** | Ask Copilot about your recent work |
| **Get a Session Summary** | Summarize what you worked on |
| **Remember a Decision** | Tell Copilot to remember an architectural choice |

**Axyome: Show Onboarding Dashboard** opens the full tour: 17 steps in 4
tracks (Essentials, Discovery, Intelligence, Power User).

---

## Step 3 - Ask Copilot About Your Work (2 minutes)

Open Copilot Chat (`Ctrl+Shift+I`) and try these prompts:

```
What did I work on today?
```

```
What errors did I have in the last hour?
```

```
What files do I edit most often this week?
```

```
Have I seen this error before: [paste error message]
```

Copilot uses your local memory to answer with **real context** from your sessions - not generic advice.

---

## Step 4 - Enable Terminal Capture (Optional, 1 minute)

Terminal capture is opt-in for privacy. To enable:

1. Open VS Code Settings (`Ctrl+,`)
2. Search for `axyome terminal`
3. Enable **Axyome XM: Terminal Capture**

Terminal commands are stored locally with **automatic secret redaction** - values matching patterns like `*_TOKEN`, `*_KEY`, `*_PASSWORD`, AWS credentials, and Bearer tokens are replaced with `[REDACTED]` before storage.

---

## Step 5 - Initialize Workspace Memory (2 minutes)

Run the workspace scanner to give your AI instant project context:

1. Open Command Palette (`Ctrl+Shift+P`)
2. Run: **Initialize Workspace Memory (B035)**

This scans your repository and detects:
- Languages and frameworks
- Package managers (npm, pnpm, yarn, bun)
- Test frameworks (Vitest, Jest, Playwright, Cypress)
- Build tools (Vite, Webpack, esbuild, tsc)
- CI/CD configuration (GitHub Actions, GitLab CI, etc.)
- Code quality metrics (complexity, technical debt, maintainability)

---

## What Happens Automatically From Now On

Axyome XM runs silently in the background:

| Trigger | What gets captured |
|---------|-------------------|
| File save | Path, language, LOC delta |
| Git commit | Message, branch, files changed |
| Error detected | File, line, error text, severity |
| Copilot tool use | Tool name, parameters (for analytics) |
| Session start | A session-start note, plus the last 8 hours of context loaded into memory |
| Session end | Session duration, files touched, errors |
| Terminal command (opt-in) | Command text with secret redaction |

---

## Your First Week

By the end of your first week, Axyome XM will have:

- Captured thousands of development events
- Started your personal XM Wiki (once you ingest a session)
- Calculated your first Developer Intelligence score
- Identified your most-used file patterns

Ask Copilot every Monday:
```
Summarize my development week and give me my DIP score.
```

-> [Power-user tips for getting the most out of Axyome XM](tips.md)
