# Font Catalog — UI Typography Reference

Curated shortlist of fonts for digital interfaces, organized by category. Each entry includes x-height rating, variable font availability, cost, and best-fit use cases.

---

## §GF — Google Fonts (Free)

### Geometric Sans
High-structure, neutral, modern. Good for tech, data, SaaS, fintech.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Inter** | ★★★★★ | ✅ | Dashboards, SaaS, developer tools, any dense UI | Luxury, lifestyle brands |
| **DM Sans** | ★★★★☆ | ✅ | B2B SaaS, product apps, clean marketing | Heavy data density |
| **Geist** (Vercel) | ★★★★☆ | ✅ | Developer tools, minimal SaaS | Consumer lifestyle |
| **Plus Jakarta Sans** | ★★★★☆ | ✅ | Startup SaaS, modern dashboards | Very formal/institutional |
| **Outfit** | ★★★☆☆ | ✅ | Consumer apps, friendly SaaS | Dense data tables |

### Humanist Sans
Warm, organic letterforms. Trustworthy, accessible.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Nunito** | ★★★★☆ | ✅ | EdTech, health apps, friendly consumer products | Enterprise, premium |
| **Source Sans 3** | ★★★★★ | ✅ | Government, accessibility-critical, reading-heavy | Luxury, playful |
| **Lato** | ★★★★☆ | ❌ | Corporate apps, HR tools, mid-market SaaS | Cutting-edge tech feel |
| **Mulish** | ★★★★☆ | ✅ | Clean consumer apps, lifestyle | Very dense UIs |
| **Figtree** | ★★★★☆ | ✅ | Modern consumer apps, health, wellness | Heavy enterprise |

### Rounded Sans
Playful, approachable. Consumer apps, kids, wellness.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Nunito** | ★★★★☆ | ✅ | EdTech, kids apps, social | Enterprise B2B |
| **Poppins** | ★★★☆☆ | ❌ | Consumer apps, lifestyle, fashion | Body text at small sizes |
| **Varela Round** | ★★★☆☆ | ❌ | Small apps, simple UIs | Dense data |
| **Comfortaa** | ★★★☆☆ | ✅ | Very casual consumer | Professional contexts |

### Grotesk / Neo-Grotesque
Systematic, rational. Strong brand identity, minimal UI.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Space Grotesk** | ★★★★☆ | ✅ | Crypto, web3, tech startups, bold SaaS | Conservative enterprise |
| **Syne** | ★★★☆☆ | ✅ | Creative tools, portfolios, bold marketing | Body text at 14px |
| **Cabinet Grotesk** | ★★★★☆ | ✅ | Premium SaaS, design tools | Very dense UIs |
| **Bricolage Grotesque** | ★★★★☆ | ✅ | Editorial, bold product marketing | Small body text |

### Serif (Display & Body)
Editorial gravitas, premium feel. Headers and content-heavy products.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Playfair Display** | ★★★☆☆ | ✅ | Editorial headers, luxury brands, media | Body text, dense UIs |
| **Lora** | ★★★★☆ | ✅ | Long-form reading, editorial, education | App UIs (navigation) |
| **Merriweather** | ★★★★☆ | ❌ | News, content, reading-heavy products | Light-weight headers |
| **DM Serif Display** | ★★★☆☆ | ❌ | Premium headers, media, luxury landing | Dense UI components |
| **Fraunces** | ★★★☆☆ | ✅ | Editorial, lifestyle, premium consumer | Technical/enterprise |

### Slab Serif
Strong personality, technical confidence. Developer tools, data products.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **Roboto Slab** | ★★★★☆ | ✅ | Enterprise dashboards, documentation | Playful consumer apps |
| **Zilla Slab** | ★★★★☆ | ❌ | Mozilla-style technical, developer | Luxury, fashion |

### Monospace
Code, data, terminal aesthetics.

| Font | X-Height | Variable | Best For | Avoid When |
|------|----------|----------|----------|------------|
| **JetBrains Mono** | ★★★★☆ | ✅ | Dev tools, code editors, technical dashboards | Consumer lifestyle |
| **Fira Code** | ★★★★☆ | ❌ | Code display, developer-facing products | Non-technical products |
| **Space Mono** | ★★★☆☆ | ❌ | Creative tech, retro-digital aesthetic | Small body text |
| **Geist Mono** | ★★★★☆ | ❌ | Modern dev tools, Vercel-style minimal | |

---

## §PR — Premium Fonts

For projects with budget for licensed typefaces.

### Geometric / Neutral Sans
| Font | Source | Best For |
|------|--------|----------|
| **Söhne** | Klim Type | Premium SaaS, sophisticated tech products |
| **Graphik** | Commercial Type | Corporate, editorial, high-end B2B |
| **ABC Diatype** | Dinamo | Minimal, brutalist, bold brand identity |
| **Neue Haas Grotesk** | Monotype | Swiss design, institutional, premium neutral |

### Humanist Sans
| Font | Source | Best For |
|------|--------|----------|
| **Aktiv Grotesk** | Dalton Maag | Enterprise, neutral global products |
| **Calibre** | Klim Type | Editorial, cultural institutions, news |
| **National 2** | Klim Type | Premium editorial, media companies |

### Display / Expressive
| Font | Source | Best For |
|------|--------|----------|
| **Editorial New** | Pangram Pangram | Fashion, luxury, bold editorial |
| **Canela** | Commercial Type | Luxury, premium lifestyle, editorial |
| **Signifier** | Klim Type | Premium, literary, editorial |

---

## §SYS — System Font Stacks

Use when performance is critical or native feel is desired.

```css
/* Cross-platform safe */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;

/* Apple-first */
font-family: -apple-system, 'Helvetica Neue', Arial, sans-serif;

/* Windows-first */
font-family: 'Segoe UI', system-ui, Arial, sans-serif;
```

Best for: PWAs, admin tools, internal dashboards, performance-critical products.

---

## Quick Pick by Product Type

| Product Type | First Pick | Second Pick |
|---|---|---|
| B2B SaaS / Dashboard | Inter | DM Sans |
| Developer Tool | Geist | JetBrains Mono (accent) |
| Fintech / Banking | Inter | Source Sans 3 |
| Health / Wellness | Figtree | Nunito |
| EdTech | Nunito | Source Sans 3 |
| E-commerce | Plus Jakarta Sans | Poppins |
| Consumer Social App | Figtree | DM Sans |
| Editorial / Media | Lora (body) + Playfair (display) | Merriweather |
| AI Product | Space Grotesk | Geist |
| Crypto / Web3 | Space Grotesk | Cabinet Grotesk |
| Enterprise / Internal Tool | Source Sans 3 | Lato |
| Portfolio / Creative | Syne | Cabinet Grotesk |
