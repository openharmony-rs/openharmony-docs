# Camera_Rect

```c
typedef struct Camera_Rect {...} Camera_Rect
```

## 概述

相机矩形。用于各类检测对象的矩形框绘制。<br> 检测点坐标系以设备横向位置（充电口朝右）为基准。<br> 坐标系原点位于左上角 (0, 0)，右下角对应相机预览流的像素分辨率。<br> 所有参数均为整型像素值，其中topLeftX与topLeftY表示矩形左上角坐标，width与height分别表示矩形的宽高。

**起始版本：** 11

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t topLeftX |  |
| int32_t topLeftY |  |
| int32_t width |  |
| int32_t height |  |


