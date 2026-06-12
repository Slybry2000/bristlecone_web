# Apply the Bristlecone brand to a product surface

Goal: every operator tool reads as the same family — **warm near-black console,
Living Amber as the single accent, serif voice, the bristlecone mark in the
header.** Minimal diff. Never break layout or functionality.

## Canonical values (from brand-book-a4.html v1)

| role | light | dark / console |
|---|---|---|
| accent (THE one) | Living Amber `#C8893D` | brightened amber `#D9A04A` |
| ink / text | Charcoal `#2B2B2B` | bone `#EFE7D6` |
| surface / page | Parchment `#F2EDE3` | warm near-black `#14110D` |
| raised card | Bone `#FAF6EC` | `#232019` |
| hairline | `#D9CFB8` | `#2A2520` |
| secondary | Forest `#2F4A3A` (the "done/shipped" green) · Sky `#6B8FA8` (info) |
| display font | `'EB Garamond', Georgia, ui-serif, serif` |
| body font | `'Lora', Georgia, ui-serif, serif` |
| mono / data | `'IBM Plex Mono', ui-monospace, Consolas, monospace` |

Amber is used **sparingly** — primary buttons, active/selected state, key links,
the logo's lit branch. It is not a fill color for big areas. Forest green is only
for "done / shipped / landed". Never pure `#000` / `#fff`.

## Steps

1. Copy `bristlecone-brand.css` and the chosen logo PNG into the surface's
   served static dir (next to its other assets).
2. In every page `<head>`, before the page's own styles, add:
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
   <link rel="stylesheet" href="<relpath>/bristlecone-brand.css">
   <link rel="icon" type="image/png" href="<relpath>/darkBristleconeIcon.png">
   ```
3. **Retarget the surface's own tokens** to the brand. If it uses CSS variables,
   point them at brand values. If colors are hardcoded, override the dominant
   ones: page background → warm near-black (or parchment if the surface is
   light), body text → bone/charcoal, the existing primary/accent/link color →
   amber, fonts → the brand stacks above. Keep the surface's spacing/layout.
4. Put the mark in the header: `<img class="bc-mark" src="…/darkBristleconeIcon.png">`
   beside the existing title, or drop a `<header class="bc-brandbar bc-night">`
   if the surface has no header. Use the dark icon on dark surfaces.
5. Verify it loads (screenshot via the running server or playwright) — amber
   accent visible, serif type, mark present, nothing broken — then report the
   exact files you changed.

## Logos in this kit
- `darkBristleconeIcon.png` — tree mark only, for favicons + compact headers (dark surfaces)
- `Bristlecone_Dark.png` — full lockup (tree + wordmark + tagline) for dark hero headers
- `LightBristleconeIcon.png` / `Bristlecone_Light.png` — light-surface equivalents
- `Bristlecone_alt.png` — rings cross-section variant (parchment)
