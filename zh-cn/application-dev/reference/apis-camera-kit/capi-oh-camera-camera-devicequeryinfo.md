# Camera_DeviceQueryInfo
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} Camera_DeviceQueryInfo
```

## 概述

相机设备的查询信息。

**起始版本：** 23

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| Camera_Type* cameraType | 相机类型属性列表。 |
| uint32_t cameraTypeSize | 相机类型属性列表的大小。 |
| [Camera_Position](capi-camera-h.md#camera_position) cameraPosition | 相机位置属性。 |
| [Camera_Connection](capi-camera-h.md#camera_connection) connectionType | 相机连接类型属性。 |