## Button On/Off Control with Optional Actions

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_on_off.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint maps an **On Button** and an **Off Button** (designed for event-based smart switches and remotes) to control any switch, light, or input boolean. It also includes support for **optional secondary actions** for each button press.

### Features
* **Dual Button Mapping:** Separate controls for turning a device **On** and **Off**.
* **Optional Actions:** Run extra actions, scenes, or scripts alongside the standard On or Off states without needing separate automations.
* **Modern Event Triggers:** Uses event-based triggers (such as `initial_press`) optimized for modern button devices.
* **Queued Mode:** Gracefully handles rapid or simultaneous button presses.

### Input Configuration Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **On Button** | Event Entity | The button entity triggered when turning the device on (e.g., `event.balcony_switch_button_1`). |
| **Off Button** | Event Entity | The button entity triggered when turning the device off (e.g., `event.balcony_switch_button_3`). |
| **Target Entity** | Target | The switch, light, or input boolean to turn on and off. |
| **Optional On Action** | Action (Optional) | Additional action, script, or automation to execute when the On button is pressed. |
| **Optional Off Action** | Action (Optional) | Additional action, script, or automation to execute when the Off button is pressed. |

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_on_off.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `button_on_off.yaml` file from this repository. [`button_on_off.yaml`](button_on_off.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `button_on_off.yaml`.
4. Reload your automations or restart Home Assistant.
