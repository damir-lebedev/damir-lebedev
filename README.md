<h1 align="center">Hi, I'm Damir 👋</h1>

<p align="center">
  <b>Firmware Engineer · Software Architect</b><br>
  Reliable, modular, mission-critical embedded systems in modern C++ and RTOS.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

I design hardware-agnostic systems from scratch: a thin HAL under everything, drivers that don't know which bus they sit on, and tests that prove it. I work with AI-assisted development and keep the architecture and the verification in my own hands.

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

**Where it really stands:** the first prototype flew in manual mode; the autopilot is verified on the bench, in tests and in simulation, and is waiting for flight trials. The STM32H743 board is already [driven from a transmitter](https://t.me/lisnmylife/420) (iBUS, ARM, servos and motor) — sensors come next.

I keep the status table in that README honest on purpose: what flew, what ran on a bench, what is only tested.

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

## 💼 Looking for

**Mid-level / strong Junior+ Embedded Firmware Engineer** or **Software Architect** — remote roles in robotics, UAVs, aerospace, IoT or high-load hardware systems.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane on GitHub](https://github.com/damir-lebedev/OpenPlaneProject)
