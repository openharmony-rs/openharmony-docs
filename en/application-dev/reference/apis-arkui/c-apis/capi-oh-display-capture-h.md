# oh_display_capture.h

## Overview

The file declares the capability to take screenshots.

**Library**: libnative_display_manager.so

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)](#oh_nativedisplaymanager_capturescreenpixelmap) | Takes a screenshot of the entire screen. This function can be used to capture a full-screen screenshot on the specified display. |

## Function description

### OH_NativeDisplayManager_CaptureScreenPixelmap()

```c
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)
```

**Description**

Takes a screenshot of the entire screen. This function can be used to capture a full-screen screenshot on the specified display.

**Required permission**: ohos.permission.CUSTOM_SCREEN_CAPTURE [since 14]

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t displayId | ID of the display. The value must be a non-negative integer. |
| OH_PixelmapNative **pixelMap | Double pointer to an OH_PixelmapNative object, which is the screenshot taken. |

**Returns**:

| Type | Description |
| -- | -- |
| NativeDisplayManager_ErrorCode | <ul><li>{@link DISPLAY_MANAGER_OK} If the operation is successful.</li><br>    <li>{@link DISPLAY_MANAGER_ERROR_NO_PERMISSION} If no permission.</li><br>    <li>{@link DISPLAY_MANAGER_ERROR_INVALID_PARAM} If parameter error.</li><br>    <li>{@link DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED} If device not support.</li><br>    <li>{@link DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL} If display manager service works abnormally.</li></ul> |


