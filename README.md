# Marketing OS for Claude Code

**An AI marketing team you can clone and run in 30 minutes.**

4 specialized agents. 5 skills. Structured handoffs. Memory that compounds. No code required.

[![Setup Time](https://img.shields.io/badge/setup-30%20minutes-brightgreen)]()
[![Agents](https://img.shields.io/badge/agents-4%20specialists-blue)]()
[![Skills](https://img.shields.io/badge/skills-5%20included-orange)]()
[![License](https://img.shields.io/badge/license-MIT-lightgrey)]()

---

## The Problem

You're using Claude for marketing, but every session starts from scratch. You re-explain your brand voice. You re-describe your audience. You copy-paste context between chats. The AI doesn't remember what worked last time or what failed.

You have a powerful tool with no operating system.

## The Solution

Marketing OS gives you a structured system inside Claude Code:

- **4 AI specialists** that hand off work to each other using structured JSON schemas
- **Persistent memory** that accumulates brand voice, campaign history, and audience intelligence across sessions
- **Proactive routing** that detects what you need and invokes the right skill automatically
- **Quality control** built into every content output

After 10 campaigns, the system knows your brand better than a new hire would.

---

## What's Inside

```
marketing-os-starter/
├── CLAUDE.md                    # The brain — your agency context, priorities, rules
├── .claude/
│   ├── agents/marketing-os/     # 4 specialist agents with defined roles
│   ├── skills/                  # 5 marketing skills (research, briefs, copy, social, email)
│   └── rules/                   # Proactive intent routing (auto-invokes skills)
├── brands/                      # Your agency + client brand files
├── memory/                      # Persistent memory (voice, campaigns, task queue)
└── schemas/                     # JSON contracts for agent-to-agent handoffs
```

### The 4 Agents

| Agent | Role | What It Does |
|-------|------|-------------|
| **Orchestrator** | Traffic controller | Routes every request to the right specialist. Tracks pipeline progress. Never writes copy — only routes and coordinates. |
| **Researcher** | Intelligence gatherer | Produces audience profiles and competitive analysis. Every finding is cited and confidence-rated. |
| **Strategist** | Campaign architect | Turns research into structured creative briefs with specific deliverables, proof points, and constraints. |
| **Copywriter** | Execution engine | Writes copy from briefs with brand voice enforcement. Never writes without a brief. Never uses vague marketing language. |

### The Pipeline

```
You: "I need to promote our new product"

  Orchestrator detects "promote" → triggers full pipeline:

  1. Researcher → audience-profile.json (who to target, what they care about)
  2. Strategist → creative-brief.json (what to say, where, with what proof)
  3. Copywriter → finished copy (landing page, emails, social posts)

  Each agent reads the previous agent's structured output.
  No context lost. No re-explaining.
```

### The 5 Skills

| Skill | Trigger Phrases | Output |
|-------|----------------|--------|
| `/research` | "who's our audience", "competitive landscape", "market analysis" | Audience profiles, research reports (JSON) |
| `/campaign-brief` | "plan a campaign", "what should we say", "creative brief" | Creative briefs with deliverable specs (JSON) |
| `/copywriting` | "write copy for", "landing page", "headline ideas" | Finished marketing copy |
| `/social-content` | "LinkedIn post", "tweet this", "content calendar" | Platform-specific social content |
| `/email-sequence` | "drip campaign", "welcome sequence", "nurture flow" | Multi-email sequences with subject lines |

**You don't need to remember these commands.** The proactive routing system detects your intent and invokes the right skill automatically.

---

## Setup (30 Minutes)

### Prerequisites
- [Claude Code](https://claude.ai/download) installed
- Claude Pro subscription or higher
- Git

### Step 1: Clone

```bash
git clone https://github.com/ericosiu/marketing-os-starter.git my-marketing-os
cd my-marketing-os
```

### Step 2: Fill in CLAUDE.md (10 min)

Open `CLAUDE.md` and replace every `[FILL IN]` placeholder:

- Your agency name and primary service
- Your 3 priorities for the next 12 months
- Your minimum ROI bar
- Your client portfolio

**This is the most important file.** Claude reads it at the start of every session.

### Step 3: Set up your brand (10 min)

Fill in `brands/your-agency/BRAND.md`:
- Agency overview and value proposition
- Public-facing client examples

Fill in `brands/your-agency/voice.md`:
- Tone and voice markers
- Words to always/never use
- 2-3 copy examples that nail your voice

### Step 4: Add your first client (5 min)

Copy `brands/your-agency/clients/example-client/` to a new folder with your client's name. Fill in their details.

### Step 5: Run it

```bash
claude
```

Then just talk to it naturally:

```
"I need to promote our client's new SaaS product to marketing directors"
```

The system will automatically research the audience, create a campaign brief, and write the copy — checking your brand voice and campaign history at every step.

---

## How Memory Works

Three files persist across every session:

| File | What It Does | How It Helps |
|------|-------------|-------------|
| `brand-voice.md` | Accumulates voice patterns from approved copy | After 5 campaigns, the Copywriter matches your voice without direction |
| `campaign-history.md` | Logs what ran and what worked | The Strategist never repeats a failed approach without flagging it |
| `working.md` | Tracks the current task queue | Pick up exactly where you left off in any session |

**The compounding effect**: Session 1 requires full context. Session 10 feels like working with someone who knows your business. Session 50 feels like a senior team member.

---

## Your First Campaign (Complete Walkthrough)

**Scenario**: Generate 10 demo calls via LinkedIn for a B2B SaaS client.

**You type**:
```
Build me a LinkedIn campaign to get 10 demo calls for [client].
They sell [product] to companies with $5M-$20M ARR.
Budget: $3,000. Deadline: 30 days.
```

**What happens automatically**:

1. Orchestrator detects "campaign" + "LinkedIn" → triggers full pipeline
2. Researcher produces audience profile (pain points, language, competitors)
3. Strategist produces creative brief (messaging, proof points, 5 ad specs)
4. Copywriter produces 5 LinkedIn ad variations + landing page copy
5. You review, approve, and deploy

**Total time**: 20-40 minutes for what used to take 2-3 days.

---

## Growing From Here

| When This Happens... | Add This |
|---------------------|----------|
| You need paid ads strategy | `/paid-ads` skill |
| You want SEO audits | `/seo-audit` skill |
| You need page-level CRO | `/page-cro` skill |
| You connect Google Analytics | GA4 MCP server |
| You connect your CRM | HubSpot MCP server |
| You need weekly reports | MOS-Analyst agent |

Full expansion guide: `.claude/docs/how-to-grow.md`

---

## Marketing Frameworks Included

Every skill and agent is built on battle-tested marketing frameworks — not generic prompts.

| Framework | What It Does | Used By |
|-----------|-------------|---------|
| **6 Proven Hook Formulas** | Tested content hooks that stop the scroll — Observation+Stat, Contrarian Challenge, Harsh Reality, and more | Copywriter, Social Content |
| **BOFU Domination Framework** | Optimize for revenue, not traffic. 6 content categories that convert 10-50x better than top-of-funnel. | Researcher, Strategist |
| **7 Exponential Growth Playbooks** | Free Tool Flywheel, LLM Citation Strategy, Vertical Domination, Programmatic SEO 2.0, Language Arbitrage, Marketing Mistakes Content, Data Network Effects | Strategist, Campaign Brief |
| **Activation & Retention Science** | 5-move activation playbook + 3 user segments (Ghost Users, One-and-Done, Power Users) with specific interventions for each | Email Sequence, Campaign Brief |
| **Price Ladder Architecture** | Strategic price escalation with signal-based upsell triggers | Email Sequence, Strategist |
| **Revenue-First Measurement** | Every campaign measured against revenue outcomes, not vanity metrics | Campaign Brief, Strategist |

All frameworks live in `memory/marketing-os/marketing-wisdom.md` — the master reference file every agent consults.

---

## How It's Different from Just Using Claude

| Without Marketing OS | With Marketing OS |
|---------------------|-------------------|
| Re-explain brand voice every session | Brand voice loaded automatically |
| Copy-paste context between chats | Structured JSON handoffs between agents |
| Start from scratch every time | Campaign history informs every brief |
| Generic marketing language | Voice-enforced copy with banned word lists |
| You manage the workflow | Orchestrator manages the pipeline |
| One-shot outputs | Research → Strategy → Copy pipeline |
| Generic marketing advice | Battle-tested frameworks baked into every skill |

---

## FAQ

**Do I need to be technical?**
No. You fill in text files and talk to Claude naturally. No code.

**What does it cost?**
Your Claude subscription. No additional API costs for the base setup.

**Can I use it for multiple clients?**
Yes. Create a `brands/[client]/` folder for each. Reference the right client when you start a campaign.

**What if the output is bad?**
Add the correction to `.claude/docs/lessons.md`. The system loads these rules every session, so it learns permanently from every mistake.

**How is this different from ChatGPT custom instructions?**
This is a multi-agent system with structured handoffs, persistent memory, and proactive skill routing. Custom instructions are a paragraph of text. This is an operating system.

---

## Credits

Created by [Eric Siu](https://twitter.com/ericosiu), CEO of [Single Grain](https://www.singlegrain.com) — a marketing agency that uses Claude Code to run 5-7 parallel AI sessions daily.

Individual skill patterns inspired by [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills). Marketing OS adds the agent layer, persistent memory, proactive routing, structured schema handoffs, and proprietary marketing frameworks.

If you find this useful, give it a star and share it with someone running a marketing team.

---

## License

MIT — use it however you want. If you improve it, consider opening a PR.
