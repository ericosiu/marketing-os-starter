# Lessons Learned

**Purpose**: Every correction gets turned into a rule. Rules compound. Fewer corrections = more autonomous sessions.

**How to use**: After any correction from the agency owner, add a rule here immediately. Tell them: "Added rule: [one-line summary]."

**When to review**: Monthly. Promote critical rules to CLAUDE.md. Prune outdated ones.

---

## Rule Format

```
### [Category]: [Short title]
- **Trigger:** What happened
- **Rule:** What to always/never do going forward
- **Added:** YYYY-MM-DD
```

### Categories
- `OUTPUT` — Formatting, tone, deliverable structure
- `DATA` — Accuracy, sources, never fabricate
- `CODE` — Patterns, architecture, testing
- `WORKFLOW` — Process, coordination, parallel work
- `BUSINESS` — Priorities, ROI, decision-making

---

## Mandatory Rules (Active From Day One)

### DATA: Never fabricate
- **Trigger:** N/A — pre-loaded rule
- **Rule:** Never fabricate client names, revenue numbers, case study data, or statistics. If you don't have it, say "needs research" or ask.
- **Added:** [Your setup date]

### DATA: Never guess credentials
- **Trigger:** N/A — pre-loaded rule
- **Rule:** Never guess API keys, credentials, or secrets. Ask the owner or check .env files.
- **Added:** [Your setup date]

### OUTPUT: Plain English for owner
- **Trigger:** N/A — pre-loaded rule
- **Rule:** Always summarize recommendations in plain English. No jargon. No code blocks in summaries unless asked.
- **Added:** [Your setup date]

### WORKFLOW: Never publish without approval
- **Trigger:** N/A — pre-loaded rule
- **Rule:** Never publish, post, send, or deploy anything without explicit human approval. Always draft and wait.
- **Added:** [Your setup date]

### BUSINESS: Check priorities first
- **Trigger:** N/A — pre-loaded rule
- **Rule:** Before starting any task, confirm it serves one of the 3 priorities in CLAUDE.md. If it doesn't, ask before proceeding.
- **Added:** [Your setup date]

---

## Agency-Specific Lessons

Add lessons here as they accumulate. The list will grow with each session.

<!-- Example format:
### OUTPUT: [Title]
- **Trigger:** [What the owner corrected]
- **Rule:** [The rule extracted from that correction]
- **Added:** YYYY-MM-DD
-->
