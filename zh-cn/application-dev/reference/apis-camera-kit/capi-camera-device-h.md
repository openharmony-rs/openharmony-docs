# camera_device.h
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 概述

定义相机的基本接口和功能。

**引用文件：** <ohcamera/camera_device.h>

**库：** libohcamera.so

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 12

**相关模块：** [OH_Camera](capi-oh-camera.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Camera_ErrorCode OH_CameraDevice_GetCameraOrientation(Camera_Device* camera, uint32_t* orientation)](#oh_cameradevice_getcameraorientation) | 获取相机设备的传感器方向属性。 |
| [Camera_ErrorCode OH_CameraDevice_GetHostDeviceName(Camera_Device* camera, char** hostDeviceName)](#oh_cameradevice_gethostdevicename) | 获取远程设备名称。 |
| [Camera_ErrorCode OH_CameraDevice_GetHostDeviceType(Camera_Device* camera, Camera_HostDeviceType* hostDeviceType)](#oh_cameradevice_gethostdevicetype) | 获取远程设备类型。 |
| [Camera_ErrorCode OH_CameraDevice_GetLensEquivalentFocalLengths(const Camera_Device* camera, uint32_t** equivalentFocalLengths, uint32_t* size)](#oh_cameradevice_getlensequivalentfocallengths) | 获取相机设备的等效焦距。 |
| [Camera_ErrorCode OH_CameraDevice_IsLogicalCamera(const Camera_Device* camera, bool* isLogicalCamera)](#oh_cameradevice_islogicalcamera) | 检查相机设备是否为逻辑摄像头（由一个或多个物理摄像头组成）。 |
| [Camera_ErrorCode OH_CameraDevice_GetLogicalCameraConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device** constituentCameras, uint32_t* size)](#oh_cameradevice_getlogicalcameraconstituentcameradevices) | 获取组成逻辑摄像头的所有物理摄像头。 |
| [Camera_ErrorCode OH_CameraDevice_GetLensFocalLength(const Camera_Device* camera, float* lensFocalLength)](#oh_cameradevice_getlensfocallength) | 获取相机镜头的焦距。 |
| [Camera_ErrorCode OH_CameraDevice_GetMinimumFocusDistance(const Camera_Device* camera, float* minimumFocusDistance)](#oh_cameradevice_getminimumfocusdistance) | 获取相机设备的最小对焦距离。 |
| [Camera_ErrorCode OH_CameraDevice_GetLensDistortion(const Camera_Device* camera, float** lens, uint32_t* size)](#oh_cameradevice_getlensdistortion) | 获取相机设备的镜头畸变参数。 |
| [Camera_ErrorCode OH_CameraDevice_GetIntrinsicCalibration(const Camera_Device* camera, float** intrinsicCalibration, uint32_t* size)](#oh_cameradevice_getintrinsiccalibration) | 获取相机设备的内参标定参数。 |
| [Camera_ErrorCode OH_CameraDevice_GetSensorPhysicalSize(const Camera_Device* camera, float* width, float* height)](#oh_cameradevice_getsensorphysicalsize) | 获取相机传感器的物理尺寸。 |
| [Camera_ErrorCode OH_CameraDevice_GetSensorPixelArraySize(const Camera_Device* camera, uint32_t* width, uint32_t* height)](#oh_cameradevice_getsensorpixelarraysize) | 获取相机传感器的像素阵列大小。 |
| [Camera_ErrorCode OH_CameraDevice_GetSensorColorFilterArrangement(const Camera_Device* camera, OH_Camera_SensorColorFilterArrangement* sensorCFA)](#oh_cameradevice_getsensorcolorfilterarrangement) | 获取相机传感器的滤色阵列排列方式。 |

## 函数说明

### OH_CameraDevice_GetCameraOrientation()

```c
Camera_ErrorCode OH_CameraDevice_GetCameraOrientation(Camera_Device* camera, uint32_t* orientation)
```

**描述**

获取相机设备的传感器方向属性。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device。 |
| uint32_t* orientation | 返回相机sensor角度属性。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功，返回传感器方向属性。<br>         CAMERA_CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetHostDeviceName()

```c
Camera_ErrorCode OH_CameraDevice_GetHostDeviceName(Camera_Device* camera, char** hostDeviceName)
```

**描述**

获取远程设备名称。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device。 |
| char** hostDeviceName | 返回远程设备名称属性。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功，将返回远程设备名称属性。<br>         CAMERA_CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetHostDeviceType()

```c
Camera_ErrorCode OH_CameraDevice_GetHostDeviceType(Camera_Device* camera, Camera_HostDeviceType* hostDeviceType)
```

**描述**

获取远程设备类型。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device。 |
| [Camera_HostDeviceType](capi-camera-h.md#camera_hostdevicetype)* hostDeviceType | 远程设备类型属性。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功，将返回远程设备名称属性。<br>         CAMERA_CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetLensEquivalentFocalLengths()

```c
Camera_ErrorCode OH_CameraDevice_GetLensEquivalentFocalLengths(const Camera_Device* camera, uint32_t** equivalentFocalLengths, uint32_t* size)
```

**描述**

获取相机设备的等效焦距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| uint32_t** equivalentFocalLengths | 输出参数，返回等效焦距数组。 |
| uint32_t* size | 输出参数，返回数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_IsLogicalCamera()

```c
Camera_ErrorCode OH_CameraDevice_IsLogicalCamera(const Camera_Device* camera, bool* isLogicalCamera)
```

**描述**

检查相机设备是否为逻辑摄像头（由一个或多个物理摄像头组成）。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| bool* isLogicalCamera | 输出参数，返回表示是否为逻辑摄像头的布尔值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetLogicalCameraConstituentCameraDevices()

```c
Camera_ErrorCode OH_CameraDevice_GetLogicalCameraConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device** constituentCameras, uint32_t* size)
```

**描述**

获取组成逻辑摄像头的所有物理摄像头。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* logicalCamera | 逻辑摄像头的Camera_Device指针。 |
| [Camera_Device](capi-oh-camera-camera-device.md)** constituentCameras | 输出参数，返回组成逻辑摄像头的物理摄像头集合指针数组。 |
| uint32_t* size | 输出物理摄像头数量数组的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetLensFocalLength()

```c
Camera_ErrorCode OH_CameraDevice_GetLensFocalLength(const Camera_Device* camera, float* lensFocalLength)
```

**描述**

获取相机镜头的焦距。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| float* lensFocalLength | 输出参数，返回镜头焦距值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetMinimumFocusDistance()

```c
Camera_ErrorCode OH_CameraDevice_GetMinimumFocusDistance(const Camera_Device* camera, float* minimumFocusDistance)
```

**描述**

获取相机设备的最小对焦距离。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| float* minimumFocusDistance | 输出参数，返回最小对焦距离。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetLensDistortion()

```c
Camera_ErrorCode OH_CameraDevice_GetLensDistortion(const Camera_Device* camera, float** lens, uint32_t* size)
```

**描述**

获取相机设备的镜头畸变参数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| float** lens | 输出参数，返回镜头畸变参数数组。 |
| uint32_t* size | 输出参数，返回数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetIntrinsicCalibration()

```c
Camera_ErrorCode OH_CameraDevice_GetIntrinsicCalibration(const Camera_Device* camera, float** intrinsicCalibration, uint32_t* size)
```

**描述**

获取相机设备的内参标定参数。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| float** intrinsicCalibration | 输出参数，返回内参标定参数数组。 |
| uint32_t* size | 输出参数，返回数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetSensorPhysicalSize()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorPhysicalSize(const Camera_Device* camera, float* width, float* height)
```

**描述**

获取相机传感器的物理尺寸。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| float* width | 输出参数，返回传感器宽度（单位：毫米）。 |
| float* height | 输出参数，返回传感器高度（单位：毫米）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetSensorPixelArraySize()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorPixelArraySize(const Camera_Device* camera, uint32_t* width, uint32_t* height)
```

**描述**

获取相机传感器的像素阵列大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| uint32_t* width | 输出参数，返回像素阵列宽度（单位：像素）。 |
| uint32_t* height | 输出参数，返回像素阵列高度（单位：像素）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |

### OH_CameraDevice_GetSensorColorFilterArrangement()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorColorFilterArrangement(const Camera_Device* camera, OH_Camera_SensorColorFilterArrangement* sensorCFA)
```

**描述**

获取相机传感器的滤色阵列排列方式。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Camera_Device](capi-oh-camera-camera-device.md)* camera | 用于获取属性的Camera_Device指针。 |
| [OH_Camera_SensorColorFilterArrangement](capi-camera-h.md#oh_camera_sensorcolorfilterarrangement)* sensorCFA | 输出参数，返回传感器滤色阵列排列枚举值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | CAMERA_OK：方法调用成功。<br>         CAMERA_INVALID_ARGUMENT：参数丢失或者参数不正确。<br>         CAMERA_SERVICE_FATAL_ERROR：相机服务异常。 |


