# Timed Light Scene Cycler

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flight_scene_cycler.yaml)

[← Back to Main Blueprints Repository](README.md)

A clean, robust, snapshot-free Home Assistant blueprint designed to cycle a light or light group through an ordered sequence of custom scenes **controlled by a dedicated input boolean switch**. Features smooth transitions, an optional startup check, a dedicated turn-off scene, and a built-in auto-off timer.

---

> ⚠️ **Prerequisite Note:** This automation is designed around an **Input Boolean (`input_boolean.*`)** helper switch. You must create this helper entity first in Home Assistant (`Settings > Devices & Services > Helpers`) before setting up this automation, as it serves as the master switch to start, hold, and stop your scene cycle.

---

## Features

- **Switch-Controlled Lifecycle:** Turning your input boolean switch `on` starts the cycle; turning it `off` instantly triggers a clean shutdown.
- **Sequential Scene Cycling:** Effortlessly loops your light through a custom list of scenes in order.
- **Dedicated Turn-Off Scene & Safety Fallback:** Smoothly triggers a user-defined turn-off scene paired with a direct safety command to ensure clean termination when stopped.
- **Smooth Transitions:** Customizes fade durations for both the active scenes and the final shutdown.
- **Optional Auto-Off Timer:** Automatically shuts off the control switch after a set duration (0–480 minutes) or runs indefinitely.
- **"Turn On If Off" Protection:** Optionally forces the light to turn on via the first scene if it is currently off when enabled, or gracefully aborts if disabled.
- **Operation Summary:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Switch Turned On** | Checks light state, handles initialization, and concurrently starts the scene loop and optional auto-off timer. |
  | **Switch Turned Off** | Interrupts any active loop instantly, executing the custom turn-off scene and direct light off command with smooth transitions. |
  | **Timer Expires** | Automatically turns off the control switch, gracefully triggering the shutdown sequence. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Target Light or Light Group** | The light or light group entity to control and cycle. | **Yes** | N/A |
| **Scene Sequence** | Select the scenes you want to cycle through in order. | **Yes** | N/A |
| **Turn Off Scene** | Select the scene to trigger when the helper switch is turned off. | **Yes** | N/A |
| **Transition Time (seconds)** | Fade duration between scenes and for the final shutdown. | No | `5` |
| **Hold Time (seconds)** | Duration to hold each scene before transitioning to the next (chunked for instant abort responsiveness). | No | `20` |
| **Auto-Off Timer (minutes)** | Automatically turns off the switch after this duration. Set to 0 to run indefinitely. | No | `0` (Disabled) |
| **Turn On If Off** | Automatically turn on the light if it is currently off when enabled. | No | `true` |
| **Control Switch (Input Boolean)** | The input boolean entity (`input_boolean.*`) used as the master switch to start and stop the cycle. | **Yes** | N/A |

---

## 💡 Important Notes & Pro-Tips

- **Designing for Smooth Scene Transitions:** While the blueprint applies a global transition time between scenes, pay close attention to the **order** of your scene sequence. Because the cycle loops continuously, the transition from your *last* scene back to your *first* scene can feel abrupt if their colors or brightness levels are drastically different. Try to order your scenes progressively (or ensure the last scene flows naturally into the first) to maintain a seamless ambient loop.
- **Ensure Entity Inclusion in Off Scene:** Make sure your selected **Turn Off Scene** explicitly includes your target light saved in an "off" state. (The blueprint also fires a direct safety `light.turn_off` command right after as a fallback).
- **Instant Abort Responsiveness:** The hold time is broken down into 1-second chunks internally, meaning turning off your control switch stops the loop immediately without waiting for a long delay to finish.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flight_scene_cycler.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`light_scene_cycler.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/light_scene_cycler.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `light_scene_cycler.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/light_scene_cycler.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
5. 
