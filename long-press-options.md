# Switch Event Long-Press Control (with Optional NFC)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flong_press_options.yaml)

> **Version:** 1.1 | **Initial Release:** 2026-10-20 | [← Back to Main Blueprints Repository](README.md)

A clean, flexible Home Assistant blueprint designed to trigger light and switch actions (**Turn Off**, **Turn On**, or **Toggle**) via button **long-presses** and an **optional NFC tag scan** with custom labeling.

---

## Features

- **Multi-Trigger Architecture:** Control your lights and switches by holding down a physical switch button or by scanning an optional NFC tag.
- **Flexible Action Modes:** Easily configure each automation instance to **Turn Off**, **Turn On**, or **Toggle** target devices.
- **Universal Target Support:** Compatible with any individual light or switch entity, as well as complex custom light/switch groups.
- **Optional NFC Tag Integration:** Paste an NFC tag UUID to add physical touch-to-scan support alongside your long-press buttons.
- **UI Labeling Metadata:** Includes a non-functional description field to clearly document and remind yourself which NFC tag corresponds to each automation.
- **Safe Fallback Handling:** Dynamically evaluates target fields so left-blank categories are skipped cleanly without throwing missing-target errors.
- **Operation Summary:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Long-Press Event Received** | Fires the selected service (`light.*` or `switch.*`) against targeted entities or groups. |
  | **Optional NFC Tag Scanned** | Triggers identical actions when the specified tag UUID is detected. |
  | **Blank Target Fields** | Safely ignored and skipped without crashing the automation sequence. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Switch Button Event Entities** | Select one or more event entities (`event.*`) capturing long-press states. | **Yes** | N/A |
| **Optional NFC Tag ID** | (Optional) Paste the UUID of an NFC tag that should also trigger this action. Leave blank if unused. | No | `""` |
| **NFC Tag Description / Label** | Non-functional text field just to label or remind yourself which NFC tag this is (e.g., "Front Door Keyfob"). | No | `""` |
| **Action** | Choose what action to perform on the target devices (`Turn Off`, `Turn On`, `Toggle`). | **Yes** | `turn_off` |
| **Target Lights** | The lights or custom light groups you want to control. | No | `{}` |
| **Target Switches** | The switches or custom switch groups you want to control. | No | `{}` |

---

## 💡 Important Notes & Pro-Tips

- **Event Entity Compatibility:** This blueprint relies on Home Assistant's `event.received` trigger architecture, making it ideal for buttons, remotes, and switches that expose `event` entities (such as modern Philips Hue or Zigbee integrations).
- **Reusable Blueprint:** You can instantiate multiple separate automations from this single blueprint file—using one for zone-specific lighting and another for sweeping "All Off" functions across different buttons or tags.
- **Group Support:** Because it uses native Home Assistant target selectors, you can seamlessly combine individual bulbs/switches or custom Home Assistant light/switch groups.
- **Optional Triggers:** The NFC trigger utilizes dynamic templating (`enabled: "{{ nfc_tag | trim != '' }}"`), ensuring that leaving the NFC tag field blank safely deactivates that trigger listener without causing parsing errors.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Flong_press_options.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`long_press_options.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/long_press_options.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `long_press_options.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/long_press_options.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (`Settings > Automations & Scenes > Blueprints`).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.

---
## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-20 | Initial release |
