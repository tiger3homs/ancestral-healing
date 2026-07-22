---
title: "Connector Stack"
researched: 2026-07-22
---

# Connector Stack

Everything you need to connect, in setup order. <cite index="9-1">Anthropic's connector directory listed 369 connectors as of June 19, 2026, up from around 50 at the start of the year</cite> — <cite index="12-1">with other trackers counting 439 by July</cite>. The directory moves weekly, so check for newer options before building anything custom.

---

## Layer 1 — Intelligence (read)

### 1. YouTube analytics ⭐ essential

**The catch:** <cite index="51-1">there's no one-click YouTube connector in Claude's directory — connecting takes a custom MCP server and a paid plan.</cite>

Three routes:

| Option | Setup | Cost | Best for |
|---|---|---|---|
| **Composio (Rube)** | OAuth, managed | Free tier → paid | Recommended. <cite index="46-1">Provides structured access to channel data — searching videos, managing playlists, retrieving channel insights</cite> |
| **Windsor MCP** | No-code, ~60 sec | <cite index="45-1">Included on every plan, including free-forever</cite> | Fastest analytics-only path |
| **Self-hosted** | Node + OAuth | Free (your infra) | Full control; <cite index="44-1">reads analytics, fetches metadata including unlisted/private/draft, and updates titles/descriptions/tags</cite> |

**Start with Windsor** for analytics-only, then add Composio when you need write access.

> ⚠️ **Quota warning.** <cite index="48-1">The YouTube Data API has a daily quota of 10,000 units, and search operations are the most expensive — use get_channel_videos (1 unit) instead of search_within_channel (100 units) when you just need recent uploads.</cite> A careless routine can exhaust a day's quota in one run. Cache aggressively.

### 2. TubeLab ✅ already connected

Competitive intelligence and outlier detection. Covers what the YouTube API doesn't:
cross-channel benchmarking, outlier scoring, related-channel discovery.

**Note:** your credit balance is currently **0** — `search_related_channels` returned a
402. Top up before relying on it in a routine.

### 3. Web search ✅ built in

Trend monitoring, fact-checking, competitor research. No setup.

---

## Layer 2 — Generation

### 4. Image generation ⭐ essential

For thumbnails, carousels, B-roll stills.

| Option | Model access | Pricing |
|---|---|---|
| **CreativeClaw** | <cite index="54-1">100+ models including Nano Banana Pro, Flux 2 Pro, GPT Image 2, Recraft V3 — no API keys, pay per generation</cite> | Credit-based |
| **Nano Banana MCP** | <cite index="58-1">Gemini image generation, 2K images, session consistency across generations</cite> | Google AI API key |
| **Higgsfield** | <cite index="55-1">Soul V2, Seedream 5.0 Lite, Flux.2 Pro, Nano Banana; ~$0.09–$0.19/image; plans $15/$39/$99 per month</cite> | Subscription + credits |

**Recommended: CreativeClaw** — <cite index="54-1">it renders social cards, OG images and YouTube thumbnails from a layout engine, so text and logos come out pixel-perfect</cite>. Text-on-thumbnail is exactly where raw diffusion models fail.

Per-image economics for reference: <cite index="60-1">Nano Banana 2 at $0.067/image (3–5 sec generation), GPT Image 1.5 at $0.04, FLUX.2 Schnell at $0.015 — or free self-hosted</cite>.

### 5. Voice — ElevenLabs ⭐ essential

<cite index="36-1">The official ElevenLabs MCP server lets you generate speech, clone voices and transcribe audio, and is fully compatible with Claude Desktop and other MCP-native environments.</cite>

**Use your own cloned voice, not a stock one.** This matters for both brand continuity
and policy: it keeps the channel recognisably yours.

### 6. Video / avatar — HeyGen

<cite index="39-1">HeyGen ships an official MCP server connecting to Claude Web, Claude Code, Gemini CLI and Cursor, using your existing HeyGen plan with no extra billing.</cite> <cite index="37-1">It exposes tools to retrieve voices, avatar groups, video status, and to generate avatar videos with specified text and voices.</cite>

Use for: consistent intro/outro segments, repurposing scripts into short-form, and
multi-language versions. **Not** for the main personal-experience content — that's the
part that has to be actually you.

### 7. B-roll video generation

No mature MCP; call via API from a skill. 2026 pricing:

| Model | Per second | Notes |
|---|---|---|
| Wan 2.6 | <cite index="30-1">$0.05/sec — budget king, native 1080p</cite> | Cheapest usable |
| Veo 3.1 Lite | <cite index="29-1">$0.05/sec, no audio</cite> | |
| Kling 3.0 | <cite index="30-1">$0.10/sec — uniquely strong multi-angle subject consistency, great for character-driven and short-form social</cite> | **Best value** |
| Veo 3.1 Fast | <cite index="30-1">$0.15/sec</cite> | |
| Runway Gen-4.5 | <cite index="30-1">$0.15/sec — best creative control tools</cite> | |
| Veo 3.1 Standard | <cite index="30-1">$0.75/sec — native 4K, best lip-sync, audio included</cite> | Hero shots only |

<cite index="30-1">Draft in fast/budget tiers before final renders, and disable audio generation when not needed — it saves 30–50%.</cite>

**Recommended: Kling 3.0** for volume, Veo 3.1 Standard sparingly for hero shots.

---

## Layer 3 — Storage & publishing

### 8. YouTube write access ⭐ essential

Composio YouTube with OAuth write scope. <cite index="44-1">Note that enabling write access requires re-running the auth flow to request the YouTube write scope.</cite>

**Scope discipline:** grant upload + metadata edit. Do not grant delete. There is no
upside to letting an automated pipeline delete your catalogue.

### 9. GitHub ✅ you have the repo

Version-controls the AH Brain archive, scripts, and — importantly — <cite index="24-1">routines can be triggered by GitHub events such as pull requests or releases</cite>. So a merged script PR can kick off asset generation.

### 10. Google Drive

Asset storage for renders, thumbnails, audio. Directory connector, one-click.

---

## Optional

| Connector | Why |
|---|---|
| Notion / Linear | Content calendar and production board |
| Slack | Routine output notifications and approvals |
| Ahrefs ✅ connected | Keyword and search-demand research |
| Supabase ✅ connected | Custom performance database over time |

---

## Custom skills (you build these)

Skills are **not** connectors. They're reusable instruction bundles that encode your
process. These are the four worth writing:

| Skill | Job |
|---|---|
| `ah-script-writer` | Takes a topic + archive docs → script in AH voice, applying the hook rules from the analytics (no questions, no ALL CAPS, 20+ min structure) |
| `ah-thumbnail` | Generates thumbnail concepts + text overlays matching brand |
| `ah-metadata` | Titles, descriptions, tags, chapters — with the AI disclosure checklist |
| `ah-factcheck` | Runs scripts against the Tier 1/2/3 claim system in `EDITORIAL-GUIDELINES.md` |

That last one is the most important thing in this document. It's the difference between
a pipeline that scales your voice and one that scales your liability.

---

## Setup order

1. **Windsor MCP** → analytics flowing (60 seconds, free)
2. **Top up TubeLab** → competitive intel working again
3. **CreativeClaw** → thumbnails
4. **ElevenLabs** → clone your voice
5. **Write `ah-script-writer` + `ah-factcheck`** → the core value
6. **Composio YouTube write** → publishing
7. **HeyGen** → only once 1–5 are proven

Do not connect everything on day one. Each connector is an integration surface to
maintain, and half of these you may find you don't need.
