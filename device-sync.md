## Two-Way Device Sync: Binary State Mirroring & Loop Prevention

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_sync.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint allows you to synchronize the state of **any two binary entities** (such as lights, switches, fans, and input booleans) mutually in both directions. Effortlessly mirror states between paired devices without writing complex YAML or worrying about cascading infinite loops.

### Features
- **Bi-directional Syncing:** Toggling either device on or off instantly mirrors the exact state to the other device.
- **Infinite Loop Protection:** Utilizes Home Assistant context tracing (`parent_id != this.context.id`) to block self-triggering automation loops cold.
- **Smart Filtering:** Automatically ignores attribute-only state updates and skips unnecessary action execution if devices already match.
- **Domain Agnostic:** Dynamically handles multiple entity domains (`light`, `switch`, `input_boolean`, `fan`) on the fly using runtime variables.

### Prerequisites
1. **Home Assistant Core:** Ensure your instance supports modern blueprint syntax and action variables.
2. **Paired Entities:** Two or more binary entities (`light`, `switch`, `input_boolean`, or `fan`) that you want to keep permanently synced.

### Input Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **First Entity** | Entity Selector | Select the first device, switch, light, or helper to synchronize. |
| **Second Entity** | Entity Selector | Select the second device, switch, light, or helper to synchronize. |

### Pro Tips
- **Decoupled Timers:** If you want a countdown timer associated with your synced devices, keep the timer logic in a separate dedicated automation (or companion blueprint) so your sync layer stays lightweight and modular.
- **Multi-Way Control:** Perfect for pairing smart plugs, virtual switches, or redundant wall switches that need to act as a single logical unit.

### Acknowledgments & Credits
Special thanks to the Home Assistant community for documentation, context-tracing patterns, and architectural best practices regarding loop prevention in two-way device mirroring.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fdevice_sync.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `device_sync.yaml` file from this repository. [`device_sync.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/device_sync.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/home-assistant-blueprints/`).
3. Paste the code into a file named `device_sync.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easiest)
1. Copy the following URL
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/device_sync.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (Settings > Automations & Scenes > Blueprints).
3. In the bottom right corner, click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.
