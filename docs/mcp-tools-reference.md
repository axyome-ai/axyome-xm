# MCP Tool Reference

Axyome XM provides **45 MCP tools** (`axm_*`) automatically available in GitHub Copilot (VS Code 1.100+). No configuration required.

> **How to use**: Just ask Copilot naturally. Examples are shown for each tool.

---

## Memory & Recall

### `axm_recall_activity`
Search past work: files edited, errors encountered, terminal commands, git commits.

| Parameter | Type | Description |
|-----------|------|-------------|
| `query` | string | What to search for |
| `hoursAgo` | number | Look back window (default: 24) |
| `eventType` | string | Filter: `file`, `terminal`, `diagnostic`, `git` |
| `limit` | number | Max results (default: 20) |

**Example prompts:**
```
What files did I edit yesterday?
What errors did I have in the last 2 hours?
What git commits did I make this week?
```

---

### `axm_get_session_summary`
Summarize work in a time window with files, commands, and key events.

| Parameter | Type | Description |
|-----------|------|-------------|
| `hours` | number | Hours to look back (default: 8) |
| `date` | string | Specific date: `"2026-07-20"` |
| `since` | string | ISO datetime start |
| `until` | string | ISO datetime end |
| `includeCode` | boolean | Include code snippets |
| `includeTerminal` | boolean | Include terminal history |

**Example prompts:**
```
What did I work on today?
Summarize last Friday's session.
What was I doing between 2pm and 5pm yesterday?
```

---

### `axm_search_sessions`
Search past Copilot conversations using hybrid semantic + keyword search.

| Parameter | Type | Description |
|-----------|------|-------------|
| `query` | string | What to search for |
| `hoursAgo` | number | Time window (default: 30 days) |
| `limit` | number | Max results |
| `mode` | string | `hybrid`, `semantic`, or `keyword` |

**Example prompts:**
```
Find our conversation about the auth bug.
What did we discuss about database migrations?
Search my chat history for Redux patterns.
```

---

### `axm_search_patterns`
Find recurring coding habits and patterns in your work history.

**Example prompts:**
```
What patterns do I use for error handling?
How do I usually structure async functions?
What testing patterns do I repeat?
```

---

## Error Intelligence

### `axm_find_similar_errors`
Find similar past errors using semantic matching — the most powerful debugging tool.

| Parameter | Type | Description |
|-----------|------|-------------|
| `errorText` | string | The error message to match |
| `hoursAgo` | number | Look back window (default: 720 = 30 days) |
| `includeResolved` | boolean | Include resolved errors (default: true) |
| `limit` | number | Max results (default: 5) |

**Example prompts:**
```
Have I seen this error before: TypeError: Cannot read properties of undefined (reading 'map')
Find similar errors to "ECONNREFUSED 127.0.0.1:5432"
Have I fixed this pattern before?
```

---

### `axm_get_error_forensics`
Analyze recent errors with full context — what was happening before each error.

| Parameter | Type | Description |
|-----------|------|-------------|
| `hoursAgo` | number | Look back window (default: 168 = 7 days) |
| `filePath` | string | Filter to specific file |
| `limit` | number | Max errors (default: 20) |

**Example prompts:**
```
What caused my errors today?
Analyze errors in src/api/users.ts this week.
Show me unresolved errors from the last 24 hours.
```

---

### `axm_error_resolution_stats`
Statistics on how quickly you resolve different types of errors.

**Example prompts:**
```
How long does it take me to fix TypeScript errors?
Show my error resolution trends this week.
What severity errors take me longest to fix?
```

---

### `axm_get_error_playbook`
Auto-generated fix suggestions based on learned error-resolution patterns.

**Example prompts:**
```
How did I fix this error before?
Show me the fix playbook for SQLITE_BUSY errors.
What fixes worked for undefined property errors?
```

---

## Decisions & Knowledge

### `axm_log_decision`
Remember a decision, preference, or architectural choice.

| Parameter | Type | Description |
|-----------|------|-------------|
| `decision` | string | What was decided |
| `title` | string | Short title |
| `context` | string | Why this was needed |
| `rationale` | string | Why this choice |
| `alternatives` | string | Other options considered |

**Example prompts:**
```
Remember that I chose Zod over Joi for validation because of TypeScript inference.
Note that we decided to use PostgreSQL over MongoDB for this project.
Remember I prefer arrow functions over function declarations.
```

---

### `axm_search_decisions`
Search past logged decisions and architectural choices.

**Example prompts:**
```
What did I decide about the database?
Why did I choose this authentication approach?
What are my preferences for error handling?
```

---

### `axm_wiki_query`
Search your personal XM Wiki — auto-generated from session data.

| Parameter | Type | Description |
|-----------|------|-------------|
| `question` | string | What to look up |
| `maxPages` | number | Max results (default: 5) |

**Example prompts:**
```
What do we know about the AuthService?
Find wiki pages about database migrations.
What patterns are documented for async error handling?
```

---

### `axm_wiki_read`
Read a specific wiki page.

**Example prompts:**
```
Show the wiki page for MemoryService.
Read the wiki entry on jwt-validation-error.
```

---

### `axm_wiki_ingest`
Generate wiki entities from recent session data.

**Example prompts:**
```
Ingest this week's sessions into the wiki.
Build wiki pages from today's coding session.
```

---

### `axm_wiki_update`
Create or update a wiki page manually.

---

### `axm_wiki_export`
Export your full wiki in LLM-optimized format for AI context injection.

**Example prompts:**
```
Export my wiki for AI context.
Give me my full knowledge base.
```

---

## Developer Intelligence

### `axm_get_developer_intelligence`
Full Developer Intelligence Platform (DIP) score with recommendations.

Measures 4 pillars: **Velocity**, **Quality**, **Efficiency**, **Learning**.

**Example prompts:**
```
How am I doing this week?
Show my developer intelligence score.
What should I improve as a developer?
```

---

### `axm_get_skills`
Inferred skill levels by programming category based on your activity.

**Example prompts:**
```
What are my strongest skills?
How good am I at TypeScript error handling?
What should I practice more?
```

---

### `axm_get_antipattern_stats`
Anti-patterns you're using — with trend data.

**Example prompts:**
```
What bad patterns am I using?
Show my anti-pattern detection stats.
Am I getting better or worse at avoiding anti-patterns?
```

---

### `axm_get_file_hotspots`
Files with high churn, many errors, or technical debt.

**Example prompts:**
```
Which files need the most refactoring?
What are my problem files this week?
Show high-risk files in the project.
```

---

### `axm_get_prompt_insights`
Analysis of your AI prompting patterns and habits.

**Example prompts:**
```
How do I use AI tools?
What are my most common prompt types?
How can I improve my AI interactions?
```

---

## Search

### `axm_semantic_search`
Search memory by meaning, not just keywords.

**Example prompts:**
```
Find authentication-related patterns.
Search for database optimization decisions.
```

---

### `axm_hybrid_search`
Best-of-both: combines semantic vector search with FTS5 keyword matching.
Ideal for finding specific identifiers like bug IDs.

**Example prompts:**
```
Find bug-123 in my history.
Search for JIRA-456 across all my sessions.
```

---

### `axm_find_similar`
Find items semantically similar to given text.

**Example prompts:**
```
What's similar to this error message?
Find code similar to this pattern.
```

---

## Feedback & Observations

### `axm_feedback`
Record whether a suggestion was accepted, rejected, or modified.

| Signal | When to use |
|--------|-------------|
| `accepted` | "Thanks!" / "Perfect!" / "Exactly!" |
| `rejected` | "No" / "Wrong" / "Not what I wanted" |
| `modified` | "Close, but I changed it to..." |

---

### `axm_observe`
Record a significant event or milestone.

**Example prompts:**
```
Note that I fixed the auth bug.
I just deployed to production.
Record that I finished the API redesign.
```

---

## Analytics

### `axm_get_session_analytics`
ATI (AI Tool Index) metrics and session breakdown.

**Example prompts:**
```
Show my session analytics this week.
What's my tools-per-prompt ratio?
```

---

### `axm_get_token_stats`
Token usage and AI cost estimates.

---

### `axm_get_tool_analytics`
Detailed breakdown of which MCP tools you use most.

---

### `axm_get_wellness`
Cognitive load score, flow state analysis, work boundary adherence.

**Example prompts:**
```
How's my developer wellness?
Am I in flow state today?
Show my work boundary adherence.
```

---

## Achievements

### `axm_get_achievements`
View your unlocked achievement badges and progress toward the next ones.

**Example prompts:**
```
What achievements have I unlocked?
Show my badge progress.
How close am I to the next achievement?
```

---

## System

### `axm_health`
Check the MCP server and database status.

**Example prompts:**
```
Is the memory server healthy?
Check the Axyome XM system status.
```

---

### `axm_preflight`
Run pre-flight checks on all database tables and indexes.

**Example prompts:**
```
Run a preflight check before my coding session.
Verify the memory system is ready.
```

---

### `axm_get_stats`
Memory database statistics — event counts, table sizes, storage used.

**Example prompts:**
```
How much data is in my memory?
What's stored in the database?
```

---

## Advanced

### `axm_chunk_document`
Chunk large documents for better embedding precision.

### `axm_generate_embeddings_batch`
Generate semantic embeddings for items that don't have them yet.

### `axm_get_learned_patterns`
Patterns learned from past sessions (error→fix sequences, refactoring habits).

### `axm_get_pattern_suggestions`
Get fix suggestions based on learned error-resolution patterns.

### `axm_get_defect_predictions`
Risk scores for files based on churn, error history, and complexity.

### `axm_get_context_snapshot`
Compact context snapshot for the current file — errors, decisions, style patterns.

---

## Tool Count by Category

| Category | Count |
|----------|-------|
| Memory & Recall | 4 |
| Error Intelligence | 4 |
| Decisions & Wiki | 7 |
| Developer Intelligence | 5 |
| Search | 3 |
| Feedback & Observations | 2 |
| Analytics | 4 |
| Achievements | 1 |
| System | 3 |
| Advanced | 7 |
| Sessions & Training | 5 |
| **Total** | **45** |
