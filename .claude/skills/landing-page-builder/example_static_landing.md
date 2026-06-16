# Worked Example — Static-HTML Landing Page (Target Fidelity)

> This is the gold-standard reference for the **depth and quality** the
> `landing-page-builder` skill should produce. It is illustrative, not a template to
> copy. The output is always a single self-contained `index.html`.

## The brief (example)
> "Create a landing page for **Cedar & Stone Plumbing**. Family-owned, serving the
> Austin metro. Services: emergency repairs, water heaters, drain cleaning, repiping.
> Licensed & insured, 15 years in business. Phone 512-555-0147. Goal: get people to call."

- **Category**: plumbing → references in `website-template/plumbers/`.
- **Mode**: net-new (no URL) → all facts from the prompt; nothing invented.
- **Aesthetic direction** (from `design_system.md`): "Industrial Utility" fits a trade
  that signals reliability — Gunmetal / Safety Orange / Steel, IBM Plex type.

## What "target fidelity" means here
A small-business owner should look at the result and think *"this looks like a real,
trustworthy company,"* and a developer should see clean, valid, dependency-free HTML.

### Structure of the single `index.html`
- `<head>`: title, meta description, Open Graph tags, one Google Fonts `<link>`,
  a single inline `<style>` block using CSS custom properties for the palette.
- **Hero**: company name, one-line value prop, a large tap-to-call button showing the
  real phone number, and a trust line ("Licensed & insured · 15 years in Austin").
- **Services**: a responsive grid of the four real services — no invented services.
- **Trust strip**: license/insured/years/local cues drawn only from the brief.
- **Social proof**: if no reviews were provided, omit honestly or use a neutral
  "what to expect" block — do NOT fabricate testimonials.
- **Service area**: "Serving the Austin metro" — exactly as given, not expanded.
- **Contact / CTA**: prominent phone CTA repeated; a simple contact block. (A working
  contact *form* is a later backend upgrade — the static page leaves a clean place for it.)
- **Footer**: name, phone, area, copyright.
- Minimal vanilla JS only if needed (e.g. mobile nav toggle, smooth scroll). No libraries.

### Fact-handling in this example
Every fact on the page (name, phone, area, services, "15 years", "licensed & insured")
traces directly to the brief. If the brief had omitted the phone number, the CTA would
read `[[PHONE — CONFIRM]]` and `REVIEW.md` would flag it — never a guessed number.

### How the references were used
The `plumbers/` screenshots informed *qualities only*: a prominent click-to-call pattern,
a credentials strip near the top, warm local-business tone, before/after photo placement.
The layout, colors, and copy are original to Cedar & Stone — no screenshot was reproduced.

## Self-annealing in this example
Pass 1 produced a solid page but failed two rubric items: a hero image lacked `alt` text
(item 5) and the Open Graph tags were missing (item 8). Pass 2 fixed both; all 8 items
passed; `REVIEW.md` recorded all-green and the loop stopped at pass 2 — well under the
5-pass cap.

## Key takeaway
Quality comes from: original copy in the brand's voice, a fitting aesthetic direction,
strict use of only real facts, and the rubric-driven loop — not from copying a reference
or reaching for a framework. One static file, production-ready.
