# Humidity-Triggered Fan with Timer & Low Cutoff

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fhumidity_fan_control.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-11-15 | [← Back to Main Blueprints Repository](README.md)

An advanced, flexible Home Assistant blueprint for bathroom or laundry room climate control. It automatically activates a primary device (and an optional secondary device) based on high humidity or manual switch triggers, manages an optional auto-shutoff timer with full two-way synchronization, and supports an optional low-humidity cutoff to prevent excessive runtimes.

---

> ⚠️ **Prerequisites:**
> - **Humidity Sensor:** A properly paired humidity sensor with a `humidity` device class configured in Home Assistant.
> - **Timer Helper (Optional):** If you want to use timed auto-shutoff, create a helper via **Settings > Devices & Services > Helpers > Create Helper > Timer**.

---

## Use Cases

- **Automated Bathroom Ventilation:** Automatically kick on the ceiling exhaust fan when someone takes a hot shower and humidity spikes above your comfort threshold, running it for a set duration before automatically shutting down.
- **Dual-Device Control (Fan & Light):** Simultaneously control your primary exhaust fan alongside an optional secondary device (such as a shower vanity light or secondary booster fan) without complex scripting.
- **Manual Wall Switch Integration:** Flipping your physical wall switch on manually initiates the exact same timer and auto-shutoff routine as a natural humidity spike.
- **Smart Two-Way Synchronization:** Turning either device off manually immediately cancels the active timer and shuts off the other device, keeping everything clean and in sync.

---

## Features

- **Dual-Device Flexibility:** Supports a required primary target device (fan, switch, or light) and an optional secondary target device that follows identical automation logic.
- **Configurable Thresholds:** Set your preferred high-humidity trigger percentage along with an optional low-humidity cutoff threshold to automatically stop fans when the room dries out.
- **Optional Timer Helper:** Integrate Home Assistant native timers with customizable durations, or omit the timer to let humidity thresholds handle the entire operational cycle.
- **Full Two-Way Sync:** Manual switch shut-offs clear out pending countdowns instantly, preventing desynced states between paired hardware.
- **Operation Summary:**

  | Event | Timer Helper Present? | Low Humidity Threshold Set? | System Action Taken |
  | :--- | :--- | :--- | :--- |
  | **Humidity rises above High Threshold** | Yes (`> 0`) | Either | Turns **ON** both Primary & Secondary devices, starts the timer, and waits for either the timer to finish or be cancelled. |
  | **Humidity rises above High Threshold** | No (Blank/None) | Either | Turns **ON** both Primary & Secondary devices and stays on until humidity drops or a manual turn-off occurs. |
  | **Timer Expires** | Yes | Either | Turns **OFF** both Primary & Secondary devices. |
  | **Humidity drops below Low Threshold** | Either | Yes (`> 0`) | Turns **OFF** both Primary & Secondary devices and cancels any active timer. |
  | **Humidity drops below Low Threshold** | Either | No (`0` / Disabled) | Ignored (Low-humidity cutoff is disabled). |
  | **Manual Turn-On** (Primary device flipped on) | Yes (`> 0`) | Either | Turns **ON** the Secondary device (if defined), starts the timer, and sets up auto-shutoff. |
  | **Manual Turn-Off** (Either device turned off) | Yes (`> 0`) | Either | Turns **OFF** the other device (keeping them in sync) and **cancels** the active timer immediately. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Humidity Sensor** | The sensor that monitors room humidity (`sensor.*`). | **Yes** | N/A |
| **Primary Target Device** | The main fan, light, or switch to control (`light.*`, `switch.*`, `fan.*`). | **Yes** | N/A |
| **Secondary Target Device** | An optional second fan, light, or switch to turn on/off together. Leave blank if not used. | No | `[]` |
| **High Humidity Threshold (%)** | The humidity level that triggers the devices ON. | **Yes** | `55` |
| **Low Humidity Threshold (%)** | Turn off devices when humidity drops below this level. Set to `0` to disable. | No | `0` |
| **Timer Helper** | Optional Timer helper to auto-shutoff the devices (`timer.*`). Leave blank if not using a timer. | No | `[]` |
| **Timer Duration** | How long the timer should run when triggered. | No | `15 minutes` |

---

## 💡 Important Notes & Pro-Tips

- **Restart Mode:** This blueprint uses `mode: restart`. If a new humidity spike or manual trigger occurs while the fan is already running, the timer resets and restarts its countdown from zero.
- **Disabling Low Cutoff:** If you prefer to rely strictly on your timer rather than a dry humidity level, simply set the **Low Humidity Threshold** to `0` to disable it completely.
- **Safe Empty Execution:** Leaving the secondary device or timer helper blank causes the automation to gracefully adapt and run with single-device or threshold-only logic without throwing errors.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fhumidity_fan_control.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`humidity_fan_control.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/humidity_fan_control.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `humidity_fan_control.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/humidity_fan_control.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.

---

## Related Links
| Blueprint | Description |
| :--- | :--- | 
| **[Binary Sensor State Sync](binary-sensor-state-sync.md)** | Directly syncs the state of any binary sensor (such as a door or window) to an input boolean, switch, or light using explicit state mapping. |
| **[Sync Device and Timer](device-timer-sync.md)** | Keep lights, switches, or fans synchronized with a Home Assistant timer helper. |
| **[Sync Device and Scheduled Off-Time](device-sync-scheduled-time-off.md)** | Sync switches, lights, or fans with a scheduled off-time picker, dynamically computing countdown durations with optional timer helper tracking. |
| **[Two-Way Device Sync](device-sync.md)** | Synchronize the state of any two binary entities (lights, switches, fans, input booleans) mutually in both directions without infinite loops. |

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-11-15 | Initial release. |
