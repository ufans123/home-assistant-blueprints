<a name="top"></a>
# Home Assistant Blueprints 🏠

Welcome! This repository features my collection of custom Home Assistant blueprints designed to simplify, synchronize, and elevate your smart home automations.

---

## 💡 Quick Overview & Release Status

* **Exchange Released:** Blueprints with an exchange date have been published to the official [Home Assistant Blueprint Exchange](https://community.home-assistant.io/c/blueprints-exchange/53).
* **In Development:** Blueprints without a release date are functional, undergoing testing, or pending exchange posting.
* **Merged / Legacy:** Blueprints combined into all-in-one versions for better maintenance.

---

## 📌 Table of Contents

- ⚠️ [Disclaimer & Usage Notice](#disclaimer)
- ⏱️ [Schedulers & Time-Based Automation](#-schedulers-time-based-automation)
- 🔄 [State Synchronization & Helpers](#-state-synchronization--helpers)
- 🎨 [Lighting, Scenes & Dynamic Modes](#-lighting-scenes-dynamic-modes)
- 🔘 [Physical Controls, Buttons & NFC](#-physical-controls-buttons--nfc)
- 🔔 [Notifications, Alerts & Tasks](#-notifications-alerts-tasks)
- 🔋 [Power, Hardware & Network Management](#-power-hardware-network-management)
- 🛡️ [Security & Keypads](#-security-keypads)
- 🌤️ [Weather & Environment](#-weather-environment)
- ♣️ [About the Author](https://about.me/andylund)

---

<details id="disclaimer">
<summary><b>⚠️ Disclaimer & Usage Notice (Click to expand)</b></summary>

<br/>

These Home Assistant blueprints are provided **"as-is"** and shared freely with the Home Assistant community.

By using these blueprints, you acknowledge and agree to the following:
- **No Warranty:** The author makes no warranties regarding the stability, reliability, security, or functionality of these blueprints.
- **Assumption of Risk:** Smart home environments vary widely. Test these blueprints thoroughly in your setup before relying on them for core tasks.
- **Artificial Intelligence (AI) Notice:** Portions of these blueprints may have been generated or optimized using AI tools. If integrating with live AI APIs (e.g., OpenAI or Google Gemini), the author is not responsible for non-deterministic behavior, hallucinations, or unexpected API usage fees.
- **Limitation of Liability:** The author shall not be held liable for loop triggers, device malfunctions, excessive API costs, or physical property damage resulting from blueprint use.

Always review raw YAML and test safely before deploying to critical production hardware (e.g., smart locks, heaters, or sirens).

</details>

[⬆ Back to top](#top)

---

## 🧰 Blueprint Collection

### ⏱️ Schedulers & Time-Based Automation

Automations driven by time, calendar days, sunrise/sunset, or dashboard pickers.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Daily Dashboard-Controlled Device Scheduler](dashboard-controlled-daily-device-scheduler.md)** | Dynamic switch/light scheduler driven by `input_datetime` helpers with day-of-week filters and dynamic timer sync. | `v1.0` | `2026-10-28` |
| **[Daily Sun-Based Multi-Device Scheduler](daily-sunset-sunrise-device-scheduler.md)** | Controls switches, lights, or fans using dynamic sunset/sunrise triggers with custom offsets and shutoff rules. | `v1.0` | `2026-10-23` |
| **[Daily Sun-Based Device Scheduler](daily-sun-based-device-scheduler.md)** | Basic sunset and weekday device scheduling with optional bidirectional timer synchronization. | `v1.0` | `2026-10-12` |
| **[Daily Sun-Based Multi-Device & Scene Scheduler](daily-sun-based-multi-device-scheduler-with-scenes.md)** | Schedule multiple devices, switches, and scenes with sunset rules and smart remaining-time recovery. | `v1.0` | `2026-10-13` |
| **[Daily Time-Based Device Scheduler](daily-time-based-device-scheduler.md)** | Schedule lights or switches using time-of-day and day-of-week rules with timer recovery. | `v1.0` | `2026-10-10` |
| **[Trigger on a Specific Date and Time](trigger-on-a-specific-date-time.md)** | Fires a one-time automation at an exact future calendar date/time for single-occurrence events. | `v1.0` | `2026-10-31` |

[⬆ Back to top](#top)

---

### 🔄 State Synchronization & Helpers

Keep physical devices, timers, and input helpers synchronized seamlessly without feedback loops.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Two-Way Device Sync](device-sync.md)** | Mutually synchronizes two binary entities (lights, switches, booleans) bidirectionally without infinite loops. | `v1.0` | `2026-10-25` |
| **[Binary Sensor State Sync](binary-sensor-state-sync.md)** | Syncs binary sensor states (doors, windows, motion) directly to an input boolean or switch. | `v1.0` | `2026-10-16` |
| **[Sync Device and Timer](device-timer-sync.md)** | Synchronize device power states (lights, fans) directly with a Home Assistant timer helper. | `v1.0` | `2026-10-08` |
| **[Sync Device and Scheduled Off-Time](device-sync-scheduled-time-off.md)** | Syncs devices with a scheduled off-time picker, computing countdown durations on the fly. | `v1.0` | `2026-10-16` |
| **[Reset Dropdown Helper on Light Turn Off](reset-select-helper.md)** | Quickly resets an `input_select` dropdown helper back to its default state when a light or trigger turns off. | `v1.0` | — |

[⬆ Back to top](#top)

---

### 🎨 Lighting, Scenes & Dynamic Modes

Enhance scene switching, dynamic lighting schedules, and hardware light effects.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Turn On to Default Scene](target-turn-on-synchronizer.md)** | Automatically sets a light or switch to a default scene whenever turned on externally. | `v1.0` | `2026-10-25` |
| **[Turn On to Time-Based Default Scene](turn-on-scene-based-on-time-period.md)** | Dynamic default scene application based on up to 4 time windows when a device turns on. | `v1.0` | `2026-10-30` |
| **[Timed Light Scene Cycler](light-scene-cycler.md)** | Cycles a light or group through custom scenes using an input switch with auto-off timers. | `v1.0` | `2026-10-17` |
| **[Scene Selector with Light Effect Support](input-select-scene-selector.md)** | Trigger HA scenes or native hardware effects (e.g., Hue, Govee, WLED) using an `input_select` helper. | `v1.0` | — |

[⬆ Back to top](#top)

---

### 🔘 Physical Controls, Buttons & NFC

Automations bound to wall switches, long-press gestures, NFC tags, and media actions.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Button On/Off Control with Optional Actions](button-on-off.md)** | Control switches or lights using dedicated On/Off event buttons with secondary action support. | `v1.0` | `2026-10-22` |
| **[Button Scene Cycling and Off Control](button-scene-cycling-and-off-control.md)** | Sequential scene cycling using an On/Scene button and counter helper, with shutdown on Off. | `v1.1` | `2026-10-14` |
| **[Cycle Through Multiple Scenes (NFC & Switches)](cycle-scenes-by-trigger.md)** | Cycle scenes sequentially via NFC tag scans, buttons, or custom triggers. | `v1.0` | `2026-11-02` |
| **[On/Off or Toggle Control with Scene Options](on-off-toggle-nfc-trigger-options.md)** | On/Off/Toggle logic via buttons or NFC tags, featuring optional scene presets. | `v1.0` | `2026-10-15` |
| **[Switch Event Long-Press Control](long-press-options.md)** | Triggers actions via long-press switch events or optional NFC scans with custom UI labels. | `v1.0` | `2026-10-20` |
| **[Spotify NFC Jukebox with Smart Tracker](spotify-nfc-trigger.md)** | Tap NFC tags to play, resume, or switch Spotify playlists with offline speaker safety protection. | `v1.0` | `2026-10-24` |
| **[Motion Sensor Enable or Disable](motion-control-enable-disable.md)** | Enable or disable motion automation via buttons or automatically when lights turn off. | `v1.0` | `2026-10-12` |

[⬆ Back to top](#top)

---

### 🔔 Notifications, Alerts & Tasks

Engaging notifications, dashboard to-do list generators, and persistent alerts.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Scheduled Notifications To-Do List](scheduled-task-notifications-manager.md)** | Generates up to 10 sequential persistent notifications and/or To-Do list items bound to calendar days. | `v2.1` | `2026-10-29` |
| **[Scheduled Notifications To-Do List (Day of Week)](scheduled-task-notifications-dow.md)** | Weekly task generator creating notifications and To-Do items for specific weekdays with auto-recycling. | `v1.0` | `2026-10-29` |
| **[Persistent Notification via Manual Switch](persistent-notification-manual-nfc.md)** | Triggers persistent dashboard notifications via an input boolean toggle or optional NFC trigger. | `v1.0` | — |

[⬆ Back to top](#top)

---

### 🔋 Power, Hardware & Network Management

Monitors device health, safeguards battery charging, and automates equipment reboots.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Safer Battery Charging & Timed Failsafe Manager](battery-charging-control-combined.md)** | Combined smart plug charging manager using percentage thresholds, safety timers, and network recovery. | `v1.0` | `2026-10-27` |
| **[Battery Level & Status Monitor](low-battery-alert.md)** | Automatically scans and reports devices with low batteries or unavailable states on a schedule or trigger. | `v1.0` | `2026-10-23` |
| **[Offline Device Notifications](offline-device-check.md)** | Monitors devices and sensors for unavailable/unknown states with whitelist and blacklist filtering. | `v1.0` | `2026-10-19` |
| **[Manual Z-Wave Outlet Restart (Router Reboot)](manual-zwave-reboot.md)** | Safely power-cycles network routers/modems via a Z-Wave smart plug with built-in recovery delays. | `v1.0` | `2026-10-20` |
| *[Battery-Controlled Charging Switch]* | *Merged into "Safer Battery Charging & Timed Failsafe Manager"* | `v1.0` | `Merged` |
| *[Battery-Controlled Charging Switch - Failsafe]* | *Merged into "Safer Battery Charging & Timed Failsafe Manager"* | `v1.0` | `Merged` |

[⬆ Back to top](#top)

---

### 🛡️ Security & Keypads

Keypad integrations, sound routing, and security system state triggers.

| Blueprint | Description | Version | Exchange Release |
| :--- | :--- | :---: | :---: |
| **[Alarmo State Manager (Custom Actions)](alarmo-state-manager.md)** | Executes custom actions (lights, TTS, chimes) during Alarmo state transitions without breaking security logic. | `v1.0` |
