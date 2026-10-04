<p align="center">
  <a href="../../../README.md"><img src="../../images/flags/gb.svg" height="14" alt="">&nbsp;English</a>
  ·
  <a href="../ru/README.md"><img src="../../images/flags/ru.svg" height="14" alt="">&nbsp;Русский</a>
  ·
  <a href="../zh-CN/README.md"><img src="../../images/flags/cn.svg" height="14" alt="">&nbsp;中文</a>
  ·
  <a href="../es/README.md"><img src="../../images/flags/es.svg" height="14" alt="">&nbsp;Español</a>
  ·
  <a href="../hi/README.md"><img src="../../images/flags/in.svg" height="14" alt="">&nbsp;हिन्दी</a>
  ·
  <a href="../ar/README.md"><img src="../../images/flags/sa.svg" height="14" alt="">&nbsp;العربية</a>
  ·
  <a href="../pt-BR/README.md"><img src="../../images/flags/br.svg" height="14" alt="">&nbsp;Português</a>
  ·
  <a href="../fr/README.md"><img src="../../images/flags/fr.svg" height="14" alt="">&nbsp;Français</a>
  ·
  <a href="../de/README.md"><img src="../../images/flags/de.svg" height="14" alt="">&nbsp;Deutsch</a>
  ·
  <a href="../ja/README.md"><img src="../../images/flags/jp.svg" height="14" alt="">&nbsp;日本語</a>
  ·
  <img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;<b>한국어</b>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev — RC 비행기에서 궤도까지" width="100%">
</p>

<h1 align="center">안녕하세요, Damir입니다 👋</h1>

<p align="center">
  <b>현대적인 C++와 RTOS로 신뢰성 높고 모듈화된 미션 크리티컬 임베디드 시스템을 만듭니다.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

<p align="center" dir="ltr">
  ⚙️ <b>1</b>개 펌웨어 · <b>2</b>종 MCU
  &nbsp;·&nbsp;
  ⏱️ <b>500 Hz</b> 제어 루프
  &nbsp;·&nbsp;
  🧪 테스트 <b>387</b>개
  &nbsp;·&nbsp;
  📊 커버리지 <b>98%</b>
</p>

<p align="center">🌍 <b>전 세계 원격 근무 가능</b> &nbsp;·&nbsp; 📧 <a href="mailto:dam.lebedev2018@yandex.ru">dam.lebedev2018@yandex.ru</a></p>

하드웨어에 종속되지 않는 임베디드 시스템을 처음부터 설계하고, 테스트로 증명합니다.

---

## 🚀 대표 프로젝트 — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

RC 비행기를 위한 오픈소스 비행 컨트롤러 겸 오토파일럿. 같은 펌웨어가 **ESP32-S3**와 **STM32H743**에서 동작합니다.

| | |
|---|---|
| ✈️ **오토파일럿** | 12가지 비행 모드: 스태빌라이즈, 고도 유지, 크루즈, 로이터, 자동 귀환, 자동 이착륙, 열상승기류 비행, 구조 |
| 🛡️ **페일세이프** | 엄격한 우선순위(링크 끊김 > ARM > 모드 > 스로틀): 어떤 모드도 스로틀을 ARM 한계 너머로 올릴 수 없으며, 무전이 끊기면 기체가 스스로 귀환합니다 |
| 🧱 **아키텍처** | 헤더 온리 C++, MCU를 아는 계층은 HAL뿐, 센서 드라이버는 I2C/SPI와 무관, 제어 루프에서 동적 메모리 사용 안 함 |
| ⏱️ **실시간** | 500 Hz 제어 루프, ESP32에서는 듀얼코어 태스크, STM32에서는 FreeRTOS |
| 📡 **텔레메트리** | 기체 탑재 웹 대시보드, QGroundControl / Mission Planner용 MAVLink(프레임을 `pymavlink`와 바이트 단위로 대조) |
| 📼 **블랙박스** | 모든 비행을 500 Hz로 기록: 온보드 플래시(ESP32-S3) 또는 SD 카드(STM32)에 저장하고 Python 도구로 CSV 변환 |
| 🧪 **검증** | 자동화 테스트 387개, 라인 커버리지 98%, 모든 모드의 폐루프 비행 시뮬레이션, 보드 × 센서 24가지 빌드 경고 0건 |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="무전 두절: 기체가 스스로 귀환해 선회합니다" width="480"><br>
  <sub>송신기를 껐더니 기체가 스스로 귀환합니다. 실제 펌웨어의 폐루프 시뮬레이션.</sub>
</p>

### 📍 실제 현황

| | |
|---|---|
| ✈️ **첫 시제기, 수동 모드** | 비행함 |
| 🧪 **오토파일럿** | 벤치, 테스트, 시뮬레이션에서 검증 완료 — 비행 시험 대기 중 |
| 🔌 **STM32H743 보드** | 이미 [송신기로 조종](https://t.me/lisnmylife/420)할 수 있습니다(iBUS, ARM, 서보, 모터) — 다음은 센서 |

OpenPlane README의 상태 표는 일부러 솔직하게 유지합니다: 날아본 것, 벤치에서 돌려본 것, 테스트만 한 것.

그 외: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — FlySky FS-i6를 비행 시뮬레이터용 USB 조이스틱으로.

---

## 🛠️ 기술 스택

| | |
|---|---|
| **언어** | C++(최신 표준, OOP), C, Python(도구, 자동화) |
| **MCU** | ESP32(S3, C3, 클래식), STM32H743 |
| **RTOS·프레임워크** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **아키텍처** | SOLID, 의존성 주입, HAL, 이벤트 기반 설계, 페일세이프 상태 머신 |
| **인터페이스** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **품질** | Unity 테스트 프레임워크, 네이티브(호스트) 테스트 빌드, gcovr, cppcheck, clang-tidy, GitHub Actions |
| **도구** | Git, Linux, Wi-Fi / HTTP 텔레메트리, KiCad |

---

## 🧭 만드는 방식

| | |
|---|---|
| 🛡️ **페일세이프 우선** | 장애 시 동작과 상태 머신은 기능보다 먼저 설계합니다. |
| 🧪 **약속이 아닌 증명** | 모든 변경마다 호스트 빌드, 폐루프 시뮬레이션, 커버리지, 정적 분석, CI. |
| 🤝 **AI는 보조, 결정은 사람이** | AI로 더 빠르게 일하되, 아키텍처와 검증은 제 손에 둡니다. |

---

## 🌌 Ad astra

제 목표는 단순합니다. **우주로 가는 것을 만들고 싶습니다.** 지금은 RC 비행기와 UAV 오토파일럿이지만, 향하는 곳은 항공우주입니다 — 단번에 제대로 동작해야 하고, 리셋 버튼을 눌러 줄 사람이 곁에 없는 비행 소프트웨어.

우주는 어느 한 나라의 것이 아니므로, 이 프로필도 한 가지 언어로만 말하지 않습니다 — 위에서 원하는 언어를 골라 주세요.

---

## 💼 찾고 있는 자리

**미들 레벨 / 탄탄한 주니어+ 임베디드 펌웨어 엔지니어** 또는 **소프트웨어 아키텍트** — 전 세계 어디서든 가능한 원격 포지션: 로보틱스, UAV, 항공우주 및 우주 시스템, IoT, 고부하 하드웨어.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [GitHub의 OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
