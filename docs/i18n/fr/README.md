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
  <img src="../../images/flags/fr.svg" height="14" alt="">&nbsp;<b>Français</b>
  ·
  <a href="../de/README.md"><img src="../../images/flags/de.svg" height="14" alt="">&nbsp;Deutsch</a>
  ·
  <a href="../ja/README.md"><img src="../../images/flags/jp.svg" height="14" alt="">&nbsp;日本語</a>
  ·
  <a href="../ko/README.md"><img src="../../images/flags/kr.svg" height="14" alt="">&nbsp;한국어</a>
</p>

<p align="center">
  <img src="../../images/banner.svg" alt="Damir Lebedev — des avions RC à l'orbite" width="100%">
</p>

<h1 align="center">Salut, moi c'est Damir 👋</h1>

<p align="center">
  <b>Systèmes embarqués fiables, modulaires et critiques<br>en C++ moderne et RTOS.</b>
</p>

<p align="center" dir="ltr">
  <img src="https://img.shields.io/badge/C%2B%2B-header--only-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/FreeRTOS-dual--core-3fb950?style=for-the-badge" alt="FreeRTOS">
  <img src="https://img.shields.io/badge/ESP32--S3-flight%20ready-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32-S3">
  <img src="https://img.shields.io/badge/STM32H743-running-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32H743">
  <img src="https://img.shields.io/badge/Python-tooling-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

<p align="center" dir="ltr">
  ⚙️ <b>1</b> firmware · <b>2</b> MCU
  &nbsp;·&nbsp;
  ⏱️ boucle de contrôle à <b>500 Hz</b>
  &nbsp;·&nbsp;
  🧪 <b>387</b> tests
  &nbsp;·&nbsp;
  📊 <b>98 %</b> de couverture
</p>

<p align="center">🌍 <b>Disponible pour du télétravail partout dans le monde</b> &nbsp;·&nbsp; 📧 <a href="mailto:dam.lebedev2018@yandex.ru">dam.lebedev2018@yandex.ru</a></p>

Je conçois de zéro des systèmes embarqués indépendants du matériel — et je le prouve par des tests.

---

## 🚀 Projet phare — [OpenPlane](https://github.com/damir-lebedev/OpenPlaneProject)

Un contrôleur de vol et pilote automatique open source pour avions RC. Le même firmware tourne sur **ESP32-S3** et **STM32H743**.

| | |
|---|---|
| ✈️ **Pilote automatique** | 12 modes de vol : stabilisé, maintien d'altitude, croisière, loiter, retour au point de départ, décollage et atterrissage automatiques, vol thermique, sauvetage |
| 🛡️ **Failsafe** | Ordre de priorité strict (perte de liaison > ARM > mode > gaz) : aucun mode ne peut pousser les gaz au-delà de ARM ; quand la radio se tait, l'avion rentre tout seul |
| 🧱 **Architecture** | C++ header-only, la HAL est la seule couche qui connaît le MCU, pilotes de capteurs indépendants d'I2C/SPI, aucune allocation dynamique dans la boucle de contrôle |
| ⏱️ **Temps réel** | Boucle de contrôle à 500 Hz, tâches double cœur sur ESP32, FreeRTOS sur STM32 |
| 📡 **Télémétrie** | Tableau de bord web embarqué, MAVLink vers QGroundControl / Mission Planner (trames vérifiées octet par octet avec `pymavlink`) |
| 📼 **Boîte noire** | Chaque vol est enregistré à 500 Hz : dans la flash embarquée (ESP32-S3) ou sur une carte SD (STM32), puis décodé en CSV par un outil Python |
| 🧪 **Vérification** | 387 tests automatisés, 98 % de couverture de lignes, simulations de vol en boucle fermée de chaque mode, 24 builds carte × capteur sans aucun avertissement |

<p align="center">
  <img src="https://raw.githubusercontent.com/damir-lebedev/OpenPlaneProject/main/docs/images/sim/replay_rth.gif" alt="Radio perdue : l'avion rentre et tourne en cercle" width="480"><br>
  <sub>Radio coupée — l'avion rentre tout seul. Simulation en boucle fermée du vrai firmware.</sub>
</p>

### 📍 Où en est vraiment le projet

| | |
|---|---|
| ✈️ **Premier prototype, mode manuel** | A volé |
| 🧪 **Pilote automatique** | Vérifié au banc, en tests et en simulation — en attente d'essais en vol |
| 🔌 **Carte STM32H743** | Déjà [pilotée depuis un émetteur](https://t.me/lisnmylife/420) (iBUS, ARM, servos et moteur) — les capteurs viennent ensuite |

Je tiens volontairement honnête le tableau d'état du README d'OpenPlane : ce qui a volé, ce qui a tourné au banc, ce qui est seulement testé.

Aussi : [esp32-rc-joystick](https://github.com/damir-lebedev/esp32-rc-joystick) — une FlySky FS-i6 en joystick USB pour simulateurs de vol.

---

## 🛠️ Stack technique

| | |
|---|---|
| **Langages** | C++ (standards modernes, POO), C, Python (outils, automatisation) |
| **MCU** | ESP32 (S3, C3, classique), STM32H743 |
| **RTOS et frameworks** | FreeRTOS, Arduino framework, STM32duino, PlatformIO |
| **Architecture** | SOLID, injection de dépendances, HAL, conception événementielle, machines à états tolérantes aux pannes |
| **Interfaces** | I2C, SPI, UART, SDMMC, iBUS, UBX (GPS), MAVLink |
| **Qualité** | Unity, builds de test natifs (hôte), gcovr, cppcheck, clang-tidy, GitHub Actions |
| **Outils** | Git, Linux, télémétrie Wi-Fi / HTTP, KiCad |

---

## 🧭 Ma façon de construire

| | |
|---|---|
| 🛡️ **La sûreté de fonctionnement d'abord** | Le comportement en cas de panne et les machines à états sont conçus avant les fonctionnalités, pas après. |
| 🧪 **Prouvé, pas promis** | Builds sur hôte, simulation en boucle fermée, couverture, analyse statique et CI à chaque changement. |
| 🤝 **L'IA aide, l'humain décide** | L'IA me fait avancer plus vite ; l'architecture et la vérification restent entre mes mains. |

---

## 🌌 Ad astra

Mon objectif est simple : **je veux travailler sur des choses qui vont dans l'espace.** Aujourd'hui, ce sont des avions RC et des pilotes automatiques pour drones ; le cap, c'est l'aérospatial — du logiciel de vol qui doit fonctionner du premier coup, sans personne pour appuyer sur reset.

L'espace n'appartient à aucun pays, donc ce profil ne parle pas non plus une seule langue — choisissez la vôtre en haut.

---

## 💼 Je recherche

**Embedded Firmware Engineer confirmé / Junior+ solide** ou **Software Architect** — postes en télétravail, partout dans le monde : robotique, drones, aérospatial et systèmes spatiaux, IoT, matériel à forte charge.

📧 **dam.lebedev2018@yandex.ru** · 🐙 [OpenPlane sur GitHub](https://github.com/damir-lebedev/OpenPlaneProject)

<p align="center"><sub>Per aspera ad astra ✦</sub></p>
