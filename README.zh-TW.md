<p align="right"><a href="README.md">韓語</a> · <a href="README.en.md">English</a> · <a href="README.zh-CN.md">简体中文</a> · <b>繁體中文</b></p>

# Battle3D — 活俠傳 團戰 3D 模組

這是一個 BepInEx 模組，把 **活俠傳（Legend of Mortal）** 的團戰替換為全新製作的 3D 戰鬥。
原版戰鬥場景只用來讀取資料（人數、數值、規則、UI、音效），3D 世界全部重新生成。未指定的戰鬥保持原版。

## 模組簡介
將活俠傳的團戰替換為全新製作的 3D 戰鬥的模組。由玩家直接操作主角趙活，單位、數值和規則均沿用原版資料。

模組中自己寫的文字（技能說明、被動、介面）會隨遊戲語言顯示：支援遊戲自帶的三種語言（韓語、簡體中文、繁體中文）。技能、人物等名稱沿用遊戲裡原有的翻譯。遊戲本身沒有英語。

## 安裝（如果已經安裝了模組基礎包 Mod base，請跳過第 1、2 步）

**最新版本：[v0.1.6](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)** · **[下載 Battle3D_v0.1.6.zip](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/download/v0.1.6/Battle3D_v0.1.6.zip)**（約 120 MB）

1. 下載 **BepInEx 6**（Unity Mono，`6.0.0-be.692`），解壓到遊戲資料夾（`Mortal.exe` 所在位置）。
   - 在 [BepInEx 構建頁面](https://builds.bepinex.dev/projects/bepinex_be) 下載 `be.692` 的 *Unity Mono, Windows x64*。
2. 先執行一次遊戲，確認生成了 `BepInEx` 資料夾，然後關閉遊戲。
3. 點選上方的 **下載 Battle3D_v0.1.6.zip** 獲取安裝包。在[最新發布頁面](https://github.com/texp0323/LegendOfMortal-Battle3D/releases/latest)，請選擇 **Assets → `Battle3D_v0.1.6.zip`**。`Source code (zip)` 和 `Source code (tar.gz)` 不是安裝包。
4. 解壓下載的 ZIP，把裡面的 `BepInEx` 資料夾 **直接貼上（覆蓋）到遊戲資料夾**。
   結果：`...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. 啟動遊戲並進入團戰，即可看到 3D 戰鬥。

解除安裝只需刪除 `BepInEx\plugins\Battle3D` 資料夾。設定儲存在 `BepInEx\config\mortal.battle3d.cfg`（可以刪除）。

## 操作

操作方式有三種，預設為 Mouse。可在戰鬥中暫停選單的鍵盤設定按鈕裡切換。

<details>
<summary><b>Mouse（預設）</b></summary>

| 動作 | 按鍵 |
|---|---|
| 移動 | W A S D |
| 攻擊（三連擊） | 滑鼠左鍵 |
| 暗器 | 滑鼠右鍵（長按為拋射） |
| 翻滾 / 衝刺 | Space |
| 技能 1~4 | Q E R F |

</details>

<details>
<summary><b>ClickMove</b></summary>

| 動作 | 按鍵 |
|---|---|
| 移動 | 滑鼠右鍵（按住持續跟隨），S 原地停下 |
| 攻擊（三連擊） | 滑鼠左鍵 |
| 暗器 | F（長按為拋射） |
| 翻滾 / 衝刺 | Space |
| 技能 1~4 | Q W E R |

</details>

<details>
<summary><b>Keyboard</b></summary>

| 動作 | 按鍵 |
|---|---|
| 移動 | 方向鍵 |
| 攻擊（三連擊） | Z |
| 暗器 | X（長按為拋射） |
| 翻滾 / 衝刺 | Space |
| 技能 1~4 | A S D C |

</details>

**通用**

- 自動瞄準開 / 關：左 Ctrl
- 設定面板：F4
- 隱藏操作列表：F11

**輕功對翻滾、衝刺與移動速度的影響**

- 按 Space 時，**輕功低於 25 使用翻滾**，**輕功達到 25 使用衝刺**。兩種動作都需要氣力。
- 輕功帶來的基礎移動速度倍率為 **`1 + max(0, 輕功) × 0.0005`**。每點輕功增加 0.05%：輕功 25 為 **1.0125 倍**，50 為 **1.025 倍**，100 為 **1.05 倍**。
- 衝刺最大距離為 **`3 + (輕功 - 25) × 0.06` 米**：輕功 25 為 **3 米**，50 為 **4.5 米**，100 為 **7.5 米**。朝較近的滑鼠位置衝刺時，距離會縮短，最短為 1 米。
- 翻滾的基礎距離為 **4.6 米**，完整動作持續 **0.95 秒**，不隨輕功變化。上述移動速度倍率適用於普通移動。

<details>
<summary><b>主角的技能</b></summary>

- **奮力一擊**：稍作蓄力後，在無敵狀態下向前連斬三次，同樣會累積連擊。
- **護體氣罩**：展開持續 5 秒、免疫一切傷害與異常狀態的屏障。
- **防禦**：進入無敵狀態，把正面的敵人推開。
- **點破雲關**：連擊 8 以上時，消耗全部連擊，向前突刺。傷害為終結技傷害 × 0.5 × 連擊數。
- **雲霄雷霆霹靂刀**：以普通攻擊第一擊揮砍，同時在前方扇形降下雷電，造成傷害與麻痺。
- **風雷神腳**：連擊 4 以上時，消耗全部連擊，以飛踢向前衝出。傷害為終結技傷害 × 0.45 × 連擊數。
- **飛天腳**：跳起後向下踩落。

尚未找到風雷神腳與飛天腳在劇情中的獲得方式，透過 F4 面板進入的戰鬥中視為已學會。

</details>

<details>
<summary><b>被動</b></summary>

顯示在準備介面右上角，戰鬥開始後消失。

- **颯踏流星劍**：連擊為 0 時，下一次普通攻擊傷害變為三倍。
- **思想戰**：以已累積的連擊開始戰鬥，等級越高越多。
- **徐如林**：氣力每次恢復時多恢復一些，與技能「戰術」等級成正比。
- **似草針**：投出的暗器命中時，有 30% 機率造成失衡。
- **動如雷震**：被雲霄雷霆霹靂刀擊中的敵人會倒地。

</details>

<details>
<summary><b>友軍技能</b></summary>

在準備介面裝備其技能即可召喚的同伴招式。

- **唐門暗器總綱**（大師兄）：從天而降，旋轉並向周圍的隨機敵人投擲匕首，最後投下三顆炸彈後離開。
- **毒藥**（二師兄）：向自身位置與周圍隨機敵人投擲毒藥瓶，留下毒。
- **全都是我的錢**（四師兄）：聚集場上的銅錢，投出回復藥與巨大炮彈。
- **天地無聲勢**（小師妹）：分身衝向敵人以匕首斬擊，最後穿身而過。
- **點破雲關．雷動九天**（葉雲舟）：以長劍橫向衝刺，連斬六次。
- **強力攻擊**（龍湘）：從天而降，向隨機敵人衝刺斬擊兩次。
- **金錢鏢**（上官螢）：擲出金錢鏢並以長劍斬擊。
- **大鐵鎚、虎戰車**（夏侯蘭）：投擲武器或召喚推車掃蕩敵人。

</details>

<details>
<summary><b>首領與特殊敵人</b></summary>

- **石公遠**：開戰即衝鋒，之後走近揮擊，或投擲石頭與刀。
- **丹霞子**：雙持武器的四連斬，攻擊範圍覆蓋四周。
- **虞小梅**：在連擊中穿插跳躍攻擊與衝刺斬，速度與主角相當。
- **瑞笙**：動作與虞小梅相似，攻擊範圍更廣，以墨色特效施展。
- 所有首領都擁有霸體，不易被攻擊擊退。

</details>

<details>
<summary><b>配置檔案</b></summary>

`BepInEx\config\mortal.battle3d.cfg` — 首次執行後生成。請在遊戲關閉時用文字編輯器修改。

| 項目 | 預設值 | 說明 |
|---|---|---|
| `[General] Enabled` | `true` | 是否使用 3D 戰鬥（關閉則所有戰鬥為原版）。也可在 F4 面板中開關。 |
| `[General] ExcludedBattles` | `""` | 保持原版 2D 的戰鬥程式碼（不含 `BL_`，用逗號分隔），其餘戰鬥均為 3D。例：`1000,0001` |
| `[Controls] Scheme` | `Mouse` | 操作方式：`Mouse` / `ClickMove` / `Keyboard` |
| `[Controls] AutoAim` | `true` | 自動瞄準敵人（戰鬥中也可用左 Ctrl 切換） |
| `[Skills] Slot1Key ~ Slot4Key` | `q, e, r, f` | 技能欄 1~4 的按鍵（Input System 按鍵名） |
| `[Skills] RememberLoadout` | `true` | 下一場戰鬥繼續沿用主角的技能欄裝備 |
| `[Camera] Pitch` | `35` | 鏡頭俯角（度） |
| `[Camera] Yaw` | `45` | 鏡頭水平角（度） |
| `[Camera] Distance` | `23` | 預設鏡頭距離（滑鼠滾輪縮放） |
| `[Camera] ShakeStrength` | `0` | 畫面震動強度（0 = 關閉，1 = 原樣） |
| `[Graphics] PostProcessing` | `true` | 泛光、色彩校正、暗角 |
| `[Graphics] Intro` | `true` | 進入戰鬥時鏡頭從天空穿過雲層降下的演出 |
| `[Graphics] ToonShader` | `true` | 卡通著色（關閉則為普通 URP 著色） |
| `[Graphics] Outline` | `true` | 角色與武器描邊 |
| `[Sound] CustomVolume` | `1` | 模組自帶音效（Audio 資料夾）的音量（0~1） |
| `[Sound] BasicSwingVolume` | `0.7` | 主角普通攻擊揮動聲的額外音量倍率（0~1） |

</details>

## 常見問題
請先開啟 `BepInEx\LogOutput.log`。模組執行時會寫入以 `[Battle 3D]` 開頭的行。反饋問題時請附上這個檔案。

<details>
<summary><b>模組沒有啟動（日誌裡沒有 <code>[Battle 3D]</code> 行）</b></summary>

- 如果根本沒有 `BepInEx\LogOutput.log`，說明 BepInEx 沒有執行。請確認遊戲資料夾（`Mortal.exe` 旁邊）裡有 `winhttp.dll`、`doorstop_config.ini` 和 `BepInEx` 資料夾。（請重新做安裝的第 1、2 步。）
- 檢查檔案位置。下面四項必須都在 `BepInEx\plugins\Battle3D\` 裡：`Battle3D.dll`、`battle3d.bundle`、`battle3d_environment.bundle`、`Audio` 資料夾。不能多套一層（`Battle3D\Battle3D\...`）。
- BepInEx 必須是 **6.0.0-be.692（Unity Mono）**。5.x 版本或 IL2CPP 版本無法使用。
- 暫時把其他模組全部移出 `BepInEx\plugins`，只留這個模組再試。如果單獨可以、與其他模組一起就不行，請告訴我們用了哪些模組。
- 解壓時 Windows 可能會攔截檔案。請在 zip 檔案屬性裡勾選“解除鎖定”後重新解壓。也請確認防毒軟體沒有隔離 `Battle3D.dll`。

</details>

<details>
<summary><b>模組已啟動，但戰鬥沒有變成 3D</b></summary>

- 在 `F4` 設定面板裡確認 3D 戰鬥已開啟。也請檢查 `BepInEx\config\mortal.battle3d.cfg` 裡的 `[General] Enabled` 和 `ExcludedBattles`。
- 尚未製作 3D 版本的戰鬥仍是原版。
- 如果日誌裡有帶 `Battle 3D` 的錯誤（`Exception`），請把那一行發給我們。

</details>

<details>
<summary><b>出現 <code>file ... is corrupted! Position out of bounds</code> 之類的錯誤並閃退</b></summary>

- 這是因為 `battle3d.bundle` 或 `battle3d_environment.bundle` 沒有下載完整，或者在遊戲執行時被覆蓋。請完全關閉遊戲，重新下載 zip 並覆蓋。（兩個資源包分別約 70 MB 和 56 MB。）

</details>

<details>
<summary><b>想把設定恢復預設</b></summary>

- 關閉遊戲，刪除 `BepInEx\config\mortal.battle3d.cfg`。下次啟動時會按預設值重新生成。

</details>

<details>
<summary><b>遊戲更新後出錯</b></summary>

- 遊戲更新改動了原版程式碼時，模組可能不再適用。請檢視是否有新版本，沒有的話請在 Issues 裡附上日誌反饋。

</details>

## 許可 / 使用說明
依據 [MIT 許可證](LICENSE)，任何人都可以免費自由使用。

- 本許可僅適用於作者自行創作的程式碼和內容。釋出檔案中包含的第三方素材遵循各自權利人的條款，遊戲《活俠傳（Legend of Mortal）》及其資料的權利歸遊戲開發商所有。
- 本模組為非官方的愛好者作品，與遊戲開發商無關。不包含任何遊戲原始資料檔案，資料在執行時讀取。
- 本模組按“現狀”提供，不提供任何形式的擔保。
