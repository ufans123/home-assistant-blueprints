# Scheduled Notifications To Do List (Day of the Month)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fscheduled_task_notifications_manager.yaml)

> **Version:** 2.1 | **Latest update:** 2026-10-29 | [← Back to Main Blueprints Repository](README.md)

*(Previously: Scheduled Task Notifications Manager v1.0)*

An advanced, highly flexible scheduling blueprint engine that generates up to 10 sequential persistent notification cards and/or pushes tasks to a persistent dashboard To-Do list, bound to an optional day of the month, an input helper switch, or custom system events.

## Key Architectural Features

This blueprint functions as a comprehensive software application model utilizing several advanced design patterns:

- **Decoupled Flag Routing Engine:** Solves traditional top-level calendar block conflicts by evaluating triggers upfront inside a localized Jinja block. It sets a strict boolean flag (`should_run`), allowing manual helper forces to effortlessly bypass calendar day locks while keeping automatic time schedules strictly day-bound.
- **Variable Scope Protection:** Maps blueprint input definitions down into local runtime script variables at the exact millisecond of execution. This prevents the `blueprint_inputs` scope-loss bug common to long automation scripts.
- **Top-Down Visual Feed Layering:** Reverses execution layout paths for notifications (firing Task 10 down to Task 1) to force the Home Assistant desktop notification pane to layer alerts in a logical, top-down reading order (Overview → Task 1 → Task 2).
- **Native To-Do List Synchronization:** Safely pushes tasks to any dashboard `todo` entity. Dynamically sequences the insertion order so that Task 1 consistently lands at the top of a manual-sort list without manual intervention.
- **Dynamic Carriage-Return Message Digest:** Sweeps populated inputs on the fly, hiding empty text rows, and using embedded Markdown block trailing trim overrides (`{"\n"}`) to automatically compile a clean, single-line bulleted text summary.
- **Isolated Multi-Instance Capacity:** Anchors notification tracking handles to `{{ this.entity_id }}`. You can spin up 31 separate automations from this single file (one for every day of the month) without any duplicate entity keys or visual card clashing.

## Configuration Properties

| Field Name | Type | Description |
| :--- | :--- | :--- |
| **Enable Daily Time Schedule** | Toggle | Uncheck to turn off the automatic time execution. The list will then function purely on-demand via helpers or manual execution. |
| **Target Calendar Day** | Number (1-31) | The specific numeric day of the month this automation is allowed to execute on schedule. |
| **Scheduled Execution Time** | Time Picker | What time of day the automation executes its calendar date check routine. |
| **Manual Force Helper** | Entity (`input_boolean`) | *Optional.* An input helper switch that immediately triggers your tasks, automatically resetting itself to `OFF` within 1 second. |
| **Enable Persistent Notifications** | Toggle | Check to generate dismissible Home Assistant persistent notification cards for each task. |
| **Enable To-Do List Integration** | Toggle | Check to push tasks to a persistent dashboard To-Do list entity. |
| **Dashboard To-Do List Entity** | Entity (`todo`) | *Optional.* Select a To-Do list entity (e.g., `todo.monthly_chores`) if To-Do integration is enabled. |
| **Enable Summary Digest Card** | Toggle | When checked, it generates a master summary card listing all your active custom body messages as an itemized bulleted checklist. |
| **Overview Card Title** | Text String | Custom title for the summary digest card. |
| **Task Slots (1 - 10)** | Text String Pairs | 10 independent input lanes allowing you to type distinct titles and body descriptions for your reminders. Empty slots are cleanly ignored. |

## Setting Up a Local To-Do List (Prerequisite)

If you plan to use the To-Do list integration and don't have a target list set up yet, create one quickly in Home Assistant:

1. **Enable the Integration:** Go to **Settings > Devices & Services > Add Integration**, search for **Local To-Do**, and add it.
2. **Create the Helper:** Go to **Settings > Devices & Services > Helpers**, click **+ Create Helper**, and select **Local To-Do**. 
3. Name your list (e.g., `Monthly Chores`) and click **Submit**. You can then select this new entity in your blueprint configuration.

## How to Install

### Method 1: Click to Import (Easiest)
Click the badge below to import this blueprint directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fufans123%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fscheduled_task_notifications_manager.yaml)

### Method 2: Manual Installation
1. Copy the raw contents of [scheduled_task_notifications_manager.yaml](https://github.com/ufans123/home-assistant-blueprints/blob/main/scheduled_task_notifications_manager.yaml).
2. In your Home Assistant configuration directory, navigate to your blueprints folder (e.g., `config/blueprints/automation/ufans123/`).
3. Paste the code into a file named `scheduled_task_notifications_manager.yaml`.
4. Reload your automations or restart Home Assistant. 

### Method 3: Manual Installation using the Blueprints Dashboard (Easier) 
1. Copy the following URL...
```
https://github.com/ufans123/home-assistant-blueprints/blob/main/scheduled_task_notifications_manager.yaml
```
2. Navigate to your Home Assistant Blueprints Dashboard UI
3. In the bottom right corner click on the *'Import blueprint'* button
4. Paste in the URL and follow the prompts

## Related Blueprints
[Scheduled Notifications To Do List (Day of Week)](https://github.com/ufans123/home-assistant-blueprints/blob/main/scheduled-task-notifications-dow.md)

## Changelog

| Version | Date | Summary of Changes |
| :--- | :--- | :--- |
| **Version 2.1** | 2026-10-29 | Added **Smart To-Do List Recycling**, enabling the blueprint to automatically find, update descriptions, and reactivate (`needs_action`) completed or existing tasks to prevent duplicate list spam. |
| **Version 2.0** | 2026-10-29 | Added dashboard **To-Do List** integration, top-down sequence handling, modular toggles, and renamed to **Scheduled Notifications To Do List** |
| **Version 1.0** | 2026-10-05 | Initial release of **Scheduled Task Notifications Manager** |
