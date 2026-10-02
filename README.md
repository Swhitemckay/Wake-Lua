# Wake Lua — Monitor Studio

Draw Stormworks monitor screens, connect touch controls and sensor inputs, and export compact Lua.

[![GitHub release downloads](https://img.shields.io/github/downloads/Swhitemckay/Wake-Lua/total?label=downloads)](https://github.com/Swhitemckay/Wake-Lua/releases)

## Download Wake Lua

### Windows

**[Download the latest Windows installer](../../releases/latest)** (`.exe`)

### macOS

**[Download the latest Mac installer](../../releases/latest)** (`.dmg`; one universal build for Apple Silicon and Intel)

Open the latest release and choose the installer for your computer from **Assets**. The installers are unsigned. On Mac, the first launch may require approval in **System Settings → Privacy & Security**. See [desktop details](desktop/README.md) before installing.

## What it does

- Draw pixel art, shapes, readouts, gauges and HUD tapes on a monitor canvas.
- Add touch zones and map them to momentary Boolean outputs.
- Simulate sensor inputs, button presses and generated or custom Lua.
- Build multi-screen projects with touch or signal based navigation.
- Convert images into paintable blocks and export Stormworks vehicle XML.
- Export optimized Lua, separate page renderers, project backups and share links.

Projects are stored locally in the browser or desktop app. See the [release notes](BETA.md) for tested behavior and limitations.

## Get started

### Browser preview

Requires Node.js 22 or newer and pnpm 10.11.0.

```sh
pnpm install --frozen-lockfile
pnpm run preview
```

Open http://127.0.0.1:4173. To check the project and run its regression suite, use `pnpm run check`.

### Desktop app

Install a downloaded `.exe` on Windows or open the `.dmg` on Mac. Projects are saved in that app’s local storage; use **Projects → Import** to bring in a browser project backup. Export opens a native Save dialog. Read [desktop instructions](desktop/README.md) for local builds and platform notes.

## Using the editor

- **Draw:** hold Shift for square rectangles and 45° lines. Escape cancels a gesture; Shift + arrows nudges 10 pixels; ⌘/Ctrl D duplicates. Center ↔ / ↕ aligns selected elements.
- **Edit elements:** select layers to move, resize, hide, lock or reorder them. Box sizes count occupied pixels for both filled and outlined rectangles.
- **Touch zones:** press Z, draw a zone, then select **Boolean OUT 1–32** in the inspector. Zones appear in the editor but do not draw in exported Lua. The topmost overlapping control receives touch.
- **Test inputs:** adjust named sensor channels and Boolean values beside the monitor preview. Touch uses number inputs 3/4 for X/Y and Boolean input 1 for pressed.
- **Create screens:** use **+ Screen**, then click the screen name for settings and navigation rules. Navigation triggers on a new button, zone or Boolean input press.
- **Export Lua:** choose **One script** for a compact program, or **Separate page scripts** for a navigation controller and one renderer per page. Each component has its own 8,192-character game limit; the editor flags oversized components.

For a hands-on tour, load the single **3×3 Flight Systems Showcase**. It combines pixel geometry, live sensor readouts and touch controls in one editable project.

## Releases and builds

Stable download links are at the top of this page. The latest GitHub release has one Windows installer and one Mac installer. To build installers locally, use `pnpm desktop:mac` on macOS or `pnpm desktop:windows` on Windows. See [desktop instructions](desktop/README.md).

To create browser archives and checksums, run `pnpm run package:beta` after `pnpm run check`. The resulting source and prebuilt ZIP files are in `release/`. See [BETA.md](BETA.md) for package contents and limitations.

## Project and license

Copyright © 2026 Swhitemckay. All rights reserved. The software is proprietary and governed by [LICENSE](LICENSE). Third-party notices are included with the app.

## Acknowledgments

Thanks to [Tajin’s Stormworks Toolbox](https://rising.at/Stormworks/paint.php) for the image-to-XML idea, and to [Pony IDE](https://lua.flaffipony.rocks) for its original inspiration.

Community feedback has informed priorities around visual drawing, touch behavior and compact Lua exports. See requests about [drawing without scripting each stroke](https://www.reddit.com/r/Stormworks/comments/tq32ml), [repeated touch actions](https://www.reddit.com/r/Stormworks/comments/16gwexl) and [Lua limits and touch state](https://www.reddit.com/r/Stormworks/comments/1694riu).
