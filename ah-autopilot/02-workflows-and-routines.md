---
title: "Workflows and Routines"
researched: 2026-07-22
---

# Workflows and Routines

## What "routines" actually are

<cite index="23-1">Claude Code routines are saved configurations — a prompt, one or more repositories, and your connectors — that run on Anthropic's cloud infrastructure. No terminal window, no local machine. They shipped April 14, 2026 in research preview across all paid plans: Pro, Max, Team and Enterprise.</cite>

<cite index="24-1">Each routine can have one or more triggers: scheduled (hourly, nightly, weekly, or once at a future time), API (an HTTP POST to a per-routine endpoint), or GitHub (repository events such as pull requests or releases). A single routine can combine triggers.</cite>

**The constraint that shapes your design:** <cite index="16-1">daily run caps range from 5 to 25 depending on plan tier.</cite> You cannot run something every 15 minutes. Design around a handful of meaningful runs per day, not constant polling.

**Two other limits worth knowing:**

- <cite index="19-1">Routines don't remember last week — each run starts fresh.</cite> If a workflow needs to track findings over time, write state to the GitHub repo or Supabase.
- <cite index="24-1">The feature is in research preview; request shapes, rate limits and token semantics may change.</cite>

### Which scheduler to use

| Tool | Runs where | Use for |
|---|---|---|
| **Claude Code Routines** | Anthropic cloud | Everything unattended. The default choice. |
| **Cowork Scheduled Tasks** | <cite index="19-1">Locally</cite> | Jobs needing local files or rendering |
| **`/loop`** | Terminal session | Ad-hoc polling while you work |

---

## The six routines

### R1 · Morning Intelligence Brief
**Daily, 07:00 · Connectors: YouTube, TubeLab, web search**

Pulls yesterday's performance, flags anything outside normal range, checks 3–5
competitor channels for new uploads, scans for trending topics in the ancestral/carnivore
space. Outputs a short brief — not a dashboard.

> Compare yesterday's metrics against the 30-day baseline in `/analytics/baseline.json`.
> Report only: (a) videos outside ±30% of expected, (b) competitor uploads exceeding
> 2× their channel average, (c) any emerging topic appearing across 2+ sources.
> Under 300 words. If nothing qualifies, say "nothing notable" and stop.

**Why the "stop" instruction matters:** without it you get 800 words of filler daily,
stop reading it by week two, and the routine becomes theatre.

---

### R2 · Weekly Content Council
**Mondays, 09:00 · Connectors: YouTube, TubeLab, GitHub (AH Brain), Ahrefs**

The strategic one. Cross-references the archive against demand and proposes next topics.

> Using `04-ah-brain-crosswalk.md` and last week's performance, propose 3 video concepts.
> For each: working title (no questions, no ALL CAPS), which archive docs source it,
> target length (favour 20+ min — it returns 1.70×), the personal-experience angle only
> the host can supply, and predicted demand tier with reasoning.
> Flag any Tier-3 claims requiring attribution per `EDITORIAL-GUIDELINES.md`.

**Output: a proposal, not a decision.** You pick.

---

### R3 · Script Draft
**Triggered manually or by GitHub issue · Skill: `ah-script-writer`**

Runs *after* you choose a topic. Pulls relevant archive docs, drafts in AH voice,
applies the hook rules, structures for the 20-minute format.

> Draft a script on {topic}. Source from {archive docs}. Apply AH voice from
> `EDITORIAL-GUIDELINES.md`. Structure: hook (0–15s) → stakes → mechanism →
> personal experience [MARK AS `[HOST: your story here]`] → practical takeaway → CTA.
> Target 20+ min. Mark every Tier-2/3 claim inline with the required attribution.
> Leave `[HOST]` blocks empty — do not invent personal anecdotes.

**That last line is the whole ballgame.** The AI drafts structure and research. It never
fabricates your experience. Fake personal stories are both a policy risk and the fastest
way to lose an audience that trusts you.

---

### R4 · Asset Generation
**Triggered on script approval (GitHub PR merge) · Connectors: CreativeClaw, ElevenLabs, video API**

Fires once you approve. Generates 3 thumbnail concepts, 5 title variants, B-roll clips
for marked segments, chapter markers, description and tags.

> From the approved script at {path}: generate 3 thumbnail concepts (high contrast,
> face-forward, ≤4 words of text), 5 title variants applying how-to or contrarian
> framing, B-roll for each `[BROLL: ...]` marker using Kling 3.0, and a description
> with chapters. Save to Drive under `/AH/{video-slug}/`.

---

### R5 · Publish Checklist
**Manual trigger · Connectors: YouTube (write)**

Never scheduled. This is the gate.

> Pre-publish check on {video}: (1) AI disclosure toggle set if synthetic voice or
> visuals used, (2) every Tier-3 claim attributed by name, (3) medical disclaimer
> present, (4) title is not a question and not ALL CAPS, (5) chapters present,
> (6) thumbnail text legible at 210px wide.
> Report pass/fail per item. Do not upload — output the checklist only.

---

### R6 · Comment Triage
**Daily, 18:00 · Connectors: YouTube**

Surfaces comments needing a real reply: questions, corrections, criticism worth engaging.
Drafts responses for your approval.

> Pull comments from the last 24h. Categorise: genuine question / factual correction /
> criticism / spam / praise. Draft replies for the first three categories only, in AH
> voice. Never post — output drafts for review.

**Do not auto-post comments.** Engagement is where the audience decides whether a real
person is behind the channel.

---

## The weekly rhythm

| Day | Automated | You |
|---|---|---|
| Mon | R1 brief · R2 council | Pick next topic (~15 min) |
| Tue | R3 script draft | Review, fill `[HOST]` blocks (~45 min) |
| Wed | R4 assets | Record (~90 min) |
| Thu | — | Edit, or hand to editor |
| Fri | R5 checklist | Approve and publish (~20 min) |
| Daily | R1, R6 | Skim brief, approve comment replies (~10 min) |

**Human time: roughly 3–4 hours per video.** Against a full manual pipeline of 10–15
hours. That's the honest gain — not zero, but 3× throughput on the same effort.

---

## Failure modes to design against

| Risk | Guard |
|---|---|
| **API quota exhaustion** | Cache analytics daily; never let a routine call `search` in a loop |
| **Routine amnesia** | Persist state to GitHub or Supabase; assume every run is cold |
| **Silent drift** | Monthly manual read of 3 random scripts — is this still your voice? |
| **Cost runaway** | Hard caps on video-gen spend; draft in cheap tiers first |
| **Preview instability** | Routines are research preview — expect breakage, keep manual fallbacks |
| **Approval fatigue** | If you find yourself rubber-stamping, the gate has failed. Cut cadence instead. |

That last one is the real risk. A human gate you stop reading is worse than no gate,
because it produces false confidence.
