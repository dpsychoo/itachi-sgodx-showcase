# Validation record — 17 October 2026

This record documents checks performed for this presentation and its linked live experience. It is not a claim that a Playwright Test suite is included in this repository.

## Static project checker

From the local production project, `npm run check` completed successfully:

```text
PASS: JavaScript syntax, 122 frames, 127 local resources, DOM targets, links, path case, SGODX metadata and text format.
```

The checker is a native Node.js script; the project has no npm package dependencies or build step.

## Chromium browser smoke

The local project and deployed demo at <https://itachi-sgodx.vercel.app/> were exercised using Chromium and Playwright on desktop (1440 × 900) and mobile (390 × 844). The deployed demo responded HTTP 200.

| Check | Result |
| --- | --- |
| Preloader completion and first canvas frame | Passed on desktop and mobile |
| Local image requests | 123 JPG requests observed per profile (122 sequence frames plus storm background); no HTTP or request failures |
| Scene navigation | EYES, JUTSU, and END anchors reached |
| Gaze response | Readout changed on pointer movement in desktop profile |
| Jutsu reveal | Pointer interaction activated the reveal in desktop profile |
| Sound control | Toggle changed to ON and was returned to OFF |
| Responsive layout | No horizontal overflow at either viewport |
| Console and page errors | None observed |
| Reduced motion with WebGL disabled | Canvas frame and Jutsu reveal remained functional; no browser errors |

The no-WebGL check used a browser context that disabled WebGL and emulated `prefers-reduced-motion`. It verified the fallback interaction, not GPU performance. The browser captures are private review material and are not included because they contain character imagery with unresolved redistribution permissions.

## Limits

- This was a focused smoke check, not an exhaustive accessibility, load, or cross-browser audit.
- The case-study page itself has no application runtime dependencies; it was separately rendered locally and its own links and SVG assets were checked before release.
- Live deployment behavior can change after this dated check.
