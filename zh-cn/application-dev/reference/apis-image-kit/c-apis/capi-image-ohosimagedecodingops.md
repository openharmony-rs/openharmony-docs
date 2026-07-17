# OhosImageDecodingOps

```c
struct OhosImageDecodingOps {...}
```

## 概述

定义图像源解码的范围选项。是[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)的成员变量。

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int8_t editable | Defines output pixel map editable. |
| int32_t pixelFormat | Defines output pixel format. |
| int32_t fitDensity | Defines decoding target pixel density. |
| uint32_t index | Defines decoding index of image source. |
| uint32_t sampleSize | Defines decoding sample size option. |
| uint32_t rotate | Defines decoding rotate option. |
| struct [OhosImageSize](capi-image-ohosimagesize.md) size | Defines decoding target pixel size of width and height. |
| struct [OhosImageRegion](capi-image-ohosimageregion.md) region | Defines image source pixel region for decoding. |


