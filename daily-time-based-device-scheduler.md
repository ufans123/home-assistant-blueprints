# Daily Time-Based Device Scheduler with Optional Timer

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_time_based_device_scheduler.yaml)

> **Version:** 1.2 | **Last Updated:** 2026-11-05 | [← Back to Main Blueprints Repository](README.md)

A robust, "set-and-forget" Home Assistant blueprint for scheduling multiple switches, lights, and fans with built-in day-of-week filtering and **fully optional, bidirectional timer synchronization**. This blueprint includes edge-case handling for manual physical overrides and smart recovery logic after system reboots or mid-schedule turn-ons.

## Use Cases

- **Automated Landscape & Holiday Lighting:** Schedule outdoor porch lights, garden lights, or holiday displays to turn on automatically at 18:00 and off at 23:00 every day. Syncing with a timer gives family members a real-time countdown on dashboard wall tablets showing when the lights will turn off.
- **Overnight Fan & White Noise Control:** Turn on bedroom fans or white noise air purifiers at 22:00 and turn them off at 06:30 only on weekdays (`Mon`–`Fri`). If you wake up and turn the fan on manually in the middle of the night, smart recovery instantly calculates the remaining time until 06:30 and synced timers keep it on schedule without manual intervention.
- **Living Room Entertainment & Accent Scene:** Synchronize ambient floor lamps, TV LED backlight strips, and plug-in accent lights across the living room to kick off every evening on weekends (`Fri`–`Sun`). Turning off one switch or cancelling the timer turns off all grouped accent lights together.

---

## Features

- **Flexible Time Scheduling:** Easily set daily Turn On and Turn Off times directly in the UI.
- **Multi-Device Support:** Select multiple switches, lights, or fans to control simultaneously under a single schedule.
- **Day-of-Week Filtering:** Toggle individual days of the week (`Mon`–`Sun`) on or off. 
- **Optional Bidirectional Timer Sync:** Link a timer helper (`timer.*`) for live dashboard tracking. The blueprint keeps the timer and devices in sync automatically:

  | Event | Action Taken |
  | :--- | :--- |
  | **Schedule Starts** | Starts the timer with the calculated duration between On and Off times. |
  | **Devices Turned On Manually / Mid-Schedule** | Detects physical or external turn-on events and starts the timer countdown using the **smart remaining time** left until the scheduled off-time. |
  | **Timer Ends or Cancelled** | Automatically turns off all controlled devices. |
  | **Devices Turned Off** | Automatically cancels the running timer helper. |
  | **Home Assistant Restarts** | Evaluates whether any controlled device is on after a reboot, syncing the timer to the exact remaining time left in the schedule rather than restarting the full duration. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Devices to Control** | One or more switch, light, or fan entities to automate. | **Yes** | N/A |
| **Turn On Time** | Time of day to turn the devices on. | **Yes** | N/A |
| **Turn Off Time** | Time of day to turn the devices off. | **Yes** | N/A |
| **Timer Helper (Optional)** | A timer helper (`timer.*`) to track countdowns and enable sync. | No | *Blank (Disabled)* |
| **Monday – Sunday** | Individual day toggles to restrict scheduled execution. | No | `true` (All enabled) |

---

## 💡 Important Notes & Pro-Tips

- **Manual Override & Smart Recovery:** If any device is flipped on manually or after a system restart midway through an active schedule, the automation automatically calculates and syncs to the *remaining time* left until the off-time rather than restarting the full total duration.
- **Disabling the Schedule:** If you uncheck all day-of-week toggles, the scheduled on/off automation actions will never execute, acting identically to pausing or disabling the automation.
- **Timer Restarts & Power Loss Safety:** If you use an optional timer helper, make sure to enable the **"Restore"** option in its helper settings (`Settings > Devices & Services > Helpers`). This allows the timer to survive Home Assistant system restarts and accurately finish the countdown.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdaily_time_based_device_scheduler.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`daily_time_based_device_scheduler.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_time_based_device_scheduler.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `daily_time_based_device_scheduler.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/daily_time_based_device_scheduler.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI
3. In the bottom right corner click on the *'Import blueprint'* button
4. Paste in the URL and follow the prompts

---
## Related Links
| Blueprint | Description |
| :--- | :--- |
| **[Daily Dashboard-Controlled Device Scheduler](dashboard-controlled-daily-device-scheduler.md)** | Dynamic scheduler for switches, lights, or fans driven by `input_datetime` helpers on your dashboard, featuring day-of-week filtering, an optional enable toggle, and dynamic timer synchronization. |
| **[Daily Sun-Based Multi-Device Scheduler with Sunrise Off & Optional Timer](daily-sunset-sunrise-device-scheduler.md)** | Control multiple switches, lights, or fans using dynamic sunset/sunrise triggers with custom offsets, featuring optional bidirectional timer synchronization and selective multi-device shutoff. |
| **[Daily Sun-Based Device Scheduler](daily-sun-based-device-scheduler.md)** | Schedule switches, lights, or fans using sunset and day-of-week rules with optional bidirectional timer synchronization and smart remaining-time recovery. |
| **[Daily Sun-Based Multi-Device & Multi-Scene Scheduler with Timer](daily-sun-based-multi-device-scheduler-with-scenes.md)** | Schedule multiple switches, lights, fans, and scenes using sunset rules and day-of-week filtering, featuring bidirectional timer synchronization and smart remaining-time recovery. | 
| **[Trigger on a Specific Date and Time](trigger-on-a-specific-date-time.md)** | Fires a one-time automation at a precisely defined calendar date and time for single-occurrence events, reminders, or seasonal actions. | 
---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.2** | 2026-11-05 | Added support for selecting multiple target devices |
| **v1.1** | 2026-10-28 | Minor UI Improvements for Clarity |
| **v1.0** | 2026-10-10 | Initial release |
