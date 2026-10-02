# Wake Lua desktop app

**Find installers on the [repository front page](../README.md#download-wake-lua) or in the [latest GitHub release](../../releases/latest).** Choose the Windows `.exe` or the universal Mac `.dmg` for Apple Silicon and Intel.

The app includes the workbench and Lua simulator locally. No website login or internet connection is needed. Projects are saved in the app's own local storage; use Projects → Import to bring in a browser project backup. Export opens a native Save dialog.

## Build and run

Install Node 22+ and pnpm, then run `pnpm install`.

- `pnpm desktop`: open the desktop app.
- `pnpm desktop:mac`: build one universal DMG for Apple Silicon and Intel Macs (run on macOS).
- `pnpm desktop:windows`: build the Windows x64 installer (run on Windows).

Installers appear in `release/desktop`.

Adding a source ZIP to the main branch starts the **Desktop installers** workflow. It builds and checks both installers, then publishes only the Windows `.exe` and Mac `.dmg` in a versioned GitHub release. To rebuild manually, run Actions → Desktop installers → Run workflow.

The installers are unsigned. The Mac app has a valid ad hoc signature, but it is not notarized. On first launch, macOS may block it until you try opening it and choose **Open Anyway** in **System Settings → Privacy & Security**. Windows may display an unidentified publisher warning. Follow the access terms in [LICENSE](../LICENSE) when sharing installers.

The renderer has no Node access. The app serves only bundled assets using a secure local protocol and blocks external navigation. Existing project JSON and Lua import/export remain available.
