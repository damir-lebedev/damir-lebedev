<p align="center">
  <img src="docs/images/flags/gb.svg" height="14" alt="">&nbsp;<b>English</b>
  ·
  <a href="docs/i18n/ru/README.md"><img src="docs/images/flags/ru.svg" height="14" alt="">&nbsp;Русский</a>
  ·
  <a href="docs/i18n/zh-CN/README.md"><img src="docs/images/flags/cn.svg" height="14" alt="">&nbsp;中文</a>
  ·
  <a href="docs/i18n/es/README.md"><img src="docs/images/flags/es.svg" height="14" alt="">&nbsp;Español</a>
  ·
  <a href="docs/i18n/hi/README.md"><img src="docs/images/flags/in.svg" height="14" alt="">&nbsp;हिन्दी</a>
  ·
  <a href="docs/i18n/ar/README.md"><img src="docs/images/flags/sa.svg" height="14" alt="">&nbsp;العربية</a>
  ·
  <a href="docs/i18n/pt-BR/README.md"><img src="docs/images/flags/br.svg" height="14" alt="">&nbsp;Português</a>
  ·
  <a href="docs/i18n/fr/README.md"><img src="docs/images/flags/fr.svg" height="14" alt="">&nbsp;Français</a>
  ·
  <a href="docs/i18n/de/README.md"><img src="docs/images/flags/de.svg" height="14" alt="">&nbsp;Deutsch</a>
  ·
  <a href="docs/i18n/ja/README.md"><img src="docs/images/flags/jp.svg" height="14" alt="">&nbsp;日本語</a>
  ·
  <a href="docs/i18n/ko/README.md"><img src="docs/images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="docs/images/banner.svg" alt="Damir Lebedev — from RC airplanes to orbit" width="100%">
</p>

<h1 align="center">Hi, I'm Damir 👋</h1>

<p align="center">
  <b>Reliable, modular, mission-critical embedded systems<br>in modern C++ and RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

<p align="center" dir="ltr">
  ⚙️ <b>1</b> firmware · <b>2</b> MCUs
  &nbsp;·&nbsp;
  ⏱️ <b>500 Hz</b> control loop
  &nbsp;·&nbsp;
  🧪 <b>387</b> tests
  &nbsp;·&nbsp;
  📊 <b>98%</b> coverage
</p>

<p align="center">🌍 <b>Open to remote roles worldwide</b> &nbsp;·&nbsp; 📧 <a href="mailto:dam.lebedev2018@yandex.ru">dam.lebedev2018@yandex.ru</a></p>

I design hardware-agnostic embedded systems from scratch — and prove them with tests.

---

## 🚀 Flagship project — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

An open-source flight controller and autopilot for RC airplanes. The same firmware runs on **ESP32-S3** and **STM32H743**.

| | |
|---|---|
| ✈️ **Autopilot** | 12 flight modes: stabilize, altitude hold, cruise, loiter, return-to-home, auto take-off and landing, thermal soaring, rescue |
| 🛡️ **Failsafe** | Strict priority order (link loss > ARM > mode > throttle): no mode can push throttle past ARM; the plane returns home on its own when the radio goes silent |
| 🧱 **Architecture** | Header-only C++, HAL as the only layer that knows the MCU, sensor drivers independent of I2C/SPI, no dynamic memory in the control loop |
| ⏱️ **Real time** | 500 Hz control loop, dual-core tasks on ESP32, FreeRTOS on STM32 |
| 📡 **Telemetry** | Web dashboard on board, MAVLink to QGroundControl / Mission Planner (frames checked byte for byte against `pymavlink`) |
| 📼 **Black box** | Every flight recorded at 500 Hz: to on-board flash (ESP32-S3) or an SD card (STM32), decoded to CSV by a Python tool |
| 🧪 **Verification** | 387 automated tests, 98% line coverage, closed-loop flight simulations of every mode, 24 board × sensor builds with zero warnings |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Radio lost: the plane flies home and circles" width="480"><br>
  <sub>Radio switched off — the plane returns home on its own. Closed-loop simulation of the real firmware.</sub>
</p>

### 📍 Where it really stands

| | |
|---|---|
| ✈️ **First prototype, manual mode** | Flown |
| 🧪 **Autopilot** | Verified on the bench, in tests and in simulation — waiting for flight trials |
| 🔌 **STM32H743 board** | Already [driven from a transmitter](https://t.me/lisnmylife/420) (iBUS, ARM, servos and motor) — sensors come next |

I keep the status table in the OpenPlane README honest on purpose: what flew, what ran on a bench, what is only tested.

Also: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — a FlySky FS-i6 as a USB joystick for flight simulators.

---

## 🛠️ Tech stack

| | |
|---|---|
| **Languages** | C++ (modern standards, OOP), C, Python (tools, automation) |
| **MCUs** | ESP32 (S3, C3, classic), STM32H743 |
| **RTOS & frameworks** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Architecture** | SOLID, dependency injection, HAL, event-driven design, fail-safe state machines |
| **Interfaces** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Quality** | Unity test framework, native (host) test builds, gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Tools** | Git, Linux, Wi-Fi / HTTP telemetry, KiCad |

---

## 🧭 How I build

| | |
|---|---|
| 🛡️ **Fail-safe first** | Failure behaviour and state machines are designed before features, not after. |
| 🧪 **Proven, not promised** | Host builds, closed-loop simulation, coverage, static analysis and CI on every change. |
| 🤝 **AI-assisted, human-owned** | AI helps me move faster; the architecture and the verification stay in my own hands. |

---

## 🌌 Ad astra

My goal is simple: **I want to work on things that go to space.** Today that is RC airplanes and UAV autopilots; the direction is aerospace — flight software that has to work the first time, with nobody around to press reset.

Space belongs to no single country, so this profile doesn't speak a single language either — pick yours at the top.

---

## 💼 Looking for

**Mid-level / strong Junior+ Embedded Firmware Engineer** or **Software Architect** — remote roles anywhere in the world: robotics, UAVs, aerospace and space systems, IoT, high-load hardware.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane on GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
