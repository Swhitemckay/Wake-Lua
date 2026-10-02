# Wake Lua 0.1.1 — Release Notes

Visual monitor drawing, live sensor previews and Lua export for Stormworks.

## Included

- Crisp pixel shapes, eraser, symmetry, layer editing and monitor rotation.
- Readouts with size controls, input gauges and clipped HUD tapes.
- Invisible touch zones mapped to Boolean outputs, pressable buttons and screen navigation.
- Multiple screens, project snapshots, JSON backups and Lua import.
- Live Lua character budget, direct minify, readable formatting and separate page exports.
- One editable 3×3 Flight Systems Showcase with geometric drawing, live sensor values and touch controls.
- Image-to-paint preview and Stormworks vehicle XML export.

## Release verification

The Mac app is now packaged as one universal DMG with a verified ad hoc signature. The Windows installer is installed and launched on a Windows runner before each release is published.

The build and 49 automated regression checks passed. Checks exercise actual Lua execution, the blank starter and curated showcase, all 32 number channels with negative/fractional/zero/large values, touch press/release, overlap rules, navigation, geometry, rotation, project round trips, HUD tapes, character limits and separate page exports.

The browser review covered the blank first-run project, the 3×3 Flight Systems Showcase and its drawing, sensor and touch features, plus the Code and Art views. Automated tests do not certify every browser interaction or every possible numeric combination.

## Known limitations

- This release has not been certified inside Stormworks. Verify exported scripts and separate-page wiring in game.
- Fonts, bezels, maps and color correction are browser approximations. Game world, HTTP and network services are not simulated.
- Each Lua component is limited to 8,192 characters. Unminified source may exceed the limit and shows a warning. Custom scripts cannot be split automatically.
- Saved projects belong to the browser origin. Moving from the hosted site to localhost does not move browser storage; download and import a project backup.
- Whole-number live controls are selected by names such as count, ammo, quantity, rounds and missiles. Other sensor values support decimals.
- Proprietary software: copyright © 2026 Swhitemckay, all rights reserved. See LICENSE. Third-party notices are included in dist/assets/.

## Report a bug

Include browser/version, monitor size, reproduction steps, expected and actual behavior, and a project JSON backup with any private information removed. For exported Lua issues, include the script and whether it failed in the browser or in Stormworks.

## Install

For the prebuilt ZIP, extract it and run `node scripts/preview.mjs` with Node.js 22 or newer. Open http://127.0.0.1:4173. Keep the server running while editing.

For the source ZIP, install pnpm 10.11.0, run `pnpm install --frozen-lockfile`, then `pnpm run check` and `pnpm run preview`.
