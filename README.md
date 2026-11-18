# YUNG's Better Ocean Monuments — a Horizon port

**YUNG's Better Ocean Monuments** is a Minecraft mod. Redesigns & enhances vanilla's ocean monuments. This repository is a **port of it to [Horizon](https://github.com/horizon-rust/horizon)**, the Rust engine for Minecraft Java 26.3. It carries the complete source of the port plus the content files it ships, and installs as a single `.hmod` package.

Upstream: [YUNG-GANG/YUNGs-Better-Ocean-Monuments](https://github.com/YUNG-GANG/YUNGs-Better-Ocean-Monuments) — licence **LGPL-3.0-only**.

| | |
|---|---|
| Upstream mod | YUNG's Better Ocean Monuments ([source](https://github.com/YUNG-GANG/YUNGs-Better-Ocean-Monuments)) |
| Ported to | Horizon 0b14f8a, Minecraft Java 26.3, mod API `0.2` |
| Package | `betteroceanmonuments.hmod` (install it with the Horizon launcher) |
| Licence | **LGPL-3.0-only** — the upstream mod's licence; see [Licence and credit](#licence-and-credit) |

## What this port implements

The port's behaviour is recorded in the repository's `notes.md` (the campaign's per-mod record); this slice ships what that file describes.

## Not yet ported

- **Vanilla ocean monuments are not disabled.** The mod's
- **`PersistentTridentMixin`** (tridents in monument water persist) and
- **The mod's config (`disableVanillaMonuments`) is not carried.** Content mods
- **`data/yungsapi/tags/worldgen/structure/remove_magma_feature_in.json` is not
- **`yungsapi` (required dependency) is not ported.** It is a library
- **Structure spawn overrides** (guardians, `bounding_box: piece`) are carried in

## Installing

1. Install the [Horizon launcher](https://github.com/horizon-rust/horizon/releases) (0.2.70 or newer).
2. Add `betteroceanmonuments.hmod` to the instance's mods.
3. The package is pinned to a specific Horizon build; the launcher checks that pin.

## Licence and credit

YUNG's Better Ocean Monuments was created by its upstream authors; the code, models and assets in the original mod
remain theirs and are used here under **LGPL-3.0-only**. The Rust in this repository is a clean-room
rewrite for Horizon, not a translation of the original source.

- `LICENSE` — the upstream licence text.
- `LICENSE-NOTICE.md` — what this port carries and where it came from.
- The upstream project: https://github.com/YUNG-GANG/YUNGs-Better-Ocean-Monuments

## Technical details

```
horizon-mod.toml   package manifest (id, version, api, [native] pin)
Cargo.toml         the crate; depends on `horizon-mod-api` from the fetched SDK
src/               lib.rs (the one `impl Hooks`), runtime.rs (pure logic + tests), glue
assets/ data/      the content the package ships
tools/             content generators and the e2e scenario
```

- Build: `cargo horizon-mod build` (packages; it does not compile against the game).
- Test: `cargo test`, `cargo clippy --all-targets -- -D warnings`.
- In-game: `ports/tools/launcher-game.sh run betteroceanmonuments` in the campaign tree, or install the
  `.hmod` and play; the harness scenario is `tools/e2e.sh`.

This repository is generated from the campaign's port at `ports/betteroceanmonuments/`; the port's own
`notes.md` is the full record (decisions, traps, evidence).
