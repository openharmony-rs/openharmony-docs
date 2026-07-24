# OhosPixelMapCreateOps
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OhosPixelMapCreateOps {...}
```

## 概述

用于定义创建PixelMap的设置选项，包含图片宽高、像素格式、是否可编辑、透明度类型及缩放类型信息，适用于在Native层创建PixelMap时指定初始化属性的场景。

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_pixel_map_mdk.h](capi-image-pixel-map-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t width | 图片的宽，单位：像素（px）。取值必须大于0。传入0时创建PixelMap失败。 |
| uint32_t height | 图片的高，单位：像素（px）。取值必须大于0。传入0时创建PixelMap失败。 |
| int32_t pixelFormat | 图片的像素格式。取值范围：<br>0：未知格式。<br>2：格式为RGB_565。<br>3：格式为RGBA_8888。<br>4：格式为BGRA_8888。<br>5：格式为RGB_888。<br>6：格式为ALPHA_8。<br>7：格式为RGBA_F16。<br>8：格式为NV21。<br>9：格式为NV12。 |
| uint32_t editable | 是否可编辑。1表示图片像素可编辑，0表示不可编辑。 |
| uint32_t alphaType | 图片的透明度类型。取值范围：<br>0：未知透明度。<br>1：没有Alpha通道或图片不透明。<br>2：预乘透明度格式。<br>3：非预乘透明度格式。 |
| uint32_t scaleMode | 图片的缩放类型。取值范围：<br>1：缩放图像以填充目标图像区域并居中裁剪区域外的效果。<br>0：等比缩放适配目标图片尺寸（保持宽高比）。 |
