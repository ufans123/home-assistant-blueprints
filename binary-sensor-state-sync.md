# Binary Sensor State Sync

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbinary_sensor_state_sync.yaml)

> **Version:** 1.1 | **Initial Release:** 2026-10-16 | [← Back to Main Blueprints Repository](README.md)

A clean, bulletproof Home Assistant blueprint for directly syncing the state of any binary sensor (such as a door, window, or motion sensor) to an input boolean, switch, or light. This blueprint uses explicit state mapping to eliminate toggle out-of-sync issues, making it ideal for climate automations (like pausing your AC when a door opens).

## Features

- **Direct State Mirroring:** Automatically tracks and mirrors `on` and `off` states precisely without relying on toggling logic.
- **Self-Correcting:** If a door or window changes state while Home Assistant is restarting, the next state change immediately forces complete alignment.
- **Multi-Domain Target Support:** Sync your sensors to input booleans, virtual switches, or indicator lights effortlessly.
- **Bi-directional State Sync:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Binary Sensor Turns On** | Immediately turns on the target entity (`input_boolean`, `switch`, or `light`). |
  | **Binary Sensor Turns Off** | Immediately turns off the target entity. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Binary Sensor** | The door sensor, window sensor, or binary sensor to monitor. | **Yes** | N/A |
| **Target Entity** | The entity to sync the state to (e.g., an `input_boolean` helper or switch). | **Yes** | N/A |

---

## 💡 Important Notes & Pro-Tips

- **AC / Climate Automation Integration:** Use an `input_boolean` helper as your target entity. This serves as a clean middleman to pause your AC or heating automations whenever a door or window is left open.
- **Restart Mode:** The automation uses `mode: restart` to handle rapid or overlapping state triggers smoothly without getting stuck.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbinary_sensor_state_sync.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`binary_sensor_state_sync.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/binary_sensor_state_sync.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `binary_sensor_state_sync.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/binary_sensor_state_sync.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-16 | Initial release |
