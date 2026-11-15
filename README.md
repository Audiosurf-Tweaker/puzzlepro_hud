# PuzzlePRO HUD

A HUD replacer script for Audiosurf, shipped with
[Audiosurf Tweaker](https://github.com/Unchpokable/Audiosurf-Tweaker). It replaces the game's HUD
for puzzle players and shows, while you ride:

- real-time statistics for every colour, read from the game;
- the chain multiplier and the chain drop timer;
- a live skill rating, and the projected final score against your personal best;
- a minimap of the colours ahead and the song you are playing.

The script is written against Lua API 4 of the Tweaker plugin.

## Install

The Tweaker ships this script already: it is built into `TweakerPlugin/assets/scripts/` in the
Tweaker's repository and installed from the Scripts tab. To install or update it by hand, copy
`puzzlepro_hud.lua` **and** `puzzlepro_hud.lua.map` into
`Audiosurf\engine\TweakerStuff\Scripts\`. The map is what makes a runtime error point at the line of
`src/…` instead of the line of the built file.

A release on this repository carries exactly those two files.

## Build

The script is a [twllink](https://github.com/Unchpokable/Audiosurf-Tweaker/blob/HEAD/Docs/scripting/authoring.md)
project. From a checkout of the Tweaker:

```
dotnet run --project TweakerLuaLinker/TweakerLuaLinker.csproj -c Release -- --project <this repo> --out build
```

or, with `twllink` on `PATH`:

```
twllink --project . --out build
```

Both write `build/puzzlepro_hud.lua` and `build/puzzlepro_hud.lua.map`.

## What is in here

| | |
|---|---|
| `twproject.json` | The project manifest: id, version, API version, what is embedded. |
| `src/` | The modules; `src/main.lua` is the entry point. |
| `docs/DESIGN.md` | The research behind the HUD. It is embedded into the built script, so it ships with it. |
| `.twllink/`, `.luarc.json` | Editor definitions for the Lua language server; refreshed by every build. |
| `.tweaker/` | The author's agent setup: a copy of the Tweaker's manuals and the skills the project was developed with. |
| `AGENTS.md`, `CLAUDE.md` | Instructions for AI coding agents working in this project. |

## Licence

MIT, see [LICENSE](LICENSE).
