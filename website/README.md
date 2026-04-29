# bristlecone.so — website build packet

This folder is the **seed** for a new repo (`bristlecone-site` or similar) that builds the public marketing site at **bristlecone.so**. Copy these files into the new repo's root before pointing Claude Code at it.

## What's in here

| File | Purpose |
|---|---|
| `README.md` | This file. Orientation. |
| `CLAUDE.md` | Instructions Claude Code reads on every session in the new repo. Read first. |
| `BRAND.md` | Voice, vocabulary, visual tokens. Source of truth for copy + design. |
| `SITEMAP.md` | Information architecture, page-by-page blueprints with content beats. |
| `BUILD-PLAN.md` | Phased roadmap (Phase 0 → Phase 4) with done-criteria per phase. |
| `STACK.md` | Tech stack decision + reasoning + initial dependency list. |

The existing `design/design-system.html` and `design/brand/` assets in the **current** repo are also part of this packet — copy them into `bristlecone-site/design/` so the new repo has its visual reference on hand.

## Why a separate repo

The website is a **marketing surface**, not part of the engine. Different deploy cadence, different audience (prospects vs. operators), different content velocity (blog/changelog/docs evolve weekly; engine ships when ready). Coupling them creates noise in both directions.

## Success criteria for the site

1. A **skeptical small business owner** lands on the homepage and within 30 seconds understands: "this is the opposite of growth-hacking — it's slow, governed, and built to compound."
2. They can read **one full page** without hitting a buzzword they'd roll their eyes at. (No "10x", "AI-powered", "supercharge", "unleash", "game-changer".)
3. They convert to **waitlist** or **book-a-call** with a clear sense of what they'd be signing up for, not a vague "learn more".
4. The site itself **demonstrates** the brand. Quiet, durable, well-made. No autoplay video, no popup nags, no chat bubble harassment.

## How to use this packet with Claude Code

1. `git init bristlecone-site` (or however you create it)
2. Copy this `design/website/` folder's contents into the new repo root.
3. Copy `design/brand/` and `design/design-system.html` into `bristlecone-site/design/`.
4. `cd bristlecone-site && claude` — Claude Code will read `CLAUDE.md` automatically.
5. First prompt: *"Read CLAUDE.md, BRAND.md, SITEMAP.md, BUILD-PLAN.md, STACK.md. Then start Phase 0."*
