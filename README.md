<p align="right"><b>한국어</b> · <a href="README.en.md">English</a> · <a href="README.zh-CN.md">简体中文</a></p>

# Battle3D — 활협전 단체전 3D 모드

**활협전(Legend of Mortal)** 의 단체전을 새로 제작한 3D 전투로 전환하는 BepInEx 모드입니다.
원본 전투 씬은 인원·수치·규칙·UI·소리 등 데이터를 읽는 용도로만 사용하며, 3D 월드는 모두 새로 생성합니다. 지정되지 않은 전투는 원본 그대로 진행됩니다.

## 주요 기능
- 단체전을 쿼터뷰 3D로 전환: 신규 맵(절벽 고원·마을·실내 등), 문파별 캐릭터 모델, 툰 셰이딩 및 외곽선
- 원본 데이터 그대로 적용: 유닛 구성, 체력·공격력·기력, 암기(평사·포사), 상태이상(중독·마비), 전투 특수 규칙
- 직접 조작: WASD 이동, 좌클릭 3연격, 우클릭 암기, Space 구르기·대시, Q E R F 스킬. 조작 방식 3가지 지원(마우스 / 클릭 이동 / 키보드)
- **연격** 시스템 및 스킬 **점파운관**(연격 8 이상에서 사용 가능)
- 패시브: 삽답유성검, 사상전, 서여림, 사초침 (준비 화면 우측 상단에 표시되며, 전투가 시작되면 사라집니다)
- 조활의 스킬 장착 상태를 다음 전투에도 유지
- 아군·적 스킬, 보스 패턴, 효과음, 이펙트
- **F4 설정 패널**: 소리, 카메라, 조작, 그래픽(툰 셰이딩·외곽선), 전투 코드로 바로 입장

## 설치 (모드 베이스를 이미 설치하셨다면 1, 2번은 건너뛰십시오)
1. **BepInEx 6** (Unity Mono, `6.0.0-be.692`)를 내려받아 게임 폴더(`Mortal.exe`가 있는 폴더)에 압축 해제합니다.
   - [BepInEx 빌드 페이지](https://builds.bepinex.dev/projects/bepinex_be)에서 `be.692` 의 *Unity Mono, Windows x64* 를 내려받습니다.
2. 게임을 한 번 실행하여 `BepInEx` 폴더가 생성된 것을 확인한 뒤 종료합니다.
3. [Releases](../../releases)에서 `Battle3D_vX.Y.Z.zip` 을 내려받습니다.
4. zip 안의 `BepInEx` 폴더를 **게임 폴더에 그대로 붙여넣기(덮어쓰기)** 합니다.
   결과: `...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. 게임을 실행하고 단체전에 진입하면 3D 전투가 시작됩니다.

제거하려면 `BepInEx\plugins\Battle3D` 폴더를 삭제하십시오. 설정은 `BepInEx\config\mortal.battle3d.cfg`에 저장되며, 이 파일은 삭제해도 무방합니다.

## 조작 (기본: Mouse)
| 동작 | 키 |
|---|---|
| 이동 | W A S D |
| 공격 (3연격) | 좌클릭 |
| 암기 | 우클릭 (길게 누르면 포물선 포사) |
| 구르기 / 대시 | Space |
| 스킬 1~4 | Q E R F |
| 자동 조준 켜기·끄기 | 왼쪽 Ctrl |
| 설정 패널 | F4 |
| 조작 목록 숨기기 | F11 |

조작 방식은 전투 중 일시정지 메뉴의 키보드 설정 버튼에서 변경할 수 있습니다.

## 문제 해결
먼저 `BepInEx\LogOutput.log` 를 열어 확인하십시오. 모드가 정상적으로 실행되면 `[Battle 3D]` 로 시작하는 줄이 기록됩니다. 문제를 문의하실 때는 이 파일을 함께 첨부해 주십시오.

<details>
<summary><b>게임을 실행해도 모드가 켜지지 않습니다 (로그에 <code>[Battle 3D]</code> 줄이 없음)</b></summary>

- `BepInEx\LogOutput.log` 파일 자체가 없다면 BepInEx가 실행되지 않은 것입니다. 게임 폴더(`Mortal.exe` 옆)에 `winhttp.dll`, `doorstop_config.ini`, `BepInEx` 폴더가 있는지 확인하십시오. (설치 1, 2번을 다시 진행해 보십시오.)
- 파일 위치를 확인하십시오. 다음 네 항목이 모두 `BepInEx\plugins\Battle3D\` 안에 있어야 합니다: `Battle3D.dll`, `battle3d.bundle`, `battle3d_environment.bundle`, `Audio` 폴더. 폴더가 한 단계 더 들어가 있으면(`Battle3D\Battle3D\...`) 인식되지 않습니다.
- BepInEx는 **6.0.0-be.692 (Unity Mono)** 이어야 합니다. 5.x 버전이나 IL2CPP 빌드에서는 동작하지 않습니다.
- 다른 모드를 모두 `BepInEx\plugins`에서 잠시 제외하고 이 모드만 실행해 보십시오. 단독으로는 정상이지만 다른 모드와 함께 쓸 때 문제가 생긴다면, 함께 사용한 모드를 알려 주십시오.
- 압축 해제 시 윈도우가 파일을 차단하는 경우가 있습니다. zip 파일 속성에서 *차단 해제*를 체크한 뒤 다시 압축을 해제하십시오. 백신 프로그램이 `Battle3D.dll`을 격리하지 않았는지도 확인하십시오.

</details>

<details>
<summary><b>모드는 실행되지만 전투가 3D로 전환되지 않습니다</b></summary>

- `F4` 설정 패널에서 3D 전투가 켜져 있는지 확인하십시오. 설정 파일(`BepInEx\config\mortal.battle3d.cfg`)의 `[General] Enabled` 와 `ExcludedBattles` 도 확인하십시오.
- 아직 3D로 제작되지 않은 전투는 원본 그대로 진행됩니다.
- 로그에 `Battle 3D` 와 함께 오류(`Exception`)가 기록되어 있다면 해당 줄을 알려 주십시오.

</details>

<details>
<summary><b><code>file ... is corrupted! Position out of bounds</code> 와 같은 오류가 표시되며 게임이 종료됩니다</b></summary>

- `battle3d.bundle` 또는 `battle3d_environment.bundle` 이 완전히 내려받아지지 않았거나, 게임이 실행 중인 상태에서 덮어쓰기가 이루어진 경우 발생합니다. 게임을 완전히 종료한 뒤 zip을 다시 내려받아 덮어쓰십시오. (번들 두 개의 크기는 각각 약 70 MB, 56 MB입니다.)

</details>

<details>
<summary><b>소리가 나지 않거나 너무 큽니다</b></summary>

- `F4` 설정 패널의 소리 항목에서 조절하십시오. `Audio` 폴더가 `Battle3D` 폴더 안에 있는지도 확인하십시오.

</details>

<details>
<summary><b>화면이 너무 어둡거나 느립니다</b></summary>

- `F4` 패널의 그래픽 항목에서 툰 셰이딩·외곽선을 끄거나, 설정 파일에서 `[Graphics] PostProcessing` 을 `false` 로 변경해 보십시오.

</details>

<details>
<summary><b>설정을 초기화하고 싶습니다</b></summary>

- 게임을 종료한 뒤 `BepInEx\config\mortal.battle3d.cfg` 를 삭제하십시오. 다음 실행 시 기본값으로 다시 생성됩니다.

</details>

<details>
<summary><b>게임 업데이트 이후 오류가 발생합니다</b></summary>

- 게임 업데이트로 원본 코드가 변경되면 모드가 맞지 않을 수 있습니다. 최신 릴리즈가 있는지 확인하시고, 없다면 로그와 함께 Issues에 문의해 주십시오.

</details>

## 라이선스 / 이용 안내
[MIT 라이선스](LICENSE)에 따라 누구나 무료로 자유롭게 이용하실 수 있습니다.

- 이 라이선스는 제작자가 직접 만든 코드와 콘텐츠에만 적용됩니다. 릴리즈 파일에 포함된 외부 에셋은 각 권리자의 이용 조건을 따르며, 게임 「활협전(Legend of Mortal)」과 그 데이터의 권리는 게임 제작사에 있습니다.
- 본 모드는 비공식 팬 제작물이며 게임 제작사와 관련이 없습니다. 게임의 원본 데이터는 파일로 포함하지 않으며 실행 중에 읽어서 사용합니다.
- 본 모드는 있는 그대로 제공되며, 사용으로 발생하는 문제에 대해 어떠한 보증도 하지 않습니다.
