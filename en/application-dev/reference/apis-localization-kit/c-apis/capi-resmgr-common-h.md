# resmgr_common.h

## Overview

Provides the enumeration and structure definitions required by the `resourcemanager` module. <br>This header file defines enumerations such as error codes, screen orientations, color modes, device types, and screen densities, as well as the device configuration structure, providing data type support for the resource retrieval functions in `ohresmgr.h`.

**Library**: libohresmgr.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

**Related module**: [resourcemanager](capi-localization-kit-resourcemanager.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ResourceManager_Configuration](capi-resourcemanager-resourcemanager-configuration.md) | ResourceManager_Configuration | Structure of the device status. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ResourceManager_ErrorCode](#resourcemanager_errorcode) | ResourceManager_ErrorCode | Enumerates resource manager error codes. |
| [ResourceManager_Direction](#resourcemanager_direction) | ResourceManager_Direction | Enumerates screen orientations. |
| [ResourceManager_ColorMode](#resourcemanager_colormode) | ResourceManager_ColorMode | Enumerates color modes. |
| [ResourceManager_DeviceType](#resourcemanager_devicetype) | ResourceManager_DeviceType | Enumerates device types. |
| [ScreenDensity](#screendensity) | ScreenDensity | Enumerates the screen density types. |

### Macros

| Name | Description |
| -- | -- |
| GLOBAL_RESMGR_COMMON_H | Provides the enumeration and structure definitions required by the `resourcemanager` module. <br>This header file defines enumerations such as error codes, screen orientations, color modes, device types, and screen densities, as well as the device configuration structure, providing data type support for the resource retrieval functions in `ohresmgr.h`.<br>**Since**: 12<br>**System capability**: SystemCapability.Global.ResourceManager |

## Enum type description

### ResourceManager_ErrorCode

```c
enum ResourceManager_ErrorCode
```

**Description**

Enumerates resource manager error codes.

<!--Device-enum ResourceManager_ErrorCode--><!--Device-enum ResourceManager_ErrorCode-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| SUCCESS = 0 | Operation successful.<br><!--Device-SUCCESS = 0--><!--Device-SUCCESS = 0-End--> |
| ERROR_CODE_INVALID_INPUT_PARAMETER = 401 | Invalid input parameter.<br><!--Device-ERROR_CODE_INVALID_INPUT_PARAMETER = 401--><!--Device-ERROR_CODE_INVALID_INPUT_PARAMETER = 401-End--> |
| ERROR_CODE_RES_ID_NOT_FOUND = 9001001 | Invalid resource ID.<br><!--Device-ERROR_CODE_RES_ID_NOT_FOUND = 9001001--><!--Device-ERROR_CODE_RES_ID_NOT_FOUND = 9001001-End--> |
| ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002 | No matching resource found based on the resource ID.<br><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002--><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_ID = 9001002-End--> |
| ERROR_CODE_RES_NAME_NOT_FOUND = 9001003 | Invalid resource name.<br><!--Device-ERROR_CODE_RES_NAME_NOT_FOUND = 9001003--><!--Device-ERROR_CODE_RES_NAME_NOT_FOUND = 9001003-End--> |
| ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004 | No matching resource found based on the resource name.<br><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004--><!--Device-ERROR_CODE_RES_NOT_FOUND_BY_NAME = 9001004-End--> |
| ERROR_CODE_RES_PATH_INVALID = 9001005 | Invalid relative path.<br><!--Device-ERROR_CODE_RES_PATH_INVALID = 9001005--><!--Device-ERROR_CODE_RES_PATH_INVALID = 9001005-End--> |
| ERROR_CODE_RES_REF_TOO_MUCH = 9001006 | Circular reference exists in the resource.<br><!--Device-ERROR_CODE_RES_REF_TOO_MUCH = 9001006--><!--Device-ERROR_CODE_RES_REF_TOO_MUCH = 9001006-End--> |
| ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007 | Failed to format the resource obtained based on the resource ID.<br><!--Device-ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007--><!--Device-ERROR_CODE_RES_ID_FORMAT_ERROR = 9001007-End--> |
| ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008 | Failed to format the resource obtained based on the resource name.<br><!--Device-ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008--><!--Device-ERROR_CODE_RES_NAME_FORMAT_ERROR = 9001008-End--> |
| ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009 | Failed to access system resources.<br><!--Device-ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009--><!--Device-ERROR_CODE_SYSTEM_RES_MANAGER_GET_FAILED = 9001009-End--> |
| ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010 | Invalid overlay path.<br><!--Device-ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010--><!--Device-ERROR_CODE_OVERLAY_RES_PATH_INVALID = 9001010-End--> |
| ERROR_CODE_OUT_OF_MEMORY = 9001100 | A memory overflow occurs.<br><!--Device-ERROR_CODE_OUT_OF_MEMORY = 9001100--><!--Device-ERROR_CODE_OUT_OF_MEMORY = 9001100-End--> |

### ResourceManager_Direction

```c
enum ResourceManager_Direction
```

**Description**

Enumerates screen orientations.

<!--Device-enum ResourceManager_Direction--><!--Device-enum ResourceManager_Direction-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| DIRECTION_VERTICAL = 0 | Portrait orientation.<br><!--Device-DIRECTION_VERTICAL = 0--><!--Device-DIRECTION_VERTICAL = 0-End--> |
| DIRECTION_HORIZONTAL = 1 | Landscape orientation.<br><!--Device-DIRECTION_HORIZONTAL = 1--><!--Device-DIRECTION_HORIZONTAL = 1-End--> |

### ResourceManager_ColorMode

```c
enum ResourceManager_ColorMode
```

**Description**

Enumerates color modes.

<!--Device-enum ResourceManager_ColorMode--><!--Device-enum ResourceManager_ColorMode-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| COLOR_MODE_DARK = 0 | Dark mode.<br><!--Device-COLOR_MODE_DARK = 0--><!--Device-COLOR_MODE_DARK = 0-End--> |
| COLOR_MODE_LIGHT = 1 | Light mode.<br><!--Device-COLOR_MODE_LIGHT = 1--><!--Device-COLOR_MODE_LIGHT = 1-End--> |

### ResourceManager_DeviceType

```c
enum ResourceManager_DeviceType
```

**Description**

Enumerates device types.

<!--Device-enum ResourceManager_DeviceType--><!--Device-enum ResourceManager_DeviceType-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| DEVICE_TYPE_PHONE = 0X00 | Smartphone.<br><!--Device-DEVICE_TYPE_PHONE = 0X00--><!--Device-DEVICE_TYPE_PHONE = 0X00-End--> |
| DEVICE_TYPE_TABLET = 0x01 | Tablet.<br><!--Device-DEVICE_TYPE_TABLET = 0x01--><!--Device-DEVICE_TYPE_TABLET = 0x01-End--> |
| DEVICE_TYPE_CAR = 0x02 | Car head unit.<br><!--Device-DEVICE_TYPE_CAR = 0x02--><!--Device-DEVICE_TYPE_CAR = 0x02-End--> |
| DEVICE_TYPE_PC = 0x03 | PC.<br><!--Device-DEVICE_TYPE_PC = 0x03--><!--Device-DEVICE_TYPE_PC = 0x03-End--> |
| DEVICE_TYPE_TV = 0x04 | Smart screen.<br><!--Device-DEVICE_TYPE_TV = 0x04--><!--Device-DEVICE_TYPE_TV = 0x04-End--> |
| DEVICE_TYPE_WEARABLE = 0x06 | Wearable.<br><!--Device-DEVICE_TYPE_WEARABLE = 0x06--><!--Device-DEVICE_TYPE_WEARABLE = 0x06-End--> |
| DEVICE_TYPE_2IN1 = 0x07 | 2-in-1 device.<br><!--Device-DEVICE_TYPE_2IN1 = 0x07--><!--Device-DEVICE_TYPE_2IN1 = 0x07-End--> |

### ScreenDensity

```c
enum ScreenDensity
```

**Description**

Enumerates the screen density types.

<!--Device-enum ScreenDensity--><!--Device-enum ScreenDensity-End-->

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| SCREEN_SDPI = 120 | Screen density with small-scale dots per inch (SDPI).<br><!--Device-SCREEN_SDPI = 120--><!--Device-SCREEN_SDPI = 120-End--> |
| SCREEN_MDPI = 160 | Screen density with medium-scale dots per inch (MDPI).<br><!--Device-SCREEN_MDPI = 160--><!--Device-SCREEN_MDPI = 160-End--> |
| SCREEN_LDPI = 240 | Screen density with large-scale dots per inch (LDPI).<br><!--Device-SCREEN_LDPI = 240--><!--Device-SCREEN_LDPI = 240-End--> |
| SCREEN_XLDPI = 320 | Screen density with extra-large-scale dots per inch (XLDPI).<br><!--Device-SCREEN_XLDPI = 320--><!--Device-SCREEN_XLDPI = 320-End--> |
| SCREEN_XXLDPI = 480 | Screen density with extra-extra-large-scale dots per inch (XXLDPI).<br><!--Device-SCREEN_XXLDPI = 480--><!--Device-SCREEN_XXLDPI = 480-End--> |
| SCREEN_XXXLDPI = 640 | Screen density with extra-extra-extra-large-scale dots per inch (XXXLDPI).<br><!--Device-SCREEN_XXXLDPI = 640--><!--Device-SCREEN_XXXLDPI = 640-End--> |


