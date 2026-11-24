# OhosImageDecodingOps

```c
struct OhosImageDecodingOps {...}
```

## 概述

定义图像源解码的范围选项。是[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)的成员变量。

<!--Device-struct OhosImageDecodingOps {...}--><!--Device-struct OhosImageDecodingOps {...}-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-image-kit-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int8_t editable | Defines output pixel map editable.<br><!--Device-int8_t editable--><!--Device-int8_t editable-End--> |
| int32_t pixelFormat | Defines output pixel format.<br><!--Device-int32_t pixelFormat--><!--Device-int32_t pixelFormat-End--> |
| int32_t fitDensity | Defines decoding target pixel density.<br><!--Device-int32_t fitDensity--><!--Device-int32_t fitDensity-End--> |
| uint32_t index | Defines decoding index of image source.<br><!--Device-uint32_t index--><!--Device-uint32_t index-End--> |
| uint32_t sampleSize | Defines decoding sample size option.<br><!--Device-uint32_t sampleSize--><!--Device-uint32_t sampleSize-End--> |
| uint32_t rotate | Defines decoding rotate option.<br><!--Device-uint32_t rotate--><!--Device-uint32_t rotate-End--> |
| [struct OhosImageSize](capi-image-ohosimagesize.md) size | Defines decoding target pixel size of width and height.<br><!--Device-struct OhosImageSize size--><!--Device-struct OhosImageSize size-End--> |
| [struct OhosImageRegion](capi-image-ohosimageregion.md) region | Defines image source pixel region for decoding.<br><!--Device-struct OhosImageRegion region--><!--Device-struct OhosImageRegion region-End--> |


