# Home Assistant Blueprints 🏠

Welcome to my personal Home Assistant blueprints repository! This project contains advanced, highly customized configuration engines designed to streamline smart home automation orchestration.

## ⚠️ Disclaimer

These Home Assistant blueprints are provided **"as-is"** and meant to be shared freely with the Home Assistant community. 

By using these blueprints, you acknowledge and agree that:
- **No Warranty:** The author makes no warranties or guarantees regarding the stability, reliability, security, or functionality of these blueprints.
- **Assumption of Risk:** Smart home environments vary widely. You are solely responsible for testing these blueprints in your specific environment before relying on them.
- **Artificial Intelligence (AI) Notice:** Portions of these blueprints may have been generated, optimized, or assisted by Artificial Intelligence tools. Additionally, if these blueprints interact with AI integration APIs (such as OpenAI or Google Gemini), the author is not responsible for AI-generated hallucinations, unexpected API usage costs, or erratic automation triggers caused by non-deterministic AI outputs.
- **Limitation of Liability:** In no event shall the author be held liable for any damages, logic errors, loop-triggers, device malfunctions, excessive API fees, security vulnerabilities, or physical property damage resulting from the use or misuse of these blueprints.

Always review the automation YAML and test changes safely before deploying them to critical production devices (e.g., locks, sirens, or heating systems).


## 📋 Available Blueprints

- **[Battery-Controlled Charging Switch](battery-charging-control.md)** - Automatically manage charging by turning a smart plug on/off based on battery percentage thresholds.
- **[Battery-Controlled Charging Switch - Time Failsafe Companion](battery-charging-control-companion.md)** — Adds a customizable time-limit layer to the threshold engine, insulating your charger from network dropouts and managing temporary unplugging.
- **[Button On/Off Control with Optional Actions](button-on-off.md)** — Controls any switch, light, or input boolean using separate On/Off event buttons, complete with support for optional secondary actions (2026-10-14).
- **[Button Scene Cycling and Off Control](button-scene-cycling-and-off-control.md)** — Cycles sequentially through a list of scenes using an On/Scene button and a counter helper, with complete shutdown and counter reset on Off.
- **[Cycle Through Multiple Scenes (NFC & Switches)](cycle-scenes-by-trigger.md)** — Cycles sequentially through a list of scenes using NFC tags, buttons, or custom triggers with a counter helper to remember your position.
- **[Daily Sun-Based Device Scheduler](daily-sun-based-device-scheduler.md)** — Schedule switches, lights, or fans using sunset and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery (2026-10-12).
- **[Daily Sun-Based Multi-Device & Multi-Scene Scheduler with Timer](daily-sun-based-multi-device-scheduler-with-scenes.md)** — Schedule multiple switches, lights, fans, and scenes using sunset rules and day-of-week filtering, featuring bidirectional timer synchronization and smart remaining-time recovery (2026-10-13).
- **[Daily Time-Based Device Scheduler](daily-time-based-device-scheduler.md)** — Schedule switches, lights, or fans using time and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery (2026-10-10).
- **[Low or Unknown Battery Alert](low-battery-alert.md)** — Automatically scan and report devices with low battery levels or unknown/unavailable statuses via scheduled checks or an optional manual trigger.
- **[Motion Sensor Enable or Disable](motion-control-enable-disable.md)** - Enable or disable motion sensors via button events or automatically when a specific light turns off (2026-10-12).
- **[On/Off or Toggle Control with Scene Options (NFC & Triggers)](on-off-toggle-nfc-trigger-options.md)** — Effortlessly control lights, switches, fans, and inputs using NFC tags or buttons with explicit On, Off, and Toggle logic, plus optional multi-scene presets (2026-10-15).
- **[Reset Dropdown Helper on Light Turn Off](reset-select-helper.md)** — Quickly reset any select input helper back to a designated default or unselected state based on triggers or automation events.
- **[Ring Keypad v2: Z-Wave Multi-Trigger Sound Player](ring-keypad-sounds.md)** — Effortlessly play built-in chimes, notification sounds, and system tones on a Ring Keypad v2 using flexible trigger sources and automated Z-Wave property key routing (2026-10-16).
- **[Scheduled Task Notifications Manager](scheduled-task-notifications-manager.md)** - An advanced scheduling blueprint engine that generates up to 10 sequential persistent notification cards bound to calendar days, helper switches, or custom events (2026-10-05).
- **[Sync Device and Timer](device-timer-sync.md)** - Keep lights, switches, or fans synchronized with a Home Assistant timer helper (2026-10-08).
