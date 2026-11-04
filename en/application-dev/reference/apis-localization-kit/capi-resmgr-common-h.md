# resmgr_common.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:34:26.372Z pushedAt=2026-11-04T08:47:59.721Z nl=1 -->

## Overview

Provides the enum types and struct definitions required by the resourcemanager module.<br> This header file defines the enums of error codes, screen orientation, color mode, device type, and screen density, as well as the device configuration struct, providing data type support for the resource acquisition functions in ohresmgr.h.

**File to include**: <resourcemanager/resmgr_common.h>

**Library**: libohresmgr.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

**Related module**: [resourcemanager](capi-resourcemanager.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) | ResourceManager_Configuration | Defines the struct of the device status. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ResourceManager_ErrorCode](#resourcemanager_errorcode) | ResourceManager_ErrorCode | Enumerates the resource management error codes. |
| [ResourceManager_Direction](#resourcemanager_direction) | ResourceManager_Direction | Enumerates screen orientations.|
| [ResourceManager_ColorMode](#resourcemanager_colormode) | ResourceManager_ColorMode | Enumerates color modes.|
| [ResourceManager_DeviceType](#resourcemanager_devicetype) | ResourceManager_DeviceType | Enumerates device types.|
| [ScreenDensity](#screendensity) | ScreenDensity | Enumerates the screen density types. |

## Enum Description

### ResourceManager_ErrorCode

```c
enum ResourceManager_ErrorCode
```

**Description**

Enumerates resource manager error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| SUCCESS = 0 | Operation successful.|
| ERROR_CODE_INVALID_INPUT_PARAMETER = 401 | Invalid input parameter.|
| ERROR_CODE_RES_ID_NOT_FOUND = 9001001 | Invalid resource ID.|
| ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002 | No matching resource is found based on the resource ID. |
| ERROR_CODE_RES_NAME_NOT_FOUND = 9001003 | Invalid resource name. |
| ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004 | No matching resource is found based on the resource name. |
| ERROR_CODE_RES_PATH_INVALID = 9001005 | Invalid relative path.|
| ERROR_CODE_RES_REF_TOO_MUCH = 9001006 | The resource has a circular reference. |
| ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007 | Failed to format the resource obtained based on the resource ID. |
| ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008 | Failed to format the resource obtained based on the resource name. |
| ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009 | Failed to access system resources.|
| ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010 | Invalid overlay path.|
| ERROR_CODE_OUT_OF_MEMORY = 9001100 | A memory overflow occurs.|

### ResourceManager_Direction

```c
enum ResourceManager_Direction
```

**Description**

Enumerates screen orientations.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| DIRECTION_VERTICAL = 0 | Portrait. |
| DIRECTION_HORIZONTAL = 1 | Landscape. |

### ResourceManager_ColorMode

```c
enum ResourceManager_ColorMode
```

**Description**

Enumerates color modes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| COLOR_MODE_DARK = 0 | Dark mode.|
| COLOR_MODE_LIGHT = 1 | Light mode.|

### ResourceManager_DeviceType

```c
enum ResourceManager_DeviceType
```

**Description**

Enumerates device types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| DEVICE_TYPE_PHONE = 0X00 | Smartphone|
| DEVICE_TYPE_TABLET = 0x01 | Tablet|
| DEVICE_TYPE_CAR = 0x02 | Head unit |
| DEVICE_TYPE_PC = 0x03 | PC device |
| DEVICE_TYPE_TV = 0x04 | Smart TV |
| DEVICE_TYPE_WEARABLE = 0x06 | Wearable|
| DEVICE_TYPE_2IN1 = 0x07 | 2-in-1 device|

### ScreenDensity

```c
enum ScreenDensity
```

**Description**

Enumerates the screen density types.

**Since**: 12

| Enum | Description |
| -- | -- |
| SCREEN_SDPI = 120 | Small screen density. |
| SCREEN_MDPI = 160 | Medium screen density. |
| SCREEN_LDPI = 240 | Large screen density. |
| SCREEN_XLDPI = 320 | Extra-large screen density. |
| SCREEN_XXLDPI = 480 | Extra-extra-large screen density. |
| SCREEN_XXXLDPI = 640 | Extra-extra-extra-large screen density. |


