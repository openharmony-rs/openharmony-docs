# Image

## 概述

提供image接口的访问。

**起始版本：** 8

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [image_pixel_map_napi.h](capi-image-pixel-map-napi-h.md) | 声明可以锁定并访问pixelmap数据的方法，声明解锁的方法。 |
| [image_packer_mdk.h](capi-image-packer-mdk-h.md) | 声明用于将图像编码到缓冲区或文件的api。可用于将像素数据编码到目标缓冲区或文件中。 |
| [image_pixel_map_mdk.h](capi-image-pixel-map-mdk-h.md) | 声明可以锁定并访问pixelmap数据的方法，声明解锁的方法。推荐使用[pixelmap_native.h](./image/pixelmap_native.h)。 |
| [image_mdk.h](capi-image-mdk-h.md) | 声明访问图像矩形、大小、格式和组件数据的函数。 |
| [image_source_mdk.h](capi-image-source-mdk-h.md) | 声明将ImageSource解码成像素位图的方法。 |
| [image_mdk_common.h](capi-image-mdk-common-h.md) | 声明图像常用的枚举值和结构体。 |
| [image_receiver_mdk.h](capi-image-receiver-mdk-h.md) | 声明从native层获取图片数据的方法。 |
