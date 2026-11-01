<p align="right"><b>한국어</b> · <a href="README.en.md">English</a> · <a href="README.zh-CN.md">简体中文</a></p>

# Battle3D — 활협전 단체전 3D 모드

**활협전(Legend of Mortal)** 의 단체전을 새로 만든 3D 전투로 바꿔 주는 BepInEx 모드예요.
원본 전투 씬은 인원·수치·규칙·UI·소리를 읽는 데만 쓰고, 3D 월드는 전부 새로 띄워요. 지정하지 않은 전투는 원본 그대로예요.

> 이 저장소에는 설명과 릴리즈(zip)만 있고 소스 코드는 공개하지 않아요.

## 주요 기능
- 단체전을 쿼터뷰 3D로: 새 맵(절벽 고원·마을·실내 등), 문파별 캐릭터 모델, 툰 셰이딩과 외곽선
- 원본 데이터 그대로: 유닛 구성, 체력·공격력·기력, 암기(평사·포사), 상태이상(중독·마비), 전투 특수 규칙
- 직접 조작: WASD 이동, 좌클릭 3연격, 우클릭 암기, Space 구르기·대시, Q E R F 스킬. 조작 방식 3가지(마우스 / 클릭 이동 / 키보드)
- **연격** 시스템과 스킬 **점파운관**(연격 8 이상)
- 패시브: 삽답유성검, 사상전, 서여림, 사초침 (준비 화면 우측 상단에 표시, 전투가 시작되면 사라짐)
- 조활 스킬 장착을 다음 전투에도 기억
- 아군·적 스킬과 보스 패턴, 효과음, 이펙트
- **F4 설정 패널**: 소리, 카메라, 조작, 그래픽(툰 셰이딩·외곽선), 전투 코드로 바로 입장

## 설치 (모드 베이스를 이미 설치했다면 1, 2번은 건너뛰세요)
1. **BepInEx 6** (Unity Mono, `6.0.0-be.692`)를 받아 게임 폴더(`Mortal.exe`가 있는 곳)에 풀어요.
   - [BepInEx 빌드 페이지](https://builds.bepinex.dev/projects/bepinex_be)에서 `be.692` 의 *Unity Mono, Windows x64* 를 받아요.
2. 게임을 한 번 켜서 `BepInEx` 폴더가 만들어지는 걸 확인하고 끄세요.
3. [Releases](../../releases)에서 `Battle3D_vX.Y.Z.zip` 을 받아요.
4. zip 안의 `BepInEx` 폴더를 **게임 폴더에 그대로 붙여넣기(덮어쓰기)** 해요.
   결과: `...\LegendOfMortal\BepInEx\plugins\Battle3D\Battle3D.dll`
5. 게임을 켜고 단체전에 들어가면 3D 전투가 열려요.

제거는 `BepInEx\plugins\Battle3D` 폴더를 지우면 돼요. 설정은 `BepInEx\config\mortal.battle3d.cfg`에 저장돼요(지워도 됨).

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

조작 방식은 전투 중 일시정지 메뉴의 키보드 설정 버튼에서 바꿀 수 있어요.

## 문제 해결
먼저 `BepInEx\LogOutput.log` 를 열어 보세요. 모드가 켜지면 `[Battle 3D]` 로 시작하는 줄이 생겨요. 문제를 알릴 때는 이 파일을 같이 올려 주세요.

**게임을 켜도 모드가 안 켜져요 (로그에 `[Battle 3D]` 줄이 없어요)**
- `BepInEx\LogOutput.log` 자체가 없다면 BepInEx가 실행되지 않은 거예요. 게임 폴더(`Mortal.exe` 옆)에 `winhttp.dll`, `doorstop_config.ini`, `BepInEx` 폴더가 있는지 확인하세요. (설치 1, 2번을 다시 해 보세요.)
- 파일 위치를 확인하세요. 아래 네 개가 모두 `BepInEx\plugins\Battle3D\` 안에 있어야 해요: `Battle3D.dll`, `battle3d.bundle`, `battle3d_environment.bundle`, `Audio` 폴더. 폴더가 한 겹 더 들어가(`Battle3D\Battle3D\...`) 있으면 안 돼요.
- BepInEx는 **6.0.0-be.692 (Unity Mono)** 여야 해요. 5.x 버전이나 IL2CPP 빌드에서는 안 돼요.
- 다른 모드를 전부 `BepInEx\plugins`에서 잠시 빼고 이 모드만 켜 보세요. 그러면 되는데 다른 모드와 같이 켜면 안 된다면 어떤 모드와 같이 썼는지 알려 주세요.
- 압축을 풀 때 윈도우가 파일을 막는 경우가 있어요. zip 파일 속성에서 *차단 해제*를 체크한 뒤 다시 풀어 보세요. 백신이 `Battle3D.dll`을 격리했는지도 확인하세요.

**모드는 켜졌는데 전투가 3D로 안 바뀌어요**
- `F4` 설정 패널에서 3D 전투가 켜져 있는지 확인하세요. 설정 파일(`BepInEx\config\mortal.battle3d.cfg`)의 `[General] Enabled` 와 `ExcludedBattles` 도 확인하세요.
- 아직 3D로 만들지 않은 전투는 원본 그대로 나와요.
- 로그에 `Battle 3D` 와 함께 오류(`Exception`)가 있으면 그 줄을 알려 주세요.

**`file ... is corrupted! Position out of bounds` 같은 오류가 나고 꺼져요**
- `battle3d.bundle` 또는 `battle3d_environment.bundle` 이 덜 받아졌거나 게임이 켜진 채로 덮어쓰였을 때 나요. 게임을 완전히 끄고 zip을 다시 받아 다시 덮어쓰세요. (파일 크기: 번들 2개는 각각 약 70 MB, 56 MB예요.)

**소리가 안 나요 / 너무 커요**
- `F4` 설정 패널의 소리 항목에서 조절하세요. `Audio` 폴더가 `Battle3D` 폴더 안에 있는지도 확인하세요.

**화면이 너무 어둡거나 느려요**
- `F4` 패널의 그래픽 항목에서 툰 셰이딩·외곽선을 끄거나, 설정 파일에서 `[Graphics] PostProcessing` 을 `false` 로 바꿔 보세요.

**설정을 처음으로 되돌리고 싶어요**
- 게임을 끄고 `BepInEx\config\mortal.battle3d.cfg` 를 지우세요. 다음 실행 때 기본값으로 새로 만들어져요.

**게임이 업데이트된 뒤 오류가 나요**
- 게임 업데이트로 원본 코드가 바뀌면 모드가 안 맞을 수 있어요. 최신 릴리즈가 있는지 확인하고, 없다면 Issues에 로그와 함께 알려 주세요.

## 라이선스 / 이용 안내
Copyright © texp0323. All rights reserved.
개인적인 사용은 자유예요. 수정, 디컴파일해서 만든 파생물, 재배포(다른 사이트에 zip 올리기 등)는 허락 없이 할 수 없어요.
이 모드는 비공식이며 게임 제작사와 관련이 없어요. 게임 원본 데이터는 파일로 포함하지 않고 실행 중에 읽어 써요.
