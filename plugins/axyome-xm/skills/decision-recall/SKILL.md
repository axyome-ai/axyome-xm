---
name: decision-recall
description: 'Use when the user asks why something was decided, what was decided, or what root cause was recorded: "why did we choose X?", "what did we decide about Y?", "what was the root cause of Z?". Answers from the recorded decisions first with axm_search_decisions, then past conversations, before reading any file.'
---

# Decision Recall

This skill answers "why" and "what did we decide" questions from the developer's own recorded decisions, not from a guess or a search of the code.

## When to Use

- "Why did we choose this database / library / approach?"
- "What did we decide about retries / naming / the release order?"
- "What root cause did we record for the upload failure?"
- "Did we already rule this option out?"

## Steps

1. **Search the decision log first.** If `axm_search_decisions` is not loaded yet, load it with tool search, and do not search files in the same turn. Call `axm_search_decisions` with the subject of the question as `query` (one or two key words work best). For an older decision, add `hoursAgo` up to `8760` (one year); the default looks back 30 days.
2. **Then search past conversations.** Call `axm_search_sessions` with the same words. A decision is often explained in the chat where it was made.
3. **Then widen the search.** If both are empty, call `axm_hybrid_search` with the key words, then `axm_recall_activity` for the files and commands of that time.
4. **Only now read the repository**, and only to confirm what memory returned: check that the decision still holds in the current code or documents.
5. **Answer with the source.** Quote the decision title, its date and its context. Say whether the answer came from memory, from the repository, or from both.

## Rules

- Do not search files before step 1. The decision log holds the reason; the code shows only the result.
- Memory is a lead, not evidence: say so when the current code no longer matches a recorded decision.
- If nothing is found, say that memory has no record. It does not prove that no decision was made.
- Record a new decision with `axm_log_decision` only when the user asks ("remember that we decided...").
- Other tools are listed by `axm_list_available_tools`.

## Example

User: "Why did we pick SQLite for local storage?"

```
axm_search_decisions  query="SQLite"
→ 2026-03-04  "Local store: SQLite"  context: offline first, one file, no server

axm_search_sessions   query="SQLite storage"
→ chat of 2026-03-04: compared SQLite with a JSON file store
```

Answer: "You decided on SQLite on 4 March (decision 'Local store: SQLite'): offline first, one file, no server to run. The chat that day compared it with a JSON file store. The current storage code still uses it."
