---
name: code-review-memory
description: 'Memory-augmented code review skill for axyome-xm. Use when reviewing code changes — checks past patterns via axm_search_patterns, anti-patterns via axm_get_antipattern_stats, file hotspots via axm_get_file_hotspots, and developer skill levels via axm_get_skills to provide calibrated, evidence-based reviews using Axyome XM tools.'
---

# Memory-Augmented Code Review

Enhance code reviews with AI memory context — past patterns, known anti-patterns, and file risk analysis.

## When to Use

- User asks for a code review
- PR review needed
- User asks "is this code good?" or "review this"

## Review Workflow

### Step 1: Gather Context

```
axm_get_file_hotspots(hoursAgo=168)      # Is this a risky file?
axm_get_antipattern_stats(hoursAgo=168)   # What anti-patterns are common?
axm_search_patterns(query="<module>")     # Past patterns in this area
axm_get_skills(category="<relevant>")     # Adapt review depth to skill level
```

### Step 2: Check for Known Issues

For each significant code pattern in the review:
```
axm_search_patterns(query="<pattern>")
axm_find_similar(text="<code snippet>", limit=5)
```

### Step 3: Review with Memory Context

Provide a review that considers:

1. **Past anti-patterns**: Flag code that matches known anti-patterns
2. **File risk**: Note if the file is a hotspot (high churn, high error rate)
3. **Consistency**: Compare against established patterns in memory
4. **Skill-calibrated**: Adjust feedback depth based on skill level

### Step 4: Structured Output

```
📝 MEMORY-ENHANCED CODE REVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📁 File Risk: [Low/Medium/High] (based on hotspot analysis)
🚫 Anti-pattern Matches: [count]

🔍 ISSUES:

1. [Critical] <issue with reference to past anti-pattern>
   History: "This pattern caused [past incident] on [date]"

2. [Warning] <potential issue>
   Similar code: Found [N] similar patterns in memory

3. [Suggestion] <improvement>
   Based on: Established pattern from [past example]

✅ GOOD PRACTICES:
   [code that follows established patterns]

💡 RECOMMENDATIONS:
   [calibrated to user's skill level]
```

### Step 5: Record Review

```
axm_observe(type="custom", summary="Code review for [file]: [key findings]")
```
