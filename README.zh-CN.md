<p align="right"><a href="README.md">한국어</a> · <a href="README.en.md">English</a> · <b>简体中文</b></p>

# Battle3D — 活侠传 团战 3D 模组

这是一个 BepInEx 模组，把 **活侠传（Legend of Mortal）** 的团战替换为全新制作的 3D 战斗。
原版战斗场景只用来读取数据（人数、数值、规则、UI、音效），3D 世界全部重新生成。未指定的战斗保持原版。

## 模组简介
将活侠传的团战替换为全新制作的 3D 战斗的模组。由玩家直接操作主角赵活，单位、数值和规则均沿用原版数据。

## 安装（如果已经安装了模组基础包 Mod base，请跳过第 1、2 步）

**最新版本：[v0.1.5](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)** · **[下载 Battle3D_v0.1.5.zip](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/download/v0.1.5/Battle3D_v0.1.5.zip)**（约 120 MB）

1. 下载 **BepInEx 6**（Unity Mono，`6.0.0-be.692`），解压到游戏文件夹（`Mortal.exe` 所在位置）。
   - 在 [BepInEx 构建页面](https://builds.bepinex.dev/projects/bepinex_be) 下载 `be.692` 的 *Unity Mono, Windows x64*。
2. 先运行一次游戏，确认生成了 `BepInEx` 文件夹，然后关闭游戏。
3. 点击上方的 **下载 Battle3D_v0.1.5.zip** 获取安装包。在[最新发布页面](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)，请选择 **Assets → `Battle3D_v0.1.5.zip`**。`Source code (zip)` 和 `Source code (tar.gz)` 不是安装包。
4. 解压下载的 ZIP，把里面的 `BepInEx` 文件夹 **直接粘贴（覆盖）到游戏文件夹**。
   结果：`...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. 启动游戏并进入团战，即可看到 3D 战斗。

卸载只需删除 `BepInEx\plugins\Battle3D` 文件夹。设置保存在 `BepInEx\config\mortal.battle3d.cfg`（可以删除）。

## 操作

操作方式有三种，默认为 Mouse。可在战斗中暂停菜单的键盘设置按钮里切换。

<details>
<summary><b>Mouse（默认）</b></summary>

| 动作 | 按键 |
|---|---|
| 移动 | W A S D |
| 攻击（三连击） | 鼠标左键 |
| 暗器 | 鼠标右键（长按为抛射） |
| 翻滚 / 冲刺 | Space |
| 技能 1~4 | Q E R F |

</details>

<details>
<summary><b>ClickMove</b></summary>

| 动作 | 按键 |
|---|---|
| 移动 | 鼠标右键（按住持续跟随），S 原地停下 |
| 攻击（三连击） | 鼠标左键 |
| 暗器 | F（长按为抛射） |
| 翻滚 / 冲刺 | Space |
| 技能 1~4 | Q W E R |

</details>

<details>
<summary><b>Keyboard</b></summary>

| 动作 | 按键 |
|---|---|
| 移动 | 方向键 |
| 攻击（三连击） | Z |
| 暗器 | X（长按为抛射） |
| 翻滚 / 冲刺 | Space |
| 技能 1~4 | A S D C |

</details>

**通用**

- 自动瞄准开 / 关：左 Ctrl
- 设置面板：F4
- 隐藏操作列表：F11

**轻功对翻滚、冲刺与移动速度的影响**

- 按 Space 时，**轻功低于 25 使用翻滚**，**轻功达到 25 使用冲刺**。两种动作都需要气力。
- 轻功带来的基础移动速度倍率为 **`1 + max(0, 轻功) × 0.0005`**。每点轻功增加 0.05%：轻功 25 为 **1.0125 倍**，50 为 **1.025 倍**，100 为 **1.05 倍**。
- 冲刺最大距离为 **`3 + (轻功 - 25) × 0.06` 米**：轻功 25 为 **3 米**，50 为 **4.5 米**，100 为 **7.5 米**。朝较近的鼠标位置冲刺时，距离会缩短，最短为 1 米。
- 翻滚的基础距离为 **4.6 米**，完整动作持续 **0.95 秒**，不随轻功变化。上述移动速度倍率适用于普通移动。

<details>
<summary><b>主角的技能</b></summary>

- **分力乱击（분력난격）**：比普通攻击更强的连续斩击，同样会累积连击。
- **护体气罩（호체기조）**：展开持续 5 秒、无视一切伤害与状态异常的屏障。
- **防御（방어）**：把正面的敌人推开，动作期间不受伤害。
- **点破云关（점파운관）**：连击 8 以上时，消耗全部连击，向前突刺。伤害为终结技伤害 × 0.5 × 连击数。
- **云霄雷霆霹雳刀**：以普通攻击第一击挥砍，同时在前方扇形降下雷电，造成伤害与麻痹并使对方失去平衡。
- **风雷神脚**：连击 4 以上时，消耗全部连击，以飞踢向前冲出。伤害为终结技伤害 × 0.45 × 连击数。
- **飞天脚**：跳起后向下踩落。

由于尚未找到风雷神脚与飞天脚在剧情中的获得方式，通过 F4 面板进入的战斗中视为已学会。

</details>

<details>
<summary><b>被动</b></summary>

显示在准备界面右上角，战斗开始后消失。

- **飒踏流星剑（삽답유성검）**：连击为 0 时，下一次普通攻击伤害变为三倍。
- **思想战（사상전）**：以已累积的连击开始战斗，等级越高越多。
- **徐如林（서여림）**：气力每次恢复时多恢复一些，与技能「战术」等级成正比。
- **似草针（사초침）**：投出的暗器命中时，有 30% 几率使对方失去平衡。
- **动如雷震（동여뢰진）**：被云霄雷霆霹雳刀击中的敌人会倒地。

</details>

<details>
<summary><b>友军技能</b></summary>

在准备界面装备其技能即可召唤的同伴招式。

- **大师兄（대사형）**：从天而降，旋转投掷匕首，投下炸弹后离开。
- **二师兄（이사형）**：投掷毒药瓶，留下毒。
- **四师兄（사사형）**：聚集场上的铜钱并投出，同时掉落回复药。
- **小师妹（소사매）**：分身瞬间冲向敌人以匕首斩击，最后穿身而过。
- **叶云舟（엽운주）**：以长剑横向冲刺，连斩六次。
- **龙翔（용상）**：从天而降，向随机敌人冲刺斩击两次。
- **上官萤（상관형）**：掷出金钱镖并以剑斩击。
- **郁竹（옥죽）**：投掷武器或召唤推车扫荡敌人。

</details>

<details>
<summary><b>首领与特殊敌人</b></summary>

- **石公远（석공원）**：开战即冲锋，之后走近挥击，或投掷石头与刀。
- **丹霞子（단하자）**：双持武器的四连斩，攻击范围覆盖四周。
- **右小梅（우소매）**：在连击中穿插跳跃攻击与冲刺斩，速度与主角相当。
- 所有首领都拥有霸体，不易被攻击击退。

</details>

<details>
<summary><b>配置文件</b></summary>

`BepInEx\config\mortal.battle3d.cfg` — 首次运行后生成。请在游戏关闭时用文本编辑器修改。

| 项目 | 默认值 | 说明 |
|---|---|---|
| `[General] Enabled` | `true` | 是否使用 3D 战斗（关闭则所有战斗为原版）。也可在 F4 面板中开关。 |
| `[General] ExcludedBattles` | `""` | 保持原版 2D 的战斗代码（不含 `BL_`，用逗号分隔），其余战斗均为 3D。例：`1000,0001` |
| `[Controls] Scheme` | `Mouse` | 操作方式：`Mouse` / `ClickMove` / `Keyboard` |
| `[Controls] AutoAim` | `true` | 自动瞄准敌人（战斗中也可用左 Ctrl 切换） |
| `[Skills] Slot1Key ~ Slot4Key` | `q, e, r, f` | 技能栏 1~4 的按键（Input System 按键名） |
| `[Skills] RememberLoadout` | `true` | 下一场战斗继续沿用主角的技能栏装备 |
| `[Camera] Pitch` | `35` | 镜头俯角（度） |
| `[Camera] Yaw` | `45` | 镜头水平角（度） |
| `[Camera] Distance` | `23` | 默认镜头距离（鼠标滚轮缩放） |
| `[Graphics] PostProcessing` | `true` | 泛光、色彩校正、暗角 |
| `[Graphics] Intro` | `true` | 进入战斗时镜头从天空穿过云层降下的演出 |
| `[Graphics] ToonShader` | `true` | 卡通着色（关闭则为普通 URP 着色） |
| `[Graphics] Outline` | `true` | 角色与武器描边 |
| `[Sound] CustomVolume` | `1` | 模组自带音效（Audio 文件夹）的音量（0~1） |
| `[Sound] BasicSwingVolume` | `0.7` | 主角普通攻击挥动声的额外音量倍率（0~1） |

</details>

## 常见问题
请先打开 `BepInEx\LogOutput.log`。模组运行时会写入以 `[Battle 3D]` 开头的行。反馈问题时请附上这个文件。

<details>
<summary><b>模组没有启动（日志里没有 <code>[Battle 3D]</code> 行）</b></summary>

- 如果根本没有 `BepInEx\LogOutput.log`，说明 BepInEx 没有运行。请确认游戏文件夹（`Mortal.exe` 旁边）里有 `winhttp.dll`、`doorstop_config.ini` 和 `BepInEx` 文件夹。（请重新做安装的第 1、2 步。）
- 检查文件位置。下面四项必须都在 `BepInEx\plugins\Battle3D\` 里：`Battle3D.dll`、`battle3d.bundle`、`battle3d_environment.bundle`、`Audio` 文件夹。不能多套一层（`Battle3D\Battle3D\...`）。
- BepInEx 必须是 **6.0.0-be.692（Unity Mono）**。5.x 版本或 IL2CPP 版本无法使用。
- 暂时把其他模组全部移出 `BepInEx\plugins`，只留这个模组再试。如果单独可以、与其他模组一起就不行，请告诉我们用了哪些模组。
- 解压时 Windows 可能会拦截文件。请在 zip 文件属性里勾选“解除锁定”后重新解压。也请确认杀毒软件没有隔离 `Battle3D.dll`。

</details>

<details>
<summary><b>模组已启动，但战斗没有变成 3D</b></summary>

- 在 `F4` 设置面板里确认 3D 战斗已开启。也请检查 `BepInEx\config\mortal.battle3d.cfg` 里的 `[General] Enabled` 和 `ExcludedBattles`。
- 尚未制作 3D 版本的战斗仍是原版。
- 如果日志里有带 `Battle 3D` 的错误（`Exception`），请把那一行发给我们。

</details>

<details>
<summary><b>出现 <code>file ... is corrupted! Position out of bounds</code> 之类的错误并闪退</b></summary>

- 这是因为 `battle3d.bundle` 或 `battle3d_environment.bundle` 没有下载完整，或者在游戏运行时被覆盖。请完全关闭游戏，重新下载 zip 并覆盖。（两个资源包分别约 70 MB 和 56 MB。）

</details>

<details>
<summary><b>想把设置恢复默认</b></summary>

- 关闭游戏，删除 `BepInEx\config\mortal.battle3d.cfg`。下次启动时会按默认值重新生成。

</details>

<details>
<summary><b>游戏更新后出错</b></summary>

- 游戏更新改动了原版代码时，模组可能不再适用。请查看是否有新版本，没有的话请在 Issues 里附上日志反馈。

</details>

## 许可 / 使用说明
依据 [MIT 许可证](LICENSE)，任何人都可以免费自由使用。

- 本许可仅适用于作者自行创作的代码和内容。发布文件中包含的第三方素材遵循各自权利人的条款，游戏《活侠传（Legend of Mortal）》及其数据的权利归游戏开发商所有。
- 本模组为非官方的爱好者作品，与游戏开发商无关。不包含任何游戏原始数据文件，数据在运行时读取。
- 本模组按“现状”提供，不提供任何形式的担保。
