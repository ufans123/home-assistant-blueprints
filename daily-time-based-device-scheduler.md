# Daily Time-Based Device Scheduler with Optional Timer

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_time_based_device_scheduler.yaml)

[← Back to Main Blueprints Repository](README.md)

A robust, "set-and-forget" Home Assistant blueprint for scheduling switches, lights, and fans with built-in day-of-week filtering and **fully optional, bidirectional timer synchronization**. This blueprint includes edge-case handling for manual physical overrides and system power loss survival.

## Features

* **Flexible Time Scheduling:** Easily set daily Turn On and Turn Off times directly in the UI.
* **Day-of-Week Filtering:** Toggle individual days of the week (`Mon`–`Sun`) on or off. 
* **Optional Bidirectional Timer Sync:** Link a timer helper (`timer.*`) for live dashboard tracking. The blueprint keeps the timer and device in sync automatically:

  | Event | Action Taken |
  | :--- | :--- |
  | **Schedule Starts** | Starts the timer with the calculated duration between On and Off times. |
  | **Device Turned On Manually** | Detects physical or external turn-on events and starts the timer countdown to prevent the device from being left running indefinitely. |
  | **Timer Ends or Cancelled** | Automatically turns off the controlled device. |
  | **Device Turned Off** | Automatically cancels the running timer helper. |
  | **Home Assistant Restarts** | Evaluates whether the device is stuck in an orphan "on" state while the system was offline, executing an emergency safety shutdown if the timer expires mid-reboot. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Device to Control** | The switch, light, or fan entity to automate. | **Yes** | N/A |
| **Turn On Time** | Time of day to turn the device on. | **Yes** | N/A |
| **Turn Off Time** | Time of day to turn the device off. | **Yes** | N/A |
| **Timer Helper (Optional)** | A timer helper (`timer.*`) to track countdowns and enable sync. | No | *Blank (Disabled)* |
| **Monday – Sunday** | Individual day toggles to restrict scheduled execution. | No | `true` (All enabled) |

---

## 💡 Important Notes & Pro-Tips

* **Manual Override & Loop Protection:** If the device is flipped on manually outside of the schedule, the automation automatically catches it and starts the timer countdown helper. Built-in logic filters prevent this manual state change trigger from starting a loop when the automation itself fires the schedule.
* **Disabling the Schedule:** If you uncheck all day-of-week toggles, the scheduled on/off automation actions will never execute, acting identically to pausing or disabling the automation.
* **Timer Restarts & Power Loss Safety:** If you use an optional timer helper, make sure to enable the **"Restore"** option in its helper settings (`Settings > Devices & Services > Helpers`). This allows the timer to survive Home Assistant system restarts and accurately finish the countdown. If the system is offline for an extended duration and boots back up *after* the timer was supposed to expire, the blueprint executes an emergency shutdown loop on boot to safeguard hardware from staying stuck on.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_time_based_device_scheduler.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`daily_time_based_device_scheduler.yaml`](daily_time_based_device_scheduler.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `daily_time_based_device_scheduler.yaml`.
4. Reload your automations or restart Home Assistant.
