# AH Brain — Ancestral Healing Knowledge Base

The complete content library for **Ancestral Healing**, a health & wellness creator
brand producing long-form video and short-form (Reels/Shorts) content.

This repo is built to be loaded as a **Claude Project knowledge base**. Every source
document has been converted to structured markdown with YAML frontmatter so Claude
can retrieve by pillar, document type, and topic.

---

## What this is

Ancestral Healing is a media brand, not a product. This archive is the **raw material
behind the channel**: research notes, video scripts, distilled podcast and lecture
summaries, reel hooks, downloadable guides, and a competitor map.

The editorial worldview is *ancestral / animal-based / quantum-biology-adjacent* —
blending traditional-diet advocacy with circadian-light science and non-toxic living.

**One-line thesis:** modern chronic disease is a *disconnection* — from ancestral
food, from natural light, and from a non-toxic environment.

---

## Repo structure

```
ah-brain/
├── README.md                      ← you are here
├── CONTENT-INDEX.md               ← full file index + what to use when
├── EDITORIAL-GUIDELINES.md        ← brand voice, claim handling, fact-check rules
│
├── 01-ancestral-nutrition/        ← 13 docs — food, sourcing, protocols
├── 02-circadian-and-light/        ← 11 docs — light, mitochondria, EMF
├── 03-non-toxic-lifestyle/        ←  2 docs — plastics, PFAS, endocrine disruptors
├── 04-content-strategy/           ←  3 docs — scripts, idea backlog, channel map
│
├── reference/
│   └── knowledge-base.html        ← visual overview of the whole archive
└── source-pdfs/                   ← original PDFs (reference only)
```

---

## The three content pillars

| Pillar | Focus | Docs |
|---|---|---|
| **01 · Ancestral Nutrition** | Nose-to-tail animal-based eating, grass-fed beef, organs, raw milk, bone broth. Anti-seed-oil, anti-processed, anti-antinutrient. Local regenerative sourcing. | 13 |
| **02 · Circadian & Light** | Light as medicine: morning sun, blue-light avoidance, red/NIR therapy, grounding, EMF caution, mitochondrial health. *Largest body of material.* | 11 |
| **03 · Non-Toxic Lifestyle** | Microplastics, PFAS, BPA and endocrine disruptors. Glass over plastic. Overlaps with hormone and fertility themes. | 2 |
| **04 · Content Strategy** | Documentary outlines, episode backlog, competitor channel map. | 3 |

---

## Frontmatter schema

Every markdown file opens with YAML frontmatter so Claude can filter and retrieve:

```yaml
---
title: "Benefits of Organs Video Script"
pillar: Ancestral Nutrition
type: video-script
source_file: "Ancestral Nutrition/Benefits of Organs Video Script.docx"
converted: 2026-07-22
---
```

### `type` values

| Type | Meaning |
|---|---|
| `research-note` | Background research, not yet shaped into content |
| `video-script` | Ready or near-ready to shoot |
| `content-ideas` | Hooks, reel concepts, series outlines |
| `protocol` | Actionable step-by-step routines |
| `guide` | Lead magnet / downloadable asset |
| `book-summary` | Distilled summary of a book or lecture |
| `reference-summary` | Summary of a third-party document |
| `book-reference` | Pointer to a copyrighted work — no text reproduced |
| `channel-map` | Competitive and positioning research |

---

## Using this as a Claude Project

1. Upload this repo (or connect it via GitHub) to a Claude Project named **AH Brain**.
2. Add `EDITORIAL-GUIDELINES.md` content to the Project's custom instructions — it
   contains the brand voice and the fact-checking rules that should apply to every
   generation.
3. Ask Claude things like:
   - *"Draft a 45-second reel on morning light using our existing hooks."*
   - *"Which episode ideas in the backlog have no script yet?"*
   - *"Turn the anti-nutrient research note into a carousel outline."*
   - *"What claims in the circadian pillar need fact-checking before publishing?"*

---

## ⚠️ Important: claim handling

This archive mixes **well-supported ideas** (circadian rhythm matters; ultra-processed
food and excessive night-time screen light are real concerns) with **contested or
fringe claims** (sun exposure preventing breast cancer, 5G causing disease spikes,
deuterium theory, DARPA/blue-light control narratives, raw-milk safety).

Documenting a claim here is **descriptive, not an endorsement**. Before anything ships:

- Fact-check specifics and add qualifiers
- Attribute contested claims to the person who made them, rather than stating them as
  settled science
- Keep medical-disclaimer language — the raw-milk and appendicitis docs already model this
- None of this is medical advice

See `EDITORIAL-GUIDELINES.md` for the full protocol.

---

## Copyright note

Two items in `source-pdfs/` are **published third-party books** (*Primal Nutrition*,
Kevin Stock's *Carnivore Guide*), and two are **third-party whitepapers**
(BioSpectral Systems). Their full text has **not** been extracted into this repo.
They are represented by reference notes and summaries only. Retain them for personal
reference; do not redistribute or bulk-load their text.
