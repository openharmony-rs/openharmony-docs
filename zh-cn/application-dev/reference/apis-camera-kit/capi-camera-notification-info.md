# camera_notification_info.h
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明相机通知信息。

**引用文件：** <ohcamera/camera_notification_info.h>

**库：** libohcamera.so

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 26.0.0

**相关模块：** [OH_Camera](capi-oh-camera.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Camera_NotificationInfo](capi-oh-camera-oh-camera-notificationinfo.md) | OH_Camera_NotificationInfo | 通知信息扩展结构体。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Camera_ErrorCode OH_CameraNotificationInfo_GetNotificationName(const OH_Camera_NotificationInfo* notificationInfo, OH_Camera_NotificationName* name)](#oh_cameranotificationinfo_getnotificationname) | - | 从摄像头通知信息实例中获取通知名称。 |
| [Camera_ErrorCode OH_CameraNotificationInfo_GetProximityStateForFocus(const OH_Camera_NotificationInfo* notificationInfo, OH_Camera_ProximityStateForFocus* state)](#oh_cameranotificationinfo_getproximitystateforfocus) | - | 从相机通知信息实例中获取对焦物体与镜头是否过近的状态。 |
| [void OH_CameraNotificationInfo_Destroy(OH_Camera_NotificationInfo* notificationInfo)](#oh_cameranotificationinfo_destroy) | - | 销毁相机通知信息实例。 |

### OH_CameraNotificationInfo_GetNotificationName()

```c
Camera_ErrorCode OH_CameraNotificationInfo_GetNotificationName(const OH_Camera_NotificationInfo* notificationInfo, OH_Camera_NotificationName* name)
```

**描述**

从摄像头通知信息实例中获取通知名称。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const OH_Camera_NotificationInfo* notificationInfo | 指向OH_Camera_NotificationInfo实例的指针。 |
| [OH_Camera_NotificationName](capi-camera-h.md#oh_camera_notificationname)* name| 指向通知名称的指针，该名称是一个OH_Camera_NotificationName实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或参数类型错误。 |

### OH_CameraNotificationInfo_GetProximityStateForFocus()

```c
Camera_ErrorCode OH_CameraNotificationInfo_GetProximityStateForFocus(const OH_Camera_NotificationInfo* notificationInfo, OH_Camera_ProximityStateForFocus* state)
```

**描述**

从相机通知信息实例中获取对焦物体与镜头是否过近的状态。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const OH_Camera_NotificationInfo* notificationInfo | 指向OH_Camera_NotificationInfo实例的指针。 |
| [OH_Camera_ProximityStateForFocus](capi-camera-h.md#oh_camera_proximitystateforfocus)* state| 指向对焦距离状态的指针，该状态是一个OH_Camera_ProximityStateForFocus实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或参数类型错误。 |

### OH_CameraNotificationInfo_Destroy()

```c
void OH_CameraNotificationInfo_Destroy(OH_Camera_NotificationInfo* notificationInfo)
```

**描述**

销毁相机通知信息实例。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Camera_NotificationInfo* notificationInfo |指向待销毁的OH_Camera_NotificationInfo实例的指针。 |