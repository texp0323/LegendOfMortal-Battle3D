<p align="right"><a href="README.md">한국어</a> · <a href="README.en.md">English</a> · <b>简体中文</b></p>

# Battle3D — 活侠传 团战 3D 模组

这是一个 BepInEx 模组，把 **活侠传（Legend of Mortal）** 的团战替换为全新制作的 3D 战斗。
原版战斗场景只用来读取数据（人数、数值、规则、UI、音效），3D 世界全部重新生成。未指定的战斗保持原版。

> 本仓库只提供说明和发布包（zip），不公开源代码。

## 主要功能
- 团战改为四分之一视角的 3D：新地图（悬崖高地、城镇、室内等）、按门派区分的角色模型、卡通着色与描边
- 沿用原版数据：单位配置、生命 / 攻击 / 气力、暗器（平射与抛射）、状态异常（中毒、麻痹）、战斗特殊规则
- 直接操作：WASD 移动，左键三连击，右键投掷，Space 翻滚 / 冲刺，Q E R F 技能。三种操作方式（鼠标 / 点击移动 / 键盘）
- **连击** 系统与技能 **点破云关（점파운관）**（连击 8 以上可用）
- 被动：飒踏流星剑、思想战、徐如林、似草针（显示在准备界面右上角，战斗开始后淡出）
- 记住主角技能栏的装备，下一场战斗继续沿用
- 友军与敌人技能、首领招式、音效、特效
- **F4 设置面板**：声音、镜头、操作、画面（卡通着色、描边），以及用战斗代码直接进入战斗

## 安装（如果已经安装了模组基础包 Mod base，请跳过第 1、2 步）
1. 下载 **BepInEx 6**（Unity Mono，`6.0.0-be.692`），解压到游戏文件夹（`Mortal.exe` 所在位置）。
   - 在 [BepInEx 构建页面](https://builds.bepinex.dev/projects/bepinex_be) 下载 `be.692` 的 *Unity Mono, Windows x64*。
2. 先运行一次游戏，确认生成了 `BepInEx` 文件夹，然后关闭游戏。
3. 从 [Releases](../../releases) 下载 `Battle3D_vX.Y.Z.zip`。
4. 把压缩包里的 `BepInEx` 文件夹 **直接粘贴（覆盖）到游戏文件夹**。
   结果：`...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. 启动游戏并进入团战，即可看到 3D 战斗。

卸载只需删除 `BepInEx\plugins\Battle3D` 文件夹。设置保存在 `BepInEx\config\mortal.battle3d.cfg`（可以删除）。

## 操作（默认：鼠标）
| 动作 | 按键 |
|---|---|
| 移动 | W A S D |
| 攻击（三连击） | 鼠标左键 |
| 暗器 | 鼠标右键（长按为抛射） |
| 翻滚 / 冲刺 | Space |
| 技能 1~4 | Q E R F |
| 自动瞄准开 / 关 | 左 Ctrl |
| 设置面板 | F4 |
| 隐藏操作列表 | F11 |

操作方式可在战斗中暂停菜单的键盘设置按钮里切换。

## 常见问题
请先打开 `BepInEx\LogOutput.log`。模组运行时会写入以 `[Battle 3D]` 开头的行。反馈问题时请附上这个文件。

**模组没有启动（日志里没有 `[Battle 3D]` 行）**
- 如果根本没有 `BepInEx\LogOutput.log`，说明 BepInEx 没有运行。请确认游戏文件夹（`Mortal.exe` 旁边）里有 `winhttp.dll`、`doorstop_config.ini` 和 `BepInEx` 文件夹。（请重新做安装的第 1、2 步。）
- 检查文件位置。下面四项必须都在 `BepInEx\plugins\Battle3D\` 里：`Battle3D.dll`、`battle3d.bundle`、`battle3d_environment.bundle`、`Audio` 文件夹。不能多套一层（`Battle3D\Battle3D\...`）。
- BepInEx 必须是 **6.0.0-be.692（Unity Mono）**。5.x 版本或 IL2CPP 版本无法使用。
- 暂时把其他模组全部移出 `BepInEx\plugins`，只留这个模组再试。如果单独可以、与其他模组一起就不行，请告诉我们用了哪些模组。
- 解压时 Windows 可能会拦截文件。请在 zip 文件属性里勾选“解除锁定”后重新解压。也请确认杀毒软件没有隔离 `Battle3D.dll`。

**模组已启动，但战斗没有变成 3D**
- 在 `F4` 设置面板里确认 3D 战斗已开启。也请检查 `BepInEx\config\mortal.battle3d.cfg` 里的 `[General] Enabled` 和 `ExcludedBattles`。
- 尚未制作 3D 版本的战斗仍是原版。
- 如果日志里有带 `Battle 3D` 的错误（`Exception`），请把那一行发给我们。

**出现 `file ... is corrupted! Position out of bounds` 之类的错误并闪退**
- 这是因为 `battle3d.bundle` 或 `battle3d_environment.bundle` 没有下载完整，或者在游戏运行时被覆盖。请完全关闭游戏，重新下载 zip 并覆盖。（两个资源包分别约 70 MB 和 56 MB。）

**没有声音 / 声音太大**
- 在 `F4` 面板的声音项里调整。也请确认 `Audio` 文件夹在 `Battle3D` 文件夹里。

**画面太暗或太卡**
- 在 `F4` 面板的画面项里关闭卡通着色 / 描边，或在配置文件里把 `[Graphics] PostProcessing` 改为 `false`。

**想把设置恢复默认**
- 关闭游戏，删除 `BepInEx\config\mortal.battle3d.cfg`。下次启动时会按默认值重新生成。

**游戏更新后出错**
- 游戏更新改动了原版代码时，模组可能不再适用。请查看是否有新版本，没有的话请在 Issues 里附上日志反馈。

## 许可 / 使用说明
Copyright © texp0323. All rights reserved.
可自由个人使用。未经许可，不得修改、基于反编译代码制作衍生作品，或再分发（例如把 zip 上传到其他网站）。
本模组为非官方作品，与游戏开发商无关。不包含任何游戏原始数据文件，数据在运行时读取。
