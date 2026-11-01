<p align="right"><a href="README.md">한국어</a> · <b>English</b> · <a href="README.zh-CN.md">简体中文</a></p>

# Battle3D — 3D group battles for Legend of Mortal

A BepInEx mod that turns the group battles of **Legend of Mortal** into newly built 3D fights.
The original battle scene is only read for its data (units, stats, rules, UI, sounds); the 3D world is created from scratch.
Battles you don't pick stay as the original.

## About
A mod that turns the group battles of Legend of Mortal into newly built 3D fights. You control Johwal directly, while units, numbers and rules follow the original data.

## Installation (if you already installed the mod base, skip steps 1 and 2)

**Latest release: [v0.1.6](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)** · **[Download Battle3D_v0.1.6.zip](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/download/v0.1.6/Battle3D_v0.1.6.zip)** (about 120 MB)

1. Download **BepInEx 6** (Unity Mono, `6.0.0-be.692`) and extract it into the game folder (where `Mortal.exe` is).
   - From the [BepInEx builds page](https://builds.bepinex.dev/projects/bepinex_be) take `be.692`, *Unity Mono, Windows x64*.
2. Run the game once so the `BepInEx` folder is created, then close it.
3. Use **Download Battle3D_v0.1.6.zip** above to get the installation package. On the [latest release page](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest), choose **Assets → `Battle3D_v0.1.6.zip`**. `Source code (zip)` and `Source code (tar.gz)` are not installation packages.
4. Extract the downloaded ZIP, then **paste its `BepInEx` folder over the game folder** (merge / overwrite).
   Result: `...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. Start the game and enter a group battle: the 3D battle opens.

To remove it, delete the `BepInEx\plugins\Battle3D` folder. Settings are stored in `BepInEx\config\mortal.battle3d.cfg` (safe to delete).

## Controls

There are three control schemes; the default is Mouse. Change it from the keyboard-settings button of the in-battle pause menu.

<details>
<summary><b>Mouse (default)</b></summary>

| Action | Key |
|---|---|
| Move | W A S D |
| Attack (3-hit combo) | Left click |
| Throw | Right click (hold for a lobbed throw) |
| Roll / dash | Space |
| Skills 1–4 | Q E R F |

</details>

<details>
<summary><b>ClickMove</b></summary>

| Action | Key |
|---|---|
| Move | Right click (hold to keep following); S stops in place |
| Attack (3-hit combo) | Left click |
| Throw | F (hold for a lobbed throw) |
| Roll / dash | Space |
| Skills 1–4 | Q W E R |

</details>

<details>
<summary><b>Keyboard</b></summary>

| Action | Key |
|---|---|
| Move | Arrow keys |
| Attack (3-hit combo) | Z |
| Throw | X (hold for a lobbed throw) |
| Roll / dash | Space |
| Skills 1–4 | A S D C |

</details>

**Common**

- Auto-aim on / off: Left Ctrl
- Settings panel: F4
- Hide the controls list: F11

**Lightness (Qinggong): roll, dash and movement speed**

- Press Space to **roll with Lightness below 25** or **dash with Lightness at 25 or above**. Both require stamina.
- The base movement speed multiplier from Lightness is **`1 + max(0, Lightness) × 0.0005`**. Each point adds 0.05%: Lightness 25 gives **1.0125×**, 50 gives **1.025×**, and 100 gives **1.05×**.
- Maximum dash distance is **`3 + (Lightness - 25) × 0.06` m**: **3 m** at 25, **4.5 m** at 50, and **7.5 m** at 100. Aiming at a nearby cursor shortens the dash, with a minimum distance of 1 m.
- A roll has a base distance of **4.6 m** and a full duration of **0.95 seconds**, regardless of Lightness. The movement speed multiplier above applies to normal movement.

<details>
<summary><b>Johwal's skills</b></summary>

- **분력난격**: A flurry of slashes stronger than the basic attack; it builds the chain like the basic attack does.
- **호체기조**: Raises a barrier for 5 seconds that ignores all damage and status effects.
- **방어 (Block)**: Pushes back the enemies in front; you take no damage during the move.
- **점파운관**: At chain 8 or more, spends the whole chain and thrusts forward. Damage is the finisher's damage × 0.5 × chain.
- **운소뇌정벽력도**: Cuts with the basic attack's first swing while lightning falls on a fan ahead, dealing damage and paralysis and breaking balance.
- **풍뢰신각**: At chain 4 or more, spends the whole chain and charges forward in a flying kick. Damage is the finisher's damage × 0.45 × chain.
- **비천각**: Jumps, then slams down.

Since no place to obtain 풍뢰신각 and 비천각 in the story has been found, they count as learned in battles entered from the F4 panel.

</details>

<details>
<summary><b>Passives</b></summary>

Shown at the upper right of the ready screen and gone once the fight starts.

- **삽답유성검**: With the chain at 0, the next basic attack deals triple damage.
- **사상전**: The fight starts with a chain already built; higher levels start higher.
- **서여림**: Stamina recovers more each time it regenerates, scaling with the 전술 (tactics) level.
- **사초침**: A thrown hidden weapon that hits has a 30% chance to throw the target off balance.
- **동여뢰진**: Targets hit by 운소뇌정벽력도 fall down.

</details>

<details>
<summary><b>Ally skills</b></summary>

Techniques of the companions you call by equipping their skill on the ready screen.

- **대사형**: Drops from the sky, spins while throwing daggers, drops bombs and leaves.
- **이사형**: Throws poison vials that leave poison behind.
- **사사형**: Gathers the coins on the field, throws them and drops healing potions.
- **소사매**: Clones dash into enemies and slash with daggers; she finishes by cutting through.
- **엽운주**: Six horizontal dash slashes with a long sword.
- **용상**: Drops in and dashes twice at random enemies, slashing.
- **상관형**: Throws coin darts and cuts with a sword.
- **옥죽**: Throws weapons or summons carts to sweep enemies away.

</details>

<details>
<summary><b>Bosses and special enemies</b></summary>

- **석공원**: Charges at the very start, then walks in to swing or throws stones and knives.
- **단하자**: A four-hit slashing combo with two weapons, hitting all around.
- **우소매**: Mixes combos with jump attacks and dash slashes, and keeps pace with Johwal.
- All bosses have super armor, so attacks hardly push them back.

</details>

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
| `[Sound] BasicSwingVolume` | `0.7` | Extra volume factor (0–1) for the swing sound of Johwal's basic attacks |

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
