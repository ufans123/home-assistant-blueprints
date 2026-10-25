# Safe Battery-Controlled Charging & Failsafe Manager

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbattery_charging_control_combined.yaml)

[← Back to Main Blueprints Repository](README.md)

This blueprint provides a complete, all-in-one solution for managing smart switch battery charging. It unifies percentage-based threshold charging with an active safety time-failsafe companion, network disconnect recovery, and manual override capabilities via `input_boolean` helper switches or NFC tags.

The system is explicitly designed so that **the device reporting an active `charging` status automatically kicks off the safety countdown timer**, ensuring the timer tracks actual active power flow. Whether your device charges automatically based on battery levels or is docked manually at night before hitting your low threshold, this automation ensures your plug turns on reliably and cuts power safely before overcharging occurs.

> **Disclaimer:** If a phone or tablet is already powered completely off or disconnected from Wi-Fi, it cannot scan an NFC tag or report its `charging` status to Home Assistant (meaning the safety timer will not auto-start). Using a nightstand NFC tag or manual trigger switch allows you to proactively turn on the plug and launch the safety timer before placing your device on the charger, guaranteeing a controlled charging session even if the battery hasn't met the low threshold yet or the device drops offline overnight.

## Features

- **All-in-One Architecture:** Combines percentage boundary controls, time-based safety limits, and manual overrides into a single, streamlined automation.
- **Charge-Activated Timer:** The helper timer is specifically designed to start as soon as the device detects and reports an active `charging` state, providing precise active-charging limit tracking.
- **Sectioned UI Schema:** Organized using Home Assistant section grouping for clean configuration of sensors, plugs, thresholds, safety durations, and manual triggers.
- **Manual Start & NFC Support:** Allows launching a charging session on demand via an `input_boolean` helper switch (which automatically resets itself to `off` after use) or by scanning an NFC tag (ideal for starting a nightstand charge before a device drops Wi-Fi or hits the threshold).
- **Network Dropout & HA Restart Resilience:** Retains state and safely evaluates battery levels during Wi-Fi drops or Home Assistant reboots without interrupting ongoing sessions.
- **Sustained Discharge Grace Period:** Allows you to pick up and briefly use your device without resetting or aborting the active countdown tracker.
- **Multi-Domain Compatibility:** Compatible with smart switches registered as either `switch` or `light` entities.

## Prerequisites

Before configuring this blueprint, you must create a standard **Timer Helper** in Home Assistant to serve as the countdown clock tracker:

1. Navigate to **Settings** > **Devices & Services** > **Helpers**.
2. Click **Create Helper** and select **Timer**.
3. Provide a name (e.g., `Phone Charging Failsafe Timer`).
4. *Optional:* You can leave the default duration as `00:00:00`, as this blueprint dynamically forces your custom duration parameters upon execution.
5. Click **Create**.

## Input Configuration

| Section | Input Field | Type | Description |
| :--- | :--- | :--- | :--- |
| **Sensors** | `Battery Percentage Sensor` | Entity (`sensor`) | The battery percentage sensor monitoring device charge state (0-100%). |
| | `Battery Status Sensor` | Entity (`sensor`) | The device sensor reporting state like `charging`, `discharging`, etc. |
| **Plug & Timer** | `Smart Switch / Plug` | Entity (`switch` / `light`) | The smart plug or converted light entity controlling power to the charger. |
| | `Helper Timer` | Entity (`timer`) | The Home Assistant tracking timer helper created in the prerequisites. |
| **Manual Start & NFC Tag** | `Manual Start Trigger Switch` | Entity (`input_boolean`) | Optional `input_boolean` helper to manually initiate charging (automatically resets to `off` after triggering). |
| | `NFC Tag ID` | Text Selector | Optional Home Assistant Tag ID/Code used to trigger power and launch the session. |
| | `NFC Tag Description / Note` | Text Selector | Optional text note to record tag details or physical placement (e.g., "Nightstand Tag"). |
| **Battery Thresholds** | `Low Battery Threshold` | Slider (%) | Percentage below which the smart plug automatically turns on. |
| | `High Battery Threshold` | Slider (%) | Percentage above which the smart plug automatically turns off. |
| **Duration & Grace Period** | `Maximum Charge Duration` | Duration Selector | Maximum continuous time window allowed for charging before power is forcefully cut. |
| | `Discharge Grace Period` | Slider (Minutes) | Unplugged grace period allowed before the timer and session are completely cancelled. |

## How the Blueprint Lifecycle Works

1. **Automated Start & Timer Trigger:** When your device drops below the **Low Battery Threshold**, the smart plug turns on. Once power flows and the device's status sensor switches to `charging`, the automation immediately triggers and starts the **Helper Timer** countdown.
2. **Manual / NFC Override:** Toggling your configured `input_boolean` helper or scanning your nightstand NFC tag before going to sleep turns on the plug, starts the timer immediately, and resets the helper switch back to `off`—bypassing the battery threshold and protecting against overnight Wi-Fi disconnects.
3. **Grace Period Protection:** Unplugging your device to send a quick text enters a grace window. If plugged back in before the **Discharge Grace Period** expires, tracking safely resumes.
4. **Safe Termination:** When the battery reaches the **High Battery Threshold**, the smart plug turns off and cancels the active timer. If the device fails to stop charging or stays plugged in too long, the **Helper Timer** finishes and forcefully shuts off power.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbattery_charging_control_combined.yaml)

### Method 2: Manual Installation
1. Download or clone the raw file from this repository: [`battery_charging_control_combined.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/battery_charging_control_combined.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `battery_charging_control_combined.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/battery_charging_control_combined.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the Import blueprint button.
4. Paste in the URL and follow the prompts.
