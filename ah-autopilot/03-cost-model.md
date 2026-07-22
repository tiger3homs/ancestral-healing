---
title: "Cost Model"
researched: 2026-07-22
currency: USD / month
---

# Cost Model

All figures researched 22 July 2026. **The video-generation market reprices constantly** —
treat these as planning estimates and re-verify before committing.

---

## Fixed costs (subscriptions)

| Item | Cost | Notes |
|---|---|---|
| **Claude Max 5×** | **$100** | <cite index="65-1">About 5× Pro usage — best for one power user who hits Pro limits daily</cite>. Needed for routine volume. |
| Claude Pro (alternative) | $20 | <cite index="64-1">$20/month, or $17/month billed annually</cite>. Viable for the Lean scenario only. |
| ElevenLabs Creator | ~$22 | Voice cloning + generation. Verify current tier. |
| HeyGen Creator | ~$29 | Optional until phase 3. <cite index="39-1">MCP uses your existing plan with no extra billing.</cite> |
| CreativeClaw / image credits | ~$10–20 | Pay-per-generation |
| Windsor MCP | **$0** | <cite index="45-1">Included on every plan, including free-forever</cite> |
| Composio | $0 → paid | Free tier covers early usage |
| GitHub | $0 | Free tier fine |
| Google Drive | $0–3 | Existing storage likely sufficient |

**Fixed subtotal: $132 (lean, Pro) → $171 (standard, Max) → $180 (with HeyGen)**

> ⚠️ **The most common Claude billing mistake:** <cite index="66-1">if you have an `ANTHROPIC_API_KEY` environment variable set, Claude Code will silently use the API key instead of your Pro or Max subscription — you keep getting billed through the API while your subscription sits unused.</cite> Check your shell profile before paying for a plan.

---

## Variable costs (per output)

### Video generation

Assumes AI B-roll only — talking-head footage is you, filmed.

| Scenario | AI video seconds | Rate | Cost |
|---|---|---|---|
| Lean · 4 long + 8 shorts | 200s | $0.05 (Wan 2.6) | **$10** |
| Standard · 8 long + 12 shorts | 660s | $0.10 (Kling 3.0) | **$66** |
| Aggressive · 12 long + 20 shorts | 1,380s | $0.15 (Veo 3.1 Fast) | **$207** |

Worked example: <cite index="29-1">a 60-second AI video in 2026 costs $3 on Veo 3.1 Lite, $24 on Veo 3.1 Standard with audio, $6–$12 on Runway Gen-4.5, and effectively $0 on local open-weights models like Wan 2.2 if you have a capable GPU.</cite>

**Two levers that cut this materially:**
1. <cite index="30-1">Draft in fast/budget tiers before final renders</cite>
2. <cite index="30-1">Disable audio generation when not needed — saves 30–50%</cite>

### Images

56 images/month standard (thumbnails + variants + stills). At <cite index="60-1">$0.04–$0.067 per image</cite> → **$2–4/month.** Negligible.

### Voice

~70 min/month standard. Covered by the ElevenLabs Creator tier; overage is minor.

### Claude API overflow

<cite index="66-1">In 2026 Anthropic added an "extra usage" toggle on every paid consumer plan — when you hit your included limit you can opt in to continue at standard API rates with a monthly spend cap you control.</cite>

**Set the cap.** Budget $0–50 depending on scenario. <cite index="67-1">Independent trackers put typical spend at $30–60/month for light use and $150–300 for professional daily use</cite> — but those are third-party estimates, not Anthropic figures.

---

## Three scenarios

### Lean — validate the pipeline
**4 long + 8 shorts/month**

| | |
|---|---|
| Claude Pro | $20 |
| ElevenLabs | $22 |
| Images | $10 |
| Video gen (Wan 2.6) | $10 |
| Windsor / Composio / GitHub | $0 |
| API overflow buffer | $30 |
| **Total** | **~$92–155** |

Prove the workflow before scaling spend. **Start here.**

---

### Standard — recommended
**8 long + 12 shorts/month**

| | |
|---|---|
| Claude Max 5× | $100 |
| ElevenLabs | $22 |
| CreativeClaw | $20 |
| Video gen (Kling 3.0) | $66 |
| TubeLab credits | $20 |
| Composio | $15 |
| API overflow | $40 |
| **Total** | **~$283** |

Roughly **$14 per published piece.** Add HeyGen (+$29) if doing avatar shorts.

---

### Aggressive — scale
**12 long + 20 shorts/month**

| | |
|---|---|
| Claude Max 20× | $200 |
| ElevenLabs Pro | $99 |
| HeyGen | $29 |
| Images | $30 |
| Video gen (Veo 3.1 Fast) | $207 |
| TubeLab + Composio | $50 |
| API overflow | $80 |
| **Total** | **~$695** |

> ⚠️ **Read `04-policy-and-risk.md` before running this tier.** 32 pieces/month with
> template similarity is exactly the upload-frequency-plus-format-similarity pattern
> that triggers inauthentic-content review.

---

## Does it pay for itself?

<cite index="5-1">Realistic 2026 RPMs: $3–$8 in premium niches and $0.30–$1 in saturated ones.</cite> Health and wellness sits mid-range; call it **$4–6 RPM**.

At your current median of 5,300 views:

| Monthly views | Revenue @ $5 RPM | Standard cost | Net |
|---|---|---|---|
| 50,000 | $250 | $283 | **−$33** |
| 100,000 | $500 | $283 | **+$217** |
| 250,000 | $1,250 | $283 | **+$967** |
| 500,000 | $2,500 | $283 | **+$1,967** |

**Break-even is roughly 57,000 views/month.** With 8 long-form at your median that's
~42,000 — so ad revenue alone doesn't cover it at current performance.

**This is why the plan targets quality over volume.** One video at 71,000 views beats
thirteen at 5,300 — and costs less to make. Ad revenue is also the weakest monetisation
line for a channel like this. The archive already contains three lead magnets and an
ebook; a $27 guide converting at 1% of 100,000 views is $27,000. That maths dominates
anything RPM does.

---

## Costs the tables miss

| Hidden cost | Reality |
|---|---|
| **Your time** | 3–4 hr/video. At any realistic hourly rate this exceeds every tool cost combined. |
| **Setup** | 15–25 hours across 6 weeks |
| **Maintenance** | 2–4 hr/month — APIs break, models deprecate |
| **Failed generations** | Budget 2–3 iterations per final clip |
| **Preview instability** | <cite index="24-1">Routines are research preview</cite> — rework is likely |
| **Editing** | Not automated here. Either your time or an editor. |

---

## Recommendation

**Start Lean at ~$92/month for 8 weeks.** Prove that AI-assisted scripts hold your voice
and that the routines actually save time. Then scale to Standard.

Do not buy the full stack up front. Half these tools you'll drop once you see which part
of the pipeline is actually your bottleneck — and on current evidence that bottleneck is
*deciding and recording*, not generating.
