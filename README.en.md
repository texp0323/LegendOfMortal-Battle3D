<p align="right"><a href="README.md">한국어</a> · <b>English</b> · <a href="README.zh-CN.md">简体中文</a></p>

# Battle3D — 3D group battles for Legend of Mortal

A BepInEx mod that turns the group battles of **Legend of Mortal** into newly built 3D fights.
The original battle scene is only read for its data (units, stats, rules, UI, sounds); the 3D world is created from scratch.
Battles you don't pick stay as the original.

## About
The brawls of the jianghu unfold in a quarter-view 3D. Newly crafted battlefields, warriors in the garb of their own schools, toon shading and ink-bold outlines come together, while the numbers and rules — headcount, vitality and stamina, hidden weapons, status effects — follow the original's decree as is.

Become the hero Johwal and wield the blade yourself. Step through the footwork, unleash the three-hit combo, hurl hidden weapons and roll clear of danger — and build up your chain to burst out with the strike **Jeompa Un-gwan (점파운관)**. The passives 삽답유성검, 사상전, 서여림 and 사초침 lend their strength, and the skills you equip carry over to the next battle.

The `F4` panel tunes sound, view, controls and graphics to your liking, and lets you leap straight into any fight by its battle code.

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

<details>
<summary><b>Configuration file</b></summary>

`BepInEx\config\mortal.battle3d.cfg` — created after the first run. Edit it with a text editor while the game is closed.

| Key | Default | Description |
|---|---|---|
| `[General] Enabled` | `true` | Use the 3D battle at all (off: every battle is the original). Also toggled in the F4 panel. |
| `[General] ExcludedBattles` | `""` | Battle codes (without `BL_`, comma separated) that stay the original 2D battle; every other battle is 3D. Example: `1000,0001` |
| `[Controls] Scheme` | `Mouse` | Control scheme: `Mouse` / `ClickMove` / `Keyboard` |
| `[Controls] AutoAim` | `true` | Auto-aim onto enemies (also toggled with Left Ctrl in battle) |
| `[Skills] Slot1Key ~ Slot4Key` | `q, e, r, f` | Keys of skill slots 1–4 (Input System key names) |
| `[Skills] RememberLoadout` | `true` | Keep Johwal's skill slots for the next battles |
| `[Camera] Pitch` | `35` | Camera pitch (degrees) |
| `[Camera] Yaw` | `45` | Camera yaw (degrees) |
| `[Camera] Distance` | `23` | Default camera distance (mouse wheel zooms) |
| `[Graphics] PostProcessing` | `true` | Bloom, colour grading and vignette |
| `[Graphics] Intro` | `true` | The camera diving through the clouds when a battle starts |
| `[Graphics] ToonShader` | `true` | Toon shading (off: plain URP shading) |
| `[Graphics] Outline` | `true` | Outline of characters and weapons |
| `[Sound] CustomVolume` | `1` | Volume (0–1) of the mod's own sound effects (Audio folder) |
| `[Sound] BasicSwingVolume` | `0.7` | Extra volume factor (0–1) for the swing sound of Johwal's and Usome's basic attacks |

</details>

## Troubleshooting
Open `BepInEx\LogOutput.log` first. When the mod is running it writes lines starting with `[Battle 3D]`. Please attach this file when reporting a problem.

<details>
<summary><b>The mod doesn't start (no <code>[Battle 3D]</code> lines in the log)</b></summary>

- If `BepInEx\LogOutput.log` doesn't exist at all, BepInEx isn't running. Check that the game folder (next to `Mortal.exe`) has `winhttp.dll`, `doorstop_config.ini` and the `BepInEx` folder. (Redo install steps 1 and 2.)
- Check the file locations. All four must be inside `BepInEx\plugins\Battle3D\`: `Battle3D.dll`, `battle3d.bundle`, `battle3d_environment.bundle` and the `Audio` folder. There must not be an extra level (`Battle3D\Battle3D\...`).
- BepInEx must be **6.0.0-be.692 (Unity Mono)**. Version 5.x or an IL2CPP build won't work.
- Temporarily move every other mod out of `BepInEx\plugins` and run with this mod alone. If that works but it fails together with other mods, tell us which ones you used.
- Windows may block files when extracting. Tick *Unblock* in the zip's properties and extract again. Also check whether your antivirus quarantined `Battle3D.dll`.

</details>

<details>
<summary><b>The mod starts but the battle doesn't turn 3D</b></summary>

- In the `F4` settings panel, check that the 3D battle is on. Also check `[General] Enabled` and `ExcludedBattles` in `BepInEx\config\mortal.battle3d.cfg`.
- Battles that aren't built in 3D yet stay as the original.
- If the log shows an error (`Exception`) with `Battle 3D`, please send that line.

</details>

<details>
<summary><b>An error like <code>file ... is corrupted! Position out of bounds</code> and the game closes</b></summary>

- This happens when `battle3d.bundle` or `battle3d_environment.bundle` was not fully downloaded, or was overwritten while the game was running. Close the game completely, download the zip again and overwrite. (The two bundles are about 70 MB and 56 MB.)

</details>

<details>
<summary><b>Reset the settings</b></summary>

- Close the game and delete `BepInEx\config\mortal.battle3d.cfg`. It is recreated with the defaults at the next start.

</details>

<details>
<summary><b>Errors after a game update</b></summary>

- If a game update changes the original code, the mod may stop fitting. Check for a newer release, and if there isn't one, open an issue with your log.

</details>

## License / terms of use
Free for anyone to use under the [MIT License](LICENSE).

- The license applies only to the code and content created by the author. Third-party assets included in the release files remain under their respective owners' terms, and the game Legend of Mortal and its data belong to its developer.
- This is an unofficial fan-made mod and is not affiliated with the game's developer. No original game data is included as files; it is read at run time.
- The mod is provided "as is", without warranty of any kind.
