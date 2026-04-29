# Tech stack

## Decision

**Astro + Tailwind (with custom design tokens) + MDX for content + Vercel for hosting.**

## Why Astro

- The site is overwhelmingly **content + static**. Astro renders to static HTML by default, which means the site is fast without doing anything special, ranks well, and has a tiny attack surface.
- **Islands architecture**: only the rare interactive thing (waitlist form, pricing toggle) ships JS. Everything else is plain HTML — which matches the brand. We are a paper-and-ink brand running on a website made of paper-and-ink primitives.
- **MDX for content**: journal entries, manifesto, changelog can be authored in Markdown with the occasional embedded component. No CMS overhead, content lives in git, version history is a feature.
- **Easy migration path** if we ever need a CMS — content collections in Astro are CMS-shaped.

## Why not Next.js

- Heavier than we need. SSR is solving a problem we don't have.
- Defaulting to React-everywhere on a content site is overkill and tempts us into client-side spaghetti.
- We may use Next.js for the **operator app** when that lands. Keep them separate.

## Why Tailwind (with restraint)

- Speed of iteration on layout, spacing, responsive.
- BUT: we treat Tailwind as a **utility layer over our design tokens**, not as the design system itself. Brand tokens go in `tailwind.config.js` extending the theme — `bg-parchment`, `text-ink`, `font-display`. Avoid arbitrary values in markup.
- No Tailwind UI component kit. No prebuilt hero components. We build from primitives.

## Why Vercel

- Astro deploys cleanly. Preview branches per PR. Zero config.
- If we ever want to leave, the build output is plain static HTML. Portable.
- (Cloudflare Pages is the equivalent backup option — pick on price/preference.)

## Initial dependency list

```json
{
  "dependencies": {
    "astro": "^4",
    "@astrojs/mdx": "^3",
    "@astrojs/tailwind": "^5",
    "@astrojs/sitemap": "^3",
    "@astrojs/rss": "^4",
    "tailwindcss": "^3",
    "@fontsource/eb-garamond": "^5",
    "@fontsource/lora": "^5",
    "@fontsource/ibm-plex-mono": "^5"
  }
}
```

That's the whole list at start. Resist additions.

## Things we are explicitly not using

- **Analytics that track individuals.** No Google Analytics, no Hotjar, no FullStory. If we measure anything, it's [Plausible](https://plausible.io) or [Fathom] — privacy-respecting, no cookie banner needed.
- **Chat widgets.** No Intercom, Drift, Crisp, etc. If someone wants to talk, they email us.
- **Marketing pixels.** No Facebook pixel, no LinkedIn Insight Tag. We are not running paid social.
- **A/B testing tooling.** Premature for a site this small, and against the brand spirit.
- **Cookie banners.** We won't need one because we won't set tracking cookies.
- **Newsletter pop-ups.** Footer signup is enough.

## Repo layout

```
bristlecone-site/
├── CLAUDE.md
├── README.md
├── BRAND.md
├── SITEMAP.md
├── BUILD-PLAN.md
├── STACK.md
├── astro.config.mjs
├── tailwind.config.js
├── package.json
├── public/
│   ├── fonts/                       (self-hosted, no Google Fonts CDN)
│   ├── images/
│   │   ├── bristlecone-hero.jpg
│   │   ├── ring-cross-section.svg
│   │   └── ...
│   └── favicon.svg
├── src/
│   ├── pages/
│   │   ├── index.astro
│   │   ├── philosophy.astro
│   │   ├── how-it-works.astro
│   │   ├── for-whom.astro
│   │   ├── pricing.astro
│   │   ├── waitlist.astro
│   │   ├── about.astro
│   │   ├── manifesto.astro
│   │   ├── colophon.astro
│   │   ├── changelog.astro
│   │   └── journal/
│   │       ├── index.astro
│   │       └── [slug].astro
│   ├── content/
│   │   ├── config.ts                (Astro content collections)
│   │   ├── journal/                 (MDX files, one per entry)
│   │   └── changelog/               (MDX files, one per entry)
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── Wordmark.astro
│   │   ├── Button.astro
│   │   ├── PaperCard.astro
│   │   ├── PullQuote.astro
│   │   ├── PipelineDiagram.astro
│   │   └── WaitlistForm.astro       (the rare interactive island)
│   ├── layouts/
│   │   ├── Base.astro
│   │   ├── Page.astro
│   │   └── LongForm.astro
│   └── styles/
│       └── tokens.css               (CSS variables from BRAND.md)
└── design/                          (copied from main repo)
    ├── design-system.html
    ├── brand-book-a4.pdf
    └── brand/
```

## Performance budget

- **Largest Contentful Paint** < 1.5s on a fast 3G profile.
- **Total page weight** < 200KB on landing pages (excluding hero image, which can add up to 150KB more if it's truly necessary).
- **JS shipped to client** < 10KB on landing pages. Waitlist form is the only place that should ship a real JS island.
- **Web fonts**: 3 families, max 4 weights total, self-hosted with `font-display: swap`.

If a page exceeds the budget, we ship something simpler before we ship something heavier.

## Accessibility floor (not aspiration — floor)

- WCAG 2.1 AA contrast on all text/background combinations.
- Real semantic HTML — `<article>`, `<nav>`, `<main>`, headings in order.
- Keyboard-navigable on every page.
- `prefers-reduced-motion` honored.
- Alt text on every image. Decorative images use `alt=""`.

This isn't a checkbox exercise — it's part of the brand. A site for "businesses built to last" should work for everyone.
