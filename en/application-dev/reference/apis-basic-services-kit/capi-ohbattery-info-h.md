# ohbattery_info.h

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b059b47d399447b512910e67cfcc81779f08ec3f translatedAt=2026-11-06T01:45:13.858Z pushedAt=2026-11-06T09:23:27.741Z nl=1 -->

## Overview

Declares the APIs that are used to obtain the current battery capacity and power supply type and define common battery events.

**File to include:** \<BasicServicesKit/ohbattery_info.h\>

**Library**: libohbattery_info.so

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Related modules**: [OH_BatteryInfo](capi-oh-batteryinfo.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [BatteryInfo_BatteryPluggedType](#batteryinfo_batterypluggedtype) | BatteryInfo_BatteryPluggedType | Enumerates the charger types. |

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_BatteryInfo_GetCapacity()](#oh_batteryinfo_getcapacity) | Obtains the current battery capacity, in percentage. |
| [BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()](#oh_batteryinfo_getpluggedtype) | Obtains the connected charger type. |

### Variables

| Name| Description|
| -- | -- |
| static const char * COMMON_EVENT_KEY_CAPACITY = "soc" | Defines the common event sent after the battery level changes.<br>**Since:** 13 |
| static const char * COMMON_EVENT_KEY_CHARGE_STATE = "chargeState" | Defines the common event indicating a charging status change.<br>**Since**: 13|
| static const char * COMMON_EVENT_KEY_PLUGGED_TYPE = "pluggedType" | Defines the common event sent after the connected charger type changes.<br>**Since:** 13 |

## Enum Description

### BatteryInfo_BatteryPluggedType

```c
enum BatteryInfo_BatteryPluggedType
```

**Description**

Enumerates the charger types.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| PLUGGED_TYPE_NONE = 0 | No power supply.|
| PLUGGED_TYPE_AC = 1 | AC charging.|
| PLUGGED_TYPE_USB = 2 | USB charging. |
| PLUGGED_TYPE_WIRELESS = 3 | Wireless charging. |
| PLUGGED_TYPE_BUTT = 4 | Unknown type.|


## Function Description

### OH_BatteryInfo_GetCapacity()

```c
int32_t OH_BatteryInfo_GetCapacity()
```

**Description**

Obtains the current battery capacity, in percentage. This method can be used to display battery information in battery monitoring apps, determine whether to prompt users when the battery is low, and determine whether to trigger power-saving mode.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Current battery level, in percentage. The value is an integer within the range of [0, 100]. If **-1** is returned, it indicates that the battery level fails to be obtained. |

### OH_BatteryInfo_GetPluggedType()

```c
BatteryInfo_BatteryPluggedType OH_BatteryInfo_GetPluggedType()
```

**Description**

Obtains the connected charger type. This method can be used to determine the current charging method in charging status detection apps, display charger type icons in charging reminder features, and adjust power-saving policies based on the charger type.

**System capability**: SystemCapability.PowerManager.BatteryManager.Core

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| [BatteryInfo_BatteryPluggedType](#batteryinfo_batterypluggedtype) | [PLUGGED_TYPE_NONE](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype): The power source is unplugged.<br>         [PLUGGED_TYPE_AC](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype): The power source is AC charging.<br>         [PLUGGED_TYPE_USB](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype): The power source is USB charging.<br>         [PLUGGED_TYPE_WIRELESS](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype): The power source is wireless charging.<br>         [PLUGGED_TYPE_BUTT](capi-ohbattery-info-h.md#batteryinfo_batterypluggedtype): The power source type is unknown. |


