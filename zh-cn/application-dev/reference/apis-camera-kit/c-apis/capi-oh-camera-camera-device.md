# Camera_Device

```c
typedef struct Camera_Device {...} Camera_Device
```

## 概述

相机设备对象。

<!--Device-struct Camera_Device {...}--><!--Device-struct Camera_Device {...}-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

**相关模块：** [OH_Camera](capi-camera-kit-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* cameraId | 相机id属性。<br><!--Device-char* cameraId--><!--Device-char* cameraId-End--> |
| [Camera_Position](capi-camera-h.md#camera_position) cameraPosition | 相机位置属性。<br><!--Device-Camera_Position cameraPosition--><!--Device-Camera_Position cameraPosition-End--> |
| [Camera_Type](capi-camera-h.md#camera_type) cameraType | 相机类型属性。<br><!--Device-Camera_Type cameraType--><!--Device-Camera_Type cameraType-End--> |
| [Camera_Connection](capi-camera-h.md#camera_connection) connectionType | 相机连接类型属性。<br><!--Device-Camera_Connection connectionType--><!--Device-Camera_Connection connectionType-End--> |


