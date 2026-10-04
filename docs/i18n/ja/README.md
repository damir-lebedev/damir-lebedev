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
  <img src="../../images/flags/jp.svg" height="14" alt="">&nbsp;<b>日本語</b>
  ·
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev — RC 機から軌道へ" width="100%">
</p>

<h1 align="center">こんにちは、Damir です 👋</h1>

<p align="center">
  <b>モダン C++ と RTOS で、信頼性が高く、モジュール化された、ミッションクリティカルな組込みシステムを作ります。</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

ハードウェアに依存しない組込みシステムをゼロから設計し、テストで証明します。

---

## 🌌 Ad astra

目標はシンプルです。**宇宙へ行くものに関わりたい。** 今は RC 機や UAV のオートパイロットですが、目指す先は航空宇宙です — 一度で正しく動かなければならず、リセットを押してくれる人が誰もいないフライトソフトウェア。

宇宙は一つの国のものではありません。だからこのプロフィールも一つの言語に閉じません — 上部からお好みの言語を選んでください。

---

## 🧭 ものづくりの流儀

| | |
|---|---|
| 🧱 **ハードウェア非依存** | 薄い HAL だけが MCU を知っています。ドライバは自分がどのバスにつながっているかを知りません。 |
| 🛡️ **フェイルセーフ第一** | 故障時の挙動とステートマシンは、機能よりも先に設計します。 |
| ⏱️ **決定論的** | 固定周期の制御ループ。重要な箇所では動的メモリを使いません。 |
| 🧪 **約束ではなく証明** | ホストビルド、クローズドループシミュレーション、カバレッジ、静的解析、そして変更ごとの CI。 |
| 🤝 **AI は補助、判断は人間** | AI で速く進みますが、アーキテクチャと検証は自分の手に残します。 |

---

## 🚀 主力プロジェクト — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

RC 機向けのオープンソースのフライトコントローラ兼オートパイロット。同じファームウェアが **ESP32-S3** と **STM32H743** で動きます。

| | |
|---|---|
| ✈️ **オートパイロット** | 12 種類の飛行モード：スタビライズ、高度維持、クルーズ、ロイター、自動帰還、自動離着陸、サーマル飛行、レスキュー |
| 🛡️ **フェイルセーフ** | 厳密な優先順位（通信断 > ARM > モード > スロットル）：どのモードも ARM を超えてスロットルを上げられず、電波が途絶えると機体は自力で帰還します |
| 🧱 **アーキテクチャ** | ヘッダオンリーの C++。MCU を知るのは HAL のみ。センサドライバは I2C/SPI から独立し、制御ループで動的メモリは使いません |
| ⏱️ **リアルタイム** | 500 Hz の制御ループ。ESP32 ではデュアルコアのタスク、STM32 では FreeRTOS |
| 📡 **テレメトリ** | 機上 Web ダッシュボード、QGroundControl / Mission Planner 向けの MAVLink（フレームは `pymavlink` とバイト単位で照合済み） |
| 📼 **ブラックボックス** | 全フライトを 500 Hz で記録：機上フラッシュ（ESP32-S3）または SD カード（STM32）に保存し、Python ツールで CSV に変換 |
| 🧪 **検証** | 自動テスト 387 件、行カバレッジ 98%、全モードのクローズドループ飛行シミュレーション、24 種のボード × センサ構成を警告ゼロでビルド |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="電波途絶：機体が自力で帰還して旋回する" width="480"><br>
  <sub>送信機の電源を切ると、機体は自力で帰還します。実際のファームウェアによるクローズドループシミュレーション。</sub>
</p>

### 📍 本当の現在地

| | |
|---|---|
| ✈️ **初号機、マニュアルモード** | 飛行済み |
| 🧪 **オートパイロット** | ベンチ、テスト、シミュレーションで検証済み — 飛行試験待ち |
| 🔌 **STM32H743 ボード** | すでに[送信機から操縦できます](https://t.me/lisnmylife/420)（iBUS、ARM、サーボ、モーター）— 次はセンサ |

OpenPlane の README のステータス表は、あえて正直に保っています：飛んだもの、ベンチで動いたもの、テストしただけのもの。

その他：[esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — FlySky FS-i6 をフライトシミュレータ用 USB ジョイスティックにします。

---

## 🛠️ 技術スタック

| | |
|---|---|
| **言語** | C++（モダン規格、OOP）、C、Python（ツール、自動化） |
| **MCU** | ESP32（S3、C3、クラシック）、STM32H743 |
| **RTOS・フレームワーク** | FreeRTOS、Arduino framework、STM32duino、PlatformIO |
| **アーキテクチャ** | SOLID、依存性注入、HAL、イベント駆動設計、フェイルセーフなステートマシン |
| **インターフェース** | I2C、SPI、UART、SDMMC、iBUS、UBX (GPS)、MAVLink |
| **品質** | Unity テストフレームワーク、ネイティブ（ホスト）テストビルド、gcovr、cppcheck、clang-tidy、GitHub Actions |
| **ツール** | Git、Linux、Wi-Fi / HTTP テレメトリ、KiCad |

---

## 💼 探しているポジション

**ミドルレベル / 実力あるジュニア+ の組込みファームウェアエンジニア**、または **ソフトウェアアーキテクト** — 世界中どこからでも可能なリモート職：ロボティクス、UAV、航空宇宙・宇宙システム、IoT、高負荷ハードウェア。

📧 **dam.lebedev2018@yandex.ru** · 🐙 [GitHub の OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
