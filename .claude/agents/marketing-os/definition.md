# Marketing OS — 4-Agent Marketing Team

**Version**: 1.0
**Status**: Phase 1 (Initial deployment, all agents at Level C)

## What This Is

An AI marketing team that replaces the core marketing execution loop: Campaign Manager (brief creation, coordination), Copywriter (all content formats), Market Researcher (competitive intelligence, audience research). The Orchestrator handles triage a Marketing Director would normally do.

**One-liner**: "AI marketing team that researches, strategizes, writes, and coordinates — connected via structured schemas so output builds on output."

## Team Structure

| Agent | Role | Model | Schedule | SOUL File |
|-------|------|-------|----------|-----------|
| **MOS-Orchestrator** | Routes work, triages requests, tracks queue | Opus 4.6 | Always-on | `team/mos-orchestrator.md` |
| **MOS-Strategist** | Campaign architecture, creative briefs, budget allocation | Sonnet 4.6 | On-demand | `team/mos-strategist.md` |
| **MOS-Copywriter** | Voice-aware copy across all formats | Sonnet 4.6 | On-demand | `team/mos-copywriter.md` |
| **MOS-Researcher** | Market analysis, competitor intel, audience profiles | Sonnet 4.6 | On-demand | `team/mos-researcher.md` |

## How the Team Coordinates

```
Request Flow:
  Incoming request → Orchestrator classifies and routes:
    Research task   → Researcher
    Strategy task   → Strategist
    Writing task    → Copywriter
    Full campaign   → Researcher → Strategist → Copywriter (sequential)

  Output flow:
  Researcher produces audience-profile.json or research-report.json →
  Strategist consumes and produces creative-brief.json →
  Copywriter consumes brief and produces finished copy →
  Orchestrator tracks completion in working.md

  Schema handoff is the key: every agent reads a structured JSON,
  never raw prose. This prevents context loss between steps.
```

## Decisions This Team Makes

| Decision | Risk Level | Starting Autonomy | Graduation Path | Owner |
|----------|------------|-------------------|-----------------|-------|
| Route request to agent | Low | C | B after 85% approval | Orchestrator |
| Produce audience profile | Low | C | B after 80% approval | Researcher |
| Produce research report | Low | C | B after 80% approval | Researcher |
| Create creative brief | Medium | C | B after 85% approval | Strategist |
| Create campaign plan | Medium | C | B after 90% approval | Strategist |
| Write copy (any format) | Medium | C | Stay at C | Copywriter |
| Allocate budget | High | C | Stay at C (always human) | Strategist |
| Publish/send anything | High | C | Stay at C (always human) | Orchestrator |

## Data Sources

- [x] Web search (researcher)
- [ ] Reddit (connect `reddit-monitor` MCP — see `.claude/docs/how-to-grow.md`)
- [ ] Google Analytics (Phase 2)
- [ ] Google Search Console (Phase 2)
- [ ] HubSpot CRM (Phase 2)

## KPIs This Team Owns

| KPI | Current | Target | Agent Responsible |
|-----|---------|--------|-------------------|
| Campaigns briefed/month | 0 | 4+ | Strategist |
| Copy deliverables/month | 0 | 15+ | Copywriter |
| Research reports/month | 0 | 4+ | Researcher |
| Brief → Copy turnaround | N/A | <2 hours | Orchestrator |
| Routing accuracy | N/A | >90% | Orchestrator |

## ROI Check

**Phase 1 (current — all at Level C):**
- Hours saved per week: 8 hours (research, brief writing, first drafts)
- Monthly value: ~$2,400 (8 hrs × $75/hr × 4 weeks) — adjust for your hourly rate
- Monthly cost: ~$50 (API costs)
- ROI: **~48:1**

## Anti-Patterns (What NOT to Do)

1. Don't write copy without a brief — always route through Strategist first
2. Don't fabricate competitor data — Researcher must cite sources
3. Don't allocate budget without human approval
4. Don't publish, send, or post anything — always human approval
5. Don't route ambiguous requests — Orchestrator asks one clarifying question
6. Don't skip the schema handoff — always pass structured JSON between agents

## Files

```
.claude/agents/marketing-os/
├── definition.md              # This file
├── autonomy.yaml              # Graduation tracking
└── team/
    ├── mos-orchestrator.md    # Router SOUL
    ├── mos-strategist.md      # Brief/strategy SOUL
    ├── mos-copywriter.md      # Writing SOUL
    └── mos-researcher.md      # Research SOUL

memory/marketing-os/
├── brand-voice.md             # Voice markers + anti-patterns
├── campaign-history.md        # What ran, what worked
└── working.md                 # Current task queue
```
