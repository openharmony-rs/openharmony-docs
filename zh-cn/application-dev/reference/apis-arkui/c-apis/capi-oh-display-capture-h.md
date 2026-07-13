# oh_display_capture.h

## 概述

The file declares the capability to take screenshots.

**库：** libnative_display_manager.so

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)](#oh_nativedisplaymanager_capturescreenpixelmap) | 获取屏幕全屏截图，可以通过设置不同的屏幕id号截取不同屏幕的截图。 |

## 函数说明

### OH_NativeDisplayManager_CaptureScreenPixelmap()

```c
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)
```

**描述**

获取屏幕全屏截图，可以通过设置不同的屏幕id号截取不同屏幕的截图。

**需要权限：** ohos.permission.CUSTOM_SCREEN_CAPTURE [since 14]

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t displayId | 需要截屏的屏幕id号，该值为非负整数。 |
| OH_PixelmapNative **pixelMap | 创建指定屏幕id的OH_PixelmapNative对象，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回DISPLAY_MANAGER_OK，表示操作成功。<br> 返回DISPLAY_MANAGER_ERROR_NO_PERMISSION，表示权限校验失败，应用无权限使用该API，需要申请权限。<br> 返回DISPLAY_MANAGER_ERROR_INVALID_PARAM，表示参数检查失败。<br> 返回DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED，表示该设备不支持此API。<br> 返回DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL，表示系统服务工作异常。 |


