## Cycle Through Multiple Scenes (NFC & Switches)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fcycle_scenes_by_trigger.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint cycles sequentially through a selected list of scenes using a flexible trigger source (such as **NFC tags**, button presses, or remote events) and a **Counter helper** to remember your place in the cycle. It is specifically optimized for scanning NFC tags with your phone to seamlessly advance through lighting presets, moods, or device states!

### Features
- **NFC Tag Optimized:** Tap your phone to an NFC tag to instantly advance to the next scene in your sequence.
- **Sequential Scene Cycling:** Step through your favorite scenes in order with every trigger activation.
- **Counter-Powered Tracking:** Uses a Home Assistant counter helper to maintain state across sessions.
- **UI Reordering Support:** Easily sort and reorder your scene sequence directly from the automation configuration UI.
- **Universal Trigger Compatibility:** Works with NFC tags, physical buttons, state changes, or any standard Home Assistant trigger source.

### Input Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Triggers** | Trigger Selector | Add your triggers here. **NFC tags** work brilliantly—scan a tag to instantly advance to the next scene. |
| **Scenes to Cycle** | Scene Entities (Multiple & Reorderable) | Select and reorder the scenes you want to cycle through in sequence. |
| **Counter Helper** | Counter Entity | The counter helper used to remember your place in the active scene cycle. |

### Pro Tips
- **Counter Step Size:** When creating your counter helper (`counter.*`), leave the step size at `1` so the cycle advances by exactly one scene per trigger. Modulo math automatically loops the sequence back to the start when it reaches the end of your scene list.
- **NFC Placement:** Place NFC stickers near your bed, desk, or entryway. Tapping your phone becomes a frictionless way to switch between "Morning," "Work," "Relax," and "Night" lighting states.
- **First Scene Priority:** Put your most commonly used or "default" scene at the very top of your selected scene list so your cycle starts predictably.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fcycle_scenes_by_trigger.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `cycle_scenes_by_trigger.yaml` file from this repository. [`cycle_scenes_by_trigger.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/cycle_scenes_by_trigger.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `cycle_scenes_by_trigger.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easiest) 
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/cycle_scenes_by_trigger.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
