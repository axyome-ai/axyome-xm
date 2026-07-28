# Power User Tips

Get the most out of Axyome XM with these workflows used daily by the team that built it.

---

## Tip 1 — Monday Morning Briefing

Start every week with a full context reset:

```
@copilot Summarize what I worked on last week and what errors are still unresolved.
```

Copilot uses `axm_get_session_summary` and `axm_get_error_forensics` to give you a 60-second context reset. No more "where was I?"

---

## Tip 2 — Search Before You Debug

Before spending 20+ minutes on a bug, always ask:

```
@copilot Have I seen this error before?
[paste your error message]
```

`axm_find_similar_errors` uses semantic matching across your full error history. If you've fixed this pattern before, you'll get the solution in seconds.

**Why it works:** Even if the exact error message differs, semantic matching finds structurally similar errors. "Cannot read property X of null" matches "Cannot read properties of undefined (reading 'X')".

---

## Tip 3 — Log Decisions As You Make Them

When you choose a technology, pattern, or approach:

```
@copilot Remember that I chose React Query over SWR because of the devtools and cache invalidation API.
```

Three months later:
```
@copilot Why did I choose React Query?
```

`axm_search_decisions` returns your exact reasoning. Essential for teams and solo developers alike.

---

## Tip 4 — Use the Time Machine After Interruptions

Got pulled into a meeting or context-switched for a day? Open **Time Machine** tab:

1. Select today's date
2. See your session broken into chapters: `🏗️ CODING`, `🐛 DEBUGGING`, `🚀 BUILD_DEPLOY`, `🔬 TEST_CYCLE`
3. Click any chapter to see every file, error, and command

Chapters are auto-detected from activity gaps (15+ minute pauses = new chapter).

---

## Tip 5 — Build Your Wiki Automatically

After a significant coding session:

```
@copilot Ingest this session into the wiki.
```

`axm_wiki_ingest` synthesizes entities from your session — services, errors, patterns, decisions — into searchable wiki pages. Over weeks, your wiki becomes a living documentation of your codebase.

Then query it:
```
@copilot What do we know about the payment service?
@copilot Find the wiki page for our database migration pattern.
```

---

## Tip 6 — Track Your Growth Weekly

Every Monday:

```
@copilot How was my developer intelligence score last week compared to the week before?
```

`axm_get_developer_intelligence` returns your DIP score across **Velocity**, **Quality**, **Efficiency**, and **Learning** — with specific, actionable recommendations.

---

## Tip 7 — Export Wiki for Fresh Conversations

At the start of a new Copilot conversation about a complex topic:

```
@copilot Export my wiki for AI context about the auth system.
```

`axm_wiki_export` returns your knowledge base in LLM-optimized format. The new conversation immediately has full context from weeks of prior work.

---

## Tip 8 — Check Anti-Patterns Before Merging

Before submitting a PR:

```
@copilot What anti-patterns am I currently using? How do they trend compared to last week?
```

`axm_get_antipattern_stats` shows detected code quality issues with trend data. Catch regressions before code review.

---

## Tip 9 — Keyboard Shortcut for Dashboard

Add a keybinding for instant dashboard access (`keybindings.json`):

```json
{
  "key": "ctrl+alt+m",
  "command": "axyome-xm.showDashboard"
}
```

---

## Tip 10 — Preflight Before Long Sessions

Before a long coding session (especially after a break):

```
@copilot Run a preflight check and tell me what I was working on yesterday.
```

This calls `axm_preflight` (verifies DB health) and `axm_get_session_summary` simultaneously. 10 seconds of checking saves potential hours of corrupted-state debugging.

---

## Tip 11 — Use the Achievement System as Focus Goals

Check your next achievement:

```
@copilot What achievements am I closest to unlocking?
```

Use it as a micro-goal system. If you're close to **Flow State** (3-hour uninterrupted session), block your calendar. If you're close to **Bug Slayer** (10 errors resolved), tackle the backlog.

---

## Tip 12 — File Hotspot Awareness

Before planning a sprint:

```
@copilot Which files in my project have the most errors and highest churn this month?
```

`axm_get_file_hotspots` surfaces files that deserve refactoring investment — backed by your real activity data, not code complexity estimates alone.

---

## Advanced: Custom Skill-Aware Prompts

Axyome XM tracks your skill levels. Reference them in prompts:

```
@copilot Given my skill level in TypeScript generics, explain how to type this utility function.
```

The AI adapts its explanation depth to your actual experience, not a generic "beginner/expert" toggle.
