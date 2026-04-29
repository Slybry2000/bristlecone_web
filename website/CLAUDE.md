# Bristlecone website — instructions for Claude Code

You are working on the marketing website for **Bristlecone** (bristlecone.so). This file is loaded automatically every session. Read `BRAND.md`, `SITEMAP.md`, `BUILD-PLAN.md`, and `STACK.md` before generating anything substantive.

## What Bristlecone is, in one paragraph

Bristlecone is a marketing OS for small businesses who don't want to grow fast — they want to grow well, for decades. It runs campaigns through a Goal → Strategy → Tactic pipeline with the operator in the loop on every consequential decision (commit / revise / jurisdiction). It doesn't promise hockey-stick growth. It doesn't replace the operator. It's a patient, governed substrate that compounds — one season, one cone, one ring at a time.

## Who you are writing for

The buyer is a **cautious small business owner who has been burned** by aggressive marketing tools, growth-hackers, and AI-slop content generators. They are wise to be skeptical. They are not stupid — they are tired. They want methodical, evidence-based, calm. They've been around long enough to recognize that anything claiming "10x" is selling them something.

When in doubt about a copy decision, ask: *would this make that person trust us less, or more?*

## Hard rules for this site

1. **No buzzword vocabulary.** Banned: 10x, supercharge, unleash, game-changer, revolutionize, disrupt, AI-powered, next-gen, blazing fast, mission-critical, synergy, leverage (as a verb), empower, robust, seamless, cutting-edge.
2. **No fake urgency.** No countdown timers, no "limited spots", no "only X left", no "Y people viewing now".
3. **No popup nags.** No exit-intent modals, no email-gate before content, no chat bubble that opens itself.
4. **No autoplay anything.** Video, audio, animation — all opt-in. Respect `prefers-reduced-motion`.
5. **No fake testimonials or logo soup.** If we don't have real customers yet, say so. Show the philosophy, not fabricated proof.
6. **No dark patterns on pricing.** Annual vs monthly is fine; pre-checked add-ons, hidden fees, or trial-by-default-then-charge are not.
7. **Plain language.** If a smart 14-year-old wouldn't understand the sentence, rewrite it.
8. **Specifics over claims.** "Faster" is a claim. "Renders in 80ms" is a specific. Always prefer the specific.

## Working style

- **Edit existing files; don't create new ones unless required.** This includes content files — prefer expanding an existing page over fragmenting into many small ones.
- **No comments in code** unless something genuinely surprises a future reader. Don't narrate what the code does.
- **No emojis in copy or code** unless the user explicitly asks. The brand is paper-and-ink, not Slack-and-confetti.
- **One change per commit.** Commits should read like sentences: "add hero illustration", "tighten /philosophy copy", "wire newsletter form to ConvertKit".
- **Verify before claiming done.** If you change a page, view it in the browser. Type-checking ≠ feature-checking.
- **Ask before destructive actions.** Deleting pages, removing routes, dropping dependencies, force-pushing — all need confirmation.

## Voice cheatsheet

| Don't write | Write instead |
|---|---|
| "Bristlecone leverages AI to supercharge your marketing" | "Bristlecone runs your campaigns. You stay in the loop on what matters." |
| "Get blazing fast results in minutes" | "Most campaigns ship in a week. The first one takes longer." |
| "Trusted by 1000+ companies" *(if untrue)* | "We're new. Here's what we believe and how we work — decide if that fits you." |
| "Unleash your growth potential" | "Grow at the pace your business can actually absorb." |
| "AI-powered automation" | "A pipeline you can read end-to-end, with agents at the thinking points." |

## Decision-making

- For ambiguous design or copy choices, **pick one, ship it, defend the choice in the commit message.** Do not present the user with multiple-choice menus. They want commit/revise/jurisdiction, not "A or B?".
- For tech-stack changes (adding a dependency, swapping a tool), **ask first.** Stack drift is expensive.
- For brand vocabulary (Rings, Roots, Soil, Season, Cone, Grove, Heartwood, Methuselah Mode), see `BRAND.md`. Use these terms when they fit; don't force them.

## When you finish a phase

Update `BUILD-PLAN.md` to check off the phase, then stop and report. Do not auto-advance to the next phase without operator approval — phases are deliberate gates.
