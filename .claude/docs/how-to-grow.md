# How to Grow Marketing OS

**Purpose**: A guide to expanding Marketing OS beyond the starter setup. Read this when the base system is running smoothly and you want more.

---

## The Growth Path

```
Phase 1: Base system running (you are here)
  → 4 agents, 5 skills, campaigns running manually

Phase 2: Connect live data
  → Analytics, CRM, and channel data flow in automatically

Phase 3: Automate handoffs
  → Agents trigger each other without manual routing

Phase 4: Expand skill library
  → Add 5-10 more specialized skills

Phase 5: Multi-client at scale
  → Run campaigns for multiple clients from one OS
```

---

## Adding More Skills

Skills are simple markdown files that tell Claude how to handle a specific type of request.

### How to Add a Skill

1. Create a new folder: `.claude/skills/[skill-name]/`
2. Create `SKILL.md` inside it — describe what the skill does and how to invoke it
3. Reference the skill in `CLAUDE.md` under "Skills Available"
4. Test it with: `/[skill-name]` followed by your input

### Skills Worth Adding Next

| Skill | What It Does | Priority |
|-------|-------------|----------|
| `/paid-ads` | Google + Meta campaign strategy, targeting, ad copy in batches | High if you run paid |
| `/seo-audit` | Technical SEO analysis for any page | High if you do SEO |
| `/page-cro` | Conversion optimization recommendations for any page | High for clients |
| `/ab-test-setup` | Design and document A/B test plans | Medium |
| `/competitor-alternatives` | "Company X vs. Company Y" comparison pages | Medium |
| `/programmatic-seo` | Generate 50-150 SEO pages from templates + data | Low/Advanced |

### Skill File Template

```markdown
---
name: [skill-name]
description: [When to use this — what user phrases trigger it]
---

# [Skill Name]

You are [role]. Your goal is [what you produce].

## Before Starting — Gather This
1. [Required context #1]
2. [Required context #2]

## Process
[Step by step process]

## Output Format
[What the output looks like]

## Rules
[Non-negotiable rules for this skill]
```

---

## Connecting Live Data (Phase 2)

Connect data sources via MCP (Model Context Protocol). This lets agents read real data instead of relying on what you paste in.

### How MCP Works

1. You configure an MCP server in Claude Code settings
2. Each skill that needs data includes an `mcp.json` file listing which tools to activate
3. Agents call those tools directly during a session

### High-Value Connections

| Integration | What It Unlocks | Difficulty |
|-------------|-----------------|------------|
| Google Analytics | Real traffic and conversion data in briefs | Medium |
| Google Search Console | Organic ranking data for SEO skills | Medium |
| HubSpot / Salesforce | Pipeline data for campaign ROI | Medium |
| Slack | Agent summaries posted automatically | Easy |
| Reddit (via Apify) | Real audience language for research | Easy |
| Google Sheets | KPI tracking and reporting | Easy |

### Adding MCP to a Skill

Create `mcp.json` in the skill folder:

```json
{
  "mcpServers": {
    "server-name": {
      "description": "What this provides",
      "includeTools": [
        "mcp__server__tool_name"
      ]
    }
  }
}
```

---

## Adding More Agents

The base team has 4 agents. You can add specialists as your needs grow.

### When to Add a New Agent

Add an agent when:
- You have a recurring type of work that doesn't fit the existing 4
- You want dedicated specialization (e.g., paid media only, SEO only, client reporting)
- You're running multiple clients and need a client-specific agent

### How to Add an Agent

1. Copy any existing team file from `.claude/agents/marketing-os/team/`
2. Rename and update the `Name`, `Role`, `Personality`, and `Decision Authority`
3. Add it to `definition.md` team table
4. Add routing logic to `mos-orchestrator.md`
5. Add tracking to `autonomy.yaml`

### Agent Ideas Worth Building

| Agent | Role | Trigger |
|-------|------|---------|
| MOS-Analyst | Data analysis, performance reporting | When you need weekly/monthly reports automated |
| MOS-Client | Client-specific communication drafts | When you have 3+ active clients |
| MOS-Scheduler | Content calendar management | When you're producing 20+ pieces/month |

---

## Multi-Client Setup

To run Marketing OS for multiple clients:

1. Create a folder per client: `brands/[client-slug]/`
2. Copy and fill in `BRAND.md`, `voice.md`, and `clients/` folder
3. When creating a brief, specify `"client_file": "brands/[client-slug]/BRAND.md"`
4. Keep `memory/marketing-os/campaign-history.md` segmented by client (or create per-client memory files)

### Recommended Structure at 3+ Clients

```
brands/
├── your-agency/
│   ├── BRAND.md
│   └── voice.md
├── client-a/
│   ├── BRAND.md
│   ├── voice.md
│   └── memory/
│       ├── brand-voice.md
│       └── campaign-history.md
└── client-b/
    ├── BRAND.md
    └── voice.md
```

---

## Automation Patterns

Once agents are working well manually, you can automate recurring workflows.

### Pattern: Weekly Content Calendar

Every Monday morning:
1. Orchestrator reads campaign-history.md for what's worked
2. Copywriter generates 5 LinkedIn posts for the week
3. Orchestrator sends to Slack for review
4. Owner approves or edits
5. Scheduled for posting

### Pattern: Research Before Every Campaign Brief

Whenever a new brief is requested:
1. Orchestrator checks if audience-profile exists for that segment
2. If not: triggers Researcher first
3. Researcher produces profile
4. Strategist builds brief from the profile

### Pattern: Post-Campaign Debrief

After each campaign completes:
1. Pull final metrics from analytics
2. Researcher synthesizes what worked/failed
3. Orchestrator updates campaign-history.md
4. Lessons added to lessons.md

---

## Reviewing and Pruning

Keep the system lean. Every 90 days:

1. **Review lessons.md** — promote critical rules to CLAUDE.md, remove outdated ones
2. **Review campaign-history.md** — archive campaigns older than 1 year
3. **Review brand-voice.md** — remove patterns that no longer apply
4. **Review skills** — retire skills that haven't been used in 60 days
5. **Review autonomy.yaml** — advance agents that have earned it

The goal is a system that gets smarter and leaner over time, not one that accumulates clutter.
