# Reset Dropdown Helper on Light Turn Off

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Freset_select_helper.yaml)

[← Back to Main README](README.md)

This Home Assistant automation blueprint resets a specified `input_select` (dropdown helper) back to a designated default option whenever a target light turns off. This is especially useful for managing lighting scenes, effect modes, or color profiles stored in helpers so they automatically revert to a baseline state when the lights are turned off.

---

## Features

* **Automatic Reset:** Triggers instantly when the selected light changes its state to `off`.
* **Customizable Defaults:** Specify any text string as the default option to fall back on.
* **Simple Setup:** Built using Home Assistant's native blueprint inputs for seamless configuration.

---

## Requirements

* Home Assistant Core 2023.x or newer.
* At least one configured `light` entity.
* An existing `input_select` (dropdown helper) entity that you wish to reset.

---

## Inputs

| Input | Description | Type | Default |
| :--- | :--- | :--- | :--- |
| **Target Light** | The light entity that triggers the reset when turned off. | `light` | *None* (Required) |
| **Dropdown Helper** | The `input_select` helper entity that will be reset. | `input_select` | *None* (Required) |
| **Default Option** | The exact text option to select when the light turns off. | `text` | `Select an option` |

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Freset_select_helper.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `battery_charging_control.yaml` file from this repository. [`reset_select_helper.yaml`](reset_select_helper.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `reset_select_helper.yaml`.
4. Reload your automations or restart Home Assistant.
