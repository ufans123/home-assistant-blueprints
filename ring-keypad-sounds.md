## Ring Keypad v2: Z-Wave Multi-Trigger Sound Player

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fring_keypad_sounds.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint allows you to use your **Ring Keypad v2** as a multi-trigger audio notification device in Home Assistant. Effortlessly play built-in chimes, notification sounds, and system tones on demand using flexible trigger sources (such as door sensors, motion detectors, light switches, or time schedules) without writing raw YAML or setting up separate scripts.

### Features
- **Multi-Trigger Support:** Combine multiple event, state, or sensor triggers into a single unified audio automation.
- **Built-in Sound Selection:** Easily choose from standard notification chimes (e.g., Doorbell Chime, Windchime) and system tones (e.g., Soft Error Beep) via a clean dropdown menu.
- **Automatic Z-Wave Routing:** Intelligently switches between `property_key: 9` (chimes) and `property_key: 1` (system tones) under the hood using Z-Wave JS Indicator Command Class (CC 135).
- **Volume Control:** Features a customizable volume percentage slider (1%–100%) with a safe default setting.
- **Clean UI Layout:** Sounds are alphabetically sorted and categorized by sound type for quick selection.

### Prerequisites
1. **Z-Wave JS Integration:** Your Home Assistant instance must have the official `zwave_js` integration running.
2. **Connected Ring Keypad v2:** The keypad must already be paired to your Z-Wave network.
   - *Note:* Ring Keypads require **S2 Security** during pairing to process Z-Wave Indicator Command Class (135) audio commands properly.

### Input Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Ring Keypad Device** | Device Selector | Select your target Ring Keypad device (automatically targets its Z-Wave entity). |
| **Automation Triggers** | Trigger Selector | Define what events, state changes, or sensors trigger the sound playback. |
| **Sound Effect or Tone** | Dropdown Selector | Choose the specific chime sample or system tone to play. |
| **Volume Level** | Slider (1%–100%) | Set the playback volume percentage (defaults to 50%). |

### Pro Tips
- **Door Chime Setup:** Map door contact sensors directly to the `Ring Doorbell Chime` or `Windchime` options for quick open/close auditory alerts.
- **Alert Tones:** Use the `Soft Error Beep (Tone)` for subtle warning feedback, such as attempting an invalid action or leaving a door open too long.
- **Z-Wave JS Health:** Ensure your Ring Keypad has a direct or strong Z-Wave mesh connection to prevent playback delays on time-sensitive triggers.

### Acknowledgments & Credits
Special thanks to these Home Assistant community members for their invaluable research and contributions to Ring Keypad v2 integrations:
- **[@ImSorryButWho](https://community.home-assistant.io/u/imsorrybutwho)** – Creator of the original *[Ring Keypad Automations](https://community.home-assistant.io/t/synchronize-ring-alarm-keypad-v2-with-alarmo/349461)* blueprint, establishing early standards for pairing and synchronizing keypads with Home Assistant.
- **[@NobleWolf](https://community.home-assistant.io/u/noblewolf)** – Creator of the *[Ring Keypad v2 Sounds SCRIPT, zwaveJS](https://community.home-assistant.io/t/ring-keypad-v2-sounds-script-zwavejs/680399)* work, providing initial technical insights into mapping Z-Wave Indicator Command Class (CC 135) audio commands.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fring_keypad_sounds.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `ring_keypad_sounds.yaml` file from this repository. [`ring_keypad_sounds.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/ring_keypad_sounds.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/home-assistant-blueprints/`).
3. Paste the code into a file named `ring_keypad_sounds.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easiest)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/ring_keypad_sounds.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.
