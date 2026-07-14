# NativeDisplayManager_DisplayInfo

```c
typedef struct NativeDisplayManager_DisplayInfo {...} NativeDisplayManager_DisplayInfo
```

## 概述

The struct describes the information about a display.

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t id | ID of the display. The value must be a non-negative integer. |
| char name[OH_DISPLAY_NAME_LENGTH + 1] | display name |
| bool isAlive | Whether the display is active. **true** if active, **false** otherwise. |
| int32_t width | Width of the display, in px. The value must be a non-negative integer. |
| int32_t height | Height of the display, in px. The value must be a non-negative integer. |
| int32_t physicalWidth | Physical width of the display, in px. The value must be a non-negative integer. |
| int32_t physicalHeight | Physical height of the display, in px. The value must be a non-negative integer. |
| uint32_t refreshRate | Refresh rate of the display, in Hz. The value must be a non-negative integer. |
| uint32_t availableWidth | Width of the available area, in px. The value must be a non-negative integer.This API can be properly called on devices running OpenHarmony 7.0.0 or later.For devices running versions earlier than OpenHarmony 7.0.0,this API can be properly called on PCs/2-in-1 devices and tablets,but does not work for other device types.To obtain the width of the available area on the current device screen, you can use the width attribute. |
| uint32_t availableHeight | Height of the available area, in px. The value must be a non-negative integer.This API can be properly called on devices running OpenHarmony 7.0.0 or later.For devices running versions earlier than OpenHarmony 7.0.0,this API can be properly called on PCs/2-in-1 devices and tablets,but does not work for other device types.To obtain the height of the available area on the current device screen, you can use the height attribute. |
| float densityDPI | Physical pixel density of the display, that is, the number of pixels per inch. The value must be a floating-point number greater than 0. The unit is px. Generally, the value is **160.0** or **480.0**. The actual valuedepends on the optional values provided by the device in use. |
| float densityPixels | Logical pixel density of the display, which is the scaling coefficient between physical pixels and logicalpixels. The value is a floating-point number greater than 0 and is restricted by the range of **densityDPI**.The value range is [0.5, 4.0]. Generally, the value is **1.0** or **3.0**. The actual value depends on thedensity DPI provided by the device in use. |
| float scaledDensity | Scaling factor for fonts displayed on the display. The value must be a floating-point number greater than 0.Generally, the value is the same as that of **densityPixels**. |
| float xDPI | Exact physical pixels per inch of the display in the X dimension. The value must be a floating-point numbergreater than 0. |
| float yDPI | Exact physical pixels per inch of the display in the Y dimension. The value must be a floating-point numbergreater than 0. |
| [NativeDisplayManager_Rotation](capi-oh-display-info-h.md#nativedisplaymanager_rotation) rotation | Clockwise rotation angle of the display. |
| [NativeDisplayManager_DisplayState](capi-oh-display-info-h.md#nativedisplaymanager_displaystate) state | State of the display. |
| [NativeDisplayManager_Orientation](capi-oh-display-info-h.md#nativedisplaymanager_orientation) orientation | Orientation of the display. |
| [NativeDisplayManager_DisplayHdrFormat](capi-oh-displaymanager-nativedisplaymanager-displayhdrformat.md) *hdrFormat | All the HDR formats supported by the display. |
| [NativeDisplayManager_DisplayColorSpace](capi-oh-displaymanager-nativedisplaymanager-displaycolorspace.md) *colorSpace | All the color spaces supported by the display. |


