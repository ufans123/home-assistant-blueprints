## Low or Unknown Battery Alert

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flow_battery_alert.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint scans all entities on a daily schedule with `device_class: battery` across your Home Assistant instance. It creates persistent notifications for low or unavailable batteries and provides manual check capabilities via an optional trigger helper.

### Features
- **Automatic Device Scanning:** Scans all entities configured with `device_class: battery` across Home Assistant dynamically.
- **Low & Offline Detection:** Flags battery levels below your configurable percentage threshold as well as sensors reporting `unknown` or `unavailable`.
- **Scheduled Checks:** Automatically checks battery statuses daily at a user-defined time.
- **Optional Manual Check:** Link an optional `input_boolean` helper to trigger an immediate battery check on demand.
- **All Clear Feedback:** Sends an "All Clear" confirmation notification when checked manually if no batteries require attention.
- **Automatic Dismissal:** Automatically dismisses low battery notifications during scheduled runs once all issues are resolved.
- **Consistent Notification ID:** Uses a uniform `notification_id` (`low_battery_alert`) to update or clear notifications cleanly without clogging your notification center.

### Input Configuration Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Daily Check Time** | Time | The scheduled time of day to run the automated battery check. |
| **Manual Trigger Helper (Optional)** | Entity (`input_boolean`) | An optional helper entity to trigger a manual check on demand. Leave blank if not needed. |
| **Battery Threshold (%)** | Number (Slider) | The battery level percentage below which devices will be flagged as low (Default: `20%`). |

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flow_battery_alert.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `low_battery_alert.yaml` file from this repository. [`low_battery_alert.yaml`](low_battery_alert.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `low_battery_alert.yaml`.
4. Go to **Developer Tools** > **YAML** and click **Reload Automation Blueprints** (or restart Home Assistant).
