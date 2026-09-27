# Wake Lua — Monitor Studio

A local-first drawing and Lua workbench for Stormworks monitors.

## Use

- **Draw**: hold Shift for square rectangles and 45° lines; Escape cancels a gesture; Shift + arrows nudges 10 pixels; ⌘/Ctrl D duplicates. Center ↔ / ↕ aligns any selected element. All box sizes count occupied pixels, so filled and outlined rectangles keep the same size.
- **Elements**: pixel tools, shapes, sensor readouts and gauges. Select layers to edit, move, resize, hide, lock or reorder them.
- **Touch zone (Z)**: drag a rectangle over any part of the monitor. Choose **Boolean OUT 1–32** in the inspector. Its outline appears in the editor; exported Lua draws nothing for the zone. Outputs are momentary (ON while touched). The topmost overlapping control receives the touch.
- **Test touch**: press controls without moving them. **Run Lua** executes the generated or edited program. Touch uses number inputs 3/4 for X/Y and boolean input 1 for pressed.
- **HUD tape**: choose direction, tick spacing, size and an input. Wrap at 360 for heading; labels clip at its edges.
- **Live inputs**: adjust named sensor channels, see Boolean outputs, and view output states beside the monitor preview.
- **Screens**: use + Screen to add a monitor screen, and the arrows beside Pixel grid to switch screens. Click the screen name for settings, starter layouts and navigation rules. Bind navigation to a button, touch zone, or Boolean input; navigation triggers on a new press.
- **Projects**: save browser snapshots, download JSON backups, import projects or Lua, and copy share links. Browser storage is local to this device.

## Develop and verify

Requires Node.js 22 or newer and pnpm 10.11.0. Use the checked-in lockfile:

```sh
pnpm install --frozen-lockfile
pnpm run check
pnpm run preview
```

Open http://127.0.0.1:4173. The preview server binds only to your computer.

```sh
npm run build
npm test
```

Or run both with `npm run check`. Serve `dist/` using a local static server. Reload the preview after building.

The regression suite executes the actual bundled Fengari worker. It covers all presets, Lua generation, rendering order, touch zone invisibility, channel outputs, overlapping controls, navigation, live values, import validation and execution limits.

## Scope

Tests protect known behavior; they cannot guarantee that future browser or game changes will never introduce bugs. Keep project backups. The browser approximates Stormworks fonts, bezels, color and map rendering; confirm exported scripts in game before using them in a vehicle.

## Optimized and separate page exports

**Export Lua → One script** minifies the generated drawing or custom script together with its library. Generated code drops unused screen aliases, duplicate color calls, unnecessary page state and empty string concatenation; it merges compatible pixel rectangles and packs dense pixel runs when that produces shorter code. Repeated generation is cached until the drawing changes.

**Export Lua → Separate page scripts** creates a navigation controller and one renderer per drawing page. Each code block has its own character counter, Copy button and download. Download the ZIP for all scripts and a complete wiring guide. An unused number channel carries page selection; the export suggests one automatically. Preserve the original touch/sensor composite and merge only the controller’s page number into it for the renderer inputs. Read action outputs directly from the controller. Chain the renderer video connections in page order.

This increases the total available code across Lua components; each individual component still has the game’s 4,096-character limit. Oversized components are flagged and downloads are disabled until simplified. Custom hand-written scripts are not split automatically. New projects use a pure **#000000** background.

## Community-informed usability priorities

- Visual authoring and useful live previews respond to [requests for drawing without coding each stroke](https://www.reddit.com/r/Stormworks/comments/tq32ml).
- Predictable touch release and screen-specific controls respond to [reports of repeated touch actions](https://www.reddit.com/r/Stormworks/comments/16gwexl) and [touch areas remaining active on another screen](https://www.reddit.com/r/Stormworks/comments/rrlbtw).
- Named inputs, explicit outputs and compact exports address [confusion about touchscreen state and the Lua character limit](https://www.reddit.com/r/Stormworks/comments/1694riu).

The cleanup keeps settings relevant to each element, names sensor inputs next to their channels, and hides Minify for already optimized generated Lua. Legacy outlined rectangles migrate once to preserve their visible dimensions.

## GitHub beta release

Current release: **0.1.0-beta.1**. Run `pnpm run package:beta` after `pnpm run check` to create source and prebuilt ZIP files in `release/`, plus SHA-256 checksums. The source ZIP includes the editor, locked dependencies, tests and GitHub check workflow. The prebuilt ZIP needs only Node.js: run `node scripts/preview.mjs` after extracting it. Both archives omit device projects, hosting identifiers, dependency folders and Git history.

Read [BETA.md](BETA.md) for tested behavior and limitations. When creating a GitHub release, mark it as a prerelease and attach both ZIPs and `SHA256SUMS.txt`. Copyright © 2026 Swhitemckay. All rights reserved. See [LICENSE](LICENSE) for private beta evaluation permissions and restrictions. Third-party notices remain included.
