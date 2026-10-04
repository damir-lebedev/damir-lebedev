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
  <img src="../../images/flags/br.svg" height="14" alt="">&nbsp;<b>Português</b>
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
  <img src="../../images/banner.svg" alt="Damir Lebedev — de aviões RC à órbita" width="100%">
</p>

<h1 align="center">Olá, eu sou o Damir 👋</h1>

<p align="center">
  <b>Sistemas embarcados confiáveis, modulares e de missão crítica<br>em C++ moderno e RTOS.</b>
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
  ⏱️ laço de controle a <b>500 Hz</b>
  &nbsp;·&nbsp;
  🧪 <b>387</b> testes
  &nbsp;·&nbsp;
  📊 <b>98%</b> de cobertura
</p>

<p align="center">🌍 <b>Aberto a vagas remotas em qualquer lugar do mundo</b> &nbsp;·&nbsp; 📧 <a href="mailto:dam.lebedev2018@yandex.ru">dam.lebedev2018@yandex.ru</a></p>

Projeto do zero sistemas embarcados independentes de hardware — e comprovo tudo com testes.

---

## 🚀 Projeto principal — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

Um controlador de voo e piloto automático de código aberto para aviões RC. O mesmo firmware roda em **ESP32-S3** e **STM32H743**.

| | |
|---|---|
| ✈️ **Piloto automático** | 12 modos de voo: estabilizado, manter altitude, cruzeiro, loiter, retorno para casa, decolagem e pouso automáticos, voo em térmicas, resgate |
| 🛡️ **Failsafe** | Ordem de prioridade estrita (perda de link > ARM > modo > acelerador): nenhum modo consegue passar o acelerador além do ARM; se o rádio ficar mudo, o avião volta para casa sozinho |
| 🧱 **Arquitetura** | C++ header-only, a HAL é a única camada que conhece o MCU, drivers de sensores independentes de I2C/SPI, sem memória dinâmica no laço de controle |
| ⏱️ **Tempo real** | Laço de controle a 500 Hz, tarefas em dois núcleos no ESP32, FreeRTOS no STM32 |
| 📡 **Telemetria** | Painel web a bordo, MAVLink para QGroundControl / Mission Planner (quadros conferidos byte a byte com o `pymavlink`) |
| 📼 **Caixa-preta** | Todo voo é gravado a 500 Hz: na flash interna (ESP32-S3) ou em um cartão SD (STM32) e decodificado para CSV por uma ferramenta Python |
| 🧪 **Verificação** | 387 testes automatizados, 98% de cobertura de linhas, simulações de voo em malha fechada de cada modo, 24 builds placa × sensor sem nenhum aviso |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Rádio perdido: o avião volta para casa e circula" width="480"><br>
  <sub>Rádio desligado — o avião volta para casa sozinho. Simulação em malha fechada do firmware real.</sub>
</p>

### 📍 Onde realmente está

| | |
|---|---|
| ✈️ **Primeiro protótipo, modo manual** | Voou |
| 🧪 **Piloto automático** | Verificado na bancada, em testes e em simulação — aguardando ensaios em voo |
| 🔌 **Placa STM32H743** | Já [é controlada por um transmissor](https://t.me/lisnmylife/420) (iBUS, ARM, servos e motor) — os sensores vêm a seguir |

Mantenho a tabela de status do README do OpenPlane honesta de propósito: o que voou, o que rodou na bancada e o que só foi testado.

Também: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — um FlySky FS-i6 como joystick USB para simuladores de voo.

---

## 🛠️ Stack técnica

| | |
|---|---|
| **Linguagens** | C++ (padrões modernos, POO), C, Python (ferramentas, automação) |
| **MCUs** | ESP32 (S3, C3, clássico), STM32H743 |
| **RTOS e frameworks** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Arquitetura** | SOLID, injeção de dependências, HAL, design orientado a eventos, máquinas de estados à prova de falhas |
| **Interfaces** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Qualidade** | Unity, builds de teste nativos (host), gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Ferramentas** | Git, Linux, telemetria Wi-Fi / HTTP, KiCad |

---

## 🧭 Como eu construo

| | |
|---|---|
| 🛡️ **Tolerância a falhas primeiro** | O comportamento em falhas e as máquinas de estados são projetados antes das funcionalidades, não depois. |
| 🧪 **Comprovado, não prometido** | Builds no host, simulação em malha fechada, cobertura, análise estática e CI a cada mudança. |
| 🤝 **IA ajuda, a decisão é humana** | A IA me deixa mais rápido; a arquitetura e a verificação continuam nas minhas mãos. |

---

## 🌌 Ad astra

Meu objetivo é simples: **quero trabalhar em coisas que vão para o espaço.** Hoje são aviões RC e autopilotos para UAVs; o rumo é o setor aeroespacial — software de voo que precisa funcionar de primeira, sem ninguém por perto para apertar o reset.

O espaço não pertence a um único país, então este perfil também não fala um único idioma — escolha o seu lá em cima.

---

## 💼 Procuro

**Embedded Firmware Engineer pleno / Junior+ forte** ou **Software Architect** — vagas remotas em qualquer lugar do mundo: robótica, UAVs, aeroespacial e sistemas espaciais, IoT, hardware de alta carga.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane no GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
