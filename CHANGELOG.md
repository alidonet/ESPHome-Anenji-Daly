# Changelog

## v1.5.0

- Enabled firmware updates from the web interface and kept native ESPHome OTA.
- Restore the Daly connection after a failed OTA update.
- Mark stale inverter power readings as unavailable and display inverter connectivity in Home Assistant.
- Restore daily PV energy only for the matching calendar date.

## v1.4

- Added independently configurable and persistent Daly and inverter polling intervals;
- Shortened entity names and grouped settings and diagnostics by device. Rarely used service entities are disabled by default;
- Updated Home Assistant entity mappings and added a Home Flow Card example;
- Added an English/Russian language setting for text sensor states;

## v1.3

- Added first-run Wi-Fi setup and web-based Daly discovery. The ESP32 saves the selected BMS after receiving telemetry. The firmware no longer requires `secrets.yaml`;
- Added a choice between 62- and 80-register Daly reads. The Daly online indicator now expires after three poll intervals without telemetry;
- Updated Modbus and the Daly BLE dependency for ESPHome 2026.11. Shortened inverter fault messages and tightened documented inverter setting limits;
- Improved Modbus recovery and stopped counting gaps in the daily PV energy estimate. Stale inverter battery power readings now expire;

## v1.2

- Added the initial ESP32 configuration and binary for Anenji over RS485 and Daly over BLE;

## v1.1
- Grouped Anenji and Daly entities under separate Home Assistant devices, added dashboard views and online indicators, and improved connection settings;

## v1.0
- Stable version with all available sensors;
- Updated the polling configuration;

## v0.3
- Few updates and bugfixes;

## v0.2
- Split sensor by devices;
- Remove unused sensors (blank);

## v0.1
- Draft version with joined Anenji and Daly sensors;
