# 🔴 Critical Switch Monitoring & Notification

**Blueprint**: [notify_critical-switches.yaml](notify_critical-switches.yaml)

Monitors critical switches and sends notifications when they become inactive, with hourly repeat notifications and automatic all-clear. **Triggers immediately when switches are manually turned off.**

## Features

- ✅ Monitors critical switches sensor for state changes to "unavailable"
- ✅ **Triggers immediately when any critical switch is turned off manually**
- ✅ Sends notifications when switches become inactive
- ✅ Hourly repeat notifications while issues persist
- ✅ Automatic all-clear notification when all switches are restored
- ✅ Persistent notification in Home Assistant UI
- ✅ Lists all inactive switches in notifications

## Requirements

- Home Assistant with notification services configured
- A sensor that counts inactive critical switches (template sensor recommended)
- A group containing all critical switches to monitor

## How to Import

**Direct Import (if repository is public):**
[![Blueprint Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/DemSt-CH/my-ha-collection/blob/main/blueprints/Notification/notify_critical-switches.yaml)

**Manual Import (for private repositories):**
1. Download [notify_critical-switches.yaml](notify_critical-switches.yaml)
2. In Home Assistant: **Settings > Automations & Scenes > Blueprints > Import Blueprint**
3. Upload or paste the YAML content

## Configuration

After importing, configure the following:
1. **Critical Switches Sensor**: Select the sensor that counts inactive switches
2. **Critical Switches Group**: Choose the group containing all switches to monitor
3. **Notification Recipients**: Select who should receive notifications
4. **Notification Interval**: Set how often to repeat notifications (default: 60 minutes)

## Example Setup

(You can use also the HA-UI for creating this Template-Sensor and the Group)

**Template Sensor** (counts inactive switches):
```yaml
template:
  - sensor:
      name: "Active Critical Switches"
      state: >
        {% set group_id = 'switch.critical_switches' %}
        
        {{ expand(group_id)
        | rejectattr('entity_id', 'in', exclude)
        | selectattr('state', 'in', ['off', 'unavailable'])
        | list 
        | count }}
```

**Switch Group**:
```yaml
group:
  critical_switches:
    name: "Critical Switches"
    entities:
      - switch.server_power
      - switch.network_switch
      - switch.security_system
```

## Changelog

### v1.0 (2026-03-13)
- Initial release
- Monitor critical switches with sensor
- Hourly repeat notifications
- Automatic all-clear notifications
- Configurable recipients and intervals

---

## Back to Blueprints

[← Back to Blueprints](../README.md)</content>
<parameter name="filePath">c:\_DemSte\my-ha-collection\blueprints\Notification\README.md