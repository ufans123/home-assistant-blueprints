# Spotify: Play Playlist, Album, or Artist

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fspotify_dashboard_player.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-11-18 | [← Back to Main Blueprints Repository](README.md)

A clean, flexible Spotify automation blueprint for Home Assistant driven by an `input_select` helper. Link any number of playlists, albums, or artists to dropdown options using a simple key-value Media Map—allowing you to launch and switch music from dashboard dropdowns, quick-action buttons, without creating separate automations for every playlist.

## Prerequisites

Before setting up this blueprint, make sure you have the following ready:
- **Spotify-Capable Media Player:** A configured media player entity capable of playing Spotify URLs/URIs—such as the official [Spotify Integration](https://www.home-assistant.io/integrations/spotify/), Spotcast, Music Assistant, or compatible Cast/smart speakers.
- **`input_select` Helper:** A Dropdown (`input_select`) helper created in Home Assistant (**Settings** > **Devices & Services** > **Helpers**) pre-populated with your desired playlist, mood, or artist names.

---

## Use Cases

- **Dashboard Music Jukebox & Mood Selector:** Add your `input_select` helper to a dashboard as a standard dropdown menu or a row of quick-tap buttons (using stile, or custom cards like `custom:bubble-card` or my favorite `custom:lcards-select-menu`) for instant one-tap playlist switching.
- **Single-Automation Library Management:** Manage dozens of playlists, albums, and artists inside a single automation. Adding new music only requires adding an option to your helper and pasting its Spotify link into the Media Map.
- **Hands-Free Routines & Voice Control:** Trigger playback from morning routines, bedtime schedules, NFC tags, or voice commands simply by calling `input_select.select_option` on your helper.
- **Make Dashboards for Each Speaker Group:** Depending on your setup you may have a dashboard for each room.
- **Build Your Dashboard Remotes:** Add media player cards and whatever methods you like to trigger the ``input_select`` options. These make perfect remotes for phones or tablets.
- **Pair with Lighting Automations** For mood and enjoyment while chilling, add lighting automations to your dashboard.

---

## Features

- **Dynamic Media Mapping:** Maps `input_select` options directly to Spotify URLs (`https://open.spotify.com/...`) or URIs using a flexible key-value YAML object—automatically detecting whether the target is a playlist, album, or artist.
- **No Practical Playlist Limits:** Add as many playlists, albums, or artists as needed (limited only by Home Assistant's 255-character state length for individual option names).
- **Non-Intrusive Starting Volume:** Optional baseline volume setting applies *only* when the speaker is currently `off`, `idle`, or `standby`. Switching playlists while music is already playing preserves any manual volume adjustments made on your media player card.
- **Graceful Unmapped Option Handling:** If an `input_select` option does not have a matching entry in the Media Map (such as a `"None"` or `"Select Playlist..."` placeholder option), the automation safely exits without errors.
- **Clean Categorized UI:** Organized into collapsible sections (`Entities & Target Device`, `Spotify Media Mapping`, and `Optional Playback Settings`) with inline descriptions and starter examples.
- **Behavior Mapping:**

  | Event / Speaker State | Action Taken |
  | :--- | :--- |
  | **Option Selected (Mapped in Media Map)** | Parses the Spotify content type and starts playback on the target media player. |
  | **Option Selected (Not in Media Map)** | Safely aborts without triggering playback or errors. |
  | **Playback Started (Speaker `off` / `idle` / `standby`)** | Applies **Initial Starting Volume** (if greater than `0`) before starting playback. |
  | **Playlist Switched (Speaker `playing` / `paused`)** | Starts the new selection immediately while preserving current speaker volume. |

---

## Blueprint Inputs

| Input | Description | Required? | Default |
| :--- | :--- | :--- | :--- |
| **Input Select Helper** | The `input_select` helper entity that triggers playback whenever its selected option changes. | **Yes** | N/A |
| **Media Player** | The target `media_player` entity where Spotify content will play. | **Yes** | N/A |
| **Media Map** | Key-value pairs (`Option Name: Spotify Link`) linking each `input_select` option to a Spotify URL or URI. Keys are case-sensitive. | **Yes** | Starter examples (`Chill`, `Workout`, `Daft Punk`) |
| **Initial Starting Volume** | Optional baseline volume (`0` to `1` in `0.05` steps) applied only when starting playback from an `off`, `idle`, or `standby` state. Set to `0` to disable. | No | `0` |

---

## 💡 Important Notes & Pro-Tips

- **Exact Case-Sensitive Matching:** The keys on the left side of your **Media Map** must match the option names in your `input_select` helper character-for-character (including capitalization and spaces).
- **Placeholder Option Trick:** Add an unmapped option like `Select Music...` as the first item in your `input_select` helper. Because it isn't listed in the Media Map, selecting it won't trigger playback—giving you a clean idle state for your dashboard dropdown.
- **Dashboard Button Setup:** Prefer tap buttons over a dropdown? Use a `horizontal-stack` of standard Button cards, `custom:mushroom-chips-card`, or `custom:lcards-select-menu` calling the `input_select.select_option` action:
  ```yaml
  type: horizontal-stack
  cards:
    - type: button
      name: Chill
      icon: mdi:coffee
      tap_action:
        action: call-service
        service: input_select.select_option
        target:
          entity_id: input_select.spotify_mood
        data:
          option: Chill
    - type: button
      name: Workout
      icon: mdi:dumbbell
      tap_action:
        action: call-service
        service: input_select.select_option
        target:
          entity_id: input_select.spotify_mood
        data:
          option: Workout
    - type: button
      name: Daft Punk
      icon: mdi:sunglasses
      tap_action:
        action: call-service
        service: input_select.select_option
        target:
          entity_id: input_select.spotify_mood
        data:
          option: Daft Punk
  ```
- **Active Spotify Connect Sessions:** If playback ever routes to multiple speakers unexpectedly, check whether your target media player is part of an active speaker group or holding onto a prior Spotify Connect session.

## Installation

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fspotify_dashboard_player.yaml)

### Method 2: Manual Installation
1. Download or clone the raw YAML file from this repository: [`spotify_dashboard_player.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/spotify_dashboard_player.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `spotify_dashboard_player.yaml`.
4. Reload your automations or restart Home Assistant.

### Method 3: Manual Installation using the Blueprints Dashboard (Easier)
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/spotify_dashboard_player.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (**Settings** > **Automations & Scenes** > **Blueprints**).
3. In the bottom right corner, click on the **Import blueprint** button.
4. Paste in the URL and follow the prompts.

---
## Related Links
| Blueprint | Description | 
| :--- | :--- | 
|[Spotify NFC Jukebox with Smart Tracker](https://github.com/ufans123/home-assistant-blueprints/blob/main/spotify-nfc-trigger.md)|Intelligent Spotify jukebox automation for NFC tags featuring smart state management (resumes, pauses, switches/restarts) and an offline/unavailable speaker safety reset.|
---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-18 | Initial release |


