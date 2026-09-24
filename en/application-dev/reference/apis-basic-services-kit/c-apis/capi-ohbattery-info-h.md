# ohbattery_info.h

## Overview

Declares the battery APIs that are used to obtain the current battery capacity and power supply type and define common battery events.

**Library**: libohbattery_info.so

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Related module**: [OH_BatteryInfo](capi-oh-batteryinfo.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [BatteryInfo_BatteryPluggedType](#batteryinfo_batterypluggedtype) | BatteryInfo_BatteryPluggedType | Enumerates the battery plugged types. |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_BatteryInfo_GetCapacity()](#oh_batteryinfo_getcapacity) | Obtains the current battery capacity in percent. |
| [BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()](#oh_batteryinfo_getpluggedtype) | Obtains the battery plugged type. |

### Variable

| Name | Description |
| -- | -- |
| static const char *COMMON_EVENT_KEY_CAPACITY = "soc" | Defines the common event indicating a battery capacity change.<br>**Since**: 13 |
| static const char *COMMON_EVENT_KEY_CHARGE_STATE = "chargeState" | Defines the common event indicating a charging status change.<br>**Since**: 13 |
| static const char *COMMON_EVENT_KEY_PLUGGED_TYPE = "pluggedType" | Defines the common event indicating a battery plugged type change.<br>**Since**: 13 |

## Enum type description

### BatteryInfo_BatteryPluggedType

```c
enum BatteryInfo_BatteryPluggedType
```

**Description**

Enumerates the battery plugged types.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| PLUGGED_TYPE_NONE |  |
| PLUGGED_TYPE_AC |  |
| PLUGGED_TYPE_USB |  |
| PLUGGED_TYPE_WIRELESS |  |
| PLUGGED_TYPE_BUTT |  |


## Function description

### OH_BatteryInfo_GetCapacity()

```c
int32_t OH_BatteryInfo_GetCapacity()
```

**Description**

Obtains the current battery capacity in percent.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | A number in the range from 0 to 100. |

### OH_BatteryInfo_GetPluggedType()

```c
BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()
```

**Description**

Obtains the battery plugged type.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| [BatteryInfo_BatteryPluggedType](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) | <ul>          <li>[PLUGGED_TYPE_NONE](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) if there is no power supply;</li>          <li>[PLUGGED_TYPE_AC](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) if the power supply is in AC charging mode;</li>          <li>[PLUGGED_TYPE_USB](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) if the power supply is in USB DC charging mode;</li>          <li>[PLUGGED_TYPE_WIRELESS](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) if the power supply is in wireless charging mode;</li>          <li>[PLUGGED_TYPE_BUTT](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype) if the battery plugged type is unknown.</li>          </ul> |


