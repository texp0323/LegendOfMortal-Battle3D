<p align="right"><a href="README.md">Korean</a> · <b>English</b> · <a href="README.zh-CN.md">简体中文</a> · <a href="README.zh-TW.md">繁體中文</a></p>

# Battle3D — 3D group battles for Legend of Mortal

A BepInEx mod that turns the group battles of **Legend of Mortal** into newly built 3D fights.
The original battle scene is only read for its data (units, stats, rules, UI, sounds); the 3D world is created from scratch.
Battles you don't pick stay as the original.

## About
A mod that turns the group battles of Legend of Mortal into newly built 3D fights. You control Johwal directly, while units, numbers and rules follow the original data.

The mod's own texts (skill descriptions, passives, screens) follow the game's language: Korean, Simplified Chinese and Traditional Chinese, the three languages the game has (there is no English in the game). Names of skills, people and the like are the game's own lines. They are shown below as in the game's Traditional Chinese version.

## Installation (if you already installed the mod base, skip steps 1 and 2)

**Latest release: [v0.1.12](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)** · **[Download Battle3D_v0.1.12.zip](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/download/v0.1.12/Battle3D_v0.1.12.zip)** (about 120 MB)

1. Download **BepInEx 6** (Unity Mono, `6.0.0-be.692`) and extract it into the game folder (where `Mortal.exe` is).
   - From the [BepInEx builds page](https://builds.bepinex.dev/projects/bepinex_be) take `be.692`, *Unity Mono, Windows x64*.
2. Run the game once so the `BepInEx` folder is created, then close it.
3. Use **Download Battle3D_v0.1.12.zip** above to get the installation package. On the [latest release page](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest), choose **Assets → `Battle3D_v0.1.12.zip`**. `Source code (zip)` and `Source code (tar.gz)` are not installation packages.
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
- Paralysis keeps a unit from moving for 1 second (it can still attack and act), then slows it as before.
- Johwal's thrown hidden weapons (straight and lobbed) hit for 50% of the item's damage. The poison and paralysis their effects give pile up 2 times as fast, and do not fall before the effect has started.
- Shout (嘴攻): R (T if R is a skill key), T in ClickMove, V in Keyboard. Enemies around turn on Johwal; cooldown 5 s. The 音功 you have learned (龍吟功, 虎嘯功, 烈火禪) apply automatically and each adds 1 s to the cooldown. 龍吟功 adds damage, 虎嘯功 paralysis, 烈火禪 a burn.
- A higher 刀劍 (blade) stat quickens the basic attack (up to +50% at 100).
- Skill picking on the ready screen: click a skill to equip or unequip, drag to swap, right click to remove. It can be turned off in the F4 panel.
- "All enemies at once" in the F4 panel puts every enemy on the field from the start.

**Lightness (Qinggong): roll, dash and movement speed**

- Press Space to **roll with Lightness below 25** or **dash with Lightness at 25 or above**. Both require stamina.
- The base movement speed multiplier from Lightness is **`1 + max(0, Lightness) × 0.0005`**. Each point adds 0.05%: Lightness 25 gives **1.0125×**, 50 gives **1.025×**, and 100 gives **1.05×**.
- Maximum dash distance is **`3 + (Lightness - 25) × 0.06` m**: **3 m** at 25, **4.5 m** at 50, and **7.5 m** at 100. Aiming at a nearby cursor shortens the dash, with a minimum distance of 1 m.
- A roll has a base distance of **4.6 m** and a full duration of **0.95 seconds**, regardless of Lightness. The movement speed multiplier above applies to normal movement.

<details>
<summary><b>Johwal's skills</b></summary>

- **奮力一擊**: After a short charge, three slashes forward in a row while invulnerable; it builds the chain like the basic attack does.
- **護體氣罩**: Raises a barrier for 5 seconds that ignores all damage and status effects.
- **防禦**: Becomes invulnerable and pushes back the enemies in front.
- **點破雲關**: At chain 8 or more, spends the whole chain and thrusts forward. Damage is the finisher's damage × 0.5 × chain.
- **雲霄雷霆霹靂刀**: Gathers strength in a crouch, then cuts with the basic attack's third swing while lightning falls on a fan ahead, dealing damage and paralysis. With 動如雷震, targets fall and stay still for 2 seconds.
- **風雷神腳**: At chain 4 or more, spends the whole chain and charges forward in a flying kick. Damage is the finisher's damage × 0.45 × chain.
- **飛天腳**: Jumps, then slams down.
- **翻浪刀法**: Cuts ahead and shoves what it hits, marks the nearest of them with a small blue flame, dashes up to it and cuts once more.
- **連環飛鏢** · **三花齊放** · **點水飛石** (slot passive skills): not skills you press; their effect applies while they sit in a slot.
  - 連環飛鏢: holding the throw key keeps firing (no lobs). The gap is 0.6 s at 暗器 0 and 0.15 s at 100.
  - 三花齊放: a lobbed throw sends 2 more hidden weapons. It cannot be equipped with 連環飛鏢; picking one takes the other's slot. Both unlock at the top level of 唐門暗器總綱.
  - 點水飛石: a straight throw that hits skips on to another enemy nearby, up to 3 times, losing half its damage each time. It unlocks at the top level of 擲石問天.

Since no place to obtain 風雷神腳 and 飛天腳 in the story has been found, they count as learned in battles entered from the F4 panel.

</details>

<details>
<summary><b>Passives</b></summary>

Shown at the upper right of the ready screen and gone once the fight starts.

- **颯踏流星劍**: With the chain at 0, the next basic attack deals triple damage.
- **思想戰**: The fight starts with a chain already built; higher levels start higher.
- **徐如林**: Stamina recovers more each time it regenerates, scaling with the 戰術 (tactics) level.
- **似草針**: A thrown hidden weapon that hits has a 30% chance to break the target's balance.
- **動如雷震**: Targets hit by 雲霄雷霆霹靂刀 fall down and stay still for 2 seconds.
- **額外暗器**: Every straight throw sends one more hidden weapon.
- **毒功**: A melee basic attack that hits gives 50% of the poison and paralysis the straight throw would (when the item has such effects).
- **醫術**: Every 10 seconds in a fight, recovers twice its level in health (14 at level 7).

</details>

<details>
<summary><b>Ally skills</b></summary>

Techniques of the companions you call by equipping their skill on the ready screen.

- **唐門暗器總綱** (the eldest senior brother): Drops from the sky, spins while throwing daggers at random enemies around, drops three bombs and leaves.
- **毒藥** (the second senior brother): Throws poison vials at his own spot and at random enemies around, leaving poison behind.
- **全都是我的錢** (the fourth senior brother): Gathers the coins on the field, throws healing potions and a giant shell.
- **天地無聲勢** (the junior sister): Clones dash into enemies and slash with daggers; she finishes by cutting through.
- **點破雲關．雷動九天** (葉雲舟): Six horizontal dash slashes with a long sword.
- **強力攻擊** (龍湘): Drops in and dashes twice at random enemies, slashing.
- **金錢鏢** (上官螢): Throws coin darts and cuts with a sword.
- **大鐵鎚, 虎戰車** (夏侯蘭): Throws weapons or summons carts to sweep enemies away.

</details>

<details>
<summary><b>Bosses and special enemies</b></summary>

- **石公遠**: Charges at the very start, then walks in to swing or throws stones and knives.
- **丹霞子**: A four-hit slashing combo with two weapons, hitting all around.
- **虞小梅**: Mixes combos with jump attacks and dash slashes, and keeps pace with Johwal (趙活).
- **瑞笙**: Moves like 虞小梅 with a wider reach, in ink-black and white effects.
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
| `[Camera] ShakeStrength` | `0` | Strength of the screen shake (0 = off, 1 = as made) |
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
