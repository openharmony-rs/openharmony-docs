# OH_Camera_PhysicalAperture
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Camera_PhysicalAperture {...} OH_Camera_PhysicalAperture
```

## 概述

物理光圈配置。

**起始版本：** 24

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Camera_ZoomRange](capi-oh-camera-oh-camera-zoomrange.md) zoomRange | 变焦范围。 |
| float* apertures | 支持的光圈值数组。 |
| size_t apertureCount | 光圈值数量。 |