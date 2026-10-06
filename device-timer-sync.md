# Sync Device and Timer

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_timer_sync.yaml)

[← Back to Main Blueprints Repository](README.md)

This Home Assistant blueprint synchronizes a target device (**light**, **switch**, or **fan**) with a **Timer helper**. It links the state of the device and the timer together so they stay in sync automatically.

## How It Works

1. **Device Turns ON:** If the associated timer helper is currently `idle`, it automatically starts the timer using your configured default duration.
2. **Device Turns OFF:** If the associated timer helper is `active`, it cancels/stops the timer.
3. **Timer Finishes:** When the timer expires (transitions from `active` to `idle`), the controlled device automatically turns `off`.

## Blueprint Inputs

| Input | Description | Allowed Domains / Types | Default |
| :--- | :--- | :--- | :--- |
| **Target Device** | The switch, light, or fan you want to sync. | `light`, `switch`, `fan` | *Required* |
| **Timer Helper** | The timer helper used to track the countdown duration. | `timer` | *Required* |
| **Default Timer Duration** | The length of time to start the timer with when the device turns on. | Duration (`HH:MM:SS`) | `02:00:00` |

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_timer_sync.yaml)

### Method 2: Manual Installation
1. Copy the raw contents of [device_timer_sync.yaml](../device_timer_sync.yaml).
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `device_timer_sync.yaml`.
4. Reload your automations or restart Home Assistant.
