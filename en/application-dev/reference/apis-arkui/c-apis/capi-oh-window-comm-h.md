# oh_window_comm.h

## Overview

The file declares the common enums and definitions of the window manager.

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [WindowManager_Rect](capi-windowmanager-windowmanager-rect.md) | WindowManager_Rect | The struct describes the window rectangle, including the window position, width, and height. |
| [WindowManager_WindowSnapshotConfig](capi-windowmanager-windowmanager-windowsnapshotconfig.md) | WindowManager_WindowSnapshotConfig | Describes the configuration of the main window screenshot. |
| [WindowManager_MainWindowInfo](capi-windowmanager-windowmanager-mainwindowinfo.md) | WindowManager_MainWindowInfo | The struct describes the main window information. |
| [WindowManager_WindowProperties](capi-windowmanager-windowmanager-windowproperties.md) | WindowManager_WindowProperties | The struct describes the window properties. |
| [WindowManager_AvoidArea](capi-windowmanager-windowmanager-avoidarea.md) | WindowManager_AvoidArea | The struct describes the avoid area. |
| [struct](capi-windowmanager-struct.md) | OH_PixelmapNative | Describes the pixel image information. |
| [OH_WindowManager_FrameMetrics](capi-windowmanager-oh-windowmanager-framemetrics.md) | OH_WindowManager_FrameMetrics | Defines a frame metric data object. |
| [OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md) | OH_WindowManager_DensityInfo | Window density information, including the system display size scaling factor, system default display size scaling factor, and custom display size scaling factor of the screen where the window is located. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [WindowManager_ErrorCode](#windowmanager_errorcode) | WindowManager_ErrorCode | Enumerates the status codes returned by the window manager interface. |
| [WindowManager_AvoidAreaType](#windowmanager_avoidareatype) | WindowManager_AvoidAreaType | Enumerates the avoid area types. |
| [WindowManager_WindowType](#windowmanager_windowtype) | WindowManager_WindowType | Enumerates the window types. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_WindowManager_FrameMetricsMeasuredCallback)(int32_t windowId, const OH_WindowManager_FrameMetrics* metrics)](#oh_windowmanager_framemetricsmeasuredcallback) | OH_WindowManager_FrameMetricsMeasuredCallback | Frame metrics callback type. |
| [typedef void (\*OH_WindowManager_DensityInfoCallback)(int32_t windowId, const OH_WindowManager_DensityInfo* info)](#oh_windowmanager_densityinfocallback) | OH_WindowManager_DensityInfoCallback | Density info callback type. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_WindowManager_FrameMetricsMeasuredCallback)( int32_t windowId, const OH_WindowManager_FrameMetrics* metrics) | Frame metrics callback type.<br>**Since**: 26.0.0 |
| void (*OH_WindowManager_DensityInfoCallback)(int32_t windowId, const OH_WindowManager_DensityInfo* info) | Density info callback type.<br>**Since**: 24 |

## Enum type description

### WindowManager_ErrorCode

```c
enum WindowManager_ErrorCode
```

**Description**

Enumerates the status codes returned by the window manager interface.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

| Enum item | Description |
| -- | -- |
| OK = 0 | Successful. |
| WINDOW_MANAGER_ERRORCODE_NO_PERMISSION = 201 |  |
| WINDOW_MANAGER_ERRORCODE_INVALID_PARAM = 401 |  |
| WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED = 801 |  |
| INVAILD_WINDOW_ID = 1000 | Invalid window ID. |
| INVALID_WINDOW_ID = INVAILD_WINDOW_ID |  |
| SERVICE_ERROR = 2000 | Service error. |
| WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL = 1300002 |  |
| WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL = 1300003 |  |
| WINDOW_MANAGER_ERRORCODE_PIP_DESTROY_FAILED = 1300011 |  |
| WINDOW_MANAGER_ERRORCODE_PIP_STATE_ABNORMAL = 1300012 |  |
| WINDOW_MANAGER_ERRORCODE_PIP_CREATE_FAILED = 1300013 |  |
| WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR = 1300014 |  |
| WINDOW_MANAGER_ERRORCODE_PIP_REPEATED_OPERATION = 1300015 |  |
| WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM = 1300016 |  |

### WindowManager_AvoidAreaType

```c
enum WindowManager_AvoidAreaType
```

**Description**

Enumerates the avoid area types.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 15

| Enum item | Description |
| -- | -- |
| WINDOW_MANAGER_AVOID_AREA_TYPE_SYSTEM = 0 | System avoid area. |
| WINDOW_MANAGER_AVOID_AREA_TYPE_CUTOUT = 1 | Cutout area. |
| WINDOW_MANAGER_AVOID_AREA_TYPE_SYSTEM_GESTURE = 2 | System gesture area. |
| WINDOW_MANAGER_AVOID_AREA_TYPE_KEYBOARD = 3 | Keyboard area. |
| WINDOW_MANAGER_AVOID_AREA_TYPE_NAVIGATION_INDICATOR = 4 | Navigation bar area. |

### WindowManager_WindowType

```c
enum WindowManager_WindowType
```

**Description**

Enumerates the window types.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 15

| Enum item | Description |
| -- | -- |
| WINDOW_MANAGER_WINDOW_TYPE_APP = 0 |  |
| WINDOW_MANAGER_WINDOW_TYPE_MAIN = 1 |  |
| WINDOW_MANAGER_WINDOW_TYPE_FLOAT = 8 |  |
| WINDOW_MANAGER_WINDOW_TYPE_DIALOG = 16 |  |


## Function description

### OH_WindowManager_FrameMetricsMeasuredCallback()

```c
typedef void (*OH_WindowManager_FrameMetricsMeasuredCallback)(int32_t windowId, const OH_WindowManager_FrameMetrics* metrics)
```

**Description**

Frame metrics callback type.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 26.0.0

### OH_WindowManager_DensityInfoCallback()

```c
typedef void (*OH_WindowManager_DensityInfoCallback)(int32_t windowId, const OH_WindowManager_DensityInfo* info)
```

**Description**

Density info callback type.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 24


