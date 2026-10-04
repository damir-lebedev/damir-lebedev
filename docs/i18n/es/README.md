<p align="center">
  <a href="../../../README.md"><img src="../../images/flags/gb.svg" height="14" alt="">&nbsp;English</a>
  ·
  <a href="../ru/README.md"><img src="../../images/flags/ru.svg" height="14" alt="">&nbsp;Русский</a>
  ·
  <a href="../zh-CN/README.md"><img src="../../images/flags/cn.svg" height="14" alt="">&nbsp;中文</a>
  ·
  <img src="../../images/flags/es.svg" height="14" alt="">&nbsp;<b>Español</b>
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
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev — de los aviones RC a la órbita" width="100%">
</p>

<h1 align="center">Hola, soy Damir 👋</h1>

<p align="center">
  <b>Sistemas embebidos fiables, modulares y de misión crítica<br>en C++ moderno y RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

Diseño desde cero sistemas embebidos independientes del hardware — y los demuestro con tests.

---

## 🌌 Ad astra

Mi objetivo es simple: **quiero trabajar en cosas que van al espacio.** Hoy son aviones RC y autopilotos para UAV; el rumbo es el sector aeroespacial: software de vuelo que tiene que funcionar a la primera, sin nadie cerca que pueda pulsar reset.

El espacio no pertenece a un solo país, así que este perfil tampoco habla un solo idioma: elige el tuyo arriba.

---

## 🧭 Cómo construyo

| | |
|---|---|
| 🧱 **Independiente del hardware** | Una HAL fina es la única capa que conoce el MCU. Los drivers no saben en qué bus están. |
| 🛡️ **Primero la tolerancia a fallos** | El comportamiento ante fallos y las máquinas de estados se diseñan antes que las funciones, no después. |
| ⏱️ **Determinista** | Bucles de control a frecuencia fija, sin memoria dinámica donde importa. |
| 🧪 **Demostrado, no prometido** | Compilaciones en host, simulación en lazo cerrado, cobertura, análisis estático y CI en cada cambio. |
| 🤝 **IA como ayuda, el control es mío** | La IA me hace más rápido; la arquitectura y la verificación siguen en mis manos. |

---

## 🚀 Proyecto principal — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

Un controlador de vuelo y autopiloto de código abierto para aviones RC. El mismo firmware funciona en **ESP32-S3** y **STM32H743**.

| | |
|---|---|
| ✈️ **Autopiloto** | 12 modos de vuelo: estabilizado, mantener altitud, crucero, loiter, regreso a casa, despegue y aterrizaje automáticos, vuelo térmico, rescate |
| 🛡️ **Failsafe** | Orden de prioridad estricto (pérdida de enlace > ARM > modo > gas): ningún modo puede subir el gas por encima de ARM; si la radio se queda en silencio, el avión vuelve solo a casa |
| 🧱 **Arquitectura** | C++ header-only, la HAL es la única capa que conoce el MCU, drivers de sensores independientes de I2C/SPI, sin memoria dinámica en el bucle de control |
| ⏱️ **Tiempo real** | Bucle de control a 500 Hz, tareas en doble núcleo en ESP32, FreeRTOS en STM32 |
| 📡 **Telemetría** | Panel web a bordo, MAVLink hacia QGroundControl / Mission Planner (tramas verificadas byte a byte con `pymavlink`) |
| 📼 **Caja negra** | Cada vuelo se graba a 500 Hz: en la flash interna (ESP32-S3) o en una tarjeta SD (STM32) y se decodifica a CSV con una herramienta Python |
| 🧪 **Verificación** | 387 tests automáticos, 98 % de cobertura de líneas, simulaciones de vuelo en lazo cerrado de cada modo, 24 compilaciones placa × sensor sin ninguna advertencia |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Radio perdida: el avión vuelve a casa y da vueltas" width="480"><br>
  <sub>Radio apagada: el avión vuelve solo a casa. Simulación en lazo cerrado del firmware real.</sub>
</p>

### 📍 Dónde está realmente

| | |
|---|---|
| ✈️ **Primer prototipo, modo manual** | Voló |
| 🧪 **Autopiloto** | Verificado en banco, en tests y en simulación — a la espera de pruebas en vuelo |
| 🔌 **Placa STM32H743** | Ya [se controla desde un transmisor](https://t.me/lisnmylife/420) (iBUS, ARM, servos y motor) — los sensores vienen después |

Mantengo la tabla de estado del README de OpenPlane honesta a propósito: lo que voló, lo que funcionó en banco y lo que solo está probado.

También: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — un FlySky FS-i6 como joystick USB para simuladores de vuelo.

---

## 🛠️ Stack tecnológico

| | |
|---|---|
| **Lenguajes** | C++ (estándares modernos, POO), C, Python (herramientas, automatización) |
| **MCU** | ESP32 (S3, C3, clásico), STM32H743 |
| **RTOS y frameworks** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Arquitectura** | SOLID, inyección de dependencias, HAL, diseño orientado a eventos, máquinas de estados a prueba de fallos |
| **Interfaces** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Calidad** | Unity, compilaciones de test nativas (host), gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Herramientas** | Git, Linux, telemetría Wi-Fi / HTTP, KiCad |

---

## 💼 Busco

**Embedded Firmware Engineer de nivel medio / Junior+ sólido** o **Software Architect** — puestos remotos en cualquier parte del mundo: robótica, UAV, aeroespacial y sistemas espaciales, IoT, hardware de alta carga.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane en GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
