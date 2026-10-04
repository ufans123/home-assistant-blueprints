# Home Assistant Blueprints 🏠

Welcome to my personal Home Assistant blueprints repository! This project contains advanced, highly customized configuration engines designed to streamline smart home automation orchestration.

## 📋 Scheduled Task Notifications Manager

An advanced, highly flexible scheduling blueprint engine that generates up to 10 sequential persistent notification cards bound to an optional day of the month, an input helper switch, or custom system events.

### 🚀 1-Click Blueprint Installation
To import this blueprint directly into your local Home Assistant instance, click the direct link below:

👉 [Click Here to Import this Blueprint to Home Assistant](https://home-assistant.io)


---

## ✨ Key Architectural Features

Unlike standard Home Assistant templates, this blueprint functions as a comprehensive software application model utilizing several advanced design patterns:

* **Decoupled Flag Routing Engine:** Solves traditional top-level calendar block conflicts by evaluating triggers upfront inside a localized Jinja block. It sets a strict boolean flag (`should_run`), allowing manual helper forces to effortlessly bypass calendar day locks while keeping automatic time schedules strictly day-bound.
* **Variable Scope Protection:** Maps blueprint input definitions down into local runtime script variables at the exact millisecond of execution. This prevents the `blueprint_inputs` scope-loss bug common to long automation scripts.
* **Top-Down Visual Feed Layering:** Reverses execution layout paths (firing Task 10 down to Task 1) to force the Home Assistant desktop notification pane to layer alerts in a logical, top-down reading order (Overview → Task 1 → Task 2).
* **Dynamic Carriage-Return Message Digest:** Sweeps populated inputs on the fly, hiding empty text rows, and using embedded Markdown block trailing trim overrides (`{"\n"}`) to automatically compile a clean, single-line bulleted text summary.
* **Isolated Multi-Instance Capacity:** Anchors notification tracking handles to `{{ this.entity_id }}`. You can spin up 31 separate automations from this single file (one for every day of the month) without any duplicate entity keys or visual card clashing.

---

## ⚙️ Configuration Properties

| Field Name | Type | Description |
| :--- | :--- | :--- |
| **Enable Daily Time Schedule** | Toggle | Uncheck to turn off the automatic time execution. The list will then function purely on-demand via helpers or manual execution. |
| **Target Calendar Day** | Number (1-31) | The specific numeric day of the month this automation is allowed to execute on schedule. |
| **Scheduled Execution Time** | Time Picker | What time of day the automation executes its calendar date check routine. |
| **Manual Force Helper** | Entity (`input_boolean`) | *Optional.* An input helper switch that immediately triggers your tasks, automatically resetting itself to `OFF` within 1 second. |
| **Enable Summary Digest Card** | Toggle | When checked, it generates a master summary card listing all your active custom body messages as an itemized bulleted checklist. |
| **Task Slots (1 - 10)** | Text String Pairs | 10 independent input lanes allowing you to type distinct titles and body descriptions for your reminders. Empty slots are cleanly ignored. |

---

## 📂 Installation Path

To install manually via your configuration directory layout without using the 1-click badge wrapper, download `scheduled_task_notifications_manager.yaml` and save it to:

```text
config/blueprints/automation/ufans123/scheduled_task_notifications_manager.yaml
```

Once saved, reload your automations via **Developer Tools > YAML > Automations** to launch the configuration wizard inside your visual automation dashboard builder!
