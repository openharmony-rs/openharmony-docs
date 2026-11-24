# oh_display_info.h

## Overview

The file declares the common enums and definitions of the display.

**Library**: libnative_display_manager.so

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

**Related module**: [OH_DisplayManager](capi-arkui-oh-displaymanager.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NativeDisplayManager_Rect](capi-oh-displaymanager-nativedisplaymanager-rect.md) | NativeDisplayManager_Rect | The struct describes a rectangle. |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-oh-displaymanager-nativedisplaymanager-waterfalldisplayarearects.md) | NativeDisplayManager_WaterfallDisplayAreaRects | The struct describes the curved area on a waterfall display. |
| [NativeDisplayManager_CutoutInfo](capi-oh-displaymanager-nativedisplaymanager-cutoutinfo.md) | NativeDisplayManager_CutoutInfo | The struct describes the unusable area of a display, including punch hole, notch, and curved area of a waterfall display. |
| [NativeDisplayManager_DisplayHdrFormat](capi-oh-displaymanager-nativedisplaymanager-displayhdrformat.md) | NativeDisplayManager_DisplayHdrFormat | The struct describes all the HDR formats supported by a display. |
| [NativeDisplayManager_DisplayColorSpace](capi-oh-displaymanager-nativedisplaymanager-displaycolorspace.md) | NativeDisplayManager_DisplayColorSpace | The struct describes all the color spaces supported by a display. |
| [NativeDisplayManager_DisplayInfo](capi-oh-displaymanager-nativedisplaymanager-displayinfo.md) | NativeDisplayManager_DisplayInfo | The struct describes the information about a display. |
| [NativeDisplayManager_DisplaysInfo](capi-oh-displaymanager-nativedisplaymanager-displaysinfo.md) | NativeDisplayManager_DisplaysInfo | The struct describes the information about displays of a device with multiple screens. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NativeDisplayManager_Rotation](#nativedisplaymanager_rotation) | NativeDisplayManager_Rotation | Enumerates the clockwise rotation angles of a display. |
| [NativeDisplayManager_Orientation](#nativedisplaymanager_orientation) | NativeDisplayManager_Orientation | Enumerates the orientations of a display. |
| [NativeDisplayManager_ErrorCode](#nativedisplaymanager_errorcode) | NativeDisplayManager_ErrorCode | Enumerates the status codes returned by the display manager interface. |
| [NativeDisplayManager_FoldDisplayMode](#nativedisplaymanager_folddisplaymode) | NativeDisplayManager_FoldDisplayMode | Enumerates the display modes of a foldable device. |
| [NativeDisplayManager_DisplayState](#nativedisplaymanager_displaystate) | NativeDisplayManager_DisplayState | Enumerates the states of a display. |
| [NativeDisplayManager_SourceMode](#nativedisplaymanager_sourcemode) | NativeDisplayManager_SourceMode | Enumerates the source modes of a device. |

### Macros

| Name | Description |
| -- | -- |
| OH_DISPLAY_NAME_LENGTH 32 | Maximum length of a display name.<br>**Since**: 14 |

## Enum type description

### NativeDisplayManager_Rotation

```c
enum NativeDisplayManager_Rotation
```

**Description**

Enumerates the clockwise rotation angles of a display.

<!--Device-enum NativeDisplayManager_Rotation--><!--Device-enum NativeDisplayManager_Rotation-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| DISPLAY_MANAGER_ROTATION_0 = 0 | The display is rotated clockwise by 0 degrees.<br><!--Device-DISPLAY_MANAGER_ROTATION_0 = 0--><!--Device-DISPLAY_MANAGER_ROTATION_0 = 0-End--> |
| DISPLAY_MANAGER_ROTATION_90 = 1 | The display is rotated clockwise by 90 degrees.<br><!--Device-DISPLAY_MANAGER_ROTATION_90 = 1--><!--Device-DISPLAY_MANAGER_ROTATION_90 = 1-End--> |
| DISPLAY_MANAGER_ROTATION_180 = 2 | The display is rotated clockwise by 180 degrees.<br><!--Device-DISPLAY_MANAGER_ROTATION_180 = 2--><!--Device-DISPLAY_MANAGER_ROTATION_180 = 2-End--> |
| DISPLAY_MANAGER_ROTATION_270 = 3 | The display is rotated clockwise by 270 degrees.<br><!--Device-DISPLAY_MANAGER_ROTATION_270 = 3--><!--Device-DISPLAY_MANAGER_ROTATION_270 = 3-End--> |

### NativeDisplayManager_Orientation

```c
enum NativeDisplayManager_Orientation
```

**Description**

Enumerates the orientations of a display.

<!--Device-enum NativeDisplayManager_Orientation--><!--Device-enum NativeDisplayManager_Orientation-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| DISPLAY_MANAGER_PORTRAIT = 0 | The display is in portrait mode.<br><!--Device-DISPLAY_MANAGER_PORTRAIT = 0--><!--Device-DISPLAY_MANAGER_PORTRAIT = 0-End--> |
| DISPLAY_MANAGER_LANDSCAPE = 1 | The display is in landscape mode.<br><!--Device-DISPLAY_MANAGER_LANDSCAPE = 1--><!--Device-DISPLAY_MANAGER_LANDSCAPE = 1-End--> |
| DISPLAY_MANAGER_PORTRAIT_INVERTED = 2 | The display is in reverse portrait mode.<br><!--Device-DISPLAY_MANAGER_PORTRAIT_INVERTED = 2--><!--Device-DISPLAY_MANAGER_PORTRAIT_INVERTED = 2-End--> |
| DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3 | The display is in reverse landscape mode.<br><!--Device-DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3--><!--Device-DISPLAY_MANAGER_LANDSCAPE_INVERTED = 3-End--> |
| DISPLAY_MANAGER_UNKNOWN | The screen orientation is unknown.<br><!--Device-DISPLAY_MANAGER_UNKNOWN--><!--Device-DISPLAY_MANAGER_UNKNOWN-End--> |

### NativeDisplayManager_ErrorCode

```c
enum NativeDisplayManager_ErrorCode
```

**Description**

Enumerates the status codes returned by the display manager interface.

<!--Device-enum NativeDisplayManager_ErrorCode--><!--Device-enum NativeDisplayManager_ErrorCode-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| DISPLAY_MANAGER_OK = 0 | Success.<br><!--Device-DISPLAY_MANAGER_OK = 0--><!--Device-DISPLAY_MANAGER_OK = 0-End--> |
| DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201 | Permission verification fails. The application does not have the permission to use the API.<br><!--Device-DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201--><!--Device-DISPLAY_MANAGER_ERROR_NO_PERMISSION = 201-End--> |
| DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202 | Permission verification fails. A non-system application attempts to call a system API.<br><!--Device-DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202--><!--Device-DISPLAY_MANAGER_ERROR_NOT_SYSTEM_APP = 202-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401 | Parameter check fails.<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_PARAM = 401-End--> |
| DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801 | The device does not support the API.<br><!--Device-DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801--><!--Device-DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED = 801-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001 | The display is invalid.<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_SCREEN = 1400001-End--> |
| DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002 | The current operation object does not have the operation permission.<br><!--Device-DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002--><!--Device-DISPLAY_MANAGER_ERROR_INVALID_CALL = 1400002-End--> |
| DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003 | The system service is abnormal.<br><!--Device-DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003--><!--Device-DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL = 1400003-End--> |
| DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004 | Invalid parameter.<br>**Since**: 20<br><!--Device-DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004--><!--Device-DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM = 1400004-End--> |

### NativeDisplayManager_FoldDisplayMode

```c
enum NativeDisplayManager_FoldDisplayMode
```

**Description**

Enumerates the display modes of a foldable device.

<!--Device-enum NativeDisplayManager_FoldDisplayMode--><!--Device-enum NativeDisplayManager_FoldDisplayMode-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0 | The display mode of the device is unknown.<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_UNKNOWN = 0-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1 | The device is displayed in full screen.<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_FULL = 1-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2 | The main screen of the device is displayed.<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_MAIN = 2-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3 | The subscreen of the device is displayed.<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_SUB = 3-End--> |
| DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4 | Both screens of the device are displayed in collaborative mode.<br><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4--><!--Device-DISPLAY_MANAGER_FOLD_DISPLAY_MODE_COORDINATION = 4-End--> |

### NativeDisplayManager_DisplayState

```c
enum NativeDisplayManager_DisplayState
```

**Description**

Enumerates the states of a display.

<!--Device-enum NativeDisplayManager_DisplayState--><!--Device-enum NativeDisplayManager_DisplayState-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 14

| Enum item | Description |
| -- | -- |
| DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0 | Unknown.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_UNKNOWN = 0-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1 | The display is shut down.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_OFF = 1-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_ON = 2 | The display is powered on.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON = 2--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON = 2-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3 | The display is in sleep mode.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE = 3-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4 | The display is in sleep mode, and the CPU is suspended.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_DOZE_SUSPEND = 4-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_VR = 5 | The display is in VR mode.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_VR = 5--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_VR = 5-End--> |
| DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6 | The display is powered on, and the CPU is suspended.<br><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6--><!--Device-DISPLAY_MANAGER_DISPLAY_STATE_ON_SUSPEND = 6-End--> |

### NativeDisplayManager_SourceMode

```c
enum NativeDisplayManager_SourceMode
```

**Description**

Enumerates the source modes of a device.

<!--Device-enum NativeDisplayManager_SourceMode--><!--Device-enum NativeDisplayManager_SourceMode-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| DISPLAY_SOURCE_MODE_NONE = 0 | The device is currently not in use.<br><!--Device-DISPLAY_SOURCE_MODE_NONE = 0--><!--Device-DISPLAY_SOURCE_MODE_NONE = 0-End--> |
| DISPLAY_SOURCE_MODE_MAIN = 1 | The primary screen of the device is currently in use.<br><!--Device-DISPLAY_SOURCE_MODE_MAIN = 1--><!--Device-DISPLAY_SOURCE_MODE_MAIN = 1-End--> |
| DISPLAY_SOURCE_MODE_MIRROR = 2 | The device is currently in mirror display mode.<br><!--Device-DISPLAY_SOURCE_MODE_MIRROR = 2--><!--Device-DISPLAY_SOURCE_MODE_MIRROR = 2-End--> |
| DISPLAY_SOURCE_MODE_EXTEND = 3 | The device is currently in extended display mode.<br><!--Device-DISPLAY_SOURCE_MODE_EXTEND = 3--><!--Device-DISPLAY_SOURCE_MODE_EXTEND = 3-End--> |
| DISPLAY_SOURCE_MODE_ALONE = 4 | The device is currently in independent display mode.<br><!--Device-DISPLAY_SOURCE_MODE_ALONE = 4--><!--Device-DISPLAY_SOURCE_MODE_ALONE = 4-End--> |


