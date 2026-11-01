<p align="right"><a href="README.md">한국어</a> · <b>English</b> · <a href="README.zh-CN.md">简体中文</a></p>

# Battle3D — 3D group battles for Legend of Mortal

A BepInEx mod that turns the group battles of **Legend of Mortal** into newly built 3D fights.
The original battle scene is only read for its data (units, stats, rules, UI, sounds); the 3D world is created from scratch.
Battles you don't pick stay as the original.

## Features
- Group battles in a quarter-view 3D: new maps (cliff plateau, town, indoor and more), per-school character models, toon shading with outlines
- The original's data is used as is: unit layout, HP / attack / stamina, hidden weapons (straight and lobbed throws), status effects (poison, paralysis), special battle rules
- Direct control: WASD move, left click 3-hit combo, right click throw, Space roll / dash, Q E R F skills. Three control schemes (mouse / click-to-move / keyboard)
- A **chain** system and the skill **Jeompa Un-gwan (점파운관)** (usable at chain 8+)
- Passives: 삽답유성검, 사상전, 서여림, 사초침 (shown at the upper right of the ready screen, faded out when the fight starts)
- Johwal's own skill slots are remembered for the next battles
- Ally and enemy skills, boss patterns, sound effects, visual effects
- **F4 settings panel**: sound, camera, controls, graphics (toon shading, outline), and entering a battle directly by its code

## Installation (if you already installed the mod base, skip steps 1 and 2)
1. Download **BepInEx 6** (Unity Mono, `6.0.0-be.692`) and extract it into the game folder (where `Mortal.exe` is).
   - From the [BepInEx builds page](https://builds.bepinex.dev/projects/bepinex_be) take `be.692`, *Unity Mono, Windows x64*.
2. Run the game once so the `BepInEx` folder is created, then close it.
3. Download `Battle3D_vX.Y.Z.zip` from [Releases](../../releases).
4. **Paste the `BepInEx` folder from the zip over the game folder** (merge / overwrite).
   Result: `...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. Start the game and enter a group battle: the 3D battle opens.

To remove it, delete the `BepInEx\plugins\Battle3D` folder. Settings are stored in `BepInEx\config\mortal.battle3d.cfg` (safe to delete).

## Controls (default: Mouse)
| Action | Key |
|---|---|
| Move | W A S D |
| Attack (3-hit combo) | Left click |
| Throw | Right click (hold for a lobbed throw) |
| Roll / dash | Space |
| Skills 1–4 | Q E R F |
| Auto-aim on / off | Left Ctrl |
| Settings panel | F4 |
| Hide the controls list | F11 |

The control scheme can be changed from the keyboard-settings button of the in-battle pause menu.

## Troubleshooting
Open `BepInEx\LogOutput.log` first. When the mod is running it writes lines starting with `[Battle 3D]`. Please attach this file when reporting a problem.

**The mod doesn't start (no `[Battle 3D]` lines in the log)**
- If `BepInEx\LogOutput.log` doesn't exist at all, BepInEx isn't running. Check that the game folder (next to `Mortal.exe`) has `winhttp.dll`, `doorstop_config.ini` and the `BepInEx` folder. (Redo install steps 1 and 2.)
- Check the file locations. All four must be inside `BepInEx\plugins\Battle3D\`: `Battle3D.dll`, `battle3d.bundle`, `battle3d_environment.bundle` and the `Audio` folder. There must not be an extra level (`Battle3D\Battle3D\...`).
- BepInEx must be **6.0.0-be.692 (Unity Mono)**. Version 5.x or an IL2CPP build won't work.
- Temporarily move every other mod out of `BepInEx\plugins` and run with this mod alone. If that works but it fails together with other mods, tell us which ones you used.
- Windows may block files when extracting. Tick *Unblock* in the zip's properties and extract again. Also check whether your antivirus quarantined `Battle3D.dll`.

**The mod starts but the battle doesn't turn 3D**
- In the `F4` settings panel, check that the 3D battle is on. Also check `[General] Enabled` and `ExcludedBattles` in `BepInEx\config\mortal.battle3d.cfg`.
- Battles that aren't built in 3D yet stay as the original.
- If the log shows an error (`Exception`) with `Battle 3D`, please send that line.

**An error like `file ... is corrupted! Position out of bounds` and the game closes**
- This happens when `battle3d.bundle` or `battle3d_environment.bundle` was not fully downloaded, or was overwritten while the game was running. Close the game completely, download the zip again and overwrite. (The two bundles are about 70 MB and 56 MB.)

**No sound / too loud**
- Adjust it in the sound section of the `F4` panel. Also check that the `Audio` folder is inside the `Battle3D` folder.

**Too dark or slow**
- Turn off toon shading / outline in the graphics section of the `F4` panel, or set `[Graphics] PostProcessing` to `false` in the config file.

**Reset the settings**
- Close the game and delete `BepInEx\config\mortal.battle3d.cfg`. It is recreated with the defaults at the next start.

**Errors after a game update**
- If a game update changes the original code, the mod may stop fitting. Check for a newer release, and if there isn't one, open an issue with your log.

## License / terms of use
Copyright © texp0323. All rights reserved.

This mod may be used freely for **personal, non-commercial purposes**. The following are prohibited without the copyright holder's prior written permission:
- Redistribution, including re-uploading the release files to other sites or repositories
- Modification and creation of derivative works, including those based on decompiled code

This is an unofficial fan-made mod and is not affiliated with the game's developer. No original game data is included as files; it is read at run time. The mod is provided "as is", without warranty of any kind, and the author accepts no responsibility for problems arising from its use.
