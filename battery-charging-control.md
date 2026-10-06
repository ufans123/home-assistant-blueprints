# Battery-Controlled Charging Switch

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbattery_charging_control.yaml)

[← Back to Main Blueprints Repository](README.md)

Turns a smart switch or plug on when a battery drops below a low threshold, and turns it off when it exceeds a high threshold to protect battery health and automate charging.

## How It Works

1. **Low Battery Trigger:** When the battery sensor value falls below your configured **Low Battery Threshold**, the smart switch or light turns `on` to start charging.
2. **High Battery Trigger:** When the battery sensor value rises above your configured **High Battery Threshold**, the smart switch or light turns `off` to stop charging.


## 🚀 How to Install

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbattery_charging_control.yaml)

### Method 2: Manual Installation
1. Download or clone the raw `battery_charging_control.yaml` file from this repository.
2. Drop the file directly into your local Home Assistant directory tree at:
   ```text
   config/blueprints/automation/ufans123/battery_charging_control.yaml
