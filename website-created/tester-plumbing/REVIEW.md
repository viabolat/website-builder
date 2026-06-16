# REVIEW — Tester Plumbing

**Output:** `website-created/tester-plumbing/index.html` (single self-contained static file, ~34 KB)
**Sourcing mode:** No URL provided → **net-new site**. Only facts given in the prompt appear on the page.
**References used:** `website-template/plumbers/` (`lentheplumber.com.png`, `proficientplumbingheating.com.png`) — used for genre *qualities* only (trust strip, click-to-call prominence, service cards, service-area emphasis). Layout/colors/copy are original; not copied from either site.
**Aesthetic:** design_system.md archetype #9 *Industrial Utility* (trades fit) blended with a hydro-blue primary so it reads as plumbing and stays visually distinct from the navy+red references. Fonts: IBM Plex Sans / IBM Plex Mono.

## Sourced facts (the only business facts on the page)
| Fact | Value | Source |
|------|-------|--------|
| Name | Tester Plumbing | prompt ("Tester plumber"; "Plumbing" added as descriptor) |
| Phone | (512) 555-1212 | prompt |
| Address | 123 Dark Rd, Bergen, NJ | prompt |
| Category | Plumber | prompt |

Nothing else is asserted as fact. No reviews, license numbers, hours, years-in-business, or extra service-area towns were invented.

## Rubric scorecard — PASS (8/8)
| # | Check | Result |
|---|-------|--------|
| 1 | Clean render (no lorem/broken assets) | ✅ 0 lorem; all icons inline SVG; favicon + OG image are self-contained data URIs; no external `<img>` to 404 |
| 2 | Required sections | ✅ hero, trust strip, services, about/trust, service area, contact + CTA, final CTA band. Social proof = **honest omission** (see below) |
| 3 | Fact accuracy | ✅ only the 4 sourced facts appear; no other phone-like strings; unsourced items flagged as visible `[[…CONFIRM]]` tokens |
| 4 | Responsive (375 / 1440) | ✅ fluid `clamp()` type, grids collapse at 900/680px, mobile hamburger nav + sticky one-tap call bar |
| 5 | Accessibility (WCAG AA) | ✅ skip link, `lang`, single h1 → ordered headings, decorative SVGs `aria-hidden`, labelled form fields, `aria-live` status, visible focus rings. Contrast: body/links ≥7:1, CTA `#c2410c`+white ≈5.2:1 (AA); safety-orange used for non-text accents only |
| 6 | Security/perf floor | ✅ one static file, no trackers, no external scripts, no secrets. Only network resource is Google Fonts. (`http://www.w3.org/2000/svg` is an XML namespace ID, never fetched) |
| 7 | Visual quality | ✅ matches reference quality level with an original layout/palette |
| 8 | SEO basics | ✅ title, meta description, 5 OG tags, canonical, JSON-LD `Plumber` LocalBusiness, clean heading hierarchy |

Passes were: pass 1 generated; one invalid leftover CSS token removed; re-validated → all green. No 5-cap hit.

## Open items to confirm with the owner (not blockers, intentionally surfaced)
These appear on the page as visible `[[…CONFIRM]]` tokens so they can't ship silently:

1. **⚠️ Phone area code vs. location.** `(512)` is an Austin, **Texas** area code, but the address is in **NJ**. Used exactly as provided — please confirm the number is correct (likely a typo for a NJ area code such as 201/551/973/908).
2. **Hours** — none provided. Shown as `[[HOURS — CONFIRM]]` in the hero card and contact block. Provide real hours (and whether you offer emergency/after-hours service).
3. **Licensed & insured** — shown with a `[[CONFIRM]]` token in the trust strip. Not asserted until confirmed; add your NJ master plumber license # when available.
4. **Service area** — only "Bergen, NJ" is stated (from the address). Nearby towns/ZIPs flagged `[[CONFIRM]]`. ("Bergen" was treated as the locality as given; if you meant **Bergen County**, confirm the towns you cover.)
5. **Services list** is genre-typical (drain/sewer, leaks, water heaters, fixtures, toilets/sump pumps, urgent) — **not yet confirmed for this business**. Trim or add to match what you actually offer.
6. **No testimonials/reviews** — honestly omitted (none were provided). Add real, attributed reviews later to strengthen trust.
7. **Quote form has no backend.** As required by the static-only stack, it does not send email; on submit it gracefully directs the visitor to call. Wiring it to email/booking is a deliberate later step that reuses this exact HTML.
8. **Domain placeholders** — `canonical`/OG use `https://www.testerplumbing.com/`; replace with the real domain when hosted.

## How to use
Open `index.html` in any browser, or drop the `tester-plumbing/` folder onto any static host (Netlify, GitHub Pages, etc.). No build step, no dependencies.
