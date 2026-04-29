# Build plan

Phased build for bristlecone.so. Each phase has a **done-criterion** — a concrete check that says "we can ship this." Don't advance to the next phase until the current one's criterion is met.

Mark phases with `[x]` when complete. Stop and report after each phase.

---

## Phase 0 — Foundation

**Goal:** A repo that can build, deploy, and render a single styled page.

- [ ] `npm create astro@latest` — minimal template, TypeScript strict, no example pages.
- [ ] Add `@astrojs/tailwind`, `@astrojs/mdx`, `@astrojs/sitemap`, `@astrojs/rss`.
- [ ] Self-host the three fonts via `@fontsource/*` packages.
- [ ] Wire `tailwind.config.js` to extend with brand tokens from `BRAND.md` (colors + font families).
- [ ] Create `src/styles/tokens.css` with the full CSS-variable set; import in the base layout.
- [ ] Build `src/layouts/Base.astro` with the paper-grain background, default fonts, and reset.
- [ ] Build `src/components/Header.astro` and `Footer.astro` per the SITEMAP nav spec.
- [ ] Build a placeholder `index.astro` that renders the wordmark, nav, footer, and a single sentence: *"Step slowly. Compound for decades."*
- [ ] Deploy preview to Vercel. Confirm static output.

**Done when:** `npm run build` produces static HTML, the deployed preview loads in <1s, and the page passes a Lighthouse run with Performance ≥ 95 and Accessibility = 100.

---

## Phase 1 — Brand spine

**Goal:** All shared primitives the site will use repeatedly. Build these once, well.

- [ ] `Wordmark.astro` — uses the SVG/PNG from `design/brand/`. Inline SVG preferred for crispness.
- [ ] `Button.astro` — primary (amber pill), ghost, with hover/focus states honoring brand tokens. No animations beyond a subtle color shift.
- [ ] `PaperCard.astro` — the bone-colored card with soft border and amber accent line.
- [ ] `PullQuote.astro` — large italic display serif, optional attribution.
- [ ] `SectionLabel.astro` — the small uppercase mono amber label that prefixes sections in the design system.
- [ ] `PipelineDiagram.astro` — static SVG of Goal → Strategy → Tactic with c/r/j gates. Hand-drawn-ish, not corporate-flowchart-ish.
- [ ] `LongForm.astro` layout — generous margins (~75ch line length), drop caps optional, no sidebar.
- [ ] Set up content collections in `src/content/config.ts` for `journal` and `changelog`.

**Done when:** A "kitchen sink" page (`/_dev/components` — gitignored or removed before launch) renders every primitive in light + dark, every state. Visual review against `design/design-system.html` shows fidelity.

---

## Phase 2 — Core pages

**Goal:** All routes from the SITEMAP exist with real (draft-quality) copy. Pages are readable end-to-end. No placeholder lorem.

Build in this order:

- [ ] `/` — Home. Use the blueprint in `SITEMAP.md` directly. Hero illustration can be a placeholder photograph at this stage.
- [ ] `/philosophy` — Long-form, ~1,500 words. Founder writes the first draft; do not generate.
- [ ] `/how-it-works` — Walk through one season. Include the pipeline diagram.
- [ ] `/for-whom` — Two-column self-selection page.
- [ ] `/pricing` — Tiers, FAQ, no nags.
- [ ] `/waitlist` — Single-purpose page. Form posts to ConvertKit/Buttondown/Postmark — pick one and document the choice in `STACK.md`.
- [ ] `/about` — Short, signed.
- [ ] `/manifesto` — Long-form, founder-written.
- [ ] `/colophon` — Credits.
- [ ] `/changelog` — Index + collection setup. Seed with 3 real entries from the engine repo's recent commits.
- [ ] `/journal` — Index + detail route via dynamic `[slug].astro`. Seed with 1 real piece (the philosophy essay can be repurposed as journal piece #1 if appropriate).
- [ ] `/legal/privacy`, `/legal/terms` — boilerplate-respectable, lawyer-reviewed before launch.

**Done when:** Every nav link resolves. Every page passes a manual read-through ("would the cautious small business owner trust this?"). No buzzword vocabulary anywhere. Lighthouse Performance ≥ 95 on every page.

---

## Phase 3 — Polish & motion

**Goal:** The site feels considered, not generic.

- [ ] Hero illustration: commission or curate a real bristlecone photograph. Optimize: AVIF + JPEG fallback, lazy-loaded below the fold.
- [ ] Subtle scroll-triggered fade-ins on long-form sections. Honor `prefers-reduced-motion`.
- [ ] Refine typography rhythm: line-height, paragraph spacing, drop caps on long-form pages, italic emphasis used surgically.
- [ ] Open Graph + Twitter card images for every page. Use the brand book's lockup against parchment.
- [ ] Favicon set (16, 32, 180 apple-touch, 512 manifest, SVG).
- [ ] `robots.txt`, `sitemap.xml` (auto from `@astrojs/sitemap`), RSS feed for journal.
- [ ] 404 page that matches the brand. Quiet, not clever.
- [ ] Print stylesheet — long-form pages should print well. This is the kind of detail that signals craft.

**Done when:** Founder reads the whole site on a phone and on a laptop and says "yes, this is us."

---

## Phase 4 — Conversion & analytics

**Goal:** Measure what matters without surveilling anyone.

- [ ] Plausible (or Fathom) installed. Verify zero cookies set, zero personal data collected.
- [ ] Waitlist form wired to actual email service. Test end-to-end: submit → land in inbox → automated confirmation back to user that says *what happens next*.
- [ ] Simple goal events: waitlist submit, journal-piece read-completion (scroll to bottom).
- [ ] No retargeting pixels. No conversion-tracking SDKs.
- [ ] Performance audit: real-world LCP measurement via [WebPageTest] from a few geos. Fix anything over budget.
- [ ] Accessibility audit: real screen-reader pass on home, philosophy, waitlist. Fix what's broken.
- [ ] Legal review of `/legal/*` pages.

**Done when:** A real prospect can land, read, decide, and join the waitlist with no friction and no surveillance.

---

## Phase 5 (later) — Earned content cadence

Not part of launch. Listed so we don't forget.

- Monthly journal piece. Quality over volume.
- Weekly changelog entry IF something shipped. No filler entries.
- Quarterly review: re-read every page; what's stale, what's drifted, what's no longer true. Fix.

---

## Things explicitly out of scope for v1

- **Operator app / dashboard.** Different repo, different time.
- **Customer testimonials.** We don't have customers yet. Don't fabricate.
- **Case studies.** Same.
- **Documentation site.** Until we have customers running real seasons, this is premature.
- **Localization.** English only at launch.
- **Comments / community / forum.** No.
- **Email newsletter beyond waitlist.** When we have something to say monthly, the journal RSS is the channel.

---

## Launch checklist (pre-flight, after Phase 4)

- [ ] All forms tested in production with a real email address.
- [ ] All external links open correctly. No dangling anchors.
- [ ] Favicon shows in browser tab and bookmark.
- [ ] OG cards render correctly when shared on LinkedIn, Twitter/X, iMessage, Slack.
- [ ] Lighthouse on every page: Performance ≥ 95, Accessibility = 100, Best Practices ≥ 95, SEO ≥ 95.
- [ ] No console errors on any page in any browser (Chrome, Safari, Firefox, mobile Safari).
- [ ] Real DNS pointed at bristlecone.so. SSL valid. www → apex redirect set.
- [ ] `robots.txt` allows indexing. `sitemap.xml` submitted to Google Search Console.
- [ ] Final read-through by someone who's not the founder. Cold reader test: "does the site sell you, or talk past you?"
