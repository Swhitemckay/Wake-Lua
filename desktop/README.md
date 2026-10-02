# Wake Lua desktop app

**Find installers on the [repository front page](../README.md#download-wake-lua) or in the [latest GitHub release](../../releases/latest).** Choose the Windows `.exe` or the Mac `.dmg` for Apple Silicon or Intel.

The app includes the workbench and Lua simulator locally. No website login or internet connection is needed. Projects are saved in the app's own local storage; use Projects → Import to bring in a browser project backup. Export opens a native Save dialog.

## Build and run

Install Node 22+ and pnpm, then run `pnpm install`.

- `pnpm desktop`: open the desktop app.
- `pnpm desktop:mac`: build DMG installers for Apple Silicon and Intel Macs (run on macOS).
- `pnpm desktop:windows`: build the Windows x64 installer (run on Windows).

Installers appear in `release/desktop`.

Adding a source ZIP to the main branch starts the **Desktop installers** workflow. It builds Windows and Mac installers, then publishes them with the source and prebuilt browser ZIP files in a versioned GitHub release. To rebuild manually, run Actions → Desktop installers → Run workflow.

The installers are unsigned. Signing and macOS notarization require the owner's developer certificates and accounts. Operating systems may display an unidentified publisher warning. Follow the access terms in [LICENSE](../LICENSE) when sharing installers.

The renderer has no Node access. The app serves only bundled assets using a secure local protocol and blocks external navigation. Existing project JSON and Lua import/export remain available.
