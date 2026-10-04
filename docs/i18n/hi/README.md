<p align="center">
  <a href="../../../README.md"><img src="../../images/flags/gb.svg" height="14" alt="">&nbsp;English</a>
  ·
  <a href="../ru/README.md"><img src="../../images/flags/ru.svg" height="14" alt="">&nbsp;Русский</a>
  ·
  <a href="../zh-CN/README.md"><img src="../../images/flags/cn.svg" height="14" alt="">&nbsp;中文</a>
  ·
  <a href="../es/README.md"><img src="../../images/flags/es.svg" height="14" alt="">&nbsp;Español</a>
  ·
  <img src="../../images/flags/in.svg" height="14" alt="">&nbsp;<b>हिन्दी</b>
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
  <img src="../../images/banner.svg" alt="Damir Lebedev — RC विमानों से कक्षा तक" width="100%">
</p>

<h1 align="center">नमस्ते, मैं Damir हूँ 👋</h1>

<p align="center">
  <b>आधुनिक C++ और RTOS में भरोसेमंद, मॉड्यूलर, मिशन-क्रिटिकल एम्बेडेड सिस्टम।</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

मैं हार्डवेयर से स्वतंत्र एम्बेडेड सिस्टम शुरू से डिज़ाइन करता हूँ — और टेस्ट से उन्हें साबित करता हूँ।

---

## 🌌 Ad astra

मेरा लक्ष्य सरल है: **मैं उन चीज़ों पर काम करना चाहता हूँ जो अंतरिक्ष में जाती हैं।** आज यह RC विमान और UAV ऑटोपायलट हैं; दिशा एयरोस्पेस की है — फ़्लाइट सॉफ़्टवेयर जिसे पहली ही बार में काम करना होता है, जहाँ रीसेट दबाने वाला कोई नहीं होता।

अंतरिक्ष किसी एक देश का नहीं है, इसलिए यह प्रोफ़ाइल भी एक भाषा तक सीमित नहीं है — ऊपर से अपनी भाषा चुनें।

---

## 🧭 मैं कैसे बनाता हूँ

| | |
|---|---|
| 🧱 **हार्डवेयर से स्वतंत्र** | एक पतली HAL ही वह एकमात्र परत है जो MCU को जानती है। ड्राइवर नहीं जानते कि वे किस बस पर बैठे हैं। |
| 🛡️ **पहले फ़ेल-सेफ़** | विफलता का व्यवहार और स्टेट मशीनें फ़ीचर से पहले डिज़ाइन होती हैं, बाद में नहीं। |
| ⏱️ **डिटरमिनिस्टिक** | निश्चित आवृत्ति वाले कंट्रोल लूप, जहाँ ज़रूरी है वहाँ डायनेमिक मेमोरी नहीं। |
| 🧪 **वादा नहीं, प्रमाण** | हर बदलाव पर होस्ट बिल्ड, क्लोज़्ड-लूप सिमुलेशन, कवरेज, स्टैटिक एनालिसिस और CI। |
| 🤝 **AI की मदद, फ़ैसला इंसान का** | AI मुझे तेज़ बनाता है; आर्किटेक्चर और सत्यापन मेरे अपने हाथ में रहते हैं। |

---

## 🚀 प्रमुख प्रोजेक्ट — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

RC विमानों के लिए ओपन-सोर्स फ़्लाइट कंट्रोलर और ऑटोपायलट। वही फ़र्मवेयर **ESP32-S3** और **STM32H743** दोनों पर चलता है।

| | |
|---|---|
| ✈️ **ऑटोपायलट** | 12 उड़ान मोड: स्टेबलाइज़, ऊँचाई होल्ड, क्रूज़, लॉइटर, वापसी (return-to-home), ऑटो टेक-ऑफ़ और लैंडिंग, थर्मल सोअरिंग, रेस्क्यू |
| 🛡️ **फ़ेलसेफ़** | सख़्त प्राथमिकता क्रम (लिंक टूटना > ARM > मोड > थ्रॉटल): कोई भी मोड थ्रॉटल को ARM से आगे नहीं बढ़ा सकता; रेडियो शांत होने पर विमान अपने आप वापस आ जाता है |
| 🧱 **आर्किटेक्चर** | Header-only C++, HAL ही एकमात्र परत जो MCU को जानती है, सेंसर ड्राइवर I2C/SPI से स्वतंत्र, कंट्रोल लूप में डायनेमिक मेमोरी नहीं |
| ⏱️ **रियल टाइम** | 500 Hz कंट्रोल लूप, ESP32 पर डुअल-कोर टास्क, STM32 पर FreeRTOS |
| 📡 **टेलीमेट्री** | बोर्ड पर वेब डैशबोर्ड, QGroundControl / Mission Planner के लिए MAVLink (फ़्रेम `pymavlink` से बाइट-दर-बाइट जाँचे गए) |
| 📼 **ब्लैक बॉक्स** | हर उड़ान 500 Hz पर रिकॉर्ड होती है: ऑन-बोर्ड फ़्लैश (ESP32-S3) या SD कार्ड (STM32) में, और Python टूल उसे CSV में डिकोड करता है |
| 🧪 **सत्यापन** | 387 ऑटोमेटेड टेस्ट, 98% लाइन कवरेज, हर मोड की क्लोज़्ड-लूप उड़ान सिमुलेशन, 24 बोर्ड × सेंसर बिल्ड बिना किसी वार्निंग के |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="रेडियो टूटा: विमान घर लौटकर चक्कर लगाता है" width="480"><br>
  <sub>रेडियो बंद — विमान अपने आप घर लौटता है। असली फ़र्मवेयर का क्लोज़्ड-लूप सिमुलेशन।</sub>
</p>

### 📍 असल स्थिति

| | |
|---|---|
| ✈️ **पहला प्रोटोटाइप, मैन्युअल मोड** | उड़ा |
| 🧪 **ऑटोपायलट** | बेंच, टेस्ट और सिमुलेशन में सत्यापित — उड़ान परीक्षणों की प्रतीक्षा में |
| 🔌 **STM32H743 बोर्ड** | पहले से [ट्रांसमीटर से चलता है](https://t.me/lisnmylife/420) (iBUS, ARM, सर्वो और मोटर) — सेंसर अगला कदम हैं |

मैं OpenPlane README की स्थिति तालिका जानबूझकर ईमानदार रखता हूँ: क्या उड़ा, क्या बेंच पर चला, और क्या सिर्फ़ टेस्ट हुआ।

साथ ही: [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — फ़्लाइट सिमुलेटर के लिए USB जॉयस्टिक के रूप में FlySky FS-i6।

---

## 🛠️ टेक स्टैक

| | |
|---|---|
| **भाषाएँ** | C++ (आधुनिक स्टैंडर्ड, OOP), C, Python (टूल, ऑटोमेशन) |
| **MCU** | ESP32 (S3, C3, क्लासिक), STM32H743 |
| **RTOS और फ़्रेमवर्क** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **आर्किटेक्चर** | SOLID, डिपेंडेंसी इंजेक्शन, HAL, इवेंट-ड्रिवन डिज़ाइन, फ़ेल-सेफ़ स्टेट मशीनें |
| **इंटरफ़ेस** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **गुणवत्ता** | Unity टेस्ट फ़्रेमवर्क, नेटिव (होस्ट) टेस्ट बिल्ड, gcovr, cppcheck, clang-tidy, GitHub Actions |
| **टूल** | Git, Linux, Wi-Fi / HTTP टेलीमेट्री, KiCad |

---

## 💼 मैं क्या खोज रहा हूँ

**मिड-लेवल / मज़बूत Junior+ एम्बेडेड फ़र्मवेयर इंजीनियर** या **सॉफ़्टवेयर आर्किटेक्ट** — दुनिया में कहीं से भी रिमोट भूमिकाएँ: रोबोटिक्स, UAV, एयरोस्पेस और अंतरिक्ष प्रणालियाँ, IoT, हाई-लोड हार्डवेयर।

📧 **dam.lebedev2018@yandex.ru** · 🐙 [GitHub पर OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
