# Persistent Notification via Manual Switch (with Optional NFC)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fpersistent_notification_manual_nfc.yaml)

[← Back to Main Blueprints Repository](README.md)

This automation blueprint provides a clean, robust mechanism to generate persistent notifications in Home Assistant. It is anchored around a required **manual input boolean toggle**, allowing you to trigger notifications reliably from dashboard buttons or automated routines, with an optional **NFC tag scan** as an extra trigger channel. It also automatically resets your switch back to "off" right after use.

### Prerequisites
Before setting up this automation from the blueprint, you will need:
* **Input Boolean Helper:** An active input boolean (toggle) helper created in Home Assistant (*Settings > Devices & Services > Helpers > Create Helper > Toggle*). This is required as the primary manual trigger and auto-reset anchor.
* **NFC Tag ID (Optional):** If you plan to use an NFC tag scan as an additional trigger, make sure you have your unique tag ID ready.

### Features
**Manual-First Anchor:** Built around a required `input_boolean` helper, eliminating UI validation errors and ensuring clean dashboard control.

**Optional NFC Integration:** Easily tie a physical NFC tag scan to the exact same notification flow, or leave it blank if you only want manual control!

**Automatic Switch Reset:** Automatically turns the manual trigger switch back to `off` immediately after the notification is sent.

**Spam Prevention:** Uses custom Notification IDs to prevent duplicate notification stacking on your dashboard.

**Clean UI Sections:** Divided into logical UI blocks for a smooth, user-friendly configuration layout inside Home Assistant.


### Input Configuration Reference

| Input | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **Manual Trigger Switch (Required)** | Entity (`input_boolean`) | *None* | Select an Input Boolean helper to trigger this notification and auto-reset. |
| **NFC Tag ID (Optional)** | Text | `""` | Paste a unique Tag ID here if you also want an NFC scan to trigger this. Leave blank otherwise. |
| **NFC Tag Name / Description** | Text | `My NFC Tag` | A friendly name or label for your reference. |
| **Notification Title** | Text | `Dads Super Secret PW` | The heading displayed on the persistent notification card. |
| **Notification Message** | Multiline Text | `12345` | The message body or code shown in the notification. |
| **Notification ID** | Text | `DS` | A unique tracking ID to prevent duplicate notification spam. |


### Pro Tips
**Dummy Switch Workaround:** If you only want to use an NFC tag and don't need a dashboard toggle, you can create a single dummy input boolean to assign to the required manual trigger field.

**Dashboard Integration:** Add your selected input boolean as a button or entity card on your dashboard for quick manual access whenever needed.

**Duplicate Prevention:** Keep your unique `Notification ID` consistent if you want subsequent triggers to update the existing notification card rather than creating a stack of new ones.


## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fpersistent_notification_manual_nfc.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `persistent_notification_manual_nfc.yaml` file from this repository. [`persistent_notification_manual_nfc.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/persistent_notification_manual_nfc.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `persistent_notification_manual_nfc.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/persistent_notification_manual_nfc.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI.
3. In the bottom right corner click on the 'Import blueprint' button.
4. Paste in the URL and follow the prompts.
