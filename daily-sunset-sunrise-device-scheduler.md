## Daily Sun-Based Multi-Device Scheduler with Sunrise Off & Optional Timer

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_sunset_sunrise_device_scheduler.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-10-23 | [← Back to Main Blueprints Repository](README.md)

This automation blueprint provides a dynamic, robust scheduler that automatically turns multiple target devices **on** at sunset and **off** at sunrise, complete with custom `HH:MM:SS` offset support. It includes optional bidirectional synchronization with a Home Assistant **timer helper**, allowing for visual dashboard countdowns and smart multi-device selective shutoff.

### Features
- **Dynamic Sun-Based Scheduling:** Automatically triggers turn-on at sunset and turn-off at sunrise, using real-time solar tracking.
- **Customizable Offsets:** Fine-tune turn-on and turn-off times with custom `HH:MM:SS` positive or negative offsets (e.g., turn on 30 minutes before sunset).
- **Optional Timer Sync:** Connect a `timer.*` helper to track countdowns dynamically to the next sunrise offset.
- **Selective Shutoff Logic:** Turning off a single device while others remain active keeps the countdown running; the timer helper is only cancelled when **all** target devices are turned off.
- **Manual Control & Reboot Resilience:** Turning any target device on manually syncs the timer helper to the remaining duration until sunrise. Automatically recalculates and restarts the timer countdown if Home Assistant reboots while devices are on.
- **Day-of-Week Filtering:** Easily toggle which days of the week the schedule is permitted to execute.
- **Multi-Device Support:** Control lights, switches, or fans individually or as a synchronized group.

### Input Configuration Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Devices to Control** | Entity Selector (`switch`, `light`, `fan`, multiple) | Select the target entities to schedule and synchronize. |
| **Sunset Offset** | Text (`HH:MM:SS`) | Time offset relative to sunset to turn devices on (e.g., `-00:30:00`). |
| **Sunrise Offset** | Text (`HH:MM:SS`) | Time offset relative to sunrise to turn devices off (e.g., `00:00:00`). |
| **Timer Helper (Optional)** | Entity Selector (`timer`) | Optional helper (`timer.*`) for visual countdowns and state tracking. Leave blank to disable. |
| **Active Days** | Boolean Toggles (Mon–Sun) | Configure which days of the week the sunset execution is permitted to run. |

### Pro Tips
- **Dashboard Countdown:** Add your selected `timer.*` helper to a Dashboard Timer card to give family members a visible live countdown of when lights will shut off.
- **Manual Shutoff:** Manually stopping or cancelling the timer helper on your dashboard will instantly turn off all associated target devices.
- **Selective Control:** Feel free to turn off individual lights during the night—the countdown will continue as long as at least one target device remains on.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_sunset_sunrise_device_scheduler.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `daily_sunset_sunrise_device_scheduler.yaml` file from this repository. [`daily_sunset_sunrise_device_scheduler.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_sunset_sunrise_device_scheduler.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `daily_sunset_sunrise_device_scheduler.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_sunset_sunrise_device_scheduler.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-23 | Initial release. |
