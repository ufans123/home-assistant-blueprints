# Configurable Daily Weather Report

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fweather_report_notification.yaml)

[← Back to Main Blueprints Repository](README.md)

A clean, mobile-optimized Home Assistant blueprint designed to generate detailed daily weather notifications with custom region headings, dynamic unit conversion, timestamps, and quick links **controlled via flexible triggers (Schedule, NFC, or Helper Switch)**.

---

> ⚠️ **Prerequisite Note:** This automation can be triggered by a daily time schedule, an NFC tag scan, or an **Input Boolean (`input_boolean.*`)** helper switch. If you plan to use manual helper triggers, create your helper entity first in Home Assistant (`Settings > Devices & Services > Helpers`).

---

## Features

- **Multi-Trigger Architecture:** Trigger your weather report automatically via a daily schedule, by scanning an NFC tag, or instantly using an input boolean helper switch.
- **Custom Region & Location Headings:** Override entity names with a specific region name (e.g., "Courtenay, BC") to format clean, custom headers.
- **Dynamic Temperature Unit Conversion:** Choose between Celsius (°C) and Fahrenheit (°F) with automatic underlying math conversion and rounding.
- **Universal Timestamps:** Includes a discreet, globally understood timestamp (`YYYY-MM-DD HH:MM`) at the footer of every report.
- **Quick Links Integration:** Easily attach links to your internal Home Assistant dashboard or external weather sources/search queries.
- **Mobile-Optimized UI Layout:** Formatted using lightweight HTML and Markdown (`<br>`, bolding, dividers) for crisp readability on smartphones.
- **Operation Summary:**
  
  | Event | Action Taken |
  | :--- | :--- |
  | **Schedule, NFC, or Helper Triggered** | Pulls modern forecast data, formats conditions/temperatures, and generates a robust persistent notification. |
  | **Helper Switch Activated** | Automatically toggles the input boolean back off after firing to keep your switches cleanly managed. |
  | **Data Unavailable** | Gracefully handles missing weather attributes or forecast keys using safe fallbacks (`N/A`) without breaking the automation. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Weather Entity** | The weather entity to pull forecasts from (`weather.*`). | **Yes** | N/A |
| **Custom Location / Region Name** | Override the entity name with a specific region (e.g., "Courtenay, BC"). Leave blank to use entity name. | No | `""` |
| **Temperature Unit** | Choose whether to display temperatures in Celsius (°C) or Fahrenheit (°F). | Yes | `°C` |
| **Daily Schedule Time** | Time of day to run the report automatically. | Yes | `07:00:00` |
| **NFC Tag ID** | Scanning this tag ID will trigger the report. | No | `""` |
| **Input Boolean Helper** | Toggle switch entity (`input_boolean.*`) to manually trigger the report. | No | `[]` |
| **Internal Dashboard Path** | Path to your HA dashboard (e.g., `/dashboard-sensors/temperatures`). Leave blank to omit. | No | `""` |
| **External Weather Link** | URL to an external weather service or search query. | No | Environment Canada coords link |

---

## 💡 Important Notes & Pro-Tips

- **Modern Weather Forecast Handling:** This blueprint utilizes Home Assistant's modern `weather.get_forecasts` service, ensuring full compatibility across standard weather integrations (Met.no, AccuWeather, Environment Canada, etc.).
- **Smart Coordinate Lookups:** The default external URL link uses coordinate lookups. You can easily find precise latitude and longitude values using tools like [GPS Coordinates Finder](https://www.gps-coordinates.net/).
- **Airtight Error Handling:** The template code utilizes Python safe `.get()` methods and fallback defaults (`N/A`), meaning temporary weather integration hiccups won't throw automation errors.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fweather_report_notification.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`weather_report_notification.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/weather_report_notification.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `weather_report_notification.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/weather_report_notification.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (`Settings > Automations & Scenes > Blueprints`).
3. In the bottom right corner, click on the *'Import blueprint'* button.
4. Paste in the URL and follow the prompts.
