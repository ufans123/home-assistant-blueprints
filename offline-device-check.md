# Offline Device Notifications (Scheduled, NFC, Manual Triggers)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2foffline_device_check.yaml)

> **Version:** 1.1 | **Initial Release:** 2026-10-19 |[← Back to Main Blueprints Repository](README.md)

A clean, optimized Home Assistant blueprint designed to monitor critical devices and sensors for offline (`unavailable` or `unknown`) states using a flexible hybrid approach of whitelist labeling, domain filtering, and blacklist exclusion **controlled via flexible triggers (Schedule, NFC, or Manual Helper Switch)**.

---

> ⚠️ **Prerequisites:**
> - **Mandatory Device Labeling:** This blueprint relies entirely on Home Assistant's native labeling engine. **Before setting up this blueprint, you must create and apply labels** (`Settings > Areas & Zones > Labels`) to the specific devices/entities you wish to monitor.
> - **Input Boolean / Helper (Optional):** If you plan to use an on-demand manual trigger switch, create your helper entity first in Home Assistant (`Settings > Devices & Services > Helpers`).

---

## 🏷️ Setting Up Your Device Labels (Required First Step)

Because this blueprint uses Home Assistant's native labeling system for precise monitoring, labeling requires a bit of initial effort—but pays off with total control over false alarms:

1. **Create Your Core Labels:** Navigate to **Settings > Areas & Zones > Labels** in Home Assistant and create your labels (e.g., `Smart Plug`, `Light`, `Ignore Offline`).
2. **Tag Individual Devices/Entities (Not Groups or Parent Devices):** For Groups lights its is recommended to label individual lights, for multi-outlet devices like power bars, tag each individual child entity (`switch.power_bar_plug_1`, `switch.power_bar_plug_2`) rather than the parent container. This ensures you receive exact pinpoint alerts when a single endpoint drops offline.
3. **Blacklist Problematic Entities:** Assign an ignore label (e.g., `Ignore Offline`) to devices you turn off or unplug seasonally. Sleepy battery devices (like some water sensors) that frequently drift into `unknown` states to prevent false alerts.

---

## Features

- **Multi-Trigger Architecture:** Run scans automatically via a configured time interval schedule, by scanning an NFC tag, or instantly using a manual helper switch (toggle or button).
- **Auto-Resetting Helper Switch:** Turning on your input boolean or switch helper triggers the audit and instantly resets the helper back to `off` (acting like a momentary push button so it's always ready for the next check).
- **Granular Whitelist Labeling:** Target specific physical devices and child entities (e.g., individual smart plugs, specific lights) by assigning them to monitored labels.
- **Blacklist Ignore Control:** Exclude transiently sleepy devices, configurable multi-sensor sub-features, or finicky hardware by tagging them with an ignore label.
- **Domain Filtering:** Restrict checks to specific entity domains (e.g., `light`, `switch`, `sensor`, `binary_sensor`, `climate`, etc.) to match your exact home setup.
- **Flexible Notification Modes:** Choose between Mobile App push notifications only, persistent UI notifications only, or both.
- **Smart UI Management:** Persistent notifications use a unique ID to automatically update (upsert) in place, avoiding clutter. All-clear schedules cleanly dismiss stale UI notifications automatically.
- **Operation Summary:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Schedule, NFC, or Helper Triggered** | Gathers whitelisted entities, filters by domains, strips out ignored labels, and evaluates core states (`unavailable` / `unknown`). |
  | **Offline Devices Found** | Dispatches a structured mobile notification and/or updates a persistent UI notification listing friendly names and entity IDs. |
  | **All Clear (0 Offline) + Manual Trigger** | Delivers explicit positive feedback confirming all monitored devices are online and functioning normally. |
  | **All Clear (0 Offline) + Scheduled Run** | Quietly dismisses any leftover UI warning notifications without cluttering logs or devices. |
  | **Helper Switch Activated** | Automatically resets the input boolean back `off` immediately after execution so it is ready for the next manual check. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Scan Interval** | How often to check for offline devices (configured in hours/minutes). | **Yes** | 1 Hour |
| **Manual Helper / Button** | Select an `input_boolean`, `switch`, or `input_button` to trigger an on-demand check with feedback. Automatically turns off upon execution. | No | `""` |
| **NFC Tag ID** | Paste the unique tag ID string from your Home Assistant NFC tag event here to trigger an on-demand check with feedback. | No | `""` |
| **Labels to Check (Whitelist)** | Select the labels whose entities you want to monitor for offline status. | **Yes** | `Smart Plug`, `Light` |
| **Labels to Ignore (Blacklist)** | Entities with these labels will be excluded from the check (ideal for sleepy sensors or configurable multi-sensor toggles). | No | `Unavailable` |
| **Entity Domains to Include** | Restrict the check to specific domains (e.g., light, switch, sensor, binary_sensor, etc.). | **Yes** | `light`, `switch` |
| **Notification Method** | Choose how you want to be notified when offline devices are found (`Mobile App Only`, `Persistent Notification Only`, or `Both`). | **Yes** | `both` |
| **Mobile Notification Targets** | Select one or more phone devices, targets, or notification groups. | No | `{}` |
| **Persistent Notification ID** | A unique ID for persistent notifications so it updates in-place instead of spamming new entries in the web UI. | **Yes** | `offline_devices_scan_alert` |

---

## 💡 Important Notes & Pro-Tips

- **Granular vs. Parent Tagging:** Tagging individual child entities (like separate plugs on a power bar or individual bulbs) rather than parent device containers gives you precise, granular troubleshooting data when a single endpoint drops offline.
- **Handling Sleepy Sensors & Multi-Sensors:** Battery-powered devices (like water leak sensors or motion sensors) or multi-sensors with user-configurable feature toggles may occasionally report `unknown` when sleeping or when features are toggled off. Use the **Labels to Ignore (Blacklist)** feature to easily bypass them without altering your broader whitelist.
- **Momentary Trigger Switch Behavior:** When triggered via your helper entity, the blueprint resets the helper back to `off` at the start of execution. This prevents switches from remaining stuck in the `on` position in your dashboard.
- **Flicker-Free Persistent Updates:** Home Assistant's native upsert functionality ensures that ongoing warnings update their message content cleanly in the UI without visual flashing or duplicate entries.

---

## 🙏 Acknowledgements & Credits

- Huge thanks to **[Smart Home Junkie (@SmartHomeJunkie)](https://www.youtube.com/@SmartHomeJunkie)** for the original concept and inspiration behind monitoring unavailable entities and ideas shared on his YouTube channel!

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2foffline_device_check.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`offline_device_check.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/offline_device_check.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `offline_device_check.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/offline_device_check.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (`Settings > Automations & Scenes > Blueprints`).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-19 | Initial release |
