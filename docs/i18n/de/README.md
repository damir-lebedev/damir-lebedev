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
  <img src="../../images/flags/de.svg" height="14" alt="">&nbsp;<b>Deutsch</b>
  ·
  <a href="../ja/README.md"><img src="../../images/flags/jp.svg" height="14" alt="">&nbsp;日本語</a>
  ·
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev — von RC-Flugzeugen bis zur Umlaufbahn" width="100%">
</p>

<h1 align="center">Hi, ich bin Damir 👋</h1>

<p align="center">
  <b>Zuverlässige, modulare, missionskritische Embedded-Systeme<br>in modernem C++ und RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

Ich entwerfe hardwareunabhängige Embedded-Systeme von Grund auf — und beweise sie mit Tests.

---

## 🌌 Ad astra

Mein Ziel ist einfach: **Ich will an Dingen arbeiten, die ins All fliegen.** Heute sind das RC-Flugzeuge und UAV-Autopiloten; die Richtung ist Luft- und Raumfahrt — Flugsoftware, die auf Anhieb funktionieren muss, ohne dass jemand in der Nähe den Reset-Knopf drücken kann.

Der Weltraum gehört keinem einzelnen Land, deshalb spricht auch dieses Profil nicht nur eine Sprache — such dir oben deine aus.

---

## 🧭 Wie ich baue

| | |
|---|---|
| 🧱 **Hardwareunabhängig** | Eine schlanke HAL ist die einzige Schicht, die den MCU kennt. Treiber wissen nicht, an welchem Bus sie hängen. |
| 🛡️ **Ausfallsicherheit zuerst** | Fehlerverhalten und Zustandsautomaten werden vor den Features entworfen, nicht danach. |
| ⏱️ **Deterministisch** | Regelschleifen mit fester Frequenz, kein dynamischer Speicher, wo es darauf ankommt. |
| 🧪 **Bewiesen, nicht versprochen** | Host-Builds, Closed-Loop-Simulation, Coverage, statische Analyse und CI bei jeder Änderung. |
| 🤝 **KI hilft, der Mensch entscheidet** | KI macht mich schneller; Architektur und Verifikation bleiben in meiner Hand. |

---

## 🚀 Hauptprojekt — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

Ein Open-Source-Flugcontroller und Autopilot für RC-Flugzeuge. Dieselbe Firmware läuft auf **ESP32-S3** und **STM32H743**.

| | |
|---|---|
| ✈️ **Autopilot** | 12 Flugmodi: Stabilize, Höhenhaltung, Cruise, Loiter, Rückkehr zum Startpunkt, automatischer Start und Landung, Thermikflug, Rettung |
| 🛡️ **Failsafe** | Strikte Prioritätsreihenfolge (Verbindungsverlust > ARM > Modus > Gas): Kein Modus kann das Gas über ARM hinaus schieben; wenn der Funk verstummt, fliegt das Flugzeug von selbst nach Hause |
| 🧱 **Architektur** | Header-only-C++, die HAL ist die einzige Schicht, die den MCU kennt, Sensortreiber unabhängig von I2C/SPI, kein dynamischer Speicher in der Regelschleife |
| ⏱️ **Echtzeit** | 500-Hz-Regelschleife, Dual-Core-Tasks auf dem ESP32, FreeRTOS auf dem STM32 |
| 📡 **Telemetrie** | Web-Dashboard an Bord, MAVLink zu QGroundControl / Mission Planner (Frames Byte für Byte gegen `pymavlink` geprüft) |
| 📼 **Black Box** | Jeder Flug wird mit 500 Hz aufgezeichnet: in den On-Board-Flash (ESP32-S3) oder auf eine SD-Karte (STM32) und von einem Python-Tool nach CSV dekodiert |
| 🧪 **Verifikation** | 387 automatisierte Tests, 98 % Zeilenabdeckung, Closed-Loop-Flugsimulationen jedes Modus, 24 Board-×-Sensor-Builds ohne eine einzige Warnung |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Funkverbindung verloren: Das Flugzeug fliegt nach Hause und kreist" width="480"><br>
  <sub>Funk ausgeschaltet — das Flugzeug fliegt von selbst nach Hause. Closed-Loop-Simulation der echten Firmware.</sub>
</p>

### 📍 Wo es wirklich steht

| | |
|---|---|
| ✈️ **Erster Prototyp, manueller Modus** | Ist geflogen |
| 🧪 **Autopilot** | Auf dem Prüfstand, in Tests und in der Simulation verifiziert — wartet auf Flugtests |
| 🔌 **STM32H743-Board** | Wird schon [per Sender gesteuert](https://t.me/lisnmylife/420) (iBUS, ARM, Servos und Motor) — Sensoren folgen als Nächstes |

Die Statustabelle im OpenPlane-README halte ich bewusst ehrlich: was geflogen ist, was auf dem Prüfstand lief und was nur getestet ist.

Außerdem: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — ein FlySky FS-i6 als USB-Joystick für Flugsimulatoren.

---

## 🛠️ Tech-Stack

| | |
|---|---|
| **Sprachen** | C++ (moderne Standards, OOP), C, Python (Tools, Automatisierung) |
| **MCUs** | ESP32 (S3, C3, Classic), STM32H743 |
| **RTOS & Frameworks** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Architektur** | SOLID, Dependency Injection, HAL, ereignisgesteuertes Design, ausfallsichere Zustandsautomaten |
| **Schnittstellen** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Qualität** | Unity, native (Host-)Test-Builds, gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Werkzeuge** | Git, Linux, Wi-Fi-/HTTP-Telemetrie, KiCad |

---

## 💼 Ich suche

**Embedded Firmware Engineer (Mid-Level / starker Junior+)** oder **Software Architect** — Remote-Stellen weltweit: Robotik, UAVs, Luft- und Raumfahrt, IoT, hochbelastete Hardware.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane auf GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
