# Swofty Launcher for F1 25

## About this fork

Upstream baseline: [v1.8.22](https://github.com/Swofty-Developments/SwoftyLauncher/releases/tag/v1.8.22), including the v1.8.21 and v1.8.22 updates, integrated on 7 November 2026.

Modified on 7 November 2026 in accordance with GNU AGPLv3 Section 3 & Section 5(a):
Removed artificial entitlement checks.

The modification deletes `packages/core/src/entitlement.rs`, removes its launch
and apply checks, and removes its module export and error variant. The changed
Rust files carry the same dated notice. This fork remains licensed under
GNU AGPLv3 or later; the original copyright and licence notices are preserved.

This fork removes the launcher's entitlement gate: unknown-store refusal,
emulator/crack filename detection, and the dedicated ownership-file hash check.
The game and store clients keep their own licence checks. Addon installation,
backup and restoration integrity checks remain. See [launch behaviour](docs/reference/launch.md#copies-swofty-plays)
for details.

The upstream content-ownership API for addons and shared-session content compatibility checks are retained.

Build this fork from source using the development commands below. The upstream
installation guide and upstream releases distribute the original launcher.

A launcher and mod loader for F1 25 on Windows and Linux. Addons change the game's data and engine, mods and community tracks drop onto the Mods page, and profiles keep separate setups.

![The launcher's Addons page with SwoftyMod, Team Simplified, Custom Grid Size and an AlphaTauri livery addon](docs/public/screenshots/hero-launcher.png)

## Features

- **Addons:** Anything with a `swofty.json`, installed on the Addons page. Data addons change the game database, text, `.erp` archives, menus and files through operations, applied at build time or while the game boots through the Asset API. Code addons use the Advanced Mod Mixin System to edit the F1 25 engine directly, from new menus and settings to bigger grids, or add pages to the launcher.
- **Mods:** Content with no code, as the Simplified Suite loads it: `.serps` packages, `.erp` archives and other game files in a zip, 7z, RAR or folder, and community tracks such as Sepang and Okayama. Drop them on the launcher's Mods page, which comes from Team Simplified's Simplified for Swofty addon.
- **DB Editor:** Change drivers, teams, line-ups, tracks, the calendar, weather, points and any other value in the game database from the launcher. Changes are saved as packages: data addons you turn on per profile, stack and share as zips. EGO GameDatabases Editor exports of value changes import as packages.
- **Profiles:** Keep separate setups like *Vanilla*, *26 car grid* or *Classic tracks*. The game folder goes back to vanilla when a session ends.
- **In-game addon settings:** Change addon settings from the game's main menu, in **ADDON SETTINGS** under Career.
- **Swofty UI:** View and edit the game's menu layouts (`.idf` scenes) with real textures, then ship the edits in an addon. It comes with every release as `bin/swofty-ui`. See [Swofty UI](https://f1.swofty.net/reference/ui/swofty-ui).

## Install

Follow the [installation guide](https://f1.swofty.net/guide/installation).

## Supported platforms

- Windows 10 and 11 with Steam.
- Linux with Steam and Proton, including Steam Deck, NixOS and Flatpak Steam.
- F1 25 on Steam, including the F1 2026 season content.

## Contributing

```bash
nix develop                     # development tools on NixOS
cargo fmt --all --check
cargo clippy --all-targets -- -D warnings
cargo test                      # set F1_25_DIR to test with your game files
cargo run -p swofty-launcher
native/build.sh
native/test/run_wine_test.sh
pnpm install
pnpm docs:dev
```

See the [development guide](https://f1.swofty.net/reference/development) for build details.

## Licence

[GNU Affero General Public License, version 3 or later](LICENSE). The plugin SDK in `packages/sdk` and the addon template in `templates/addon` use the MIT licence. The docs theme adapts MIT-licensed CSS from the Geode docs, Swofty UI's texture decoder is ported from MIT-licensed bcdec_rs and bcdec; see [THIRD_PARTY.md](THIRD_PARTY.md).

## Credits

- [xanpavle](https://github.com/xanpavle) for [F1 25 RE-Optimization](https://github.com/xanpavle/F1-25-RE-Optimization), the renderer tuning, engine overrides and GPU-aware upscaler choice behind the `xanpavle.re-optimization` addon in the Addon Browser.

## Contributors to this fork

- [Stizzzly](https://github.com/Stizzzly) — fork owner and direction of the changes.
- [Codex](https://github.com/codex), OpenAI's coding agent — AI-assisted code changes, regression tests, documentation and modification notices, under Stizzzly's direction.
