# Battery-Controlled Charging Switch - Time Failsafe Companion (DRAFT)

This is a companion blueprint designed to work alongside the primary [Battery-Controlled Charging Control](README.md). While the main automation controls charging based strictly on percentage thresholds, this companion blueprint layers an extra layer of protection by enforcing a maximum time limit on active charging sessions.

[← Back to Main Threshold Blueprint Documentation](README.md)
---

# Battery-Controlled Charging Switch - Time Failsafe Companion

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL pre-filled.](https://home-assistant.io)](https://home-assistant.io)

This is a companion blueprint designed to work alongside the primary [Battery-Controlled Charging Switch](README.md)...


By focusing on the `charging` and `discharging` states, this automation completely insulates your smart setup from network dropouts (`unavailable` or `unknown` blips) and accommodates brief device usage without resetting your tracking window.

## Features

- **Multi-Domain Compatibility:** Works seamlessly with smart plugs registered as either `switch` or `light` entities (such as Philips Hue or generic smart relays).
- **Network Dropout Immunity:** If your device temporarily loses Wi-Fi or drops offline, the automation holds its state and prevents the countdown from failing or resetting.
- **Sustained Discharge Detection:** Permits you to pick up your phone to read a message or take a call. If plugged back in within your defined grace period, tracking continues uninterrupted.
- **Dynamic Duration Overrides:** Passes your custom duration selection directly to the Home Assistant timer engine on execution, overriding any default helper zero-values.

## Prerequisites

Before configuring this blueprint, you must create a standard **Timer Helper** in Home Assistant to serve as the countdown clock tracker:

1. Navigate to **Settings** > **Devices & Services** > **Helpers**.
2. Click **Create Helper** and select **Timer**.
3. Provide a name (e.g., `Phone Charging Failsafe Timer`).
4. *Optional:* You can leave the default duration as `00:00:00`, as this blueprint dynamically forces your custom parameters upon start.
5. Click **Create**.

## Input Configuration

| Input Field | Type | Description |
| :--- | :--- | :--- |
| `Smart Plug` | Entity (`switch` / `light`) | The smart switch or converted light entity controlling power to the physical charger. |
| `Battery Status Sensor` | Entity (`sensor`) | The device state sensor tracking charging status (looks explicitly for states like `charging` or `discharging`). |
| `Helper Timer` | Entity (`timer`) | The Home Assistant tracking timer helper you created in the prerequisites. |
| `Maximum Charge Duration` | Time Selector | The maximum continuous time window allowed for charging before power is forcefully cut. |
| `Discharge Grace Period` | Slider (Minutes) | The time window the device is allowed to remain unplugged before the tracking session cancels entirely. |

## How the Blueprint Lifecycle Works

1. **The Core Trigger:** Your main threshold automation flips the smart plug `on` when your battery drops too low. This companion automation remains idle until you dock the phone and the status updates to `charging`.
2. **The Handshake:** Once `charging` is confirmed and the plug state is verified as `on`, the automation instantly programs your target helper timer with your custom duration and fires it.
3. **The Interruption (Grace Period):** If you unplug your phone to check it, the automation switches to its `restart` sequence and monitors a delay. If docked again within your chosen minute threshold, the shutdown sequence vaporizes, and tracking safely resumes.
4. **The Safe Termination:** If your primary automation tops the phone off naturally, it cuts the plug. The companion instantly catches this and cleanly breaks the active timer. If a runaway charge occurs and the timer runs out first, the companion intercepts power, cuts the plug universally, and resets.
