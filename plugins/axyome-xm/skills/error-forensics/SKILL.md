---
name: error-forensics
description: 'Deep error analysis skill for axyome-xm. Use for comprehensive error pattern analysis — finds similar past errors via axm_find_similar_errors, calculates resolution statistics via axm_error_resolution_stats, identifies error hotspots via axm_get_file_hotspots, and generates actionable remediation plans using Axyome XM tools.'
---

# Error Forensics Skill

Perform deep forensic analysis of errors using AI memory for pattern recognition and resolution history.

## When to Use

- User asks "analyze my errors" or "error patterns"
- Multiple errors occurring in same file/module
- Recurring errors that seem to come back
- Post-incident analysis

## Analysis Workflow

### Step 1: Gather Error Data

```
axm_get_error_forensics(hoursAgo=168, includeResolved=true)
axm_error_resolution_stats(hoursAgo=168, groupBy="severity")
axm_error_resolution_stats(hoursAgo=168, groupBy="file")
```

### Step 2: Find Patterns

```
axm_get_antipattern_stats(hoursAgo=168, includeTrend=true)
axm_get_file_hotspots(hoursAgo=168)
axm_search_patterns(query="error")
```

### Step 3: Semantic Similarity

For each unique error type, find similar past occurrences:
```
axm_find_similar_errors(errorText="<error>", limit=5)
axm_semantic_search(query="<error context>", threshold=0.5)
```

### Step 4: Generate Report

```
📋 ERROR FORENSICS REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━

🔴 Error Summary
   Total Errors (7d): [N]
   Resolved: [N] ([%])
   Unresolved: [N]

⏱️ Resolution Performance
   Avg Time to Fix: [X hours]
   Fastest: [Y min]
   Slowest: [Z hours]

🔥 Error Hotspots
   1. [file] — [N errors, severity distribution]
   2. [file] — [N errors]

🔄 Recurring Patterns
   [errors that keep coming back with timestamps]

🚫 Anti-Pattern Correlations
   [anti-patterns that correlate with errors]

💡 Remediation Plan
   1. [highest-impact fix]
   2. [preventive measure]
   3. [monitoring recommendation]
```

### Step 5: Record Analysis

```
axm_observe(type="custom", summary="Error forensics: [key findings]")
axm_log_decision(decision="Remediation plan: [top action]", rationale="Based on error forensics analysis")
```
