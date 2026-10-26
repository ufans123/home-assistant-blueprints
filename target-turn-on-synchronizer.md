# Turn On to Default Scene (Companion Blueprint)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftarget_turn_on_synchronizer.yaml)

[← Back to Main Blueprints Repository](README.md)

This blueprint automatically activates a preferred default scene whenever a light, switch, or input boolean turns on from an external source (such as an app, a physical wall switch, or a voice command). 

Additionally, it features an optional counter synchronization mechanism: when paired as a companion to the **"Button Scene Cycling and Off Control"** blueprint, it automatically resets the cycle counter back to zero whenever the device turns on externally, ensuring your button-cycling sequence always stays synchronized from the start.

## Features

- **External Activation Synchronization:** Detects when a monitored device switches from `off` to `on` via physical switches, voice, or apps, and immediately forces your chosen default scene.
- **Optional Companion Counter Reset:** Safely resets a designated `counter` helper entity on trigger when used as a companion to the button cycling blueprint. Functions seamlessly as a standalone blueprint if left blank.
- **Multi-Domain Compatibility:** Compatible with smart switches, lights, and input booleans.

## Prerequisites

If you plan to use this blueprint as a companion to sync with the **"Button Scene Cycling and Off Control"** blueprint, you should already have a **Counter Helper** created in Home Assistant:

1. Navigate to **Settings** > **Devices & Services** > **Helpers**.
2. Click **Create Helper** and select **Counter**.
3. Set your initial value to `0` and configure your step/minimum/maximum values as needed for your cycling setup.
4. Click **Create**.

*(Note: If you are using this blueprint purely as a standalone tool, no helper is required and you can leave the companion section blank.)*

## Input Configuration

| Section | Input Field | Type | Description |
| :--- | :--- | :--- | :--- |
| **Target Device Settings** | `Target Device` | Entity (`switch`, `light`, `input_boolean`) | The switch, light, or input boolean to monitor for external turn-on events. |
| | `Default Scene` | Entity (`scene`) | The default scene to activate whenever the target device turns on. |
| **Companion Options (Optional)** | `Counter Helper` | Entity (`counter`) | Optional Counter helper to reset to 0. Leave blank if using this blueprint standalone. |

## How the Blueprint Lifecycle Works

1. **State Monitoring:** The automation listens for the **Target Device** state to transition from `off` to `on`.
2. **Scene Enforcement:** Once triggered, it immediately commands the **Default Scene** to activate.
3. **Optional Counter Reset:** It evaluates the optional **Counter Helper**. If configured, it executes a clean variable check and resets the counter value back to `0`, allowing your button-cycling companion blueprint to start fresh from the first scene.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftarget_turn_on_synchronizer.yaml)

### Method 2: Manual Installation
1. Download or clone the raw file from this repository: [`target_turn_on_synchronizer.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/target_turn_on_synchronizer.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `target_turn_on_synchronizer.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/target_turn_on_synchronizer.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the **Import blueprint** button.
4. Paste in the URL and follow the prompts.
