# Image_Region
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct Image_Region {...}
```

## 概述

待解码的图像源区域结构体。区域坐标以图像左上角像素为原点（即(0, 0)），X轴正方向向右，Y轴正方向向下。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_common.h](capi-image-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t x | 区域左上角像素的横坐标（X坐标），以图像左上角像素为原点。单位：像素（px）。 |
| uint32_t y | 区域左上角像素的纵坐标（Y坐标），以图像左上角像素为原点。单位：像素（px）。 |
| uint32_t width | 区域的宽度。单位：像素（px）。 |
| uint32_t height | 区域的高度。单位：像素（px）。 |
