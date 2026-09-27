# Wake Lua 0.1.0-beta.1

Visual monitor drawing, live sensor previews and Lua export for Stormworks.

## Included

- Crisp pixel shapes, eraser, symmetry, layer editing and monitor rotation.
- Readouts with size controls, input gauges and clipped HUD tapes.
- Invisible touch zones mapped to Boolean outputs, pressable buttons and screen navigation.
- Multiple screens, project snapshots, JSON backups and Lua import.
- Live Lua character budget, direct minify, readable formatting and separate page exports.
- Weapons / hardpoint selector preset.

## Final verification

The build and 43 automated regression checks passed. Checks exercise actual Lua execution, presets, all 32 number channels with negative/fractional/zero/large values, touch press/release, overlap rules, navigation, geometry, rotation, project round trips, HUD tapes, character limits and separate page exports.

The earlier interface review checked editor expansion, direct minification and rename dialog spacing. Automated tests do not certify every browser interaction or every possible numeric combination.

## Known limitations

- This beta has not been certified inside Stormworks. Verify exported scripts and separate-page wiring in game.
- Fonts, bezels, maps and color correction are browser approximations. Game world, HTTP and network services are not simulated.
- Each Lua component remains limited to 4,096 characters. Unminified source may exceed the limit and shows a warning. Custom scripts cannot be split automatically.
- Saved projects belong to the browser origin. Moving from the hosted site to localhost does not move browser storage; download and import a project backup.
- Whole-number live controls are selected by names such as count, ammo, quantity, rounds and missiles. Other sensor values support decimals.
- Proprietary beta: copyright © 2026 Swhitemckay, all rights reserved. See LICENSE. Third-party notices are included in dist/assets/.

## Report a beta bug

Include browser/version, monitor size, reproduction steps, expected and actual behavior, and a project JSON backup with any private information removed. For exported Lua issues, include the script and whether it failed in the browser or in Stormworks.

## Install

For the prebuilt ZIP, extract it and run `node scripts/preview.mjs` with Node.js 22 or newer. Open http://127.0.0.1:4173. Keep the server running while editing.

For the source ZIP, install pnpm 10.11.0, run `pnpm install --frozen-lockfile`, then `pnpm run check` and `pnpm run preview`.
