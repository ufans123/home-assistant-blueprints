## Button On/Off Control with Optional Actions

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_on_off.yaml.yaml)

> **Version:** 1.0 | **Initial release:** 2026-10-22 | [← Back to Main Blueprints Repository](README.md)

This automation blueprint maps an **On Button** and an **Off Button** (designed for event-based smart switches and remotes) to control any switch, light, or input boolean. It also includes support for **optional secondary actions** for each button press.

---

## Use Cases

- **Dedicated Physical On/Off Wall Remote:** Map distinct physical button events on a smart remote or wall switch (such as Button 1 for On and Button 4 for Off) to directly toggle smart plugs, outdoor accent lights, or appliance switches (`switch.geeni_patio_plugs_socket_1`).
- **Target Toggle with Synchronized Companion Actions:** Control a main light or fixture while using the optional On/Off actions to run extra commands simultaneously—such as triggering a companion notification, running a side script, or adjusting an auxiliary light whenever the primary device is turned on or off.

---

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

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbutton_on_off.yaml.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `button_on_off.yaml` file from this repository. [`button_on_off.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/button_on_off.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `button_on_off.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/button_on_off.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI
3. In the bottom right corner click on the *'Import blueprint'* button
4. Paste in the URL and follow the prompts

---
## Related Links
| Blueprint | Description |
| :--- | :--- |
| **[Motion Sensor Enable or Disable](motion-control-enable-disable.md)** | Enable or disable motion sensors via button events or automatically when a specific light turns off. |
| **[On/Off or Toggle Control with Scene Options (NFC & Triggers)](on-off-toggle-nfc-trigger-options.md)** | Control lights, switches, fans, and inputs using NFC tags or buttons with explicit On/Off/Toggle logic, plus optional multi-scene presets. |
| **[Spotify NFC Jukebox with Smart Tracker](spotify-nfc-trigger.md)** | Intelligent Spotify jukebox automation for NFC tags featuring smart state management (resumes, pauses, switches/restarts) and an offline/unavailable speaker safety reset. |
| **[Switch Event Long-Press Control (with Optional NFC)](long-press-options.md)** | Triggers light and switch actions (Turn Off, Turn On, or Toggle) via long-press event entities and an optional NFC tag scan with custom UI labeling. |
---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-22 | Initial release |
