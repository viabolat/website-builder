# Aesthetic Direction Catalog

> **Purpose:** This is an OPTIONAL inspiration source for the `landing-page-builder` skill.
> It is a curated catalog of color palettes and typography pairings — nothing more.
>
> **Stack-agnostic by design.** This file contains NO build instructions, NO framework,
> NO scaffolding steps. The skill's output is always a single self-contained static
> `index.html` (see `SKILL.md`). Use these archetypes only to pick a *color and type
> direction* that fits the business and the category reference screenshots. Translate
> the chosen direction into inline CSS in the static HTML — never into a framework.
>
> Choosing an archetype is optional. If a category's reference screenshots already imply
> a clear direction, follow the screenshots. Use this catalog when you need a starting
> point or want a more distinctive, less generic palette than the obvious default.

## How to use this catalog
1. Look at the category reference screenshots and the brand's tone.
2. Pick the archetype whose identity best fits the business (or blend two).
3. Implement its palette as CSS custom properties and its fonts via a Google Fonts `<link>`.
4. Keep everything in the one static `index.html`. No new dependencies.

---

## Aesthetic Archetypes

Each entry is a *palette + typography* direction. Hex values are starting points — adjust
for contrast (WCAG AA is a hard requirement in the rubric).

### 1. Ethereal Clinical (Light & Breathable)
- **Fits**: modern medical, dental, wellness, high-end care services.
- **Palette**: Alabaster `#F8F9FA`, Slate Blue `#4A5568`, Soft Sage `#9AE6B4`.
- **Type**: "Outfit" (headings), "Newsreader" italic (emphasis), "Geist Mono" (data/figures).

### 2. Obsidian Vault (Ultra-Premium Dark)
- **Fits**: wealth/financial advisory, luxury services, premium contractors.
- **Palette**: Near-black `#050505`, Tungsten `#2A2A2A`, Gold Leaf `#D4AF37`.
- **Type**: "Syne" (headings), "Playfair Display" italic (emphasis).

### 3. Synthetic Neon (Vibrant, High-Energy)
- **Fits**: tech-forward services, modern startups, anything wanting a bold edge.
- **Palette**: Zinc `#18181B`, Neon Cyan `#00F0FF`, Magenta `#FF003C`.
- **Type**: "Clash Display" (headings), "JetBrains Mono" (accents/data).

### 4. Editorial Brutalism (High-Contrast Monogram)
- **Fits**: design agencies, architects, high-end specialty trades.
- **Palette**: White `#FFFFFF`, Black `#000000`, Silver `#CCCCCC`.
- **Type**: "Oswald" (large headings), "Cormorant" (body).
- **Notes**: strong grid, large type, extreme contrast — keep it readable.

### 5. Nostalgic Terminal (Retro Technical)
- **Fits**: developer tools, IT services, technical niche brands.
- **Palette**: Phosphor Green `#39FF14`, Beige `#F3E8D6`, Terminal Black `#0C0C0C`.
- **Type**: "Fira Code" throughout.
- **Notes**: monospace feel, subtle scanline texture — use lightly, stay legible.

### 6. Organic Clay (Earthy & Grounded)
- **Fits**: landscaping, sustainable goods, home & garden, family trades.
- **Palette**: Terracotta `#E2725B`, Sand `#F4A460`, Forest `#2E8B57`.
- **Type**: "Fraunces" (headings), "Inter" (body).
- **Notes**: soft shadows, generous rounded corners, warm and approachable.

### 7. Kinetic Type (Bold & Expressive)
- **Fits**: events, creative services, energetic consumer brands.
- **Palette**: Electric Blue `#7DF9FF`, Acid Yellow `#E8FF00`, Pitch `#101010`.
- **Type**: "Anton" (headings), "Space Grotesk" (body).

### 8. Frosted Glass (Sleek & Modern)
- **Fits**: SaaS-adjacent services, modern professional firms.
- **Palette**: Midnight `#191970`, Violet `#B026FF`, Frosted White `rgba(255,255,255,0.1)`.
- **Type**: "Plus Jakarta Sans" (headings), "Sora" (body).
- **Notes**: soft blurred background shapes behind cards — keep performance in check.

### 9. Industrial Utility (Dense & Functional)
- **Fits**: logistics, HVAC, plumbing, B2B trade services, anything operational.
- **Palette**: Gunmetal `#2A3439`, Safety Orange `#FF6700`, Steel `#71797E`.
- **Type**: "IBM Plex Sans" (headings), "IBM Plex Mono" (figures).
- **Notes**: clear, sturdy, no-nonsense — strong fit for trades that signal reliability.

### 10. Cinematic Editorial (Visual-Heavy)
- **Fits**: hospitality, premium real estate, photography, food.
- **Palette**: Charcoal `#36454F`, Cream `#FFFDD0`, Crimson `#DC143C`.
- **Type**: "Cinzel" (headings), "Lora" (body).
- **Notes**: large imagery with small elegant type overlaid.

---

## Reminder
These are directions, not templates. Two plumbing sites built from "Industrial Utility"
should still look different — driven by their own photos, copy, and the specific reference
screenshots. The catalog prevents generic defaults; it does not replace per-brand judgment.
The output is always one static `index.html`.
