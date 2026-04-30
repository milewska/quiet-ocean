# The Quiet Ocean — responsive interactive brief

One self-contained HTML file. No build step. Lean enough for phones, scales up to desktop.

- `index.html` — the entire site (HTML, CSS, vanilla JS, all in one file).
- `_headers` — Cloudflare Pages cache & security headers.

## Deploy to Cloudflare Pages

From this directory:

```sh
npx wrangler pages deploy . --project-name quiet-ocean
```

First deploy will create a `quiet-ocean.pages.dev` subdomain. Subsequent deploys overwrite it.

## What's inside

Six scenes from the original interactive brief, rebuilt without React/Babel:

- **Intro** — headline + descend
- **Listen** — animated ocean canvas, dB dial, mode toggle, optional WebAudio synthesis (tap to enable; iOS-Safari friendly)
- **Impact** — 8-species threshold table, mirrored dB slider
- **Range** — SVG propagation map with 6 nodes, live km calculation
- **Compare** — acoustic vs. fiber spec table; collapses to per-row cards on mobile
- **Act** — 3 CTAs, all linking to safesmartocean.org

## Mobile considerations baked in

- Mobile-first responsive layout (single column under 900px / 760px / 520px breakpoints)
- Canvas pauses when off-screen and when the tab is hidden (battery)
- Honors `prefers-reduced-motion` (single static frame, no animation loop)
- Audio gated behind a tap (WebAudio policy on iOS)
- System fallbacks if Google Fonts blocked / slow
- 14 KB gzipped (vs. ~600 KB gzipped for the original bundle)
