---
name: landing-page-builder
description: Generate a production-ready landing page for a business from a brief, using category reference screenshots as visual inspiration (never copied), then self-critique against a fixed rubric until it passes or hits a 5-pass cap. Use when creating a landing page or website for a local business or service company.
allowed-tools: Read, Write, Edit, Grep, Glob, Bash, WebFetch, WebSearch
---

# Landing Page Builder — Reference-Inspired, Self-Annealing, Static HTML

## Goal
Take a brief like *"create a landing page for XYZ Plumbing, here's their info"* and produce a single, self-contained, production-ready landing page. Use category reference screenshots as a **quality and mood guide only** — never as something to copy. Drive output through a **self-critique loop** against a fixed rubric until it passes (>95%) or hits a hard 5-pass cap, at which point it ships the best version and writes an honest `REVIEW.md`.

## Output Tech Stack (FIXED — do not substitute)
Each site is **one self-contained `index.html`** with inline `<style>` and minimal vanilla `<script>`. No frameworks, no build step, no Python, no external runtime dependencies.

Rationale (preserve this reasoning when editing):
- **Secure by construction**: a static file has no server-side attack surface, no dependencies to patch, no database.
- **Owner-friendly**: one file a non-technical owner can host anywhere (Netlify drop, GitHub Pages, any host) and hand to anyone.
- **Upgradable without loss**: the static page IS the frontend. Later backend wiring (contact form → email, booking, CMS, payments) is a deliberate additive step that reuses this exact HTML/CSS. Starting with a framework would add rot and complexity for no day-one benefit.

Allowed external resources, used sparingly: Google Fonts (via `<link>`), and `<img>` tags pointing at real, owner-provided or category-appropriate stock image URLs. **No analytics, no trackers, no third-party scripts** unless the owner explicitly requests them later.

## Inputs
- **Brand name** (required): the company/project name.
- **Brand facts** (required): services, phone, address/area served, hours, anything the owner provides.
- **Category** (required, inferred if not stated): e.g. plumbing, dental, landscaping. Maps to a reference folder.
- **Existing URL** (optional): see Sourcing Rule below.
- **Conversion goal** (optional, default: "call us / request a quote").

## Sourcing Rule (CRITICAL — prevents fabrication)
There are two modes, decided by whether a URL is provided:

1. **No URL → net-new site.** The business has no usable web presence. Every business fact on the page must come from the prompt. Web search is permitted ONLY to *confirm* a fact already given (e.g. verify the business exists, confirm the city) — **never to originate a fact that appears on the page.**

2. **URL provided → rebuild.** The existing site is "off." Fetch it and **harvest facts and the business's own real photos** (name, phone, address, hours, services, genuine testimonials, photos of their trucks/team/work). **Do NOT reuse their marketing copy** (rewrite it — stale copy is usually why the site is "off") and **do NOT reuse their layout or design** (that is what this skill replaces).

**Hard guardrail — every business fact on the page must trace to (a) the prompt or (b) the provided URL.** Any fact you cannot source must appear as a visible placeholder token like `[[PHONE — CONFIRM]]` and be listed in `REVIEW.md`. Never invent a phone number, address, review, license number, or service area. A fabricated fact is the worst possible failure for a production small-business site.

## Reference Screenshots
Category references live at `website-template/<category>/` (e.g. `website-template/plumbers/`), containing:
- 1–N screenshots (`.png` / `.jpg`) of professional sites in that category.
- An optional `category.md` describing the genre's expectations (see `category.md` template).

**Read the screenshots with vision** before generating. Extract *abstract qualities*: layout patterns, visual hierarchy, spacing rhythm, color mood, section ordering, what trust signals the genre uses. **Never reproduce a specific site's layout, color scheme, copy, or distinctive look** — using several varied references keeps output derivative-of-the-genre, not derivative-of-one-brand (which avoids trade-dress problems). If only one reference exists, treat it as *one data point about the genre*, not a template to mimic.

If `website-template/<category>/` does not exist, pick the closest existing category, note the substitution in `REVIEW.md`, and proceed.

## Aesthetic Direction (optional)
`design_system.md` is an optional, stack-agnostic catalog of palette + typography directions. Use it when the references don't imply a clear direction or when you want a more distinctive, less generic look. Translate the chosen direction into inline CSS — it never changes the output stack (still one static `index.html`). See `example_static_landing.md` for a worked example at target fidelity.

## Output Location
Write to `website-created/<company-slug>/` (create `website-created/` if absent). Slug = lowercase, hyphenated company name.

```
website-created/
  xyz-plumbing/
    index.html        # the complete, self-contained landing page
    REVIEW.md         # rubric scores + any unresolved gaps/placeholders
    assets/           # only if local images are downloaded (optional)
```

Do not overwrite an existing company folder without confirming first.

## Acceptance Rubric (the definition of "correct")
Score each pass against these. "Pass" = all items satisfied (>95%).

1. **Clean render**: no console errors, no broken images, no placeholder/lorem text (except intentional `[[… CONFIRM]]` tokens).
2. **Required sections**: hero, services/offerings, about/trust, social proof (or honest omission if none sourced), contact + clear CTA.
3. **Fact accuracy**: every business fact traces to prompt or URL; nothing invented.
4. **Responsive**: usable and unbroken at 375px (mobile) and 1440px (desktop).
5. **Accessibility (WCAG AA floor)**: alt text on images, semantic heading order, AA color contrast, focusable interactive elements.
6. **Security/perf floor**: no trackers, no inline secrets, valid HTML, all assets resolve, no render-blocking bloat.
7. **Visual quality**: matches the *quality level* of the reference screenshots without copying their layout.
8. **SEO basics**: `<title>`, meta description, Open Graph tags, sensible heading hierarchy.

## Self-Annealing Loop (with hard 5-cap)
```
pass = 0
generate initial index.html from facts + reference qualities
loop:
    pass += 1
    self-critique index.html against all 8 rubric items; score each
    if all items pass:
        finalize; write REVIEW.md (all green); STOP
    if pass >= 5:
        keep the best-scoring version produced so far
        write REVIEW.md listing every check that still FAILS and why
        STOP  ← do not loop past 5; a human decides next
    else:
        fix the specific failing items; repeat
```
The 5-cap is absolute. Shipping a best-effort version with an honest failure report is always better than silent looping or a fabricated pass. Keep each pass's score so "best version" is well-defined.

## Process
1. **Parse the brief**: extract brand, facts, category, optional URL, CTA goal. Decide Sourcing Mode.
2. **Source facts**: net-new → prompt only (search to confirm); rebuild → fetch URL, harvest facts + real photos, discard old copy/design.
3. **Read references**: open `website-template/<category>/` screenshots with vision; read `category.md` if present. Extract genre qualities.
4. **Generate** `index.html`: write fresh copy in the brand's voice; build layout informed by — not copied from — the references; insert only sourced facts; placeholder-token anything unsourced.
5. **Run the self-annealing loop** above.
6. **Write** `website-created/<slug>/index.html` + `REVIEW.md`.
7. **Return** the local path and a one-line summary of any unresolved `REVIEW.md` items.

## What NOT to Do
- **Do not copy** any reference site's layout, colors, copy, or distinctive look. Inspiration only.
- **Do not fabricate** any business fact. Unsourced → placeholder token + `REVIEW.md`.
- **Do not add** frameworks, build steps, Python, databases, or trackers. One static HTML file.
- **Do not loop past 5 passes.** Ship best-effort + honest report.
- **Do not reuse** an existing site's marketing copy or design when rebuilding — facts and real photos only.

## First-Run Setup
If `website-template/` has no category subfolders, tell the user this skill needs reference screenshots: create `website-template/<category>/`, drop in 1–N screenshots of professional sites in that genre, and optionally add a `category.md`. Then re-run.
