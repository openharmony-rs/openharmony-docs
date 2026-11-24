# NativeDisplayManager_DisplayInfo

```c
typedef struct NativeDisplayManager_DisplayInfo {...} NativeDisplayManager_DisplayInfo
```

## Overview

The struct describes the information about a display.

<!--Device-typedef struct NativeDisplayManager_DisplayInfo {...} NativeDisplayManager_DisplayInfo--><!--Device-typedef struct NativeDisplayManager_DisplayInfo {...} NativeDisplayManager_DisplayInfo-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 14

**Related module**: [OH_DisplayManager](capi-arkui-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t id | ID of the display. The value is a non-negative integer.<br><!--Device-uint32_t id--><!--Device-uint32_t id-End--> |
| char name[OH_DISPLAY_NAME_LENGTH + 1] | display name<br><!--Device-char name[OH_DISPLAY_NAME_LENGTH + 1]--><!--Device-char name[OH_DISPLAY_NAME_LENGTH + 1]-End--> |
| bool isAlive | Whether the display is active. **true** if active, **false** otherwise.<br><!--Device-bool isAlive--><!--Device-bool isAlive-End--> |
| int32_t width | Width of the display, in px. The value is a non-negative integer.<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t height | Height of the display, in px. The value is a non-negative integer.<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |
| int32_t physicalWidth | Physical width of the display, in px. The value is a non-negative integer.<br><!--Device-int32_t physicalWidth--><!--Device-int32_t physicalWidth-End--> |
| int32_t physicalHeight | Physical height of the display, in px. The value is a non-negative integer.<br><!--Device-int32_t physicalHeight--><!--Device-int32_t physicalHeight-End--> |
| uint32_t refreshRate | Refresh rate of the display, in Hz. The value is a non-negative integer.<br><!--Device-uint32_t refreshRate--><!--Device-uint32_t refreshRate-End--> |
| uint32_t availableWidth | Width of the available area on the screen of the display, in px. The value is a non-negative integer. * This API can be properly called on devices running OpenHarmony 7.0.0 or later. For devices running versions earlier than OpenHarmony 7.0.0, this API can be properly called on PCs/2-in-1 devices and tablets, but does not work for other device types. To obtain the width of the available area on the current device screen, you can use the width attribute.<br><!--Device-uint32_t availableWidth--><!--Device-uint32_t availableWidth-End--> |
| uint32_t availableHeight | Height of the available area on the screen of the display, in px. The value is a non-negative integer. * This API can be properly called on devices running OpenHarmony 7.0.0 or later. For devices running versions earlier than OpenHarmony 7.0.0, this API can be properly called on PCs/2-in-1 devices and tablets, but does not work for other device types. To obtain the height of the available area on the current device screen, you can use the height attribute.<br><!--Device-uint32_t availableHeight--><!--Device-uint32_t availableHeight-End--> |
| float densityDPI | Physical pixel density of the display, that is, the number of pixels per inch. The value must be a floating- point number greater than 0. The unit is px. Generally, the value is **160.0** or **480.0**. The actual value depends on the optional values provided by the device in use.<br><!--Device-float densityDPI--><!--Device-float densityDPI-End--> |
| float densityPixels | Logical pixel density of the display, which is the scaling coefficient between physical pixels and logical pixels. The value is a floating-point number greater than 0 and is restricted by the range of **densityDPI**. The value range is [0.5, 4.0]. Generally, the value is **1.0** or **3.0**. The actual value depends on the density DPI provided by the device in use.<br><!--Device-float densityPixels--><!--Device-float densityPixels-End--> |
| float scaledDensity | Scaling factor for fonts displayed on the display. The value must be a floating-point number greater than 0. Generally, the value is the same as that of **densityPixels**.<br><!--Device-float scaledDensity--><!--Device-float scaledDensity-End--> |
| float xDPI | Exact physical pixels per inch of the display in the X dimension. The value must be a floating-point number greater than 0.<br><!--Device-float xDPI--><!--Device-float xDPI-End--> |
| float yDPI | Exact physical pixels per inch of the display in the Y dimension. The value must be a floating-point number greater than 0.<br><!--Device-float yDPI--><!--Device-float yDPI-End--> |
| [NativeDisplayManager_Rotation](capi-oh-display-info-h.md#nativedisplaymanager_rotation) rotation | Clockwise rotation angle of the display.<br><!--Device-NativeDisplayManager_Rotation rotation--><!--Device-NativeDisplayManager_Rotation rotation-End--> |
| [NativeDisplayManager_DisplayState](capi-oh-display-info-h.md#nativedisplaymanager_displaystate) state | State of the display.<br><!--Device-NativeDisplayManager_DisplayState state--><!--Device-NativeDisplayManager_DisplayState state-End--> |
| [NativeDisplayManager_Orientation](capi-oh-display-info-h.md#nativedisplaymanager_orientation) orientation | Orientation of the display.<br><!--Device-NativeDisplayManager_Orientation orientation--><!--Device-NativeDisplayManager_Orientation orientation-End--> |
| [NativeDisplayManager_DisplayHdrFormat](capi-oh-displaymanager-nativedisplaymanager-displayhdrformat.md) *hdrFormat | All the HDR formats supported by the display.<br><!--Device-NativeDisplayManager_DisplayHdrFormat *hdrFormat--><!--Device-NativeDisplayManager_DisplayHdrFormat *hdrFormat-End--> |
| [NativeDisplayManager_DisplayColorSpace](capi-oh-displaymanager-nativedisplaymanager-displaycolorspace.md) *colorSpace | All the color spaces supported by the display.<br><!--Device-NativeDisplayManager_DisplayColorSpace *colorSpace--><!--Device-NativeDisplayManager_DisplayColorSpace *colorSpace-End--> |


