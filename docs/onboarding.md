# Getting Started: Your First 10 Minutes

Axyome XM captures development context automatically from the moment it's installed. Here's how to go from zero to productive.

---

## Step 1 — Open the Dashboard (30 seconds)

Click the **Axyome XM icon** in the Activity Bar (left sidebar — it looks like a brain).

You'll see the Dashboard with tabs:

| Tab | What's inside |
|-----|--------------|
| **Activity** | Files saved, git commits, errors, terminal commands |
| **Intel** | Developer Intelligence Platform score and recommendations |
| **Time Machine** | Replay past sessions chapter by chapter |
| **Wiki** | Your auto-generated knowledge base |
| **Analytics** | ATI score, productivity heatmap, tool usage |
| **Achievements** | 12 unlockable developer badges |

---

## Step 2 — Complete the Onboarding Missions (3 minutes)

Click the **Onboarding** tab. You'll see 4 guided missions:

| Mission | What you learn |
|---------|---------------|
| 🧠 **First Memory** | Let Axyome XM capture your first event (just save any file) |
| 🔍 **First Recall** | Ask Copilot "What did I work on today?" |
| 📝 **Log a Decision** | Tell Copilot to remember an architectural choice |
| ⭐ **First Achievement** | Unlock your first badge automatically |

Complete all 4 to finish onboarding.

---

## Step 3 — Ask Copilot About Your Work (2 minutes)

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

Copilot uses your local memory to answer with **real context** from your sessions — not generic advice.

---

## Step 4 — Enable Terminal Capture (Optional, 1 minute)

Terminal capture is opt-in for privacy. To enable:

1. Open VS Code Settings (`Ctrl+,`)
2. Search for `axyome terminal`
3. Enable **Axyome XM: Terminal Capture**

Terminal commands are stored locally with **automatic secret redaction** — values matching patterns like `*_TOKEN`, `*_KEY`, `*_PASSWORD`, AWS credentials, and Bearer tokens are replaced with `[REDACTED]` before storage.

---

## Step 5 — Initialize Workspace Memory (2 minutes)

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
| Session start | Auto-summary of last 24h work |
| Session end | Session duration, files touched, errors |
| Terminal command (opt-in) | Command text with secret redaction |

---

## Your First Week

By the end of your first week, Axyome XM will have:

- ✅ Captured thousands of development events
- ✅ Built semantic embeddings for fast recall
- ✅ Started your personal XM Wiki
- ✅ Calculated your first Developer Intelligence score
- ✅ Identified your most-used file patterns

Ask Copilot every Monday:
```
Summarize my development week and give me my DIP score.
```

→ [Power-user tips for getting the most out of Axyome XM](tips.md)
