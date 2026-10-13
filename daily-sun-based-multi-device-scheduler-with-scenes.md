# Daily Sun-Based Multi-Device & Multi-Scene Scheduler with Timer

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_sun_based_multi_device_scheduler_with_scenes.yaml)

[← Back to Main Blueprints Repository](README.md)

A robust, "set-and-forget" Home Assistant blueprint for scheduling multiple devices (switches, lights, fans) and activating multiple scenes automatically at **sunset with a custom offset**, turning off at a fixed time. It features built-in day-of-week filtering and **bidirectional timer synchronization** that seamlessly bridges scene activations and manual overrides with live countdown tracking.

## Features

- **Sunset-Based Scheduling:** Automatically turns devices on or applies scenes relative to sunset with positive or negative offsets (e.g., `-00:30:00` for 30 minutes before sunset).
- **Multi-Device & Multi-Scene Support:** Control multiple switches, lights, or fans simultaneously, and/or trigger multiple scenes at sunset.
- **Fixed Turn Off Time:** Easily specify an off-time directly in the UI.
- **Day-of-Week Filtering:** Toggle individual days of the week (`Mon`–`Sun`) on or off. 
- **Bidirectional Timer Sync:** Link a timer helper (`timer.*`) for live dashboard tracking. The blueprint keeps the timer and devices in sync automatically:

  | Event | Action Taken |
  | :--- | :--- |
  | **Sunset Trigger Starts** | Activates selected scenes, turns on target devices, and starts the timer with the calculated duration remaining until the scheduled Off time. |
  | **Device Turned On Manually / Via Scene** | Detects state changes on your required target devices (including devices included in scenes) and starts the timer countdown using the **smart remaining time** left until the scheduled off-time. |
  | **Timer Ends or Cancelled** | Automatically turns off the controlled devices. |
  | **Device Turned Off** | Automatically cancels the running timer helper. |
  | **Home Assistant Restarts** | Evaluates whether any target device is on after a reboot, syncing the timer to the exact remaining time left in the schedule rather than restarting a fixed duration. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Devices to Control** | Switches, lights, or fans to turn on/off and sync with the timer if toggled manually or via scene activation. | **Yes** | N/A |
| **Turn On Scenes (Optional)** | One or more scenes to activate at sunset alongside your devices. | No | `[]` (None) |
| **Sunset Offset** | Offset relative to sunset in `HH:MM:SS` text format. Use a minus sign for *before* sunset (e.g., `-00:30:00`) or positive for *after* sunset (e.g., `00:15:00`). | No | `-00:30:00` |
| **Turn Off Time** | Fixed time of day to turn the devices off. | **Yes** | N/A |
| **Timer Helper (Optional)** | A timer helper (`timer.*`) to track countdowns and enable sync. | No | *Blank (Disabled)* |
| **Monday – Sunday** | Individual day toggles to restrict scheduled execution. | No | `true` (All enabled) |

---

## 💡 Important Notes & Pro-Tips

- **Scenes & Timer Integration:** Because scenes are stateless snapshots, they do not trigger timers on their own when re-activated. However, by requiring **Devices to Control**, any device included in your scene that is also listed under your target devices will seamlessly trigger and sync the timer when flipped on at sunset.
- **Entering Offsets:** Because sunset times change dynamically throughout the year, the `Sunset Offset` input uses text formatting (`HH:MM:SS`). Enter a minus sign for time before sunset (e.g., `-00:45:00`) or a positive format for time after sunset (e.g., `00:20:00`).
- **Manual Override & Smart Recovery:** If devices are flipped on manually or after a system restart midway through an active schedule, the automation automatically calculates and syncs to the *remaining time* left until the off-time rather than restarting a fixed total duration.
- **Disabling the Schedule:** If you uncheck all day-of-week toggles, the scheduled on/off automation actions will never execute, acting identically to pausing or disabling the automation.
- **Timer Restarts & Power Loss Safety:** If you use an optional timer helper, make sure to enable the **"Restore"** option in its helper settings (`Settings > Devices & Services > Helpers`). This allows the timer to survive Home Assistant system restarts and accurately finish the countdown.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_sun_based_multi_device_scheduler_with_scenes.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`daily_sun_based_multi_device_scheduler_with_scenes.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_sun_based_multi_device_scheduler_with_scenes.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `daily_sun_based_multi_device_scheduler_with_scenes.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_sun_based_multi_device_scheduler_with_scenes.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI
3. In the bottom right corner click on the *'Import blueprint'* button
4. Paste in the URL and follow the prompts
