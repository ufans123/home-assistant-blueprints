# Battery-Controlled Charging Switch

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fbattery_charging_control.yaml)

[← Back to Main Blueprints Repository](README.md)

Turns a smart switch or plug on when a battery drops below a low threshold, and turns it off when it exceeds a high threshold to protect battery health and automate charging.

## How It Works

1. **Low Battery Trigger:** When the battery sensor value falls below your configured **Low Battery Threshold**, the smart switch or light turns `on` to start charging.
2. **High Battery Trigger:** When the battery sensor value rises above your configured **High Battery Threshold**, the smart switch or light turns `off` to stop charging.
