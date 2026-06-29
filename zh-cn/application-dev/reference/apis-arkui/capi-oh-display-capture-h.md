# oh_display_capture.h
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

提供屏幕截屏的能力。

**引用文件：** <window_manager/oh_display_capture.h>

**库：** libnative_display_manager.so

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)](#oh_nativedisplaymanager_capturescreenpixelmap) |获取屏幕全屏截图，可通过设置不同的屏幕ID截取指定屏幕。 |

## 函数说明

### OH_NativeDisplayManager_CaptureScreenPixelmap()

```c
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CaptureScreenPixelmap(uint32_t displayId, OH_PixelmapNative **pixelMap)
```

**描述**

获取屏幕全屏截图，可通过设置不同的屏幕ID截取指定屏幕。

**需要权限：**
- API版本22+：ohos.permission.CUSTOM_SCREEN_CAPTURE或ohos.permission.CUSTOM_SCREEN_RECORDING
- API版本14-21：ohos.permission.CUSTOM_SCREEN_CAPTURE

**起始版本：** 14

**设备行为差异：** 在API version 21之前，该接口在PC/2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。从API version 21开始，该接口在Phone设备、PC/2in1设备、Tablet设备中可正常调用，在其他设备中返回801错误码。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t displayId | 需要截屏的屏幕ID，该值为非负整数。 |
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) **pixelMap | 创建指定屏幕ID的OH_PixelmapNative对象，此处作为出参返回。使用完成需要调用[OH_PixelmapNative_Release](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release)手动释放OH_PixelmapNative对象资源。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回DISPLAY_MANAGER_OK，表示操作成功。<br>返回DISPLAY_MANAGER_ERROR_NO_PERMISSION，表示权限校验失败，应用无权限使用该API，需要申请权限。<br>返回DISPLAY_MANAGER_ERROR_INVALID_PARAM，表示参数检查失败。<br>返回DISPLAY_MANAGER_ERROR_DEVICE_NOT_SUPPORTED，表示该设备不支持此API。<br>返回DISPLAY_MANAGER_ERROR_SYSTEM_ABNORMAL，表示系统服务工作异常。 |


