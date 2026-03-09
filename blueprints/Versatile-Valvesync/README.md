# 🔧 Versatile Thermostat Valve Sync & Log

**Blueprint**: [versatile-valvesync.yaml](versatile-valvesync.yaml)

Automatically synchronizes valve positions for Versatile-Thermostats with the 'vtherm_over_valve' attribute and logs all corrections to the Home Assistant logbook.

## Features

- ✅ Runs every 15 minutes
- ✅ Automatically detects all compatible climate entities
- ✅ Syncs underlying valve entities to the target position
- ✅ Logs all corrections with thermostat and valve names
- ✅ No user input required - works automatically

## Requirements

- Home Assistant 2024.6.0 or later
- Thermostats must have a custom `vtherm_over_valve` attribute
- Attribute must contain `underlying_entities` list with valve entity IDs
- Valves must be number entities controllable via `number.set_value`

## How to Import

[![Blueprint Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint/?blueprint_url=https://raw.githubusercontent.com/DemSt-CH/my-ha-collection/main/blueprints/Versatile-Valvesync/versatile-valvesync.yaml)

## Changelog

### v1.0 (2026-03-08)
- Initial release
- Automatic valve synchronization
- Logbook integration

---

## Back to Blueprints

[← Back to Blueprints](../README.md)
