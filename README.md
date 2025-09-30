# Home Assistant Blueprints

A collection of reusable [Home Assistant](https://www.home-assistant.io/) blueprints and automations for efficient, persistent smart home setups. This repository streamlines automations, starting with a persistent timer blueprint that survives Home Assistant reboots.

## Blueprints

### Persistent Timer for Automation
- **File**: `persistent_timer.yaml`
- **Description**: Creates automations with delays that persist across reboots using an `input_datetime` helper. Works with any trigger (e.g., tag scans, motion sensors, switches).
- **Usage**:
  1. Create an `input_datetime` helper (e.g., `input_datetime.dishwasher_timer`) via **Settings > Devices & Services > Helpers > Date and/or Time**. Name it to match the slugified automation alias (e.g., "Dishwasher" for `dishwasher_timer`).
  2. Import the blueprint: **Settings > Automations & Scenes > Blueprints > Import Blueprint**, using the raw URL (`https://raw.githubusercontent.com/yourusername/home-assistant-blueprints/main/persistent_timer.yaml`).
  3. Configure the automation:
     - **Automation Alias**: Name that slugs to match the helper (e.g., `Dishwasher` for `input_datetime.dishwasher_timer`).
     - **Trigger**: Any trigger (e.g., tag scan, state change, time).
     - **Delay Duration**: Time to wait (e.g., `02:30:00` for 2h30m).
     - **Actions**: Actions to execute post-delay (e.g., send notification).
  4. Ensure `startup_timer_check.yaml` is active to catch missed timers on reboot.
- **Example**: Triggers on a tag scan, waits 2h30m, then sends a mobile notification.

## Automations

### Startup Timer Check
- **File**: `startup_timer_check.yaml`
- **Description**: Checks all persistent timers on Home Assistant startup, triggering any that expired during downtime.
- **Usage**:
  1. Add to Home Assistant via **Settings > Automations & Scenes > Create Automation > Edit in YAML**, or append to `automations.yaml`.
  2. Runs automatically on startup to support all blueprint-based timers.

## Installation

1. **Clone or Fork**: Clone this repository or fork it to your GitHub account.
2. **Import Blueprints**: Use the raw URL of each blueprint file in Home Assistant’s **Import Blueprint** feature.
3. **Add Automations**: Add non-blueprint automations (e.g., `startup_timer_check.yaml`) via the UI or `automations.yaml`.
4. **Create Helpers**: For each blueprint-based automation, create required helpers (e.g., `input_datetime.dishwasher_timer`).
5. **Add Startup Automation**: Include `startup_timer_check.yaml` to ensure timer persistence.

## Contributing

- Add new blueprints or automations by creating `.yaml` files in the repository.
- Update this README with details of new additions.
- Submit pull requests for improvements or additional automations.

## Notes

- Designed for Home Assistant setups with devices like Ubiquiti Dream Machine, Shelly, TP-Link Kasa, and ESP32.
- Blueprints prioritize efficiency and minimal configuration for robust automation.
- **Contact**: Open an issue or submit a pull request for feedback or contributions.
