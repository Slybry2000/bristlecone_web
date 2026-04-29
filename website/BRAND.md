# Bristlecone — brand reference

Source of truth for voice, vocabulary, and visual tokens. The full visual system lives in `design/design-system.html` (open in browser) and `design/brand-book-a4.pdf`.

## Positioning

**Tagline (primary):** *Step slowly. Compound for decades.*
**Tagline (alt):** *The slow-growth marketing OS for businesses built to last.*

**Anti-positioning** (what we are not):
- Not a growth-hacking tool.
- Not an AI content firehose.
- Not a "do marketing while you sleep" promise.
- Not for businesses that need to triple revenue in six months.

**Positioning** (what we are):
- A patient marketing OS for businesses with a 10–50 year horizon.
- Operator-in-the-loop by design. The human stays in command.
- Evidence-based. Every claim the system makes about a campaign is traceable.
- Boring on purpose. Compounding is boring. That's the point.

## The bristlecone metaphor

Bristlecone pines are the oldest non-clonal organisms on earth — some are over 4,800 years old. They grow on high-altitude ridgelines where conditions are harsh. They grow **millimeters per year**. Their wood is dense, twisted, and nearly impossible to kill. That is the brand.

Use this metaphor in copy when it earns its place. Don't oversell it. One bristlecone reference per page is plenty.

## Vocabulary

These terms come from the engine and should appear naturally in the website where the concept fits. Don't define every one on the homepage — introduce them where relevant on deeper pages.

| Term | What it means in product | Use on site for |
|---|---|---|
| **Rings** | Year-over-year history view | Reporting / "see your growth rings" |
| **Roots** | L2 context packs (offer, proof, brand, constraints) | Onboarding pages |
| **Soil** | Channel/audience environment | Channel-strategy pages |
| **Season** | A campaign cycle | "Plan a season" CTA |
| **Cone** | A campaign output / "drop a cone" | Launch / publish moments |
| **Grove** | Portfolio (multi-business) | Agency / multi-brand page |
| **Heartwood** | Governance substrate (c/r/j gates) | Trust/security/how-it-works |
| **Methuselah Mode** | 3–5 year planning view | Premium/pro tier feature |

Methuselah is the name of the oldest known bristlecone. Use sparingly — it's the "deep mode" easter-egg term.

## Voice

**Tone:** Calm. Grounded. Slightly weathered. A tradesperson who has been doing this for 30 years and has stopped trying to impress you.

**Cadence:** Short sentences. Periods. Few exclamation marks (zero is fine). Em-dashes are allowed but not constant.

**Pronouns:** "We" for Bristlecone the team. "You" for the operator. Avoid "users" — the operator is a person running a business, not a user.

**Humor:** Dry. Self-aware. Never zany. A wry observation lands; a joke does not.

**Authority:** We assume the reader knows their business better than we do. We are not here to teach them marketing — we are here to give them a substrate that respects what they already know.

### Voice exercises (write like these)

> "Most marketing tools assume you want to scale. Bristlecone assumes you want to last. Those aren't the same problem."

> "We don't have a 'growth hack' page. We don't have a 'success story' page yet either — we're new. What we have is a pipeline you can read end-to-end and a philosophy that doesn't change when funding rounds do."

> "The system will not send an email without you approving it. That sounds slow. It is. So is a bristlecone pine."

## Visual tokens (condensed)

Full system in `design/design-system.html`. Tokens to drop into `tailwind.config.js` or CSS variables:

```css
:root {
  --ink:        #2B2B2B;   /* primary text */
  --ink-soft:   #4A4540;   /* secondary text */
  --amber:      #C8893D;   /* accent — use sparingly */
  --amber-dim:  #9E6C2F;
  --forest:     #2F4A3A;   /* deep green */
  --sky:        #6B8FA8;   /* high-altitude blue */
  --parchment:  #F2EDE3;   /* page background */
  --bone:       #FAF6EC;   /* surface */
  --border:     #D9CFB8;
  --border-soft:#E8DEC8;
  --muted:      #6B645A;
  --dark-bg:    #14110D;
  --dark-fg:    #EDE6D6;
}
```

**Type:**
- Display: `EB Garamond` (serif, italic OK for taglines)
- Body: `Lora` (serif, comfortable reading)
- Mono: `IBM Plex Mono` (small caps, labels, code)

**No sans-serif on this site.** The brand is paper, not screen-default.

**Imagery:**
- High-altitude photography. Real. Not stock.
- Bristlecone silhouettes, growth-ring cross-sections, weathered wood textures.
- No corporate photography (people in headsets, handshakes, etc.).
- Subtle paper grain on backgrounds (already in design system).

**Motion:**
- Almost none. Fade-in on scroll is OK if subtle. No parallax. No bouncing.
- Honor `prefers-reduced-motion: reduce` — drop all motion in that case.

**Density:**
- Generous whitespace. Long-form pages should breathe.
- Long line lengths are fine for body copy (65–75ch); we are asking people to read.
