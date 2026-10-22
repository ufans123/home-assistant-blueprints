# Manual Z-Wave Outlet Restart (Router Reboot)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fmanual_zwave_reboot.yaml)

> **Version:** 1.1 | **Initial Release:** 2026-10-20 | [← Back to Main Blueprints Repository](README.md)

A robust, safe Home Assistant blueprint designed to automate a controlled power-cycle sequence for network routers or modems using a Z-Wave smart plug, featuring dynamic duration estimates, cooldown stabilization, trigger resets, and optional mobile notifications.

---

> ⚠️ **Prerequisites & Important Warning:**
> - **Z-Wave Mesh:** Ensure you use a reliable Z-Wave smart plug that can maintain its connection or recover cleanly when power is cut.
> - **Hardware Safety:** Do **NOT** use a regular non-Z-Wave plug or apply this blueprint to sensitive equipment requiring a graceful shutdown (such as a NAS or computer running filesystems). This blueprint is designed for hard power-cycling routers, modems, or network gear.
> - **Trigger Helper:** Create a toggle helper (`input_boolean.*`) or dedicated switch in Home Assistant (`Settings > Devices & Services > Helpers`) to act as the restart trigger button.

---

## Features

- **Controlled Power Sequence:** Powers down the outlet, waits for a user-specified duration (default: 30s), restores power, and enforces a stabilization cooldown before concluding.
- **Single Execution Guard (`mode: single`):** Prevents overlapping restart cycles if the trigger helper is flipped multiple times while a reboot process is actively running.
- **Dynamic Duration Math:** Uses Jinja2 templates to automatically calculate and display the total cycle duration inside the initial start notification based on your custom slider inputs.
- **Auto-Resetting Trigger Entity:** Automatically turns off the trigger entity (`input_boolean` or switch) at the end of the cooldown period so it is always ready for the next manual restart.
- **Mobile Push Notifications:** Sends customizable push notifications before the restart begins and after the cooldown cycle completes (optional).
- **Operation Summary:**

  | Event | Action Taken |
  | :--- | :--- |
  | **Trigger Switch Flipped `on`** | Sends optional start notification with calculated cycle duration. |
  | **Power Cut (`switch.turn_off`)** | Turns off the Z-Wave outlet for the defined `off_duration` seconds. |
  | **Power Restored (`switch.turn_on`)** | Turns the Z-Wave outlet back on and holds for the `cooldown_duration` minutes. |
  | **Cycle Completed** | Resets the trigger entity back `off` and sends the optional completion notification. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Trigger Entity** | The `input_boolean` or `switch` entity used to initiate the restart. | **Yes** | N/A |
| **Z-Wave Smart Plug** | The Z-Wave plug or switch connected to your router/modem (`switch.*`). | **Yes** | N/A |
| **Power Off Duration (Seconds)** | How long to keep the outlet powered off before restoring power. | Yes | `30` |
| **Cooldown Duration (Minutes)** | Stabilization delay after restoring power before resetting trigger and notifying. | Yes | `5` |
| **Notification Target (Optional)** | Mobile device target (`mobile_app_*`) for push notifications. Leave empty to disable. | No | `""` |
| **Start Notification Title** | Custom title for the initial restart push notification. | No | `"Reboot Triggered"` |
| **Start Notification Message** | Custom body text sent at start (cycle timing is automatically appended). | No | `"Internet connection will be temporarily interrupted."` |
| **Completion Notification Title** | Custom title for the completion push notification. | No | `"Reboot Completed"` |
| **Completion Notification Message** | Custom body text sent when the full cycle concludes. | No | `"Network connectivity should be restored."` |

---

## 💡 Important Notes & Pro-Tips

- **Notification Delivery Delays:** Push notifications sent through the mobile app rely on external cloud messaging services (FCM/APNs) and mobile OS background processes. If your phone is in Doze/Low Power mode or if local network routing transitions right as power cuts, push notifications may arrive with a slight delay. The notification timestamp tracks automation initiation, not necessarily instant mobile push arrival.
- **Cycle Duration vs. Router Boot Time:** The calculated total duration in the start notification (`cooldown_duration` + `off_duration`) represents the script execution time and plug power state. Actual router hardware boot times may vary depending on your network gear.
- **Concurrent Trigger Prevention:** Because the blueprint utilizes `mode: single` and maintains the trigger entity in an `on` state throughout the entire sequence, accidental manual toggles while a reboot is active will be safely ignored.
- **Error Resiliency:** Notification calls utilize `continue_on_error: true` so that network or mobile service errors will never prevent the plug from restoring power or finishing its cycle.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fmanual_zwave_reboot.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`manual_zwave_reboot.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/manual_zwave_reboot.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `manual_zwave_reboot.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/manual_zwave_reboot.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (`Settings > Automations & Scenes > Blueprints`).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-20 | Initial release |
