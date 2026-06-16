# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## What this repository is

This is a **Claude Code Skill definition**, not a runnable application. It packages the
`landing-page-builder` skill: instructions and references that tell an agent how to
generate a production-ready landing page for a business and self-critique it until it
passes a fixed quality rubric. The repo is entirely Markdown plus reference screenshots.

Files:
- `SKILL.md` — the skill entry point and **authoritative spec**. Its YAML frontmatter
  (`name`, `description`, `allowed-tools`) registers the skill; the body is the operating
  procedure.
- `design_system.md` — an **optional, stack-agnostic aesthetic catalog** (10 color +
  typography directions). Inspiration only; contains no build or framework instructions.
- `example_static_landing.md` — a worked, static-HTML example showing target fidelity.
- `website-template/<category>/` — per-category folders of **reference screenshots**
  (e.g. `plumbers/`), each optionally with a `category.md` describing the genre.

## The skill's runtime model

When invoked with a brief like *"create a landing page for XYZ Plumbing, here's their
info"*, the skill:

1. Determines the **category** and looks in `website-template/<category>/` for reference
   screenshots. It reads those screenshots **with vision** and extracts abstract qualities
   (layout patterns, hierarchy, mood, trust signals) — it never copies a specific site.
2. Sources **business facts** under a strict rule:
   - **No URL given** → net-new site; facts come only from the prompt (web search may
     *confirm* a given fact, never *originate* one).
   - **URL given** → the existing site is "off"; fetch it to harvest *facts and the
     business's own real photos only* — discard its copy and design.
   - **Hard guardrail:** every business fact on the page must trace to the prompt or the
     URL. Anything unsourced becomes a visible `[[… CONFIRM]]` token and a `REVIEW.md`
     line. Never fabricate a phone number, address, review, or service area.
3. Generates a single self-contained `index.html` (inline CSS, minimal vanilla JS).
4. Runs a **self-annealing loop**: critique against the rubric, fix failures, repeat,
   until it passes (>95%) or hits a **hard 5-pass cap**. On the cap it ships the
   best-scoring version and writes an honest `REVIEW.md` of remaining failures.
5. Outputs to `website-created/<company-slug>/` (`index.html` + `REVIEW.md`).

## Output stack (FIXED)

One self-contained static **`index.html`** per site. No frameworks, no build step, no
Python, no database, no trackers. Chosen for security (no server-side attack surface),
owner-friendliness (one hostable file), and clean upgradability (the static page becomes
the frontend if a backend is wired later). Do not introduce a framework into this skill.

## Hard constraints from SKILL.md (preserve when editing the skill)

- **Never copy** a reference site's layout, colors, copy, or distinctive look. Inspiration
  only; prefer multiple references per category to stay derivative-of-genre, not of one brand.
- **Never fabricate** business facts — unsourced facts become `[[… CONFIRM]]` tokens.
- **Never add** frameworks, build steps, Python, or trackers — output stays one static file.
- **Never loop past 5 passes** — ship best-effort plus an honest `REVIEW.md`.
- When rebuilding from a URL, reuse **facts and real photos only**; rewrite copy, replace design.

## Editing this repo

Changes here are prompt/spec edits, so:
- Keep `SKILL.md` frontmatter valid — `allowed-tools` constrains runtime behavior.
- Keep all files mutually consistent with the goal above. `design_system.md` and
  `example_static_landing.md` must never reintroduce framework/scaffolding language —
  that was the prior architecture and has been deliberately removed.
- `website-template/<category>/` must contain at least one reference screenshot for a
  category to be supported; otherwise the skill substitutes the closest category and
  notes it in `REVIEW.md`.

## History note

An earlier version of this skill modified a fixed React/Vite/Tailwind/GSAP template and
deployed to Netlify. That architecture has been **fully replaced** by the static-HTML,
reference-inspired, self-annealing approach described above. Any remaining reference to
React, Vite, GSAP, `npm create vite`, Tailwind config tokens, or Netlify deployment is
stale and should be removed on sight.
