<a name="top"></a>
# Home Assistant Blueprints 🏠

Welcome! This repository features my collection of custom Home Assistant blueprints, designed to simplify and elevate your smart home automations.

- Please note: Blueprints with an **Exchange Release** date have been published to the Home Assistant Blueprint Exchange to share with the community. 
- Blueprints without a date have not yet been posted on the exchange and may be updated before they are released.
- Also, some of the blueprints below may be niche and use cases for people may vary. Enjoy. 

---

## 📌 Table of Contents
- ⚠️[Disclaimer](#disclaimer)
- ⏱️[Scheduling & Time](#️-scheduling--time)
- 🔄[Device Synchronization & State Management](#-device-synchronization--state-management)
- 🔘[Buttons, Triggers & Scene Control](#-buttons-triggers--scene-control)
- 🔋[Power, Hardware & Notifications](#-power-hardware--notifications)
- ☀️[Weather & Information](#️-weather--information)
- ♣️ [About Me](https://about.me/andylund)

---

<details id="disclaimer">
<summary><b>⚠️ Disclaimer & Usage Notice (Click to expand)</b></summary>

<br/>

These Home Assistant blueprints are provided **"as-is"** and meant to be shared freely with the Home Assistant community. 

By using these blueprints, you acknowledge and agree that:
- **No Warranty:** The author makes no warranties or guarantees regarding the stability, reliability, security, or functionality of these blueprints.
- **Assumption of Risk:** Smart home environments vary widely. You are solely responsible for testing these blueprints in your specific environment before relying on them.
- **Artificial Intelligence (AI) Notice:** Portions of these blueprints may have been generated, optimized, or assisted by Artificial Intelligence tools. Additionally, if these blueprints interact with AI integration APIs (such as OpenAI or Google Gemini), the author is not responsible for AI-generated hallucinations, unexpected API usage costs, or erratic automation triggers caused by non-deterministic AI outputs.
- **Limitation of Liability:** In no event shall the author be held liable for any damages, logic errors, loop-triggers, device malfunctions, excessive API fees, security vulnerabilities, or physical property damage resulting from the use or misuse of these blueprints.

Always review the automation YAML and test changes safely before deploying them to critical production devices (e.g., locks, sirens, or heating systems).

</details>

[⬆ Back to top](#top)

---

## 🧰 My Home Assistant Blueprint Toolkit

### ⏱️ Scheduling & Time

| Blueprint | Description | Current Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Daily Sun-Based Multi-Device Scheduler with Sunrise Off & Optional Timer](daily-sunset-sunrise-device-scheduler.md)** | Control multiple switches, lights, or fans using dynamic sunset/sunrise triggers with custom offsets, featuring optional bidirectional timer synchronization and selective multi-device shutoff. | `v1.0` | `2026-10-23` |
| **[Daily Sun-Based Device Scheduler](daily-sun-based-device-scheduler.md)** | Schedule switches, lights, or fans using sunset and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery. | `v1.0` | `2026-10-12` |
| **[Daily Sun-Based Multi-Device & Multi-Scene Scheduler with Timer](daily-sun-based-multi-device-scheduler-with-scenes.md)** | Schedule multiple switches, lights, fans, and scenes using sunset rules and day-of-week filtering, featuring bidirectional timer synchronization and smart remaining-time recovery. | `v1.0` | `2026-10-13` |
| **[Daily Time-Based Device Scheduler](daily-time-based-device-scheduler.md)** | Schedule switches, lights, or fans using time and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery. | `v1.0` | `2026-10-10` |
| **[Dashboard-Controlled Daily Device Scheduler](dashboard-controlled-daily-device-scheduler.md)** | Dynamic scheduler for switches, lights, or fans driven by `input_datetime` helpers on your dashboard, featuring day-of-week filtering, an optional enable toggle, and dynamic timer synchronization. | `v2.1` | — |
| **[Scheduled Task Notifications Manager](scheduled-task-notifications-manager.md)** | Advanced scheduling engine that generates up to 10 sequential persistent notification cards bound to calendar days, helper switches, or custom events. | `v1.0` | `2026-10-05` |

[⬆ Back to top](#top)

---

### 🔄 Device Synchronization & State Management

| Blueprint | Description | Current Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Binary Sensor State Sync](binary-sensor-state-sync.md)** | Directly syncs the state of any binary sensor (such as a door or window) to an input boolean, switch, or light using explicit state mapping. | `v1.0` | `2026-10-16` |
| **[Reset Dropdown Helper on Light Turn Off](reset-select-helper.md)** | Quickly reset any select input helper back to a designated default or unselected state based on triggers or automation events. | `v1.0` | — |
| **[Sync Device and Timer](device-timer-sync.md)** | Keep lights, switches, or fans synchronized with a Home Assistant timer helper. | `v1.0` | `2026-10-08` |
| **[Sync Device and Scheduled Off-Time](device-sync-scheduled-time-off.md)** | Sync switches, lights, or fans with a scheduled off-time picker, dynamically computing countdown durations with optional timer helper tracking. | `v1.0` | `2026-10-16` |
| **[Turn On to Default Scene (Companion Blueprint)](target-turn-on-synchronizer.md)** | Automatically sets a light or switch to a default scene whenever turned on externally, with an optional counter helper reset companion for button cycling. | `v1.0` | `2026-10-25` |
| **[Two-Way Device Sync](device-sync.md)** | Synchronize the state of any two binary entities (lights, switches, fans, input booleans) mutually in both directions without infinite loops. | `v1.0` | ` 2026-10-25 ` |

[⬆ Back to top](#top)

---

### 🔘 Buttons, Triggers & Scene Control

| Blueprint | Description | Current Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Button On/Off Control with Optional Actions](button-on-off.md)** | Controls any switch, light, or input boolean using separate On/Off event buttons, complete with support for optional secondary actions. | `v1.0` | `2026-10-22` |
| **[Button Scene Cycling and Off Control](button-scene-cycling-and-off-control.md)** | Cycles sequentially through a list of scenes using an On/Scene button and a counter helper, with complete shutdown and counter reset on Off. | `v1.1` | `2026-10-14` |
| **[Cycle Through Multiple Scenes (NFC & Switches)](cycle-scenes-by-trigger.md)** | Cycles sequentially through a list of scenes using NFC tags, buttons, or custom triggers with a counter helper to remember your position. | `v1.0` | — |
| **[Motion Sensor Enable or Disable](motion-control-enable-disable.md)** | Enable or disable motion sensors via button events or automatically when a specific light turns off. | `v1.0` | `2026-10-12` |
| **[On/Off or Toggle Control with Scene Options (NFC & Triggers)](on-off-toggle-nfc-trigger-options.md)** | Control lights, switches, fans, and inputs using NFC tags or buttons with explicit On/Off/Toggle logic, plus optional multi-scene presets. | `v1.0` | `2026-10-15` |
| **[Scene Selector with Light Effect Support (Hue & Govee)](input-select-scene-selector.md)** | Triggers Home Assistant scenes or applies native hardware light effects (such as Govee dynamic scenes or WLED presets) using an input_select helper with auto off/reset support. *(Advanced: Requires input_select helpers & startup automation)* | `v1.0` | ` — ` |
| **[Spotify NFC Jukebox with Smart Tracker](spotify-nfc-trigger.md)** | Intelligent Spotify jukebox automation for NFC tags featuring smart state management (resumes, pauses, switches/restarts) and an offline/unavailable speaker safety reset. | `v1.0` | `2026-10-24` |
| **[Switch Event Long-Press Control (with Optional NFC)](long-press-options.md)** | Triggers light and switch actions (Turn Off, Turn On, or Toggle) via long-press event entities and an optional NFC tag scan with custom UI labeling. | `v1.0` | `2026-10-20` |
| **[Timed Light Scene Cycler](light-scene-cycler.md)** | Seamlessly cycles a light/group through custom scenes using an input boolean switch, featuring smooth transitions and auto-off timer. | `v1.0` | `2026-10-17` |

[⬆ Back to top](#top)

---

### 🔋 Power, Hardware & Notifications

| Blueprint | Description | Current Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Battery-Controlled Charging Switch](battery-charging-control.md)** | Automatically manage charging by turning a smart plug on/off based on battery percentage thresholds. Merged into blueprint `'Safe Battery-Controlled Charging & Failsafe Manager'`. | `v1.0` | `Merged` |
| **[Battery-Controlled Charging Switch - Time Failsafe Companion](battery-charging-control-companion.md)** | Adds a customizable time-limit layer to the threshold engine, insulating your charger from network dropouts. Merged into blueprint `'Safe Battery-Controlled Charging & Failsafe Manager'`. | `v1.0` | `Merged` |
| **[Safer Battery-Controlled Charging & Timed Failsafe Manager](battery-charging-control-combined.md)** | All-in-one charging engine uniting percentage thresholds, charge-activated safety timers, NFC nightstand overrides, and network recovery. | `v1.0` | `2026-10-27` |
| **[Battery Level & Status Monitor (Scheduled & Manual)](low-battery-alert.md)** | Automatically scan and report devices with low battery levels or unknown/unavailable statuses via scheduled checks or manual trigger. | `v1.0` | `2026-10-23` |
| **[Manual Z-Wave Outlet Restart (Router Reboot)](manual-zwave-reboot.md)** | Safely automates a controlled power-cycle sequence for routers/modems using a Z-Wave plug with dynamic durations and notifications. | `v1.0` | `2026-10-20` |
| **[Offline Device Notifications (Scheduled, NFC, Manual Triggers)](offline-device-check.md)** | Monitors devices and sensors for unavailable/unknown states using whitelist labels, domain filters, and blacklist exclusions. | `v1.0` | `2026-10-19` |
| **[Persistent Notification via Manual Switch (with Optional NFC)](persistent-notification-manual-nfc.md)** | Triggers persistent notifications via a manual input boolean toggle with automatic reset and optional NFC secondary trigger. | `v1.0` | — |
| **[Ring Keypad V2: Multi-Code Routine Hub (Z-Wave)](ring-keypad-routine.md)** | Map single-digit shortcuts (0–9) and custom multi-digit PIN codes on a Ring Keypad V2 to custom action sequences with audio feedback. | `v1.0` | `2026-10-21` |
| **[Ring Keypad v2: Z-Wave Multi-Trigger Sound Player](ring-keypad-sounds.md)** | Play built-in chimes, notification sounds, and system tones on a Ring Keypad v2 using flexible triggers and Z-Wave routing. | `v1.0` | `2026-10-16` |

[⬆ Back to top](#top)

---

### ☀️ Weather & Information

| Blueprint | Description | Current Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Configurable Daily Weather Report](weather-report-notification.md)** | Generates clean weather notifications with regional headings, smart unit conversion (°C/°F), timestamps, quick links, and multiple triggers. | `v1.0` | `2026-10-18` |

[⬆ Back to top](#top)
