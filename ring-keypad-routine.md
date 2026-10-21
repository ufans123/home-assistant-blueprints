## Ring Keypad V2: Multi-Code Routine Hub

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fring_keypad_routine.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint allows you to turn your **Ring Keypad V2** into a fully customizable routine hub in Home Assistant, operating completely independently of Alarmo. Map single-digit keys (`0`–`9`) and one custom multi-digit PIN code to separate Home Assistant action sequences. Pressing a shortcut followed by the **Checkmark** button executes your custom actions with optional global audio feedback chimes.

### Features
- **Multi-Code Routine Hub:** Map up to 10 single-digit shortcuts plus a custom multi-digit PIN to independent Home Assistant actions (scripts, scenes, automations, or device controls).
- **Checkmark Triggering:** Securely evaluates user input on submission via the Entry Control Command Class (CC 111).
- **Global Audio Feedback:** Features a customizable volume percentage slider (0%–100%) and a sound selection for confirmation chimes (Double Beep, Keytone Click, Wind Chime, Soft Error Beep) powered by Z-Wave JS Indicator Command Class (CC 135).
- **Clean UI Layout:** Designed with collapsible sections for every key and global setting to minimize visual clutter in the automation configuration UI.
- **Independent Operation:** Runs smoothly as a standalone routine manager without interfering with your native alarm panel integration.

### Prerequisites
1. **Z-Wave JS Integration:** Your Home Assistant instance must have the official `zwave_js` integration running.
2. **Connected Ring Keypad v2:** The keypad must already be paired to your Z-Wave network.
  - *Note:* Ring Keypads require **S2 Security** during pairing to process Z-Wave Indicator Command Class (135) audio feedback commands properly.

### Input Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Ring Keypad Device** | Device Selector | Select your target Ring Keypad device (automatically targets its Z-Wave entity). |
| **Global Audio Options** | Collapsible Section | Configure master confirmation chime volume (0%–100%) and sound effect selection. |
| **Custom / Multi-Digit PIN** | Collapsible Section | Define a multi-digit code (e.g., `1234`), audio toggle, and associated action. |
| **Key 0 – 9 Actions** | Collapsible Sections | Define specific Home Assistant action sequences and individual audio toggles for each single-digit shortcut (triggered via `Key` + `Checkmark`). |

### Pro Tips
- **Keep it Documented:** Pair this blueprint with a simple text helper and a dashboard Markdown card to maintain a living cheat sheet of your assigned button shortcuts for family or guests.
- **Audio Feedback:** Enable confirmation chimes selectively on high-impact routines (like opening a garage door) while keeping quiet shortcuts silent.
- **Z-Wave JS Health:** Ensure your Ring Keypad has a direct or strong Z-Wave mesh connection to guarantee instant event responses.

### Acknowledgments & Credits
Special thanks to these Home Assistant community members for their invaluable research and contributions to Ring Keypad v2 integrations:
- **[@ImSorryButWho](https://community.home-assistant.io/u/imsorrybutwho)** – Creator of the original *[Ring Keypad Automations](https://community.home-assistant.io/t/synchronize-ring-alarm-keypad-v2-with-alarmo/349461)* blueprint, establishing early standards for pairing and synchronizing keypads with Home Assistant.
- **[@NobleWolf](https://community.home-assistant.io/u/noblewolf)** – Creator of the *[Ring Keypad v2 Sounds SCRIPT, zwaveJS](https://community.home-assistant.io/t/ring-keypad-v2-sounds-script-zwavejs/680399)* work, providing initial technical insights into mapping Z-Wave Indicator Command Class (CC 135) audio commands.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fring_keypad_routine.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `ring_keypad_routine.yaml` file from this repository. [`ring_keypad_routine.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/ring_keypad_routine.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/home-assistant-blueprints/`).
3. Paste the code into a file named `ring_keypad_routine.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easiest)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/ring_keypad_routine.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.
