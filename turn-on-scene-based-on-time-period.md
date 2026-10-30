# Turn On to Time-Based Default Scene

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fturn_on_scene_based_on_time_period.yaml)

> **Version:** 1.0 | **Initial Release** 2026-10-30 | [← Back to Main Blueprints Repository](README.md)

This blueprint automatically sets a light, switch, or input boolean to a specific scene depending on the time of day whenever it turns on from an external source (such as a physical wall switch, app, motion sensor, or voice command).

It allows you to define up to 4 distinct time periods throughout the day. By decoupling scene selection from motion sensors or wall switches, your motion automations stay clean and minimal while this blueprint seamlessly bridges the gap to enforce the correct lighting ambiance for any time of day.

## Features

- **Time-Dependent Scene Selection:** Configure up to 4 separate time windows (e.g., Morning, Afternoon, Evening, Night) with dedicated scenes.
- **Optional Time Slots:** Unused time slots can simply be left blank and will be ignored without causing errors.
- **Overnight Time Window Support:** Full native support for periods spanning across midnight (e.g., 23:00 to 06:00).
- **Graceful Gap Handling:** If the target turns on during an uncovered time of day, no scene is forced, allowing the device to retain its standard default state.
- **Priority-Based Overlap Logic:** Overlapping time windows safely evaluate on a "first match wins" priority (Time Period 1 takes precedence over Period 2, and so on).
- **Decoupled Architecture:** Ideal for pairing with simple motion automations—let the motion sensor handle turning the device `on`/`off`, while this blueprint manages the scene selection.

## Input Configuration

| Section | Input Field | Type | Description |
| :--- | :--- | :--- | :--- |
| **Target Device Settings** | `Target Device` | Entity (`switch`, `light`, `input_boolean`) | The device to monitor for turn-on events. |
| **Time Period 1 (e.g., Morning)** | `Scene` | Entity (`scene`) | Scene to activate during this period. Leave blank to disable. |
| | `Start Time` | Time | Time when Period 1 begins (default: `06:00:00`). |
| | `End Time` | Time | Time when Period 1 ends (default: `12:00:00`). |
| **Time Period 2 (e.g., Afternoon)** | `Scene` | Entity (`scene`) | Scene to activate during this period. Leave blank to disable. |
| | `Start Time` | Time | Time when Period 2 begins (default: `12:00:00`). |
| | `End Time` | Time | Time when Period 2 ends (default: `18:00:00`). |
| **Time Period 3 (e.g., Evening)** | `Scene` | Entity (`scene`) | Scene to activate during this period. Leave blank to disable. |
| | `Start Time` | Time | Time when Period 3 begins (default: `18:00:00`). |
| | `End Time` | Time | Time when Period 3 ends (default: `23:00:00`). |
| **Time Period 4 (e.g., Night)** | `Scene` | Entity (`scene`) | Scene to activate during this period. Leave blank to disable. |
| | `Start Time` | Time | Time when Period 4 begins (default: `23:00:00`). |
| | `End Time` | Time | Time when Period 4 ends (default: `06:00:00`). |

## How the Blueprint Lifecycle Works

1. **State Monitoring:** The automation listens for the **Target Device** to transition from `off` to `on`.
2. **Time Window Evaluation:** It checks current time against configured periods sequentially (Period 1 through Period 4).
3. **Scene Enforcement:** When the first active period containing both a valid time match and a selected scene is found, the automation calls `scene.turn_on` for that scene and stops further evaluation.
4. **Fallback:** If no defined time window matches the current time or if matching periods have no scene assigned, the automation safely finishes without altering the device state or throwing log errors.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fturn_on_scene_based_on_time_period.yaml)

### Method 2: Manual Installation
1. Download or clone the raw file from this repository: [`turn_on_scene_based_on_time_period.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/turn_on_scene_based_on_time_period.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `turn_on_scene_based_on_time_period.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/turn_on_scene_based_on_time_period.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the **Import blueprint** button.
4. Paste in the URL and follow the prompts.

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **version** 1.0 | 2026-10-30 | Initial release |
