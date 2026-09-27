# Wake Lua Monitor Studio

Draw Stormworks monitor screens, connect touch controls and sensor inputs, and export compact Lua.

## Download the app

### Windows

Open the [Windows build page](https://github.com/Swhitemckay/Wake-Lua/actions/workflows/desktop.yml). Choose the newest successful **Desktop beta installers** run. Download the Windows item from **Artifacts**.

### Mac

Open the [Mac build page](https://github.com/Swhitemckay/Wake-Lua/actions/workflows/desktop.yml). Choose the newest successful **Desktop beta installers** run. Download the Mac item from **Artifacts**. The workflow creates builds for Apple Silicon and Intel.

If there is no completed run, choose **Run workflow** on the build page and wait for it to finish. These beta installers are unsigned and the workflow downloads may expire. Read [desktop details](desktop/README.md) before installing.

## What it does

1. Draw pixel art, shapes, readouts, gauges and HUD tapes on a monitor canvas.
2. Add touch zones and map them to momentary Boolean outputs.
3. Simulate sensor inputs, button presses and generated or custom Lua.
4. Build multiple screens with touch or signal based navigation.
5. Export optimized Lua, separate page renderers, project backups and share links.

Projects are stored locally in the browser or desktop app. Read [beta notes](BETA.md) for tested behavior and limitations.

## Get started

### Browser preview

Requires Node.js 22 or newer and pnpm 10.11.0.

```sh
pnpm install
pnpm run preview
```

Open http://127.0.0.1:4173. Run `pnpm run check` to build the project and run its regression suite.

### Desktop app

Install the downloaded `.exe` on Windows or open the `.dmg` on Mac. Projects are saved in the app local storage. Use **Projects → Import** to bring in a browser project backup. Export opens a native Save dialog. See [desktop instructions](desktop/README.md) for local builds and platform notes.

## Using the editor

1. **Draw:** hold Shift for square rectangles and 45 degree lines. Escape cancels a gesture. Shift with arrow keys nudges 10 pixels. Command or Control with D duplicates. Center horizontally or vertically to align selected elements.
2. **Edit elements:** select layers to move, resize, hide, lock or reorder them. Box sizes count occupied pixels for filled and outlined rectangles.
3. **Touch zones:** press Z, draw a zone, then select **Boolean OUT 1 to 32** in the inspector. Zones appear in the editor but are invisible in exported Lua. The topmost overlapping control receives touch.
4. **Test inputs:** adjust named sensor channels and Boolean values beside the monitor preview. Touch uses number inputs 3 and 4 for X and Y, and Boolean input 1 for pressed.
5. **Create screens:** use **+ Screen**, then click the screen name for settings, starter layouts and navigation rules. Navigation triggers on a new button, zone or Boolean input press.
6. **Export Lua:** choose **One script** for a compact program, or **Separate page scripts** for a navigation controller and one renderer per page. Each component has a 4,096 character game limit. The editor flags oversized components.

## Releases and builds

The desktop builds are provided in the workflow runs linked above. To create a local installer, use `pnpm desktop:mac` on macOS or `pnpm desktop:windows` on Windows. Browser source and prebuilt ZIP files are in the repository. To create fresh archives and checksums, run `pnpm run package:beta` after `pnpm run check`. See [BETA.md](BETA.md) for package details.

## Project and license

Copyright © 2026 Swhitemckay. All rights reserved. The beta is proprietary and available for evaluation under [LICENSE](LICENSE). Third party notices are included with the app.

Community feedback informed priorities around visual drawing, touch behavior and compact Lua exports. See requests about [drawing without scripting each stroke](https://www.reddit.com/r/Stormworks/comments/tq32ml), [repeated touch actions](https://www.reddit.com/r/Stormworks/comments/16gwexl) and [Lua limits and touch state](https://www.reddit.com/r/Stormworks/comments/1694riu).
