# Proactive Marketing OS Routing

## Purpose

This file makes skills invoke AUTOMATICALLY based on intent detection. Claude should NEVER wait for a slash command when it can detect what the user needs.

## Golden Rule

**If a user's request matches any pattern below, invoke the skill immediately. Do not ask "Would you like me to use /skill-name?" — just use it.**

---

## Intent -> Skill Routing Table

### Tier 1: High-Confidence Auto-Invoke

These patterns should ALWAYS trigger the skill without asking:

| User Says Something Like... | Invoke | Why |
|----------------------------|--------|-----|
| "write copy for [page]", "I need a landing page", "rewrite this page", "headline ideas" | `/copywriting` | Direct copy request |
| "write emails for", "drip campaign", "welcome sequence", "nurture flow", "re-engage" | `/email-sequence` | Direct email request |
| "LinkedIn post", "tweet this", "social calendar", "content for Instagram", "thread about" | `/social-content` | Direct social request |
| "who are our competitors", "competitive landscape", "market analysis", "audience research" | `/research` | Direct research request |
| "plan a campaign", "what should we say", "creative brief", "campaign for [product]" | `/campaign-brief` | Direct brief request |

### Tier 2: Compound Intent (Multi-Skill Chains)

When a request is bigger than one skill, chain them automatically:

| User Says Something Like... | Chain | Flow |
|----------------------------|-------|------|
| "build me a campaign for [X]" | Research -> Brief -> Copy | Full pipeline |
| "I need to promote [product]" | Research -> Brief -> Copy + Social | Full campaign |
| "launch [product] next month" | Research -> Brief -> Copy + Email + Social | Launch pipeline |
| "we need more leads from [channel]" | Research -> Brief -> skill for that channel | Channel-specific |
| "our emails aren't working" | Research (audience) -> Email Sequence | Email optimization |

**For compound requests:** Start with the first skill in the chain. After it completes, immediately proceed to the next without asking "should I continue?" — the user asked for the full thing.

### Tier 3: Implicit Intent (Read Between the Lines)

| User Says... | What They Really Need | Invoke |
|-------------|---------------------|--------|
| "[Product] needs more users" | Growth campaign | Research -> Brief -> multi-channel |
| "this client is churning" | Retention campaign | Research -> Email Sequence |
| "we're losing to [competitor]" | Competitive positioning | Research |
| "we need content for next week" | Weekly content batch | Social Content |

---

## How to Handle Ambiguity

If the request could map to multiple skills and you genuinely can't tell which one:

1. **Don't ask "which skill should I use?"** — the user doesn't think in skills
2. **Instead, ask about the OUTCOME**: "Are you trying to get more signups, improve existing conversion, or create content?"
3. Based on the answer, route to the right skill silently

---

## Memory Check on Every Marketing Request

Before executing any marketing skill, quickly check:
- `memory/marketing-os/brand-voice.md` — to maintain voice consistency
- `memory/marketing-os/campaign-history.md` — to avoid repeating what failed

This takes 2 seconds and prevents starting from scratch when prior work exists.
