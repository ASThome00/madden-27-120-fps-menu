# Madden 27 — 120 FPS Menus

Runs the front end of EA Sports Madden NFL 27 on PC at **120 FPS** instead of 60.

Madden 27's menus — main menu, Franchise hub, Superstar hub, settings screens — are
pinned to **60 FPS** regardless of the game's Frame Rate Cap settings. The front-end
render settings asset is explicitly flagged to ignore the user frame-rate setting, so
no in-game option can raise it. This mod raises the front-end render target to 120 FPS
at every graphics quality level. Gameplay and cutscenes are untouched — those already
follow the in-game Frame Rate Cap settings.

## What it changes (exactly)

One value in one asset — nothing else:

- `ContentShared/global/RenderSettings/FrontEndRenderSettings` → `RenderFPS`:
  all six quality tiers (`VeryLow` … `SuperUltra`) raised **60 → 120**.

The asset keeps its `IgnoreRenderFpsUserSettings = true` flag, so menus are pinned at
120 regardless of the in-game frame-rate cap. No gameplay, cutscene, or online changes,
and no game logic is touched.

Note for modders: Madden 27 also ships a `global/RenderSettings/FrontEnd3DRenderSettings`
asset (the one College Football 27 uses). In Madden it is unreferenced — editing it does
nothing. The live front-end asset is the `ContentShared` one above.

## Install

1. Download `Madden120FPSMenus.fbmod` from the [latest release](../../releases/latest).
2. Open **MMC Mod Manager** (Madden 27 profile), import the `.fbmod`, enable it.
3. Launch the game through the Mod Manager. If you had an older build of any menu
   FPS mod applied, use **Delete ModData and Launch** once so the new data is applied
   cleanly.

Requires [MMC Editor / Mod Manager](https://discord.gg/maddenmoddingcommunity) for
Madden NFL 27. Like all MMC mods, playing modded means playing offline.

## After a title update

Title updates reset/patch game data, and the mod may need a rebuild against the new
data. The MMC project file (`Madden120FPSMenus.fbproject`) is included — open it in
MMC Editor after an update, verify the RenderFPS values on
`ContentShared/global/RenderSettings/FrontEndRenderSettings`, and re-export.

## Related

- [CFB 27 — 60 FPS Menus](https://github.com/ASThome00/cfb-27-60-fps-menu) — the
  College Football 27 version of this mod.

## License

MIT — see [LICENSE](LICENSE).
