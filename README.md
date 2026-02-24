# Marketing OS for Claude Code

**An AI marketing team you can clone and run in 30 minutes.**

4 specialized agents. 5 skills. Battle-tested frameworks. Memory that compounds. No code required.

[![Setup Time](https://img.shields.io/badge/setup-30%20minutes-brightgreen)]()
[![Agents](https://img.shields.io/badge/agents-4%20specialists-blue)]()
[![Skills](https://img.shields.io/badge/skills-5%20included-orange)]()
[![License](https://img.shields.io/badge/license-MIT-lightgrey)]()

---

## Why I Built This

I run a marketing agency. I use Claude Code for 5-7 parallel sessions daily — research, briefs, copy, social content, email sequences.

The problem: every session started from scratch. I'd re-explain brand voice. Re-describe the audience. Copy-paste context between chats. The 47th time I typed "we're a B2B agency, our tone is direct and data-driven, never say leverage or synergize," I realized Claude needed an operating system.

So I built one. Then I realized the individual skill prompts weren't enough — they produced generic marketing advice. I injected my actual frameworks from running campaigns: the hook formulas that stop the scroll, the BOFU strategy that converts 10-50x better than blog posts, the activation playbook that turns signups into users.

**This is that system, open-sourced.** Clone it, fill in your brand, and every Claude session starts with your context, your voice, and proven frameworks — not a blank slate.

---

## See What It Produces

Don't take my word for it. Here's actual output from the system.

**You type:**
```
Build me a LinkedIn campaign to get 30 demo requests for our analytics tool.
Target marketing directors at B2B SaaS companies.
Budget: $5K. Deadline: 45 days.
```

**What the system produces (automatically, in sequence):**

**1. Researcher** outputs an [audience profile](examples/sample-audience-profile.json) with 87 data points — real voice-of-customer quotes pulled from Reddit and G2, not AI guesses:

```json
"voice_of_customer": {
  "actual_phrases": [
    "I spend more time building reports than reading them",
    "My CEO thinks marketing is a cost center because I can't prove otherwise",
    "We tried 3 attribution tools and they all showed different numbers"
  ]
}
```

**2. Strategist** outputs a [creative brief](examples/sample-campaign-brief.json) that selects Growth Playbook #6 ("Marketing Mistakes" content gets 3-5x higher engagement) and includes an activation plan:

```json
"growth_playbook": "Playbook 6: Marketing Mistakes Content",
"activation_plan": {
  "ghost_user_plan": "Auto-generate sample report using their website URL. Send within 1 hour.",
  "time_to_value": "15 minutes from signup to first connected dashboard"
}
```

**3. Copywriter** outputs [5 LinkedIn posts](examples/sample-social-posts.md), each using a specific hook formula:

> **Harsh Reality hook**: "Harsh reality: your marketing attribution is lying to you."
>
> **Contrarian Challenge hook**: "Everyone says 'just pick an attribution model and stick with it.' That's surface-level thinking."
>
> **Social Proof hook**: "I sat in on 12 SaaS board meetings last year. Same scene every time."

Every post ends with a specific engagement closer. Every claim has a number. Every CTA matches the buyer's intent stage.

**Full examples in [`examples/`](examples/)** — browse them to see exactly what the system outputs.

---

## The Frameworks Inside

This isn't generic "write better marketing copy" prompting. Every skill and agent runs on specific frameworks:

| Framework | The Insight | Where It's Used |
|-----------|------------|-----------------|
| **6 Hook Formulas** | 6 tested patterns that stop the scroll — Observation+Stat, Contrarian Challenge, Harsh Reality, Personal Limitation, Social Proof, Simple Declarative | Every headline, every post, every email subject |
| **BOFU Domination** | Decision-stage content converts 10-50x better than blog posts. A "best agency" page with 500 visits beats a "what is marketing" page with 50,000 | Research prioritization, content strategy |
| **7 Growth Playbooks** | Free Tool Flywheel, LLM Citation Strategy, Vertical Domination, Programmatic SEO 2.0, Language Arbitrage, Marketing Mistakes Content, Data Network Effects | Campaign brief creation |
| **3-Segment Activation** | Ghost Users (0 actions), One-and-Done (tried once), Power Users (5+/week) — each gets different interventions | Email sequences, onboarding |
| **Price Ladder** | Free → Self-serve → Managed → Full service, with signal-based upsell triggers | Email architecture, campaign planning |
| **Revenue-First** | Never accept "awareness" as a KPI. Measure revenue per impression, not impressions. | Every campaign brief |

All frameworks live in [`marketing-wisdom.md`](memory/marketing-os/marketing-wisdom.md) — the master reference every agent consults.

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
├── memory/                      # Persistent memory (voice, campaigns, frameworks, task queue)
├── schemas/                     # JSON contracts for agent-to-agent handoffs
└── examples/                    # Sample outputs showing what the system produces
```

### The 4 Agents

| Agent | Role | What It Does |
|-------|------|-------------|
| **Orchestrator** | Traffic controller | Routes every request to the right specialist. Tracks pipeline progress. Never writes copy — only routes and coordinates. |
| **Researcher** | Intelligence gatherer | Produces audience profiles and competitive analysis. Every finding is cited and confidence-rated. Defaults to BOFU-first research. |
| **Strategist** | Campaign architect | Turns research into structured creative briefs. Matches campaigns to growth playbooks. Requires revenue measurement plans. |
| **Copywriter** | Execution engine | Writes copy using proven hook formulas. Never writes without a brief. Every claim needs a specific number. |

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

## How It's Different

| Without Marketing OS | With Marketing OS |
|---------------------|-------------------|
| Re-explain brand voice every session | Brand voice loaded automatically |
| Copy-paste context between chats | Structured JSON handoffs between agents |
| Start from scratch every time | Campaign history informs every brief |
| Generic marketing language | Voice-enforced copy with banned word lists |
| You manage the workflow | Orchestrator manages the pipeline |
| One-shot outputs | Research → Strategy → Copy pipeline |
| Generic marketing advice | Battle-tested frameworks baked into every skill |
| Vague hooks and headlines | 6 proven hook formulas applied to every piece |
| Measure impressions | Revenue-first measurement enforced |

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

Four files persist across every session:

| File | What It Does | How It Helps |
|------|-------------|-------------|
| `brand-voice.md` | Accumulates voice patterns from approved copy | After 5 campaigns, the Copywriter matches your voice without direction |
| `campaign-history.md` | Logs what ran and what worked | The Strategist never repeats a failed approach without flagging it |
| `marketing-wisdom.md` | Proven frameworks and playbooks | Every agent consults these before defaulting to generic advice |
| `working.md` | Tracks the current task queue | Pick up exactly where you left off in any session |

**The compounding effect**: Session 1 requires full context. Session 10 feels like working with someone who knows your business. Session 50 feels like a senior team member.

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

**How is this different from Corey Haines' marketingskills repo?**
His repo provides excellent individual skill prompts (and inspired the skill patterns here — credit below). Marketing OS adds: a 4-agent system with structured JSON handoffs, persistent memory that compounds, proactive intent routing, and battle-tested marketing frameworks baked into every skill.

---

## Credits

Created by [Eric Siu](https://twitter.com/ericosiu), CEO of [Single Grain](https://www.singlegrain.com) — a marketing agency that uses Claude Code to run 5-7 parallel AI sessions daily.

Individual skill patterns inspired by [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills). Marketing OS adds the agent layer, persistent memory, proactive routing, structured schema handoffs, and proprietary marketing frameworks.

If you find this useful, give it a star and share it with someone running a marketing team.

---

## License

MIT — use it however you want. If you improve it, consider opening a PR.
