---
title: "Implementation Roadmap"
researched: 2026-07-22
duration: 6 weeks
---

# Implementation Roadmap

Ordered so that each week produces something usable, and so you can stop at any point
without having wasted the previous weeks.

---

## Week 0 — Verify before you build

Before any spend, resolve the open question from the analytics pull.

- [ ] **Confirm publishing status in YouTube Studio.** TubeLab's last publish estimate
      was mid-2023. If the channel has genuinely been dormant, that outweighs every
      optimisation in this plan — no pipeline compensates for not shipping.
- [ ] Export Studio analytics (Analytics → Advanced Mode → Export): retention, CTR,
      traffic source. These are the numbers TubeLab can't see.
- [ ] Top up TubeLab credits (currently 0)
- [ ] Decide: are you willing to be on camera / use your cloned voice? The plan assumes yes.

**Cost this week: $0**

---

## Week 1 — Intelligence layer

Get data flowing before automating anything.

- [ ] Connect **Windsor MCP** for YouTube analytics (free, ~60 sec)
- [ ] Upload the **AH Brain** repo to GitHub
- [ ] Create the **AH Brain Claude Project**; paste `EDITORIAL-GUIDELINES.md` into custom instructions
- [ ] Add `05-analytics/` from the analytics folder to the repo
- [ ] Build **R1 (Morning Brief)** as a routine, run daily for a week

**Success test:** you read the brief on day 5 without being reminded. If you're ignoring
it, fix the prompt before adding anything else.

**Cost: $20 (Claude Pro)**

---

## Week 2 — The two skills that matter

This is the highest-value week. Everything else is plumbing.

- [ ] Write **`ah-factcheck`** — encode the Tier 1/2/3 system from `EDITORIAL-GUIDELINES.md`
- [ ] Write **`ah-script-writer`** — voice, hook rules, 20-min structure, `[HOST]` blocks
- [ ] Test both against three *existing* scripts from the archive
- [ ] Compare AI output to `benefits-of-organs-video-script.md` — does it sound like you?

**Success test:** run `ah-factcheck` over `artificial-blue-light-vs-natural-sunlight.md`.
It should flag the 5G, deuterium and DARPA claims. If it doesn't, it isn't working.

**Cost: $20**

---

## Week 3 — Voice and images

- [ ] ElevenLabs: clone your voice, test 2 min of script
- [ ] CreativeClaw: generate 3 thumbnails for an existing top video, compare to originals
- [ ] Build **R2 (Weekly Content Council)**
- [ ] Produce **one** video end-to-end using the pipeline

**Success test:** the pipeline video is indistinguishable in voice from your manual work.
If not, the problem is the skill prompt, not the tools.

**Cost: ~$65**

---

## Week 4 — Assets and publishing

- [ ] Connect **Composio YouTube** with write scope (upload + metadata; **no delete**)
- [ ] Build **R4 (Asset Generation)** triggered on GitHub PR merge
- [ ] Build **R5 (Publish Checklist)** — manual trigger only
- [ ] Test video-gen: 30 sec of B-roll on Kling 3.0, verify quality at your standard
- [ ] **Set spend caps** on every API before the first real run

**Cost: ~$100**

---

## Week 5 — Close the loop

- [ ] Build **R6 (Comment Triage)**
- [ ] Publish 2 videos through the full pipeline
- [ ] Measure actual human hours per video against the 3–4 hr estimate
- [ ] Review the first month's spend against `03-cost-model.md`

**Success test:** human time per video is genuinely down and quality hasn't slipped.
If quality slipped, cut cadence — don't accept the trade.

**Cost: ~$150**

---

## Week 6 — Decide

- [ ] Read three pipeline scripts end to end. Still your voice?
- [ ] Compare pipeline videos' performance to your historical median
- [ ] Decide: scale to Standard, stay Lean, or roll back specific pieces
- [ ] Only now consider **HeyGen** — and only for shorts and multi-language

**Cost: ~$150**

---

## The first three videos to make

From the crosswalk, ordered by expected return:

**1. Raw milk / dairy** — `benefits-of-raw-milk.md`
Your "THE TRUTH ABOUT DAIRY" hit 17,000 (2.31×) and the research doc is sitting unused.
Highest-confidence pick in the archive.

**2. The seed-oil documentary** — `documentary-series-ideas.md`
Four chapters already written. 20+ min bucket returns 1.70×. The single biggest
unexploited asset you have.

**3. A bridged circadian video** — "I Watched The Sunrise Every Day For 30 Days"
Tests whether the personal-experience reframe rescues your weakest topic. If it works,
11 archive documents unlock. If it doesn't, you've learned that cheaply.

Note that all three lean on the archive and all three need *you* — the dairy video needs
your years of experience, the documentary needs your narration, the circadian one
requires you to actually do the 30 days. That's the design working as intended.

---

## Stop conditions

Roll back if any of these happen:

- Scripts stop sounding like you and prompt fixes don't recover it
- You're rubber-stamping the approval gate rather than reading
- Costs exceed 2× the projection two months running
- Any YouTube policy warning, of any kind
- Performance drops below your historical median for 3+ consecutive videos

**The last one matters most.** If AI-assisted videos underperform your manual ones, the
pipeline is subtracting value regardless of how much time it saves.

---

## What success looks like at 6 weeks

| | Before | After |
|---|---|---|
| Human hours/video | 10–15 | 3–4 |
| Videos/month | ~4 (if active) | 8 |
| Research → script | days | hours |
| Fact-checking | ad hoc | systematic |
| Analytics review | manual | daily brief |
| Cost/video | $0 tools | ~$14 |
| **Editorial control** | **yours** | **still yours** |

That last row is the point. Everything above it is throughput; that row is the business.
