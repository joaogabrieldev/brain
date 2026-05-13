---
name: font-selector
description: >
  Selects and recommends the best typeface or font pairing for digital UI projects.
  Use this skill whenever the user uploads a screenshot/print of an interface and asks
  about fonts, whenever a PRD or product brief is shared and font choices are needed,
  or whenever the user asks to "choose a font", "recommend a typeface", "suggest a font
  combination", "find the best font for my app/product/dashboard", "evaluate the
  typography of my UI", or "what font should I use for X". Also trigger for requests like
  "improve my typography", "fix my fonts", "choose between these fonts", or any question
  comparing typeface options for a digital product. Works with image input (screenshots,
  mockups, Figma prints) and text input (PRD, product description, design brief).
---

# Font Selector — UI Typography Intelligence

Recommends the best typeface or font pairing for digital interfaces based on visual analysis (screenshots/prints) or product context (PRD, brief). Always outputs: recommended font(s) with justification, and optionally a display/body pair.

---

## Workflow

### Step 1 — Identify Input Mode

| Input | Mode |
|-------|------|
| Image (screenshot, print, mockup) | **Visual Analysis** → follow §A |
| Text (PRD, brief, description) | **Context Analysis** → follow §B |
| Both | Run §A first, then enrich with §B |

---

### §A — Visual Analysis (Image Input)

Analyze the UI print/screenshot before recommending fonts. Observe:

1. **Product type** — app, dashboard, e-commerce, SaaS, fintech, health, editorial, etc.
2. **Tone & personality** — clinical, playful, premium, minimal, technical, friendly
3. **Information density** — sparse (marketing) vs. dense (data/dashboard)
4. **Existing font signals** — if a font is visible/identifiable, name it and assess fit
5. **Color palette & contrast** — dark mode, light mode, or mixed
6. **Target platform** — mobile-first, desktop, or both

Then go to **§C — Recommendation Engine**.

---

### §B — Context Analysis (PRD / Brief Input)

Extract the following from the document or description:

1. **Product name & category**
2. **Target audience** — age, profession, technical level
3. **Brand personality keywords** — (e.g., "trustworthy", "innovative", "warm", "precise")
4. **Primary use context** — reading-heavy vs. scanning/glancing vs. data monitoring
5. **Platform** — web, mobile, PWA, desktop app
6. **Any font constraints** — existing brand fonts, system font requirements, no-cost requirement

Then go to **§C — Recommendation Engine**.

---

### §C — Recommendation Engine

Use the decision matrix below to select font tier and category, then consult `references/font-catalog.md` for the specific typeface picks.

#### Decision Matrix

| Dimension | Signal | Font Direction |
|-----------|--------|----------------|
| **Product type** | Fintech, health, legal, B2B SaaS | Neutral geometric or humanist sans |
| | Consumer app, lifestyle, social | Friendly rounded or humanist |
| | Editorial, media, content | Serif display + sans body |
| | Developer tool, terminal, data | Monospace accents + neutral sans |
| | Dashboard, analytics | High-legibility geometric |
| **Tone** | Premium, luxury | Thin-weight geometric or elegant serif |
| | Playful, youthful | Rounded sans, expressive display |
| | Trustworthy, institutional | Classic humanist or transitional |
| | Minimal, brutalist | Grotesk / neo-grotesque |
| **Density** | Dense (lots of data/text) | High x-height, open apertures, generous spacing |
| | Sparse (marketing, hero) | More personality allowed in display |
| **Platform** | Mobile-first | System-adjacent or variable fonts |
| | Desktop web | More typographic freedom |
| **Cost** | Free required | Google Fonts only (see catalog §GF) |
| | Any | Include premium options (see catalog §PR) |

Read `references/font-catalog.md` for the curated shortlist per category.

---

### §D — Output Format

Always produce:

#### 1. Context Summary (2–3 lines)
Brief characterization of the product/UI and what typography needs to achieve.

#### 2. Primary Recommendation
```
Font: [Name]
Category: [Geometric Sans / Humanist Sans / Rounded / Grotesk / Serif / Slab / Mono]
Source: [Google Fonts / Adobe / Custom / System]
Why: [2–3 sentence justification tied to the product's tone, density, and audience]
CSS: @import url('...') or font-family stack
```

#### 3. Font Pair (when user asks for heading + body combination)
```
Display / Heading: [Font A] — [Weight range] — [why it leads]
Body / UI: [Font B] — [Weight range] — [why it reads well]
Pairing logic: [Why these two work together — contrast, x-height harmony, historical connection, etc.]
```

#### 4. Alternatives (always 2)
Shorter format — name + one-line rationale + source.

#### 5. What to Avoid (optional, only when clear anti-patterns exist)
Flag fonts that would conflict with the product's goals (e.g., Comic Sans on fintech, heavy decorative on dense dashboard).

---

## Quick Rules

- **Never recommend more than 2 typeface families** for a single UI (1 is often better)
- **Weights, not families** — variety comes from weight/size scale, not multiple font families
- **x-height matters** — for UI text below 16px, prefer fonts with high x-height (Inter, DM Sans, Figtree)
- **Variable fonts preferred** — single file, flexible weight axis, better performance
- **System font stacks** are valid answers for performance-sensitive or native-feeling products
- **Avoid novelty fonts** for body text — legibility at 14–16px is non-negotiable

---

## Reference Files

- `references/font-catalog.md` — Full curated catalog organized by category (geometric, humanist, rounded, grotesk, serif, slab, mono). Read when selecting specific fonts.
- `references/pairing-logic.md` — Rules and examples for combining display + body fonts. Read when the user asks for a font pair or combination.

Load only what you need. For a single-font recommendation, `font-catalog.md` is enough. For a pairing, also load `pairing-logic.md`.
