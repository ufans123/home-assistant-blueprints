# Spotify NFC Jukebox with Smart Tracker

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fspotify_nfc_trigger.yaml)

> **Version:** 1.0 | **Updated:** 2026-10-24 | [← Back to Main Blueprints Repository](README.md)

An intelligent, feature-rich Spotify automation blueprint for Home Assistant NFC tags. Designed with smart state management to handle playback seamlessly—resuming if rescanned, pausing if currently playing, and instantly switching or restarting when a different tag is scanned.

## Prerequisites

Before setting up this blueprint, make sure you have the following ready:
- **Spotify Integration:** The official [Spotify Integration](https://www.home-assistant.io/integrations/spotify/) must be successfully integrated into Home Assistant, with your Spotify account linked and media player entities available.
- **NFC Tags:** Physical NFC tags (NTAG215 or similar) capable of being scanned by your phone or a dedicated Home Assistant NFC reader.

---

## Features

- **Smart State Management:** Automatically handles playback states—resumes if rescanned, pauses if currently playing, and switches or restarts immediately if a different tag is scanned.
- **Multi-Instance Zone Tracking:** Optional shared `input_text` helpers allow multiple NFC tags across a shared area to track active sources and coordinate playback.
- **Offline / Disconnected Safety Reset:** Automatically clears the tracking helper if the target speaker becomes `unavailable` or `unknown`, preventing stale session locking when a speaker drops off Wi-Fi or powers down.
- **Flexible Fallback Mode:** Leave the tracker fields blank to effortlessly drop back to a standard standalone play/pause toggle mode.
- **Clean UI Layout:** Grouped configuration sections (`NFC Tag Configuration`, `Jukebox Configuration`, and `Smart Jukebox Tracker`) complete with comprehensive inline tooltips and explicit user guidance.
- **Behavior Mapping:**
  
  | Event / Scanned State | Action Taken |
  | :--- | :--- |
  | **Same Tag Rescanned (Playing)** | Pauses playback. |
  | **Same Tag Rescanned (Paused)** | Resumes playback. |
  | **Different Tag Scanned (Smart Tracker Paired)** | Forces a fresh play of the new playlist and updates the tracking helper. |
  | **Tag Scanned (Speaker Offline/Unavailable)** | Automatically clears the tracking helper so a new session can start cleanly. |
  | **Tag Scanned (Standalone Mode / Blank Tracker)** | Toggles play/pause or initiates playback if stopped. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **NFC Tag ID** | The ID string of the scanned physical NFC tag. | **Yes** | N/A |
| **Tag Label / Descriptor** | A friendly human-readable name or description for this physical tag (e.g., *Living Room - Jazz Tag*). Non-functional; purely for identification. | No | `""` |
| **Target Speaker** | The media player entity to output playback. **Note:** Select a single speaker or a single synchronized group to prevent tracking bugs. | **Yes** | N/A |
| **Spotify Playlist Link / URI** | The Spotify URL or URI to play (browse via [open.spotify.com](https://open.spotify.com)). Supports trimming query parameters like `?si=...` or native `spotify:playlist:...` URIs. | **Yes** | N/A |
| **Playlist ID (Smart Jukebox)** | Unique identifier string for this specific playlist/tag (e.g., `jazz` or `rock`). Required if using a tracking helper. | No | `""` |
| **Tracking Helper Entity** | Optional shared `input_text` helper entity used to track the active source across the zone (e.g., `input_text.jukebox_kitchen`). Must be paired with a Playlist ID. | No | `""` |

---

## 💡 Important Notes & Pro-Tips

- **Requirements for Smart Tracking:** Both **Playlist ID** and **Tracking Helper** must be configured together to enable multi-instance zone switching. Leave them blank to fall back to standard standalone play/pause toggle mode.
- **Speaker Selection:** Please select only a single media player speaker or a single synchronized speaker group. Selecting multiple independent speakers can cause playback control or state-tracking issues.
- **Tracking Helper Scope:** Assign a dedicated `input_text` helper entity per target speaker or synchronized group (e.g., `input_text.jukebox_kitchen` for Kitchen, `input_text.jukebox_patio` for Patio). Reusing the same tracking helper across separate physical locations will cause playback switching to cross-talk between zones.

---

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fspotify_nfc_trigger.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`spotify_nfc_trigger.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/spotify_nfc_trigger.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `spotify_nfc_trigger.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/spotify_nfc_trigger.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (**Settings** > **Automations & Scenes** > **Blueprints**).
3. In the bottom right corner, click on the **Import blueprint** button.
4. Paste in the URL and follow the prompts.

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-24 | Initial release |
