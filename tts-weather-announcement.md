# TTS Weather Announcement (with Custom Optional Actions)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Ftts_weather_announcement.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-11-03 | [← Back to Main Blueprints Repository](README.md)

A flexible, reusable Home Assistant blueprint that reads out a detailed daily weather report over text-to-speech with dynamic time-of-day greetings, real-time conditions, conditional high/low temperatures, precipitation chances, integrated volume control, and optional pre/post automation action hooks.

---

> ⚠️ **Prerequisites:**
> - **Weather Integration:** Requires a configured weather entity (e.g., `weather.home` or `weather.forecast_home`) that supports daily forecasts via `weather.get_forecasts`.
> - **TTS Engine:** Requires an active Text-to-Speech integration (e.g., `tts.google_translate_en_com`, `tts.home_assistant_cloud`, or others).

---
## Use Cases
- coming soon
---

## Features

- **Dynamic Greetings:** Automatically evaluates system time to greet you with *Good morning*, *Good afternoon*, or *Good evening*.
- **Robust Temperature Phrasing:** Dynamically adjusts spoken phrasing based on attribute availability. If daytime high or nighttime low forecast data is missing (common in evening updates), it skips the missing attribute gracefully instead of pronouncing code values like *"None"*.
- **Integrated Volume Control:** Includes an adjustable UI slider (0% to 100%) that sets your target speaker's volume level prior to speech playback.
- **Sectioned UI Layout:** Inputs are grouped into clear, collapsible visual sections (**Core Configuration**, **Automation Triggers**, **Actions Before**, and **Actions After**) for effortless configuration.
- **Pre & Post Action Hooks:** 100% optional custom action blocks allow you to turn on lights, wake up AV receivers, set scenes, or resume media playback before or after the announcement.
- **Multi-Trigger Support:** Accepts any combination of triggers (e.g., motion sensors, schedules, morning alarms, NFC tags, or physical button presses).
- **Engine-Agnostic TTS:** Built on modern `tts.speak` standards without hardcoded engine-specific parameters, ensuring maximum compatibility.
- **Operation Summary:**

  | Component | Action Taken |
  | :--- | :--- |
  | **Pre-Announcement Actions** | Runs optional user-defined sequence (e.g., waking AV receivers, flashing lights) before volume adjustment. |
  | **Volume Adjustment** | Sets the target media player volume level using percentage-to-decimal scaling. |
  | **Data Retrieval** | Calls `weather.get_forecasts` to pull daily forecast data into execution variables. |
  | **Template Rendering** | Formulates a localized announcement string with conditional handling for missing high/low attributes. |
  | **Speech Playback** | Triggers `tts.speak` with local caching enabled (`cache: true`) to minimize latency. |
  | **Post-Announcement Actions** | Runs optional user-defined sequence (e.g., turning off lights, resuming media) after speech completes. |

---

## Blueprint Inputs

### Core Configuration
| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Weather Integration Entity** | Select your Home Assistant weather entity (e.g., `weather.home`). | **Yes** | N/A |
| **TTS Engine** | Select the Text-to-Speech engine entity (e.g., `tts.google_translate_en_com` or `tts.home_assistant_cloud`). | **Yes** | N/A |
| **Target Media Player** | Select the media player to play the announcement on. | **Yes** | N/A |
| **Announcement Volume** | Set the volume level for the media player before speaking (0% to 100%). | No | `50` |

### Automation Triggers
| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Automation Triggers** | Add triggers that cause this announcement to run (e.g., motion sensor, time, button press). | No | `[]` |

### Custom Actions (Optional)
| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Actions Before Announcement** | Custom sequence of actions to run before volume setting and speech playback. | No | `[]` |
| **Actions After Announcement** | Custom sequence of actions to run after the weather report finishes speaking. | No | `[]` |

---

## 💡 Important Notes & Pro-Tips

- **Engine & Voice Selection:** Voice selection and accents are configured globally within your Home Assistant system settings (**Settings > Voice Assistants**). Keeping voice selection out of the blueprint ensures broad compatibility across all TTS engines.
- **Audio Caching (`cache: true`):** Home Assistant evaluates template variables *before* checking the cache. If weather conditions change, a new audio file is rendered. If identical, Home Assistant plays cached audio instantly.
- **Safe Empty Execution:** Both `actions_before` and `actions_after` default to `[]`. Leaving them unconfigured allows Home Assistant to skip them without logging errors or warnings.
- **Variable Pre-Mapping:** Volume inputs are mapped to local variables prior to template calculations (`(vol_setting | int) / 100`) to maintain compliance with blueprint parsing standards.

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
## Related Links
- coming soon
---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-11-03 | Initial release |
