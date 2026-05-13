# Pairing Logic — Display + Body Combinations

Rules and curated examples for combining two typefaces in a digital UI.

---

## Core Pairing Principles

### 1. Contrast Over Harmony
Pairs that are too similar feel indistinct. Pairs that contrast too sharply feel chaotic.
The goal is **deliberate contrast** in at least one dimension:
- Structure: geometric display + humanist body
- Style: serif display + sans body
- Weight: expressive bold display + neutral regular body

### 2. Shared DNA
Despite the contrast, successful pairs share something subtle:
- Similar x-height proportions
- Complementary historical period (both transitional, both 20th-century)
- Same foundry or designer (less important but often works)
- Shared design intent (both "warm", both "rational")

### 3. The 2-Font Rule
In UI, you almost never need more than 2 families. Instead:
- Use **weight variation** within the same family for hierarchy
- Use **size + color** to differentiate roles
- Add the second family only when the first can't serve both display and body roles well

### 4. Serif + Sans is the Classic Move
Most successful editorial and marketing UI pairs use:
- Serif → display, headlines, hero text
- Sans → body, UI labels, navigation, metadata

This works because the serif adds personality/authority at large sizes, while the sans maintains legibility at small sizes.

---

## Pairing Matrix by Context

| Context | Display | Body | Why It Works |
|---------|---------|------|--------------|
| **Premium SaaS** | Söhne / Cabinet Grotesk | Inter | Expressive header vs. neutral body |
| **Editorial / Media** | Playfair Display | Lora or Source Sans 3 | Classic serif contrast, both high-legibility |
| **Startup / Consumer App** | Space Grotesk | DM Sans | Tech confidence + warm legibility |
| **Health / Wellness** | Fraunces | Figtree | Organic serif + friendly rounded sans |
| **Developer Tool** | Geist (bold) | JetBrains Mono | Minimal system feel + code-native |
| **Luxury / Fashion** | Editorial New / Canela | Calibre or Graphik | Expressive display + invisible body |
| **Dashboard / Data** | Plus Jakarta Sans (bold) | Inter | Same family aesthetic, weight contrast only |
| **EdTech** | Nunito (bold) | Nunito (regular) | Single family, weight hierarchy |
| **Fintech / Banking** | DM Serif Display | Inter | Authority header + trusted neutral |
| **AI Product** | Space Grotesk | Geist | Both modern-tech, distinct weights |

---

## Curated Pairings — Free (Google Fonts)

### 1. Inter + Playfair Display
- **Use for:** SaaS with editorial ambition, content-forward apps
- **Display:** Playfair Display Bold / Black (headlines, hero)
- **Body:** Inter Regular / Medium (UI text, labels, paragraphs)
- **Why:** High-contrast duo. Playfair brings warmth and authority; Inter brings trust and legibility
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Inter:wght@400;500;600&display=swap');
--font-display: 'Playfair Display', Georgia, serif;
--font-body: 'Inter', system-ui, sans-serif;
```

### 2. Space Grotesk + DM Sans
- **Use for:** Tech startups, AI products, modern SaaS
- **Display:** Space Grotesk Bold / ExtraBold
- **Body:** DM Sans Regular / Medium
- **Why:** Both geometric, but Space Grotesk's quirky terminals contrast with DM Sans's cleaner neutrality
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@600;700&family=DM+Sans:wght@400;500&display=swap');
--font-display: 'Space Grotesk', sans-serif;
--font-body: 'DM Sans', sans-serif;
```

### 3. Plus Jakarta Sans + Inter
- **Use for:** Dashboards, product apps, clean B2B
- **Display:** Plus Jakarta Sans ExtraBold (700–800)
- **Body:** Inter Regular / Medium (400–500)
- **Why:** Similar geometry, but Jakarta's higher contrast at large sizes makes it feel expressive while Inter handles density
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@700;800&family=Inter:wght@400;500&display=swap');
--font-display: 'Plus Jakarta Sans', sans-serif;
--font-body: 'Inter', system-ui, sans-serif;
```

### 4. Fraunces + Figtree
- **Use for:** Wellness, health apps, lifestyle consumer
- **Display:** Fraunces Bold / Black (variable optical sizes)
- **Body:** Figtree Regular / Medium
- **Why:** Fraunces's organic serif personality vs. Figtree's clean, friendly circles. Warm + approachable
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:wght@700;900&family=Figtree:wght@400;500&display=swap');
--font-display: 'Fraunces', Georgia, serif;
--font-body: 'Figtree', sans-serif;
```

### 5. Syne + Source Sans 3
- **Use for:** Creative agencies, portfolio, bold editorial
- **Display:** Syne ExtraBold (800)
- **Body:** Source Sans 3 Regular (400)
- **Why:** Syne's wide, distinctive letterforms create strong identity; Source Sans 3's neutrality and excellent legibility anchor the body
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@800&family=Source+Sans+3:wght@400;600&display=swap');
--font-display: 'Syne', sans-serif;
--font-body: 'Source Sans 3', sans-serif;
```

### 6. Bricolage Grotesque + Inter
- **Use for:** AI products, bold tech, modern editorial
- **Display:** Bricolage Grotesque ExtraBold
- **Body:** Inter Regular
- **Why:** Bricolage's irregular optical quirks at large sizes create bold personality; Inter disappears at small sizes (optimal)
- **CSS:**
```css
@import url('https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@700;800&family=Inter:wght@400;500&display=swap');
--font-display: 'Bricolage Grotesque', sans-serif;
--font-body: 'Inter', system-ui, sans-serif;
```

---

## Single-Family Pairs (Weight-Only Hierarchy)

For maximum consistency and performance, use one variable font with weight contrast:

| Font | Display Weight | Body Weight | Best For |
|------|---------------|-------------|----------|
| Inter | 800 | 400 | Any neutral product |
| DM Sans | 700 | 400 | Clean consumer, SaaS |
| Plus Jakarta Sans | 800 | 400 | Modern dashboards |
| Nunito | 800 | 400 | Friendly, rounded feel |
| Figtree | 700 | 400 | Wellness, consumer |

---

## Anti-Patterns to Avoid

| Mistake | Why It Fails |
|---------|--------------|
| Two very similar sans-serifs | No contrast = no hierarchy signal |
| Two serif fonts | Clash of personalities, reading fatigue |
| Display font as body text | Decorative fonts lose legibility at 14–16px |
| More than 2 font families | Visual noise, inconsistent identity |
| Mixing incompatible eras | e.g., Art Nouveau display + Swiss grotesk body |
| Using Poppins for dense body text | Low x-height at small sizes, poor legibility |
