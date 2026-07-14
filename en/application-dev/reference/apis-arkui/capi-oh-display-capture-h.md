# oh_display_capture.h
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## Overview

The file declares the capability to take screenshots.

**File to include**: <window_manager/oh_display_capture.h>

**Library**: libnative_display_manager.so

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)](#oh_nativedisplaymanager_capturescreenpixelmap) |Takes a screenshot of the entire screen. This API can be used to capture a specified screen based on a display ID.|

## Function Description

### OH_NativeDisplayManager_CaptureScreenPixelmap()

```c
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)
```

**Description**

Takes a screenshot of the entire screen. This API can be used to capture a specified screen based on a display ID.

**Required permission**:
- API version 22+: **ohos.permission.CUSTOM_SCREEN_CAPTURE** or **ohos.permission.CUSTOM_SCREEN_RECORDING**
- API versions 14 to 21: **ohos.permission.CUSTOM_SCREEN_CAPTURE**

**Since**: 14

**Device behavior differences**: In versions earlier than API version 21, this API can be properly called on PC/2-in-1 devices and tablets. If it is called on other device types, error code 801 is returned. Since API version 21, this API can be properly called on phones, PCs/2-in-1 devices, and tablets. If it is called on other device types, error code 801 is returned.

**Parameters**

| Parameter| Description|
| -- | -- |
| uint32_t displayId | ID of the display whose screenshot is to be taken. The value is a non-negative integer.|
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) **pixelMap | Double pointer to an **OH_PixelmapNative** object associated with the specified display ID, which is the screenshot taken. After using the object, call [OH_PixelmapNative_Release](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release) to manually release its resources.|

**Return value**

| Type| Description|
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | **DISPLAY_MANAGER_OK**: The operation is successful.<br>**DISPLAY_MANAGER_ERROR_NO_PERMISSION**: The permission verification fails and the application does not have the permission to use the API. You need to apply for the permission.<br>**DISPLAY_MANAGER_ERROR_INVALID_PARAM**: The parameter check fails.<br>**DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED**: The device does not support this API.<br>**DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL**: The system service is abnormal.|
