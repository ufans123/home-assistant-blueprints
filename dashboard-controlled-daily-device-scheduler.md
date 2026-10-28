# Daily Dashboard-Controlled Device Scheduler

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdashboard_controlled_daily_device_scheduler.yaml)

> **Version:** 2.1 | **Initial Release:** 2026-10-28 | [← Back to Main Blueprints Repository](README.md)

A dynamic Home Assistant companion blueprint based on the **[Daily Time-Based Device Scheduler](daily-time-based-device-scheduler.md)**. 

While the original blueprint uses hardcoded times set directly within the automation UI, this companion version shifts time management to dashboard-based `input_datetime` helpers. This allows you to adjust scheduled "Turn On" and "Turn Off" times on the fly directly from your dashboard—without ever editing the automation configuration—while retaining full day-of-week filtering, an optional master enable toggle, and smart bidirectional timer synchronization.

## Features

- **Dynamic Dashboard Control:** Adjust "Turn On" and "Turn Off" times directly from a Lovelace card using `input_datetime` helpers in real-time.
- **Optional Master Enable Switch:** Link an `input_boolean` helper to enable or pause the schedule directly from the UI without modifying or disabling the automation itself.
- **Day-of-Week Filtering:** Toggle individual days of the week (`Mon`–`Sun`) on or off inside the automation settings.
- **Optional Bidirectional Timer Sync:** Link a timer helper (`timer.*`) for live countdown tracking on your dashboard. The blueprint automatically manages timer lifecycle events:

  | Event | Action Taken |
  | :--- | :--- |
  | **Schedule Starts** | Starts the timer with the dynamically calculated duration between On and Off helpers. |
  | **Device Turned On Manually / Mid-Schedule** | Detects physical or external turn-on events and starts the timer countdown using the **smart remaining time** left until the scheduled off-time helper. |
  | **Timer Ends or Cancelled** | Automatically turns off the controlled device. |
  | **Device Turned Off** | Automatically cancels the running timer helper. |
  | **Home Assistant Restarts** | Evaluates whether the device is on after a reboot, syncing the timer to the exact remaining time left in the schedule rather than restarting the full duration. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Device to Control** | The switch, light, or fan entity to automate. | **Yes** | N/A |
| **Turn On Time Helper** | An `input_datetime` helper (time mode) set from your dashboard. | **Yes** | N/A |
| **Turn Off Time Helper** | An `input_datetime` helper (time mode) set from your dashboard. | **Yes** | N/A |
| **Enable/Disable Switch (Optional)** | An `input_boolean` helper to toggle the schedule on/off from your dashboard. | No | *Blank (Always Enabled)* |
| **Timer Helper (Optional)** | A timer helper (`timer.*`) to track countdowns and enable sync. | No | *Blank (Disabled)* |
| **Monday – Sunday** | Individual day toggles to restrict scheduled execution. | No | `true` (All enabled) |

---

## 🎛️ Setting Up Dashboard Controls

To control your schedule from your Lovelace dashboard, create your helpers first and then add them to a card.

### Step 1: Create the Required Helpers
Navigate to **Settings > Devices & Services > Helpers** and create:
1. **Turn On Time:** `input_datetime` (Mode: **Time**)
2. **Turn Off Time:** `input_datetime` (Mode: **Time**)
3. *(Optional)* **Enable Switch:** `input_boolean` (Toggle switch)
4. *(Optional)* **Timer:** `timer` (Duration: `00:00:00`, turn on **Restore** option)

### Step 2: Add to Your Dashboard
Add an **Entities Card** (or a custom card like Tile / mod-card) to your dashboard so you can adjust the schedule anytime:

```yaml
type: entities
title: 🌱 Smart Garden Schedule
entities:
  - entity: input_boolean.plant_schedule_enabled
    name: Schedule Active
  - entity: input_datetime.plant_start_time
    name: Turn On Time
  - entity: input_datetime.plant_end_time
    name: Turn Off Time
  - entity: timer.plant_timer
    name: Countdown Timer
```
---

## 💡 Important Notes & Pro-Tips

- **Required Helpers:** Before creating an automation from this blueprint, create two `input_datetime` helpers (Time-only mode) under **Settings > Devices & Services > Helpers**. Optionally create an `input_boolean` if you want master-enable control from your dashboard.
- **Manual Override & Smart Recovery:** If the device is flipped on manually or after a system restart midway through an active schedule, the automation automatically calculates and syncs to the *remaining time* left until the off-time helper value.
- **Timer Restarts & Power Loss Safety:** If you use an optional timer helper, make sure to enable the **"Restore"** option in its helper settings (`Settings > Devices & Services > Helpers`). This allows the timer to survive Home Assistant system restarts and accurately finish the countdown.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdashboard_controlled_daily_device_scheduler.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`dashboard_controlled_daily_device_scheduler.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/dashboard_controlled_daily_device_scheduler.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `dashboard_controlled_daily_device_scheduler.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/dashboard_controlled_daily_device_scheduler.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v2.1** | 2026-10-28 | Added optional `input_boolean` master enable switch; expanded trigger-level variables for invalid Jinja `!input` parsing fixes; added dynamic timer duration calculations for `input_datetime` helpers. |
| **v2.0** | 2026-10-27 | Initial release of dashboard-controlled companion blueprint. |
