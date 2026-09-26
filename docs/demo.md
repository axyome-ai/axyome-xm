# Demo Scenarios

Real workflows showing what Axyome XM makes possible.

---

## Demo 1 - "I Fixed This Bug Before"

**The scenario:** You're staring at a `TypeError: Cannot read properties of undefined (reading 'map')`. It feels familiar, but you can't remember the fix. Stack Overflow gives you 10 generic answers.

**With Axyome XM:**

```
@copilot Have I seen this error before?
TypeError: Cannot read properties of undefined (reading 'map')
at UserList.tsx:45
```

`axm_find_similar_errors` searches your local error history semantically. 

**Response:**
> "Yes - you fixed this exact pattern on January 15th in `components/TeamList.tsx`.  
> The API was returning `null` instead of an empty array. Fix: add `?? []` to the destructuring:  
> `const { users = [] } = await fetchUsers();`  
> That error was resolved in 8 minutes."

**Time saved:** 20+ minutes of debugging.

---

## Demo 2 - Monday Morning Context Reset

**The scenario:** Monday morning. You worked on something complex last Friday but you can't remember where you left off. Your git log shows 12 commits with messages like "wip" and "fix stuff".

**With Axyome XM:**

```
@copilot Summarize what I was working on last Friday and what's unresolved.
```

**Response:**
> "Friday session (6h 23min, 09:15-17:38):  
> - **Chapter 1 (09:15-11:00)**: Built auth middleware in `packages/api/src/middleware/auth.ts`. Modified 8 files.  
> - **Chapter 2 (11:00-12:30)**: Debugging JWT validation. 3 errors in `auth.ts:92` - still unresolved.  
> - **Chapter 3 (14:00-17:38)**: Added tests for the refresh token flow.  
>  
> **Unresolved:** JWT expiry validation fails for tokens within 30s of expiry.  
> Relevant file: `packages/api/src/middleware/auth.ts:92`"

**Time saved:** 15 minutes of git archaeology.

---

## Demo 3 - "Why Did We Choose This?"

**The scenario:** A new team member (or you, 3 months later) asks why PostgreSQL instead of MongoDB.

**With Axyome XM:**

```
@copilot Why did I choose PostgreSQL over MongoDB for this project?
```

**Response:**
> "Decision logged December 14th:  
> **Choice:** PostgreSQL  
> **Rationale:** ACID compliance required for financial transactions. Team more familiar with SQL.  
> **Rejected:** MongoDB - unstructured data format not needed; joins would have been awkward.  
> **Context:** Evaluated during the data layer design sprint."

**Time saved:** 5-10 minutes of Slack archaeology or asking the team.

---

## Demo 4 - Building Your Wiki Automatically

**The scenario:** After a week of intensive development, your project knowledge exists only in your head.

**With Axyome XM:**

```
@copilot Ingest this week's sessions into the wiki.
```

`axm_wiki_ingest` synthesizes entities from your sessions automatically.

**Result:**
> Created 7 wiki pages:
> - `AuthMiddleware.md` - entity with linked sessions and error history
> - `jwt-validation-error.md` - error page with proposed resolution
> - `PostgreSQL.md` - entity with your architecture decision
> - `RefreshToken.md` - concept page with implementation pattern
> - `use-zod-for-validation.md` - pattern page
> - `packages-api.md` - entity with file hotspot data
> - `test-refresh-token-flow.md` - pattern from test activity

Now when someone asks:
```
@copilot What do we know about the auth system?
```

The answer draws from a week's worth of documented knowledge - not just this conversation.

---

## Demo 5 - Developer Intelligence Weekly Review

**The scenario:** You want to know if you're actually getting better as a developer week over week.

**With Axyome XM:**

```
@copilot How was my developer intelligence score last week versus the week before?
```

**Response:**
> "**Week of Jul 21-27** DIP Score: **72/100** up from 68  
>  
> **Velocity**: 85 (up 8) - 23 commits, 1,240 LOC/day average  
> **Quality**: 71 (up 3) - Error rate down 15%, avg time-to-fix 12min  
> **Efficiency**: 68 (up 5) - ATI ratio 3.2 tools/prompt  
> **Learning**: 65 (down 2) - 3 new patterns this week vs 5 last week  
>  
> **Recommendation:** Your error rate improved but Learning dipped. Schedule time for one new topic (e.g., TypeScript advanced types - your confidence is at 38% there)."

---

## Demo 6 - Pre-Debug Context Lookup

**The scenario:** A colleague Slacks you: "The auth service is broken in staging." You haven't touched it in 2 weeks.

**With Axyome XM:**

```
@copilot What do I know about the auth service? Any recent errors or changes?
```

Copilot calls `axm_wiki_query`, `axm_find_similar_errors`, and `axm_recall_activity` in parallel.

**Response:**
> "**Auth service context:**
> - Last modified: July 12 - added refresh token rotation
> - 3 historical errors, all resolved: JWT expiry edge case (fixed Jan 15), CORS headers missing (fixed Feb 3), token blacklist race condition (fixed Mar 28)
> - Wiki page: `AuthMiddleware.md` - shows the 30s expiry window is a known edge case
> - Relevant decision: 'Chose stateless JWT over sessions for horizontal scaling' (logged Dec 14)
>
> **Likely culprit:** The 30s JWT expiry window issue - see the January 15 fix."

**Time saved:** 30+ minutes of code archaeology.

---

## GIF Demo Storyboard

For the animated `demo.gif` in the README:

| Frame | Duration | Content |
|-------|----------|---------|
| 1 | 0-5s | Copilot Chat open. User types: "Have I seen this error before? TypeError: Cannot read X of undefined" |
| 2 | 5-8s | Loading indicator + tool call shown: `axm_find_similar_errors` |
| 3 | 8-16s | Results appear: past error with timestamp (Jan 15), file path, and fix summary |
| 4 | 1622s | User clicks Axyome XM icon - Time Machine tab - colored chapter bar appears |
| 5 | 2228s | User clicks a DEBUGGING chapter - event list expands: files, errors, commands |
| 6 | 28-32s | Final screen: DIP score panel showing 72/100 with 4 pillar bars |

**Caption text:** `"45 MCP tools. Zero cloud. Your entire dev history at your fingertips."`
