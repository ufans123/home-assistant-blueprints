# Alarmo State Manager (Custom Actions)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Falarmo_state_manager.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-11-01 | [← Back to Main Blueprints Repository](README.md)

A clean companion blueprint for Alarmo that does not replace Alarmo's core security logic, but runs alongside it to trigger custom user-defined actions (lights, TTS, chimes, notifications, or switches) whenever Alarmo changes state (`Arming`, `Disarmed`, `Armed` in any mode, or `Triggered`).

---

> ⚠️ **Prerequisites:**
> - **Alarmo Integration:** You must have the [Alarmo custom integration](https://github.com/nielsfaber/alarmo) installed and configured in Home Assistant (`alarm_control_panel.alarmo` or similar panel entity).

---

## Features

- **Companion Architecture:** Acts as an event responder alongside Alarmo without interfering with core alarm logic, sensor bypasses, exit delays, or PIN code verification.
- **Universal Armed Support:** The single `Armed` trigger covers all Alarmo armed states (`armed_away`, `armed_home`, `armed_night`, `armed_vacation`, and `armed_custom_bypass`).
- **100% Optional Action Slots:** Every action section is optional. Leave unused state blocks empty without causing errors or breaking automations.
- **Full Automation Engine Power:** Supports multi-step action sequences, delays, parallel execution, loops (`repeat`), conditions (`if/then`), text-to-speech (TTS), and local audio media playback.
- **Operation Summary:**

  | Event | Action Taken |
  | :--- | :--- |
  | **Alarmo State Changes to `Arming`** | Runs user-defined actions for the exit countdown (e.g., audio announcements, exit chimes, warning light flashes). |
  | **Alarmo State Changes to `Disarmed`** | Runs user-defined actions for disarming (e.g., turning off sirens, turning on camera privacy switches, lighting welcome scenes). |
  | **Alarmo State Changes to `Armed`** | Runs user-defined actions when fully armed in any mode (e.g., locking door locks, turning off switches, setting security scenes). |
  | **Alarmo State Changes to `Triggered`** | Runs user-defined actions during an intrusion/breach (e.g., flashing alert lights, playing warning audio messages, sending notifications). |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Alarmo Control Panel** | The Alarmo entity that triggers this automation (`alarm_control_panel.*`). | **Yes** | N/A |
| **Actions when Arming** | Custom sequence of actions to run when the alarm enters the exit countdown delay. | No | `[]` |
| **Actions when Disarmed** | Custom sequence of actions to run when the system is disarmed. | No | `[]` |
| **Actions when Armed** | Custom sequence of actions to run when armed in any mode (Away, Home, Night, Vacation, Custom). | No | `[]` |
| **Actions when Triggered** | Custom sequence of actions to run when the alarm is fully triggered. | No | `[]` |

---

## 💡 Important Notes & Pro-Tips

- **Companion Design Principle:** This blueprint does **not** handle or store security PIN codes, nor does it override Alarmo's built-in settings. It listens strictly to state change events published by your Alarmo panel.
- **Audio & Visual Alerts:** This blueprint is ideal for building custom exit countdown warnings (e.g., TTS announcements over smart speakers), ambient status cues, or emergency light-flashing sequences.
- **Error Handling & Offline Devices:** By default, Home Assistant halts execution of an action sequence if a single step fails (such as an offline speaker or unresponsive light bulb). To ensure remaining steps continue running during device outages, enable **"Continue on Error"** on individual action steps within the Home Assistant automation UI editor.
- **Safe Empty Execution:** If you leave any of the four action slots blank when instantiating an automation, Home Assistant gracefully skips that state event without logging errors.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Falarmo_state_manager.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`alarmo_state_manager.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/alarmo_state_manager.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `alarmo_state_manager.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/alarmo_state_manager.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.


## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-11-01 | Initial release |
