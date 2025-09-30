Home Assistant Blueprints
A collection of reusable Home Assistant blueprints for automations, designed for efficiency and persistence. This repository houses blueprints to streamline smart home setups, starting with a persistent timer blueprint that survives Home Assistant reboots.
Blueprints
Persistent Timer for Automation

File: persistent_timer.yaml
Description: Creates automations with delays that persist across Home Assistant reboots using an input_datetime helper. Ideal for scenarios like delayed notifications (e.g., dishwasher completion).
Usage:
Create an input_datetime helper (e.g., input_datetime.tag_dishwasher_timer) via Settings > Devices & Services > Helpers > Date and/or Time.
Import the blueprint in Home Assistant: Settings > Automations & Scenes > Blueprints > Import Blueprint, using the raw URL (https://raw.githubusercontent.com/yourusername/home-assistant-blueprints/main/persistent_timer.yaml).
Configure the automation:
Automation Alias: Name of your automation (e.g., Tag - dishwasher).
Trigger: Your trigger (e.g., tag scan, state change).
Delay Duration: Time to wait (e.g., 02:30:00 for 2h30m).
Actions: Actions to execute post-delay (e.g., send notification).


Add the startup_timer_check.yaml automation to catch missed timers on reboot.


Example: Triggers on a tag scan, waits 2h30m, then notifies a mobile device.

Startup Timer Check

File: startup_timer_check.yaml
Description: Automation that checks all persistent timers on Home Assistant startup, triggering any that expired during downtime.
Usage:
Add to Home Assistant via Settings > Automations & Scenes > Create Automation > Edit in YAML, or append to automations.yaml.
Ensure it runs automatically on startup to support all blueprint-based timers.



Installation

Clone or Fork: Clone this repository or fork it to your GitHub account.
Import Blueprints: Use the raw URL of each blueprint file in Home Assistant’s Import Blueprint feature.
Create Helpers: For each blueprint-based automation, create required helpers (e.g., input_datetime entities) as specified.
Add Startup Automation: Include startup_timer_check.yaml to ensure timer persistence.

Contributing

Add new blueprints by creating .yaml files in the repository.
Update this README with details of new blueprints.
Submit pull requests for improvements or additional automations.

Notes

Designed for Home Assistant setups using devices like Ubiquiti Dream Machine, Shelly, TP-Link Kasa, and ESP32.
Blueprints prioritize efficiency and minimal configuration for robust smart home automation.
Contact: Open an issue or submit a pull request for feedback or contributions.
