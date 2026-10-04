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
  <img src="../../images/flags/sa.svg" height="14" alt="">&nbsp;<b>العربية</b>
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
  <img src="../../images/banner.svg" alt="Damir Lebedev — من طائرات الـ RC إلى المدار" width="100%">
</p>

<div dir="rtl">

<h1 align="center">مرحبًا، أنا Damir 👋</h1>

<p align="center">
  <b>أنظمة مدمجة موثوقة وقابلة للتركيب وحرجة المهام<br>بلغة C++ الحديثة ونظام RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

أصمّم أنظمة مدمجة مستقلة عن العتاد من الصفر — وأثبت صحتها بالاختبارات.

---

## 🌌 Ad astra

هدفي بسيط: **أريد أن أعمل على أشياء تذهب إلى الفضاء.** اليوم هي طائرات RC وأنظمة طيار آلي للطائرات المسيّرة؛ والاتجاه هو الفضاء والطيران — برمجيات طيران يجب أن تعمل من المرة الأولى، دون أن يكون بجانبها من يضغط زر إعادة التشغيل.

الفضاء لا ينتمي إلى بلد واحد، لذلك لا يتحدث هذا الملف بلغة واحدة — اختر لغتك من الأعلى.

---

## 🧭 كيف أبني

| | |
|---|---|
| 🧱 **مستقل عن العتاد** | طبقة HAL رقيقة هي الوحيدة التي تعرف المتحكم الدقيق (MCU). والمشغّلات لا تعرف على أي ناقل تعمل. |
| 🛡️ **الأمان عند الأعطال أولًا** | يُصمَّم سلوك الأعطال وآلات الحالة قبل الميزات، لا بعدها. |
| ⏱️ **حتمي** | حلقات تحكم بتردد ثابت، ودون ذاكرة ديناميكية حيث يهم ذلك. |
| 🧪 **مُثبَت لا موعود** | بناء على المضيف، ومحاكاة بحلقة مغلقة، وتغطية، وتحليل ساكن، وCI مع كل تغيير. |
| 🤝 **الذكاء الاصطناعي يساعد والقرار بشري** | يساعدني الذكاء الاصطناعي على التقدم أسرع؛ أما المعمارية والتحقق فيبقيان بيدي. |

---

## 🚀 المشروع الرئيسي — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

متحكم طيران وطيار آلي مفتوح المصدر لطائرات الـ RC. يعمل البرنامج الثابت نفسه على **ESP32-S3** و**STM32H743**.

| | |
|---|---|
| ✈️ **الطيار الآلي** | 12 نمط طيران: التثبيت، ثبات الارتفاع، الإبحار، التحويم (loiter)، العودة إلى نقطة الانطلاق، الإقلاع والهبوط الآليان، التحليق الحراري، الإنقاذ |
| 🛡️ **الأمان عند الأعطال** | ترتيب أولويات صارم (فقدان الاتصال > ARM > النمط > الخانق): لا يستطيع أي نمط رفع الخانق فوق حدّ ARM؛ وعند انقطاع الراديو تعود الطائرة إلى نقطة الانطلاق وحدها |
| 🧱 **المعمارية** | C++ بملفات رأسية فقط، وطبقة HAL هي الوحيدة التي تعرف المتحكم الدقيق، ومشغّلات الحساسات مستقلة عن I2C/SPI، ولا ذاكرة ديناميكية في حلقة التحكم |
| ⏱️ **الزمن الحقيقي** | حلقة تحكم بتردد 500 Hz، ومهام على نواتين في ESP32، وFreeRTOS على STM32 |
| 📡 **القياس عن بُعد** | لوحة ويب على متن الطائرة، وMAVLink إلى QGroundControl / Mission Planner (الإطارات مُدقَّقة بايتًا ببايت مقابل `pymavlink`) |
| 📼 **الصندوق الأسود** | كل رحلة تُسجَّل بتردد 500 Hz: في الذاكرة الفلاشية على المتن (ESP32-S3) أو على بطاقة SD (STM32)، وتُفكّ إلى CSV بأداة Python |
| 🧪 **التحقق** | 387 اختبارًا آليًا، وتغطية 98% من الأسطر، ومحاكاة طيران بحلقة مغلقة لكل نمط، و24 عملية بناء «لوحة × حساس» دون أي تحذير |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="فُقد الراديو: الطائرة تعود إلى نقطة الانطلاق وتدور حولها" width="480"><br>
  <sub>أُطفئ الراديو — فتعود الطائرة وحدها. محاكاة بحلقة مغلقة للبرنامج الثابت الحقيقي.</sub>
</p>

### 📍 أين يقف المشروع فعليًا

| | |
|---|---|
| ✈️ **النموذج الأول، النمط اليدوي** | حلّق |
| 🧪 **الطيار الآلي** | تم التحقق منه على المنضدة وفي الاختبارات وفي المحاكاة — بانتظار تجارب الطيران |
| 🔌 **لوحة STM32H743** | تُدار الآن [من جهاز إرسال](https://t.me/lisnmylife/420) (iBUS وARM والمحركات المؤازرة والمحرك) — والحساسات هي الخطوة التالية |

أُبقي جدول الحالة في README مشروع OpenPlane صادقًا عن قصد: ما حلّق، وما عمل على المنضدة، وما اختُبر فقط.

وأيضًا: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — جهاز FlySky FS-i6 كذراع تحكم USB لمحاكيات الطيران.

---

## 🛠️ التقنيات

| | |
|---|---|
| **اللغات** | C++ (معايير حديثة، OOP)، C، Python (أدوات وأتمتة) |
| **المتحكمات الدقيقة** | ESP32 (S3، C3، الكلاسيكي)، STM32H743 |
| **RTOS والأطر** | FreeRTOS، Arduino framework، STM32duino، PlatformIO |
| **المعمارية** | SOLID، حقن الاعتماديات، HAL، التصميم الموجَّه بالأحداث، آلات حالة آمنة عند الأعطال |
| **الواجهات** | I2C، SPI، UART، SDMMC، iBUS، UBX (GPS)، MAVLink |
| **الجودة** | إطار Unity للاختبار، بناء اختبارات أصلي (على المضيف)، gcovr، cppcheck، clang-tidy، GitHub Actions |
| **الأدوات** | Git، Linux، قياس عن بُعد عبر Wi-Fi / HTTP، KiCad |

---

## 💼 ما الذي أبحث عنه

**مهندس برمجيات مدمجة (Firmware) بمستوى متوسط / Junior+ قوي** أو **مهندس معماري للبرمجيات** — وظائف عن بُعد من أي مكان في العالم: الروبوتات، الطائرات المسيّرة، الفضاء والطيران، إنترنت الأشياء، العتاد عالي الحِمل.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane على GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>

</div>
