# Simple TTS Weather Announcement (multi-trigger)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftts_weather_announcement.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-11-03 | [← Back to Main Blueprints Repository](README.md)

A flexible, reusable Home Assistant blueprint that reads out a detailed daily weather report over text-to-speech with dynamic time-of-day greetings, current conditions, daily high/low temperatures, precipitation chances, and integrated volume control.

---

> ⚠️ **Prerequisites:**
> - **Weather Integration:** Requires a configured weather entity (e.g., `weather.home` or `weather.forecast_home`) that supports daily forecasts via `weather.get_forecasts`.
> - **TTS Engine:** Requires an active Text-to-Speech integration (e.g., `tts.google_translate_en_com`, `tts.home_assistant_cloud`, or others).

---

## Features

- **Dynamic Greetings:** Automatically evaluates the current system time to greet you with *Good morning*, *Good afternoon*, or *Good evening*.
- **Comprehensive Weather Cues:** Announces real-time weather state, temperature, relative humidity, forecasted condition, high/low targets, and rain probability.
- **Integrated Volume Control:** Includes an adjustable UI slider (0% to 100%) that sets your speaker's volume level prior to speaking.
- **Multi-Trigger Support:** Accepts any combination of automation triggers (e.g., motion sensors, time schedules, morning alarms, NFC tags, or physical button presses).
- **Engine-Agnostic TTS:** Built on modern `tts.speak` standards without hardcoded engine-specific voice parameters, ensuring broad compatibility across TTS engines.
- **Operation Summary:**

  | Component | Action Taken |
  | :--- | :--- |
  | **Volume Adjustment** | Sets the target media player volume level using percentage-to-decimal scaling before playback. |
  | **Data Retrieval** | Calls `weather.get_forecasts` to pull daily forecast data dynamically into execution variables. |
  | **Template Rendering** | Formulates a localized, human-friendly announcement string based on current and forecasted attributes. |
  | **Speech Playback** | Triggers `tts.speak` with local caching enabled (`cache: true`) to minimize latency and cloud API hits. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Weather Integration Entity** | Select your Home Assistant weather entity (e.g., `weather.home`). | **Yes** | N/A |
| **TTS Engine** | Select the Text-to-Speech engine entity to use (e.g., `tts.google_translate_en_com` or `tts.home_assistant_cloud`). | **Yes** | N/A |
| **Target Media Player** | Select the media player to play the announcement on. | **Yes** | N/A |
| **Announcement Volume** | Set the volume level for the media player before speaking (0% to 100%). | No | `50` |
| **Automation Triggers** | Add triggers that cause this announcement to run (e.g., motion sensor, time, button press). | No | `[]` |

---

## 💡 Important Notes & Pro-Tips

- **Engine & Voice Selection:** Voice selection and regional accents are configured globally within your Home Assistant system or integration settings (e.g., **Settings > Voice Assistants** for Nabu Casa). Leaving voice settings out of the blueprint ensures it never throws errors on engines that do not support voice parameters.
- **Audio Caching (`cache: true`):** Home Assistant evaluates template variables *before* checking the cache. If the weather conditions or temperatures change, a new audio file is generated. If the report is identical to a recent run, Home Assistant plays the cached audio instantly.
- **PC & Browser Speaker Ducking:** If playing to a PC or web browser player and you notice unexpected volume drops to 15% or 0%, this is usually caused by OS-level communications audio ducking or browser media session resets rather than Home Assistant logic.
- **Variable Pre-Mapping:** Volume percentage inputs are mapped to local variables prior to template calculations (`(vol_setting | int) / 100`) to remain compliant with Home Assistant blueprint parser standards.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftts_weather_announcement.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`tts_weather_announcement.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/tts_weather_announcement.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `tts_weather_announcement.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/tts_weather_announcement.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (**Settings > Automations & Scenes > Blueprints**).
3. In the bottom right corner, click on the **'Import blueprint'** button.
4. Paste in the URL and follow the prompts.

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-11-03 | Initial release |
