## Battery Level & Status Monitor (Scheduled & Manual)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flow_battery_alert.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint scans all entities with `device_class: battery` across your Home Assistant instance. It supports dual scheduling modes (once daily or recurring hourly intervals), delivers flexible notification options (mobile app push, persistent UI cards, or both), and includes manual check capabilities with optional dashboard links.

### Features
- **Automatic Device Scanning:** Dynamically scans all entities configured with `device_class: battery` across Home Assistant.
- **Low & Offline Detection:** Flags battery levels below your configurable percentage threshold as well as sensors reporting `unknown` or `unavailable`.
- **Dual Scheduling Engine:** 
  - **Once Daily:** Run the check at a specific time of day (e.g., `08:00:00`).
  - **Recurring Interval:** Repeat the check automatically every $N$ hours (e.g., every 6, 12, or 24 hours).
- **Flexible Notification Modes:** Choose between **Mobile App Only**, **Persistent Notification Only**, or **Both**.
- **Formatted Mobile Push:** Cleanly formatted mobile notifications with explicit line breaks for easy reading on iOS and Android.
- **Optional Dashboard Link:** Attach a custom URL or dashboard path (e.g., `/maintenance`) directly to persistent notifications.
- **Optional Manual Check:** Link an optional `input_boolean` helper to trigger an immediate battery scan on demand.
- **All Clear Feedback:** Sends an explicit "All Clear" confirmation notification when triggered manually if no batteries require attention, then automatically turns the helper off.
- **Automatic Dismissal:** Automatically dismisses persistent UI notifications during scheduled runs once all battery issues are resolved.
- **Consistent Notification ID:** Uses a uniform `notification_id` (`low_battery_alert`) to update or clear web UI alerts cleanly without clogging your notification center.

---

### Input Configuration Reference

#### Section 1: Schedule Mode
| Input | Type | Description |
| :--- | :--- | :--- |
| **Schedule Type** | Select | Choose whether to check once daily at a fixed time (`daily`) or repeatedly every N hours (`interval`). Default: `daily`. |

#### Section 2: Daily Schedule Settings
| Input | Type | Description |
| :--- | :--- | :--- |
| **Daily Check Time** | Time | Time of day to run the check when 'Once Daily' mode is selected. Default: `08:00:00`. |

#### Section 3: Interval Schedule Settings
| Input | Type | Description |
| :--- | :--- | :--- |
| **Check Interval (Hours)** | Number | How often to repeat the check in hours (e.g., 6, 12, or 24) when 'Recurring Interval' mode is selected. Default: `12`. |

#### Section 4: Advanced / Manual Control
| Input | Type | Description |
| :--- | :--- | :--- |
| **Manual Trigger Helper (Optional)** | Entity (`input_boolean`) | An optional helper entity to trigger an on-demand check with explicit feedback. Resets back to `off` automatically. Leave blank if not used. |

#### Section 5: Alert & Dashboard Settings
| Input | Type | Description |
| :--- | :--- | :--- |
| **Battery Threshold (%)** | Number (Slider) | The percentage threshold below which batteries will be flagged (Default: `20%`). |
| **Notification Method** | Select | Choose how alerts are delivered: `Mobile App Only`, `Persistent Notification Only`, or `Both`. Default: `persistent`. |
| **Mobile Notification Targets** | Target | Select one or more mobile phone devices, targets, or notification groups to receive push alerts. |
| **Dashboard Link (Optional)** | Text | Path or URL to include in persistent notifications (e.g., `/maintenance`). Clear to omit. |

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flow_battery_alert.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `low_battery_alert.yaml` file from this repository. [`low_battery_alert.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/low_battery_alert.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `low_battery_alert.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/low_battery_alert.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI
3. In the bottom right corner click on the *'Import blueprint'* button
4. Paste in the URL and follow the prompts
