# Image_PositionArea
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct Image_PositionArea {...} Image_PositionArea
```

## 概述

要读取或写入的图像像素区域。

**起始版本：** 22

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_common.h](capi-image-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t *pixels | 读取或写入的图像像素数据。在非YUV类型像素的情况下仅支持BGRA_8888格式的数据。 |
| size_t pixelsSize | 图像像素数据的长度（单位：字节）。 |
| uint32_t offset | `pixels`缓冲区内首像素的字节偏移量，即区域像素数据在缓冲区中的起始位置（单位：字节）。读写区域数据时，从`pixels[offset]`处开始读取或写入。 |
| uint32_t stride | 区域的跨距，即区域中每行像素（含行末填充字节）所占的空间（单位：字节）。stride >= region.size.width * 每像素字节数。 |
| [Image_Region](capi-image-nativemodule-image-region.md) region | 读取或写入的区域。指定区域的宽度加X坐标不能大于原图的宽度，指定区域的高度加Y坐标不能大于原图的高度。 |


