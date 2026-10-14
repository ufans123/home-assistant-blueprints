## Button Scene Cycling and Off Control

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_scene_cycling_and_off_control.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint cycles sequentially through a selected list of scenes using an **On Button** (or scene button) and a **Counter helper** to remember your place in the cycle. Pressing the **Off Button** (or power toggle configured for off) shuts down target devices and resets the counter to `0`, ensuring your cycle always starts fresh on your preferred first scene every time you turn it back on.

### Features
- **Sequential Scene Cycling:** Step through your favorite scenes in order with every press of the On button.
- **Counter-Powered Tracking:** Uses a Home Assistant counter helper to maintain state across sessions.
- **Automatic Reset on Off:** Shuts down multiple devices and resets the counter to `0` when the Off button is used.
- **UI Reordering Support:** Easily sort and reorder your scene sequence directly from the automation configuration UI.
- **Modern Event Triggers:** Uses event-based triggers (such as `initial_press`) optimized for modern button hardware.
- **Hardware Compatibility Note:** Works seamlessly across different remote generations (older separate On/Off buttons or newer Philips Hue remotes configured with dedicated scene and power-off buttons).

### Input Configuration Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **On Button** | Event Entity | The event entity used to cycle through your scenes. |
| **Off Button** | Event Entity | The event entity used to turn off target devices and reset the counter. |
| **Scenes to Cycle** | Scene Entities (Multiple & Reorderable) | Select and reorder the scenes you want to cycle through in sequence. |
| **Target Devices for Off Button** | Target Entity | The switches, lights, or input booleans to turn off when the off button is pressed. |
| **Counter Helper** | Counter Entity | The counter helper used to remember your place in the active scene cycle. |

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_scene_cycling_and_off_control.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `button_scene_cycling_and_off_control.yaml` file from this repository. [`button_scene_cycling_and_off_control.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/button_scene_cycling_and_off_control.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `button_scene_cycling_and_off_control.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/button_scene_cycling_and_off_control.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
