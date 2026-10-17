# Uchiha Itachi — SGODX project overview

## Project context

An unofficial Japanese-English creative frontend experience focused on Uchiha Itachi. Its long-form page uses scroll progress, pointer/touch input, and realtime effects to reveal a sequence of visual acts. This document describes the observed experience and verified technologies; it does not publish the production implementation.

## Experience flow

1. **Preloader:** reports image-sequence loading progress before releasing the layout.
2. **Act I — scroll scrub:** the main canvas draws through a 71-frame sequence as visitors scroll in either direction; feather motion responds to scroll direction and velocity.
3. **Act II — gaze:** a 51-frame eye sequence and nine-position lookup make the gaze respond to pointer or touch movement.
4. **Act III — Jutsu:** pointer movement reveals a storm background through a radial mask; parallax and an optional WebGL smoke cursor add atmosphere.
5. **End:** a compact credits footer closes the experience.

The site also draws flame and feather layers on Canvas, lightning with SVG, and optional thunder through Web Audio synthesis.

## Technology inventory

| Concern | Verified technology |
| --- | --- |
| Document and layout | HTML5 and CSS |
| Interaction and scene timing | Vanilla JavaScript |
| Image sequence drawing | Canvas 2D |
| Cursor smoke | WebGL and GLSL |
| Feather and flame layers | Canvas 2D |
| Lightning | Inline SVG |
| Thunder | Web Audio API; no bundled samples |
| Local tools | Node.js native server and static checks; no npm runtime dependencies |
| External typefaces | Shippori Mincho, Zen Kaku Gothic New, Cinzel, Space Grotesk via Google Fonts |

## Architecture and local checks

The production page is static and self-contained at runtime: `index.html` loads `style.css` and `main.js`, with image sequences under `frames/`. `scripts/serve.mjs` provides a local HTTP server; `scripts/check.mjs` checks syntax, local paths and casing, frame counts, IDs, metadata, and UTF-8/LF formatting. There is no build step, backend, API, database, or application analytics according to the project documentation.

## Third-party and asset scope

The production project's notice attributes the Ghost Cursor fragment to React Bits at commit `1b252c1cf7dea759b4ce77f72ab64566b0f81d5a`. The checked upstream license at that commit is MIT + Commons Clause v1.0. This showcase contains no implementation code, fragment shader, frame sequence, background, icon, or application screenshot.

The production experience requests four typefaces remotely from Google Fonts and synthesizes sound in the browser. No font binary or sound sample is copied into this repository. Character-frame provenance and redistribution permission remain unverified; see [NOTICE.md](../NOTICE.md).

## Verification

The static checker and a browser smoke run were executed on 17 October 2026. Exact scope and limitations are in [VALIDATION.md](VALIDATION.md). These results describe a dated verification, not a guarantee about later versions of the live deployment.
