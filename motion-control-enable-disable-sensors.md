# Motion Control Enable or Disable

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fmotion_control_enable_disable_sensors.yaml)

[← Back to Main Blueprints Repository](README.md)

Enables or disables motion sensors via button/event entities or automatically when a monitored light turns off.

## How It Works

1. **Disable Motion:** Triggering the **Disable Event Entity** (such as a button press) turns off the selected motion switch(es).
2. **Enable via Event:** Triggering the **Enable Event Entity** turns the motion switch(es) back on.
3. **Auto-Enable via Light:** When the **Monitored Light** changes state to `off`, it automatically re-enables the motion switch(es).

## ⚙️ Configuration Properties

| Field Name | Type | Description | Default |
| :--- | :--- | :--- | :--- |
| **Disable Event Entity** | Entity | The event entity (e.g., button press) that disables the motion sensors. | *Required* |
| **Enable Event Entity** | Entity | The event entity (e.g., button press) that enables the motion sensors. | *Required* |
| **Monitored Light** | Entity (`light`) | Turning this light off will automatically re-enable the motion sensors. | *Required* |
| **Motion Sensor Switch(es)** | Target (`switch`) | Select the motion sensor enable/disable switch entity or target group. | *Required* |

