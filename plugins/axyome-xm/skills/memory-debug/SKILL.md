---
name: memory-debug
description: 'Memory-enhanced debugging skill for axyome-xm. Use when investigating errors, exceptions, or issues. Searches past errors via axm_find_similar_errors, finds resolution patterns via axm_search_patterns, checks anti-patterns via axm_get_antipattern_stats, and provides evidence-based debugging using Axyome XM tools.'
---

# Memory-Enhanced Debugging

This skill provides a systematic debugging workflow that leverages AI memory to accelerate root cause analysis.

## When to Use

- User encounters an error, exception, or unexpected behavior
- User asks "have I seen this before?"
- User is debugging a regression
- User pastes a stack trace or error message

## Debugging Workflow

### Phase 1: Memory Recall (MANDATORY — do this first)

1. **Search for similar past errors**:
   ```
   axm_find_similar_errors(errorText="<the error text>", limit=5)
   ```

2. **Check for anti-patterns**:
   ```
   axm_search_patterns(query="<error keywords>")
   axm_get_antipattern_stats(hoursAgo=168)
   ```

3. **Get error forensics context**:
   ```
   axm_get_error_forensics(hoursAgo=48, includeResolved=true)
   ```

4. **Check file risk**:
   ```
   axm_get_file_hotspots(hoursAgo=168)
   ```

### Phase 2: Git-First Investigation

```bash
git status                           # Check for uncommitted changes
git diff <affected-file>             # What changed locally?
git log --oneline -10 -- <file>      # Recent commit history
```

### Phase 3: Analyze & Fix

Use evidence from Phase 1 and 2 to:
- Identify if this is a known issue vs. new
- Compare with past resolution strategies
- Apply the fix that worked before (if applicable)
- Use `axm_get_skills()` to adapt explanation depth to user level

### Phase 4: Record Resolution

After fixing:
```
axm_observe(type="custom", summary="Fixed: <error description>. Root cause: <cause>. Fix: <what was done>")
axm_feedback(signal="accepted")  # If user confirms fix works
```

## Example Error Investigation

```
User: "Getting SQLITE_BUSY error when running backfill"

Step 1: axm_find_similar_errors(errorText="SQLITE_BUSY")
  → Found 3 past occurrences

Step 2: axm_search_patterns(query="sqlite busy lock")
  → Anti-pattern: Running DB scripts while VS Code is open

Step 3: Resolution from memory:
  → "Close VS Code first, then run script"

Step 4: axm_observe(type="custom", summary="SQLITE_BUSY resolved by closing VS Code")
```
