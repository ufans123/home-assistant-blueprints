## Scene Selector with Light Effect Support (Hue & Govee)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Finput_select_scene_selector.yaml)

> **Version:** 1.0 | **Initial Release:** 2026-10-27 | [← Back to Main Blueprints Repository](README.md)

This automation blueprint allows you to trigger **Home Assistant scenes** or execute native **hardware light effects** (such as Govee dynamic hardware scenes or WLED presets) using an `input_select` dropdown helper. When an option is selected, the blueprint seamlessly detects whether to trigger a standard HA `scene` or call `light.turn_on` with the dynamic `effect` payload. Choosing the reset/default option cleanly turns off the target light.

### Complexity & Setup Effort

> ⚠️ **Advanced User Project**
> 
> While this blueprint handles the core automation logic seamlessly, putting the entire ecosystem together requires intermediate-to-advanced Home Assistant knowledge. 
> 
> * **Estimated Setup Time:** ~30 to 45 minutes (depending on how many rooms/lights you are configuring).
> * **Moving Parts:** This setup relies on a coordinated chain of custom components:
>   1. Manual creation of `input_select` helper entities.
>   2. A custom YAML startup automation to dynamically populate dropdown options.
>   3. Optional custom dashboard cards or UI popups (like Bubble Card) to drive the selection interface.
> 
> *If you are looking for a simple, out-of-the-box automation, this might feel heavy on manual configuration. However, if you love clean, dynamic dashboards and automated helper syncing, the end result is exceptionally powerful!*

### Features
- **Dual Support (Scenes & Hardware Effects):** Seamlessly handles both standard Home Assistant scenes (like Philips Hue) and native light hardware effects (like Govee or WLED).
- **Dynamic Matching:** Evaluates if a dropdown selection matches an entry in the target light's `effect_list` attribute, falling back safely to standard HA scene execution.
- **Off/Reset Handling:** Automatically turns off the target light when the designated default/reset option is selected.
- **Dashboard Flexible:** Works with standard HA dropdown select entities or custom UI cards (such as Bubble Card popups or custom button cards calling `input_select.select_option`).

### Prerequisites
1. **Scene & Effect Availability:**
  - **Philips Hue:** Scenes must first be created in the Hue App (or natively in Home Assistant) and assigned to their respective Home Assistant Areas.
  - **Govee / Hardware Effects:** Built-in hardware effects are automatically exposed out-of-the-box by the Govee integration via the light entity's `effect_list` attribute.
2. **Input Select Helpers:** You must create an `input_select` dropdown helper for each light or target area (e.g., `input_select.living_room_scenes`).
3. **Startup Automation:** A startup automation (`homeassistant.start`) must be configured to dynamically harvest those pre-existing area scenes and light effects, populating your `input_select` options on boot.

---

### Startup Automation Example

To ensure your dropdown helpers automatically stay in sync with your available scenes and hardware effects, create a startup automation like the shortened example below:

```yaml
alias: "On Startup: Populate Scene and Effect Options"
description: "Dynamically populates input_select dropdowns for area scenes and light effects on boot."
triggers:
  - trigger: homeassistant
    event: start
conditions: []
actions:
  - delay: "00:00:05"

  # Populate Govee / Light Hardware Effects
  - repeat:
      for_each:
        - light: light.den_floor_lamp
          select: input_select.den_floor_lamp_effects
        - light: light.bedroom_floor_lamp
          select: input_select.bedroom_floor_lamp_effects
      sequence:
        - action: input_select.set_options
          target:
            entity_id: "{{ repeat.item.select }}"
          data:
            options: >-
              {% set effects = state_attr(repeat.item.light, 'effect_list') or [] %}
              {{ ['Select an option'] + (effects | reject('eq', '') | list) }}

  # Populate Area Scenes (Philips Hue / HA Scenes)
  - repeat:
      for_each:
        - area: Den
          select: input_select.den_table_lamp_scenes
        - area: Bedroom
          select: input_select.bedroom_table_lamp_scenes
        - area: Living Room
          select: input_select.living_room_scenes
      sequence:
        - action: input_select.set_options
          target:
            entity_id: "{{ repeat.item.select }}"
          data:
            options: |-
              {% set entities = area_entities(repeat.item.area) or [] %}
              {% set scenes = expand(entities)
                | selectattr('domain', 'eq', 'scene')
                | map(attribute='name')
                | sort
                | list %}
              {{ ['Select an option'] + scenes }}
mode: single
```
### Input Reference

| Input | Type | Description |
| :--- | :--- | :--- |
| **Scene Input Select** | Entity Selector (`input_select`) | Select the `input_select` helper entity used to choose scenes or effects for this light/area. |
| **Target Light** | Entity Selector (`light`) | The specific light entity to control or turn off when the reset option is selected. |
| **Default / Reset Option** | Text Input | The exact text string in the dropdown that represents turning off the light (Default: `"Select an option"`). |

### Pro Tips
- **Exact String Matching:** Ensure your startup automation populates option text verbatim from the `effect_list` attribute to guarantee exact case-sensitive matching for Govee effects.
- **Single Entity Targeting:** Target specific light entities (`light.den_floor_lamp`) rather than light groups, as standard HA light groups do not aggregate `effect_list` attributes from child devices.
- **Custom UI Popups:** Pair this blueprint with custom dashboard popups (like **Bubble Card**) or tile buttons by setting their `tap_action` to `input_select.select_option`.

### Installation

#### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Finput_select_scene_selector.yaml)

#### Method 2: Manual Installation
1. Download or clone the raw `input_select_scene_selector.yaml` file from this repository. [`input_select_scene_selector.yaml`](https://github.com/ufans123/home-assistant-blueprints/blob/main/input_select_scene_selector.yaml)
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/home-assistant-blueprints/`).
3. Paste the code into a file named `input_select_scene_selector.yaml`.
4. Reload your automations or restart Home Assistant.

#### Method 3: Manual Installation using the Blueprints Dashboard
1. Copy the following URL:
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/input_select_scene_selector.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI (**Settings > Automations & Scenes > Blueprints**).
3. In the bottom right corner, click on the **'Import blueprint'** button.
4. Paste in the URL and follow the prompts.

---

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **v1.0** | 2026-10-27 | Initial release with dual Hue scene and Govee effect support |
