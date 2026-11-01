# Trigger on a Specific Date and Time

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftrigger_on_a_specific_date_time.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-10-31 | [← Back to Main Blueprints Repository](README.md)

A clean, lightweight Home Assistant blueprint designed to fire a one-time automation at a precisely defined date and time. Perfect for scheduling future single-occurrence events, reminders, seasonal actions, or scheduled system tweaks.

---

> ⚠️ **Prerequisites:**
> - No special integrations or helpers are required! This blueprint uses Home Assistant's native time trigger and template condition.

---

## Features

- **Specific Date & Time Targeting:** Define an exact calendar date (`YYYY-MM-DD`) and clock time (`HH:MM:SS`) for your automation to trigger.
- **Precision Matching:** Checks the system time dynamically against your chosen date to ensure actions only fire when both the date and time match.
- **Customizable Actions:** Run any native Home Assistant action or sequence of actions when the scheduled time arrives (e.g., send notifications, toggle lights, or run scenes).
- **Lightweight & Efficient:** Executes a simple check on daily time matches without requiring complex persistent helpers or external dependencies.
- **Operation Summary:**

  | Event | Action Taken |
  | :--- | :--- |
  | **Time Target Reached (Date Matches)** | Validates that today's date matches your target date and executes all configured custom actions. |
  | **Time Target Reached (Date Mismatch)** | Evaluates the condition template to `false` and safely halts execution without running actions. |
  | **After Trigger Execution** | The automation stays idle and will evaluate to `false` on all subsequent days unless reconfigured. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Target Date** | Pick the exact date (`YYYY-MM-DD`) for the automation to run. | **Yes** | N/A |
| **Target Time** | What time should the actions run on that day? | **Yes** | `08:00:00` |
| **Actions** | Define what actions or sequences should happen on this date. | **Yes** | N/A |

---

## 💡 Important Notes & Pro-Tips

- **Post-Execution Cleanup or Reuse:** Once the target date and time pass and the automation runs, Home Assistant does **not** automatically delete the automation. You can safely:
  - **Delete or Disable:** Remove or turn off the created automation instance from your Home Assistant UI (`Settings > Automations & Scenes`).
  - **Reuse for Future Events:** Simply edit the automation in the UI and pick a new target date and time for another upcoming event.
- **One-Time Execution:** While the time trigger checks daily at the specified target time, the blueprint's condition ensures the actions **only execute once** on the specific date selected.
- **Past Target Dates:** If you select a date that has already passed, the condition template will evaluate to `false` and the automation will not execute.
- **Single Mode Guard:** The blueprint runs in `single` mode to prevent duplicate concurrent runs if multiple triggers occur at the same exact timestamp.
- **System Clock Reliance:** Ensures actions are triggered using your Home Assistant instance's local time zone configuration (`now()`).

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftrigger_on_a_specific_date_time.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`trigger_on_a_specific_date_time.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/trigger_on_a_specific_date_time.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `trigger_on_a_specific_date_time.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/trigger_on_a_specific_date_time.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (`Settings > Automations & Scenes > Blueprints`).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-31 | Initial release |
