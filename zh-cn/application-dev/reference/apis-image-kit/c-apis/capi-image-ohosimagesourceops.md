# OhosImageSourceOps

```c
struct OhosImageSourceOps {...}
```

## 概述

定义图像源选项信息。此选项给{@link OH_ImageSource_CreateFromUri}、{@link OH_ImageSource_CreateFromFd}、<br>{@link OH_ImageSource_CreateFromData}和{@link OH_ImageSource_CreateIncremental}接口使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t density | 图像源像素密度。 |
| int32_t pixelFormat | 图像源像素格式，通常用于描述YUV缓冲区。 |
| struct OhosImageSize size | 图像源像素宽高的大小。 |


