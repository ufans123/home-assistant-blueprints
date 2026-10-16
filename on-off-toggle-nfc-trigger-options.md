## On/Off or Toggle Control with Scene Options (NFC & Triggers)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fon_off_toggle_nfc_trigger_options.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint provides a robust, universal controller optimized for **NFC tags** and custom triggers, while working wonderfully with buttons and switches. It gives you explicit control over **On**, **Off**, and **Toggle** actions, with seamless support for optional, multi-scene presets that fire immediately after turning your target devices on.

### Features
- **NFC-First Optimization:** Designed to make tapping NFC tags around your home feel instantaneous and reliable.
- **Explicit Action Control:** Choose whether the trigger executes an explicit **Turn On**, **Turn Off**, or smart **Toggle** behavior.
- **Optional Scene Presets:** Select multiple scenes to apply automatically right after your target devices turn on.
- **Smart Toggle Logic:** Automatically detects if your target devices are currently active. If anything is on, it shuts them down; if everything is off, it powers them up and applies your selected scenes.
- **Multi-Device Support:** Control lights, switches, fans, or input booleans—individually or as a group.

### Input Configuration Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Triggers** | Trigger Selector | Add your custom triggers here (NFC tags work brilliantly here!). |
| **Target Entity** | Target Entity | The lights, switches, fans, or input booleans to control. |
| **Action** | Select Dropdown | Choose what happens when triggered (`Turn On`, `Turn Off`, or `Toggle`). |
| **Optional Scenes (Turn On Presets)** | Scene Entities (Multiple & Reorderable) | Optional: Applied right after turning ON (or toggling on). |

### Pro Tips
- **NFC Placement:** Place NFC tags near entryways, bedside tables, or desks to quickly toggle room states or activate your favorite mood lighting with a simple tap of your phone.
- **Scene Sequencing:** If you select multiple optional scenes, Home Assistant will apply them in sequence right after the target devices wake up.
- **Group Control:** Target a Home Assistant light or switch group to control an entire room's worth of devices with a single NFC tap or button press.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fon_off_toggle_nfc_trigger_options.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `on_off_toggle_nfc_trigger_options.yaml` file from this repository. [`on_off_toggle_nfc_trigger_options.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/on_off_toggle_nfc_trigger_options.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `on_off_toggle_nfc_trigger_options.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/on_off_toggle_nfc_trigger_options.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
