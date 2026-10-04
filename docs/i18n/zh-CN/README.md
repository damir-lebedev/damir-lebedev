<p align="center">
  <a href="../../../README.md"><img src="../../images/flags/gb.svg" height="14" alt="">&nbsp;English</a>
  ·
  <a href="../ru/README.md"><img src="../../images/flags/ru.svg" height="14" alt="">&nbsp;Русский</a>
  ·
  <img src="../../images/flags/cn.svg" height="14" alt="">&nbsp;<b>中文</b>
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
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev —— 从遥控飞机到轨道" width="100%">
</p>

<h1 align="center">你好，我是 Damir 👋</h1>

<p align="center">
  <b>使用现代 C++ 与 RTOS，构建可靠、模块化、关键任务级的嵌入式系统。</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

我从零开始设计与硬件无关的嵌入式系统，并用测试来证明它们。

---

## 🌌 Ad astra

我的目标很简单：**我想参与那些飞向太空的项目。** 今天是遥控飞机和无人机自动驾驶仪；方向是航空航天——飞行软件必须一次成功，身边没有人能按下复位键。

太空不属于任何一个国家，所以这个主页也不只用一种语言——请在顶部选择你的语言。

---

## 🧭 我如何构建

| | |
|---|---|
| 🧱 **与硬件无关** | 薄薄的 HAL 是唯一了解 MCU 的一层，驱动并不知道自己挂在哪条总线上。 |
| 🛡️ **故障安全优先** | 故障行为与状态机先于功能进行设计，而不是事后补上。 |
| ⏱️ **确定性** | 固定频率的控制回路，在关键位置不使用动态内存。 |
| 🧪 **用证据说话** | 主机构建、闭环仿真、覆盖率、静态分析，每次变更都经过 CI。 |
| 🤝 **AI 辅助，人来把关** | AI 帮我提高速度；架构与验证始终掌握在我自己手中。 |

---

## 🚀 旗舰项目 — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

面向遥控飞机的开源飞控与自动驾驶仪。同一套固件可运行在 **ESP32-S3** 和 **STM32H743** 上。

| | |
|---|---|
| ✈️ **自动驾驶** | 12 种飞行模式：自稳、定高、巡航、盘旋（loiter）、自动返航、自动起降、热气流滑翔、救援 |
| 🛡️ **故障保护** | 严格的优先级顺序（失联 > ARM > 模式 > 油门）：任何模式都不能让油门越过 ARM 的限制；遥控信号中断时，飞机会自动返航 |
| 🧱 **架构** | Header-only C++，HAL 是唯一了解 MCU 的层，传感器驱动与 I2C/SPI 无关，控制回路中不使用动态内存 |
| ⏱️ **实时性** | 500 Hz 控制回路，ESP32 上为双核任务，STM32 上运行 FreeRTOS |
| 📡 **遥测** | 机载 Web 仪表盘，通过 MAVLink 对接 QGroundControl / Mission Planner（数据帧已与 `pymavlink` 逐字节核对） |
| 📼 **黑匣子** | 每次飞行以 500 Hz 记录：写入机载闪存（ESP32-S3）或 SD 卡（STM32），再由 Python 工具解码为 CSV |
| 🧪 **验证** | 387 个自动化测试，98% 行覆盖率，每种模式的闭环飞行仿真，24 种“开发板 × 传感器”组合构建零警告 |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="遥控信号丢失：飞机飞回起点并盘旋" width="480"><br>
  <sub>关闭遥控器——飞机自动飞回起点。真实固件的闭环仿真。</sub>
</p>

### 📍 项目的真实进展

| | |
|---|---|
| ✈️ **首架原型机，手动模式** | 已试飞 |
| 🧪 **自动驾驶仪** | 已在台架、测试和仿真中验证——等待飞行试验 |
| 🔌 **STM32H743 开发板** | 已可[通过发射机控制](https://t.me/lisnmylife/420)（iBUS、ARM、舵机和电机）——接下来是传感器 |

我刻意让 OpenPlane README 中的状态表保持诚实：哪些飞过，哪些在台架上跑过，哪些只是测试过。

另外：[esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) —— 把 FlySky FS-i6 变成飞行模拟器用的 USB 摇杆。

---

## 🛠️ 技术栈

| | |
|---|---|
| **语言** | C++（现代标准、面向对象）、C、Python（工具、自动化） |
| **MCU** | ESP32（S3、C3、经典款）、STM32H743 |
| **RTOS 与框架** | FreeRTOS、Arduino framework、STM32duino、PlatformIO |
| **架构** | SOLID、依赖注入、HAL、事件驱动设计、故障安全状态机 |
| **接口** | I2C、SPI、UART、SDMMC、iBUS、UBX (GPS)、MAVLink |
| **质量** | Unity 测试框架、原生（主机）测试构建、gcovr、cppcheck、clang-tidy、GitHub Actions |
| **工具** | Git、Linux、Wi-Fi / HTTP 遥测、KiCad |

---

## 💼 正在寻找

**中级 / 实力较强的初级+ 嵌入式固件工程师** 或 **软件架构师** —— 全球范围内的远程岗位：机器人、无人机、航空航天与太空系统、物联网、高负载硬件。

📧 **dam.lebedev2018@yandex.ru** · 🐙 [GitHub 上的 OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
