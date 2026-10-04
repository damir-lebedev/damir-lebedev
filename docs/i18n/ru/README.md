<p align="center">
  <a href="../../../README.md"><img src="../../images/flags/gb.svg" height="14" alt="">&nbsp;English</a>
  ·
  <img src="../../images/flags/ru.svg" height="14" alt="">&nbsp;<b>Русский</b>
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
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Дамир Лебедев — от радиоуправляемых самолётов до орбиты" width="100%">
</p>

<h1 align="center">Привет, я Дамир 👋</h1>

<p align="center">
  <b>Надёжные, модульные, критичные к отказам встраиваемые системы<br>на современном C++ и RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

Проектирую встраиваемые системы с нуля, независимые от железа, — и доказываю их работу тестами.

---

## 🌌 Ad astra

Моя цель проста: **я хочу работать над тем, что летает в космос.** Сегодня это радиоуправляемые самолёты и автопилоты для БПЛА; направление — аэрокосмос: полётное ПО, которое должно сработать с первого раза, когда рядом нет никого, кто нажмёт reset.

Космос не принадлежит одной стране, поэтому и у этого профиля не один язык — выберите свой вверху.

---

## 🧭 Как я строю

| | |
|---|---|
| 🧱 **Независимость от железа** | Тонкий HAL — единственный слой, который знает про MCU. Драйверы не знают, на какой шине сидят. |
| 🛡️ **Сначала отказоустойчивость** | Поведение при отказах и конечные автоматы проектируются раньше функций, а не после. |
| ⏱️ **Детерминизм** | Циклы управления с фиксированной частотой, без динамической памяти там, где это важно. |
| 🧪 **Доказано, а не обещано** | Хост-сборки, замкнутое моделирование, покрытие, статический анализ и CI на каждое изменение. |
| 🤝 **ИИ помогает, решает человек** | ИИ ускоряет работу; архитектура и верификация остаются в моих руках. |

---

## 🚀 Флагманский проект — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

Открытый полётный контроллер и автопилот для радиоуправляемых самолётов. Одна и та же прошивка работает на **ESP32-S3** и **STM32H743**.

| | |
|---|---|
| ✈️ **Автопилот** | 12 режимов полёта: стабилизация, удержание высоты, круиз, ожидание над точкой (loiter), возврат домой, автовзлёт и автопосадка, термический парящий полёт, спасение |
| 🛡️ **Failsafe** | Строгий порядок приоритетов (потеря связи > ARM > режим > газ): ни один режим не может поднять газ выше ARM; при потере радиосвязи самолёт сам возвращается домой |
| 🧱 **Архитектура** | Header-only C++, HAL — единственный слой, знающий про MCU, драйверы датчиков не зависят от I2C/SPI, нет динамической памяти в контуре управления |
| ⏱️ **Реальное время** | Контур управления 500 Гц, задачи на двух ядрах ESP32, FreeRTOS на STM32 |
| 📡 **Телеметрия** | Веб-дашборд на борту, MAVLink для QGroundControl / Mission Planner (кадры побайтно сверены с `pymavlink`) |
| 📼 **Чёрный ящик** | Каждый полёт пишется на 500 Гц: во флеш (ESP32-S3) или на SD-карту (STM32), расшифровывается в CSV Python-утилитой |
| 🧪 **Верификация** | 387 автотестов, 98% покрытия строк, замкнутое моделирование полёта каждого режима, 24 сборки «плата × датчик» без предупреждений |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Потеря радиосвязи: самолёт летит домой и кружит" width="480"><br>
  <sub>Радио выключено — самолёт сам возвращается домой. Замкнутое моделирование реальной прошивки.</sub>
</p>

### 📍 Где проект на самом деле

| | |
|---|---|
| ✈️ **Первый прототип, ручной режим** | Летал |
| 🧪 **Автопилот** | Проверен на стенде, в тестах и в симуляции — ждёт лётных испытаний |
| 🔌 **Плата STM32H743** | Уже [управляется с передатчика](https://t.me/lisnmylife/420) (iBUS, ARM, сервы и мотор) — дальше датчики |

Таблицу статусов в README OpenPlane я веду честно: что летало, что работало на стенде, а что только протестировано.

Также: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — FlySky FS-i6 как USB-джойстик для авиасимуляторов.

---

## 🛠️ Стек

| | |
|---|---|
| **Языки** | C++ (современные стандарты, ООП), C, Python (утилиты, автоматизация) |
| **МК** | ESP32 (S3, C3, classic), STM32H743 |
| **RTOS и фреймворки** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Архитектура** | SOLID, внедрение зависимостей, HAL, событийная архитектура, отказоустойчивые конечные автоматы |
| **Интерфейсы** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Качество** | Unity, нативные (хостовые) сборки тестов, gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Инструменты** | Git, Linux, Wi-Fi / HTTP-телеметрия, KiCad |

---

## 💼 Ищу работу

**Embedded Firmware Engineer уровня Middle / сильный Junior+** или **Software Architect** — удалённо, из любой страны: робототехника, БПЛА, аэрокосмос и космические системы, IoT, высоконагруженное железо.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane на GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
