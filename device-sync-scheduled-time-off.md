# Sync Device and Scheduled Off-Time

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_sync_scheduled_time_off.yaml)

[← Back to Main Blueprints Repository](README.md)

A clean, flexible Home Assistant blueprint for syncing switches, lights, and fans with a designated daily turn-off time. This blueprint uses a native UI time picker to dynamically calculate countdown durations from **now** until the scheduled target off-time (with automatic overnight rollover support) and features **optional timer synchronization** for UI dashboard tracking.

## Features

- **Native UI Time Picker:** Easily set the target turn-off time directly in the automation interface without needing helper entities.
- **Dynamic Duration Calculation:** Automatically calculates remaining seconds from the moment the device turns on until the targeted turn-off time (handling overnight schedules past midnight effortlessly).
- **Optional Timer Sync:** Optionally link a timer helper (`timer.*`) for live countdown visibility on dashboards.
- **Bi-directional State Sync:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Device Turned On** | Calculates seconds until off-time and starts the optional timer with the exact remaining duration. |
  | **Device Turned Off** | Automatically cancels the running optional timer helper. |
  | **Timer Expires** | Automatically turns off the controlled device when the countdown completes. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Target Device** | The switch, light, or fan entity to control and sync. | **Yes** | N/A |
| **Target Turn-Off Time** | Time of day when the device should turn off. | **Yes** | N/A |
| **Optional Timer Helper** | A timer helper (`timer.*`) to track duration for dashboard cards. | No | *Blank (Disabled)* |

---

## 💡 Important Notes & Pro-Tips

- **Overnight Rollover Support:** The embedded Jinja calculation checks if the selected turn-off time is earlier in the day than the current time (e.g., turning on a device at 10:00 PM with a turn-off time set to 2:00 AM) and automatically adds 24 hours (86,400 seconds) to ensure the target duration is computed accurately.
- **Dashboard Visibility:** If you choose to attach a timer helper, make sure to enable the **"Restore"** option in its settings (`Settings > Devices & Services > Helpers`) so the timer state survives Home Assistant reboots cleanly.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_sync_scheduled_time_off.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`device_sync_scheduled_time_off.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/device_sync_scheduled_time_off.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `device_sync_scheduled_time_off.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/device_sync_scheduled_time_off.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
