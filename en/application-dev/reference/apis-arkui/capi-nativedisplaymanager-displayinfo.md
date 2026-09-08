# NativeDisplayManager_DisplayInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @logn; @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=2c124bd0b2ec980b0ce8b960a5620bdca08e9d12 translatedAt=2026-08-27T08:38:08.307Z pushedAt=2026-08-27T12:03:00.040Z -->

```c
typedef struct {...} NativeDisplayManager_DisplayInfo
```

## Overview

Describes the information about a display.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t id | Screen ID of the display, which is a non-negative integer.|
| char name[[OH_DISPLAY_NAME_LENGTH](capi-oh-display-info-h.md#macros) + 1]| Name of the display.|
| bool isAlive | Whether the display is alive. **true** if alive, **false** otherwise.|
| int32_t width | Screen width of the display, in px. The value is a non-negative integer.|
| int32_t height | Screen height of the display, in px. The value is a non-negative integer.|
| int32_t physicalWidth | Physical width of the display, in px. The value is a non-negative integer.|
| int32_t physicalHeight | Physical height of the display, in px. The value is a non-negative integer.|
| uint32_t refreshRate | Refresh rate of the display, in Hz. The value is a non-negative integer.|
| uint32_t availableWidth | Width of the available area of the screen in the display, in px. The value is a non-negative integer.<br> **Device behavior difference:**<br>On devices running OpenHarmony 7.0.0 or later, this API can be called normally.<br>For devices running versions earlier than OpenHarmony 7.0.0, this API can be called normally on PC/2-in-1 devices and tablets, and is unavailable on other devices. Use the **width** attribute to obtain the width of the available area of the current screen. |
| uint32_t availableHeight | Height of the available area of the screen in the display, in px. The value is a non-negative integer.<br> **Device behavior difference:** <br>On devices running OpenHarmony 7.0.0 or later, this API can be called normally.<br>For devices running versions earlier than OpenHarmony 7.0.0, this API can be called normally on PC/2-in-1 devices and tablets, and is unavailable on other devices. Use the **height** attribute to obtain the height of the available area of the current screen. |
| float densityDPI | Physical pixel density of the screen in the display, indicating the number of pixels per inch. The value is a floating-point number greater than 0. Common values include 160.0 and 480.0. The actual value depends on the options provided in the settings of different devices. |
| float densityPixels | Logical pixel density of the display, indicating the scale factor between physical pixels and logical pixels. The value is a floating-point number greater than 0, limited by the **densityDPI** range. The value range is [0.5, 4.0]. Common values include 1.0 and 3.0. The actual value depends on the **densityDPI** provided by different devices. |
| float scaledDensity | Font scale factor of the display. The value is a floating-point number greater than 0, usually the same as the value of **densityPixels**. The value range is [0.5, 4.0]. |
| float xDPI | Exact physical pixel value per inch in the x direction of the screen in the display. The value is a floating-point number greater than 0. |
| float yDPI | Exact physical pixel value per inch in the y direction of the screen in the display. The value is a floating-point number greater than 0. |
| [NativeDisplayManager_Rotation](capi-oh-display-info-h.md#nativedisplaymanager_rotation) rotation | Clockwise rotation angle of the display.|
| [NativeDisplayManager_DisplayState](capi-oh-display-info-h.md#nativedisplaymanager_displaystate) state | State of the display.|
| [NativeDisplayManager_Orientation](capi-oh-display-info-h.md#nativedisplaymanager_orientation) orientation | Orientation of the display.|
| [NativeDisplayManager_DisplayHdrFormat](capi-nativedisplaymanager-displayhdrformat.md)* hdrFormat | All the HDR formats supported by the display.|
| [NativeDisplayManager_DisplayColorSpace](capi-nativedisplaymanager-displaycolorspace.md)* colorSpace | All the color spaces supported by the display.|


