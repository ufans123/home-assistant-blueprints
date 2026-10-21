# Home Assistant Blueprints 🏠

Welcome to my personal Home Assistant blueprints repository! This project contains advanced, highly customized configuration engines designed to streamline smart home automation orchestration. 

- Please note anything with a date beside has been uploaded to the Home Assistant Blueprint Exchange to share with the community. 
- Blueprints without a date have not as yet been posted on the exchange and may be updated before they are posted to the exchange.
- Also some of the blueprints below maybe niche and use cases for people may vary. Enjoy. 

## ⚠️ Disclaimer

These Home Assistant blueprints are provided **"as-is"** and meant to be shared freely with the Home Assistant community. 

By using these blueprints, you acknowledge and agree that:
- **No Warranty:** The author makes no warranties or guarantees regarding the stability, reliability, security, or functionality of these blueprints.
- **Assumption of Risk:** Smart home environments vary widely. You are solely responsible for testing these blueprints in your specific environment before relying on them.
- **Artificial Intelligence (AI) Notice:** Portions of these blueprints may have been generated, optimized, or assisted by Artificial Intelligence tools. Additionally, if these blueprints interact with AI integration APIs (such as OpenAI or Google Gemini), the author is not responsible for AI-generated hallucinations, unexpected API usage costs, or erratic automation triggers caused by non-deterministic AI outputs.
- **Limitation of Liability:** In no event shall the author be held liable for any damages, logic errors, loop-triggers, device malfunctions, excessive API fees, security vulnerabilities, or physical property damage resulting from the use or misuse of these blueprints.

Always review the automation YAML and test changes safely before deploying them to critical production devices (e.g., locks, sirens, or heating systems).

---

## 🧰 My Home Assistant Blueprint Toolkit

### ⏱️ Scheduling & Time
- **[Daily Sun-Based Device Scheduler](daily-sun-based-device-scheduler.md)** — Schedule switches, lights, or fans using sunset and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery (2026-10-12).
- **[Daily Sun-Based Multi-Device & Multi-Scene Scheduler with Timer](daily-sun-based-multi-device-scheduler-with-scenes.md)** — Schedule multiple switches, lights, fans, and scenes using sunset rules and day-of-week filtering, featuring bidirectional timer synchronization and smart remaining-time recovery (2026-10-13).
- **[Daily Time-Based Device Scheduler](daily-time-based-device-scheduler.md)** — Schedule switches, lights, or fans using time and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery (2026-10-10).
- **[Scheduled Task Notifications Manager](scheduled-task-notifications-manager.md)** — An advanced scheduling blueprint engine that generates up to 10 sequential persistent notification cards bound to calendar days, helper switches, or custom events (2026-10-05).

### 🔄 Device Synchronization & State Management
- **[Binary Sensor State Sync](binary-sensor-state-sync.md)** — Directly syncs the state of any binary sensor (such as a door or window) to an input boolean, switch, or light using explicit state mapping (2026-10-16).
- **[Reset Dropdown Helper on Light Turn Off](reset-select-helper.md)** — Quickly reset any select input helper back to a designated default or unselected state based on triggers or automation events.
- **[Sync Device and Timer](device-timer-sync.md)** — Keep lights, switches, or fans synchronized with a Home Assistant timer helper (2026-10-08).
- **[Sync Device and Scheduled Off-Time](device-sync-scheduled-time-off.md)** — Sync switches, lights, or fans with a scheduled off-time picker, dynamically computing countdown durations with optional timer helper tracking (2026-10-16).
- **[Two-Way Device Sync: Binary State Mirroring & Loop Prevention](device-sync.md)** — Synchronize the state of any two binary entities (lights, switches, fans, and input booleans) mutually in both directions without infinite loops (2026-10-16).

### 🔘 Buttons, Triggers & Scene Control
- **[Button On/Off Control with Optional Actions](button-on-off.md)** — Controls any switch, light, or input boolean using separate On/Off event buttons, complete with support for optional secondary actions (2026-10-14).
- **[Button Scene Cycling and Off Control](button-scene-cycling-and-off-control.md)** — Cycles sequentially through a list of scenes using an On/Scene button and a counter helper, with complete shutdown and counter reset on Off.
- **[Cycle Through Multiple Scenes (NFC & Switches)](cycle-scenes-by-trigger.md)** — Cycles sequentially through a list of scenes using NFC tags, buttons, or custom triggers with a counter helper to remember your position.
- **[Switch Event Long-Press Control (with Optional NFC)](long-press-options.md)** — Triggers light and switch actions (Turn Off, Turn On, or Toggle) via long-press event entities and an optional NFC tag scan with custom UI labeling (2026-10-20).
- **[On/Off or Toggle Control with Scene Options (NFC & Triggers)](on-off-toggle-nfc-trigger-options.md)** — Effortlessly control lights, switches, fans, and inputs using NFC tags or buttons with explicit On, Off, and Toggle logic, plus optional multi-scene presets (2026-10-15).
- **[Motion Sensor Enable or Disable](motion-control-enable-disable.md)** — Enable or disable motion sensors via button events or automatically when a specific light turns off (2026-10-12).
- **[Timed Light Scene Cycler](light-scene-cycler.md)** — Seamlessly cycles a light or light group through an ordered sequence of custom scenes using an input boolean switch, featuring smooth transitions, a dedicated turn-off scene, and an optional auto-off timer (2026-10-17).

### 🔋 Power, Hardware & Notifications
- **[Battery-Controlled Charging Switch](battery-charging-control.md)** — Automatically manage charging by turning a smart plug on/off based on battery percentage thresholds.
- **[Battery-Controlled Charging Switch - Time Failsafe Companion](battery-charging-control-companion.md)** — Adds a customizable time-limit layer to the threshold engine, insulating your charger from network dropouts and managing temporary unplugging.
- **[Battery Level & Status Monitor (Scheduled & Manual)](low-battery-alert.md)** — Automatically scan and report devices with low battery levels or unknown/unavailable statuses via scheduled checks or an optional manual trigger.
- **[Manual Z-Wave Outlet Restart (Router Reboot)](manual-zwave-reboot.md)** — Safely automates a controlled power-cycle sequence for network routers or modems using a Z-Wave smart plug, featuring dynamic duration estimates, cooldown stabilization, trigger resets, and optional mobile notifications (2026-10-20).
- **[Offline Device Notifications](offline-device-check.md)** — Monitors devices and sensors for unavailable or unknown states using whitelist labels, domain filters, and blacklist exclusions, triggered by schedules, NFC tags, or auto-resetting helper switches (2026-10-19).
- **[Persistent Notification via Manual Switch (with Optional NFC)](persistent-notification-manual-nfc.md)** — Triggers persistent notifications via a required manual input boolean toggle with automatic switch reset, featuring an optional NFC tag scan secondary trigger channel.
- **[Ring Keypad v2: Z-Wave Multi-Trigger Sound Player](ring-keypad-sounds.md)** — Effortlessly play built-in chimes, notification sounds, and system tones on a Ring Keypad v2 using flexible trigger sources and automated Z-Wave property key routing (2026-10-16).

### ☀️ Weather & Information
- **[Configurable Daily Weather Report](weather-report-notification.md)** — Generates clean, optimized weather notifications with custom region headings, smart unit conversion (°C/°F), timestamps, quick links, and multiple triggers including a momentary auto-resetting helper switch (2026-10-18).
