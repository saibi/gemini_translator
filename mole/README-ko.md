<div align="center">
  <h1>Mole</h1>
  <p><em>Mac을 딥 클린하고 최적화하세요.</em></p>
</div>

<p align="center">
  <a href="https://github.com/tw93/mole/stargazers"><img src="https://img.shields.io/github/stars/tw93/mole?style=flat-square" alt="Stars"></a>
  <a href="https://github.com/tw93/mole/releases"><img src="https://img.shields.io/github/v/tag/tw93/mole?label=version&style=flat-square" alt="Version"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square" alt="License"></a>
  <a href="https://github.com/tw93/mole/commits"><img src="https://img.shields.io/github/commit-activity/m/tw93/mole?style=flat-square" alt="Commits"></a>
  <a href="https://twitter.com/HiTw93"><img src="https://img.shields.io/badge/follow-Tw93-red?style=flat-square&logo=Twitter" alt="Twitter"></a>
  <a href="https://t.me/+GclQS9ZnxyI2ODQ1"><img src="https://img.shields.io/badge/chat-Telegram-blueviolet?style=flat-square&logo=Telegram" alt="Telegram"></a>
</p>

<p align="center">
  <img src="https://cdn.tw93.fun/img/mole.jpeg" alt="Mole - 95.50GB 확보됨" width="1000" />
</p>

## 주요 기능

- **올인원 툴킷**: CleanMyMac, AppCleaner, DaisyDisk, iStat Menus의 기능을 **단일 바이너리**에 통합
- **딥 클린**: 캐시, 로그, 브라우저 잔여물을 스캔하고 제거하여 **기가바이트 단위의 공간 확보**
- **스마트 언인스톨러**: 실행 에이전트(Launch Agents), 설정 파일 및 **숨겨진 잔재**까지 앱을 철저히 제거
- **디스크 통찰**: 사용량 시각화, 대용량 파일 관리, **캐시 재구축** 및 시스템 서비스 새로고침
- **실시간 모니터링**: CPU, GPU, 메모리, 디스크, 네트워크의 실시간 통계를 제공하여 **성능 문제 진단**

## 빠른 시작

**Homebrew를 통한 설치:**

```bash
brew install mole
```

**또는 스크립트를 통한 설치:**

```bash
# 선택적 인자: main 브랜치 코드는 -s latest, 특정 버전은 -s 1.17.0
curl -fsSL https://raw.githubusercontent.com/tw93/mole/main/install.sh | bash
```

**Windows:** Mole은 macOS용으로 설계되었지만, 사용자 요청에 따라 실험적인 Windows 버전을 제공합니다. 초기 사용자만 [windows 브랜치](https://github.com/tw93/Mole/tree/windows)를 확인하세요.

**실행:**

```bash
mo                           # 대화형 메뉴
mo clean                     # 딥 클린 실행
mo uninstall                 # 앱 및 잔여물 제거
mo optimize                  # 캐시 및 서비스 새로고침
mo analyze                   # 시각적 디스크 탐색기
mo status                    # 실시간 시스템 상태 대시보드
mo purge                     # 프로젝트 빌드 아티팩트 정리
mo installer                 # 설치 파일 검색 및 제거

mo touchid                   # sudo를 위한 Touch ID 구성
mo completion                # 쉘 탭 완성 설정
mo update                    # Mole 업데이트
mo remove                    # 시스템에서 Mole 제거
mo --help                    # 도움말 표시
mo --version                 # 설치된 버전 표시

mo clean --dry-run           # 정리 계획 미리보기
mo clean --whitelist         # 보호된 캐시 관리
mo clean --dry-run --debug   # 위험 수준 및 파일 정보를 포함한 상세 미리보기

mo optimize --dry-run        # 최적화 작업 미리보기
mo optimize --debug          # 상세 작업 로그와 함께 실행
mo optimize --whitelist      # 보호된 최적화 규칙 관리
mo purge --paths             # 프로젝트 스캔 디렉토리 구성
```

## 팁

- **터미널**: iTerm2는 알려진 호환성 문제가 있습니다. Alacritty, kitty, WezTerm, Ghostty 또는 Warp 사용을 권장합니다.
- **안전**: 엄격한 보호 기능을 갖추고 설계되었습니다. [보안 감사(Security Audit)](SECURITY_AUDIT.md)를 확인하세요. `mo clean --dry-run`으로 변경 사항을 미리 볼 수 있습니다.
- **주의 사항**: 설계상 안전하지만, 파일 삭제는 영구적입니다. 작업을 신중하게 검토하세요.
- **디버그 모드**: 상세 로그를 보려면 `--debug`를 사용하세요(예: `mo clean --debug`). `--dry-run`과 조합하면 위험 수준과 파일 상세 정보를 포함한 종합적인 미리보기가 가능합니다.
- **작업 로그**: 문제 해결을 위해 파일 작업 내용이 `~/.config/mole/operations.log`에 기록됩니다. `MO_NO_OPLOG=1`로 비활성화할 수 있습니다.
- **탐색**: 화살표 키와 Vim 바인딩(`h/j/k/l`)을 지원합니다.
- **상태 단축키**: `mo status`에서 `k`를 눌러 고양이 표시 여부를 전환하고 설정을 저장할 수 있으며, `q`를 눌러 종료합니다.
- **구성**: Touch ID sudo를 위해 `mo touchid`를, 쉘 탭 완성을 위해 `mo completion`을, 보호된 경로 관리를 위해 `mo clean --whitelist`를 실행하세요.

## 상세 기능

### 시스템 딥 클린

```bash
$ mo clean

캐시 디렉토리 스캔 중...

  ✓ 사용자 앱 캐시                                           45.2GB
  ✓ 브라우저 캐시 (Chrome, Safari, Firefox)                  10.5GB
  ✓ 개발자 도구 (Xcode, Node.js, npm)                        23.3GB
  ✓ 시스템 로그 및 임시 파일                                  3.8GB
  ✓ 앱 전용 캐시 (Spotify, Dropbox, Slack)                   8.4GB
  ✓ 휴지통                                                   12.3GB

====================================================================
확보된 공간: 95.5GB | 현재 여유 공간: 223.5GB
====================================================================
```

### 스마트 앱 언인스톨러

```bash
$ mo uninstall

제거할 앱 선택
═══════════════════════════
▶ ☑ Photoshop 2024            (4.2G) | 오래됨
  ☐ IntelliJ IDEA             (2.8G) | 최근
  ☐ Premiere Pro              (3.4G) | 최근

제거 중: Photoshop 2024

  ✓ 애플리케이션 제거 완료
  ✓ 12개 위치에서 52개의 관련 파일 정리 완료
    - Application Support, Caches, Preferences
    - Logs, WebKit storage, Cookies
    - Extensions, Plugins, Launch daemons

====================================================================
확보된 공간: 12.8GB
====================================================================
```

### 시스템 최적화

```bash
$ mo optimize

시스템: 5/32 GB RAM | 333/460 GB 디스크 (72%) | 업타임 6일

  ✓ 시스템 데이터베이스 재구축 및 캐시 정리
  ✓ 네트워크 서비스 재설정
  ✓ Finder 및 Dock 새로고침
  ✓ 진단 및 크래시 로그 정리
  ✓ 스왑 파일 제거 및 동적 페이저 재시작
  ✓ 실행 서비스(Launch Services) 및 Spotlight 인덱스 재구축

====================================================================
시스템 최적화 완료
====================================================================

특정 최적화 항목을 제외하려면 `mo optimize --whitelist`를 사용하세요.
```

### 디스크 공간 분석기

```bash
$ mo analyze

디스크 분석  ~/Documents  |  합계: 156.8GB

 ▶  1. ███████████████████  48.2%  |  📁 Library                     75.4GB  >6개월
    2. ██████████░░░░░░░░░  22.1%  |  📁 Downloads                   34.6GB
    3. ████░░░░░░░░░░░░░░░  14.3%  |  📁 Movies                      22.4GB
    4. ███░░░░░░░░░░░░░░░░  10.8%  |  📁 Documents                   16.9GB
    5. ██░░░░░░░░░░░░░░░░░   5.2%  |  📄 backup_2023.zip              8.2GB

  ↑↓←→ 탐색  |  O 열기  |  F 보기  |  ⌫ 삭제  |  L 대용량 파일  |  Q 종료
```

### 실시간 시스템 상태

시스템 헬스 스코어, 하드웨어 정보 및 성능 지표를 보여주는 실시간 대시보드입니다.

```bash
$ mo status

Mole 상태  헬스 ● 92  MacBook Pro · M4 Pro · 32GB · macOS 14.5

⚙ CPU                                    ▦ 메모리
전체    ████████████░░░░░░░  45.2%       사용 중  ███████████░░░░░░░  58.4%
부하    0.82 / 1.05 / 1.23 (8 코어)      전체    14.2 / 24.0 GB
코어 1  ███████████████░░░░  78.3%       여유    ████████░░░░░░░░░░  41.6%
코어 2  ████████████░░░░░░░  62.1%       사용 가능 9.8 GB

▤ 디스크                                 ⚡ 전원
사용 중  █████████████░░░░░░  67.2%       레벨    ██████████████████  100%
여유    156.3 GB                         상태    충전됨
읽기    ▮▯▯▯▯  2.1 MB/s                  상태    정상 · 423 사이클
쓰기    ▮▮▮▯▯  18.3 MB/s                 온도    58°C · 1200 RPM

⇅ 네트워크                                ▶ 프로세스
다운    ▁▁█▂▁▁▁▁▁▁▁▁▇▆▅▂  0.54 MB/s      Code       ▮▮▮▮▯  42.1%
업      ▄▄▄▃▃▃▄▆▆▇█▁▁▁▁▁  0.02 MB/s      Chrome     ▮▮▮▯▯  28.3%
프록시   HTTP · 192.168.1.100             Terminal   ▮▯▯▯▯  12.5%
```

헬스 스코어는 CPU, 메모리, 디스크, 온도 및 I/O 부하를 기반으로 하며, 범위에 따라 색상으로 표시됩니다.

### 프로젝트 아티팩트 제거

디스크 공간을 확보하기 위해 프로젝트에서 오래된 빌드 아티팩트(`node_modules`, `target`, `build`, `dist` 등)를 정리합니다.

```bash
mo purge

정리할 카테고리 선택 - 18.5GB (8개 선택됨)

➤ ● my-react-app       3.2GB | node_modules
  ● old-project        2.8GB | node_modules
  ● rust-app           4.1GB | target
  ● next-blog          1.9GB | node_modules
  ○ current-work       856MB | node_modules  | 최근
  ● django-api         2.3GB | venv
  ● vue-dashboard      1.7GB | node_modules
  ● backend-service    2.5GB | node_modules
```

> **주의:** 선택한 아티팩트가 영구적으로 삭제됩니다. 확인 전에 신중하게 검토하세요. 7일 미만의 최근 프로젝트는 표시가 되며 기본적으로 선택되지 않습니다.

<details>
<summary><strong>사용자 정의 스캔 경로</strong></summary>

`mo purge --paths`를 실행하여 스캔할 디렉토리를 구성하거나, `~/.config/mole/purge_paths`를 직접 편집하세요:

```shell
~/Documents/MyProjects
~/Work/ClientA
~/Work/ClientB
```

사용자 정의 경로가 설정되면 해당 디렉토리만 스캔합니다. 그렇지 않으면 기본적으로 `~/Projects`, `~/GitHub`, `~/dev` 등을 스캔합니다.

</details>

### 설치 파일 정리

다운로드, 데스크탑, Homebrew 캐시, iCloud, Mail 등에 흩어져 있는 대용량 설치 파일을 찾아 제거합니다. 각 파일은 출처가 라벨로 표시되어 어디에 공간이 낭비되고 있는지 알 수 있습니다.

```bash
mo installer

제거할 설치 파일 선택 - 3.8GB (5개 선택됨)

➤ ● Photoshop_2024.dmg     1.2GB | 다운로드
  ● IntelliJ_IDEA.dmg       850.6MB | 다운로드
  ● Illustrator_Setup.pkg   920.4MB | 다운로드
  ● PyCharm_Pro.dmg         640.5MB | Homebrew
  ● Acrobat_Reader.dmg      220.4MB | 다운로드
  ○ AppCode_Legacy.zip      410.6MB | 다운로드
```

## 빠른 실행기

Raycast 또는 Alfred에서 Mole 명령을 즉시 실행하세요:

```bash
curl -fsSL https://raw.githubusercontent.com/tw93/Mole/main/scripts/setup-quick-launchers.sh | bash
```

5개의 명령어가 추가됩니다: `clean`, `uninstall`, `optimize`, `analyze`, `status`.

### Raycast 설정

위의 스크립트를 실행한 후, **Raycast에서 다음 단계를 완료하세요**:

1. Raycast 설정 열기 (⌘ + ,)
2. **Extensions** → **Script Commands**로 이동
3. **"Add Script Directory"** (또는 **"+"**) 클릭
4. 경로 추가: `~/Library/Application Support/Raycast/script-commands`
5. Raycast에서 검색: **"Reload Script Directories"** 실행
6. 완료! 이제 `mole`, `clean` 또는 `optimize`를 검색하여 명령어를 사용하세요.

> **참고**: 스크립트가 명령어를 자동으로 생성하지만, Raycast에서는 스크립트 디렉토리를 수동으로 추가해야 합니다. 이는 한 번만 설정하면 됩니다.

### 터미널 감지

Mole은 터미널 앱(Warp, Ghostty, Alacritty, Kitty, WezTerm 등)을 자동으로 감지합니다. 재정의하려면 환경 변수에 `MO_LAUNCHER_APP=<이름>`을 설정하세요.

## 커뮤니티의 사랑

Mole 구축을 도와주신 모든 기여자분들께 큰 감사를 드립니다. 그들을 팔로우해 주세요! ❤️

<a href="https://github.com/tw93/Mole/graphs/contributors">
  <img src="./CONTRIBUTORS.svg?v=2" width="1000" />
</a>

<br/><br/>
X에서 Mole을 공유해 주신 사용자들의 실제 피드백입니다.

<img src="https://cdn.tw93.fun/pic/lovemole.jpeg" alt="Mole에 대한 커뮤니티 피드백" width="1000" />

## 지원

- Mole이 도움이 되었다면, 저장소에 스타를 눌러주시거나 친구들에게 [공유](https://twitter.com/intent/tweet?url=https://github.com/tw93/Mole&text=Mole%20-%20Deep%20clean%20and%20optimize%20your%20Mac.)해 주세요.
- 아이디어가 있거나 버그를 발견하셨나요? [기여 가이드(Contributing Guide)](CONTRIBUTING.md)를 확인하고 이슈나 PR을 열어주세요.
- Mole이 마음에 드시나요? <a href="https://miaoyan.app/cats.html?name=Mole" target="_blank">Tw93에게 콜라 한 잔 사주기</a>로 프로젝트를 지원해 주세요! 🥤 후원자 명단은 아래에 있습니다.

<a href="https://miaoyan.app/cats.html?name=Mole"><img src="https://miaoyan.app/assets/sponsors.svg" width="1000" loading="lazy" /></a>

## 라이선스

MIT 라이선스이며, 자유롭게 즐기고 오픈 소스에 참여하세요.
