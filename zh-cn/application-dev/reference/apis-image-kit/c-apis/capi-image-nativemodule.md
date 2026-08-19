# Image_NativeModule

## 概述

Provides APIs for obtaining image data.

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [image_receiver_native.h](capi-image-receiver-native-h.md) | 声明从native层获取图片数据的方法。 |
| [pixelmap_native.h](capi-pixelmap-native-h.md) | 访问Pixelmap的API。提供对Pixelmap（像素图）的访问能力，支持通过像素数据、Surface、NativeBuffer等多种方式创建像素图、克隆像素图、读写像素数据，以及进行缩放、旋转、翻转、平移、裁剪等图像变换操作，同时支持HDR元数据管理、色彩空间设置、透明度类型转换、Native与Napi对象互转和内存直接访问等功能，适用于需要在Native层对解码后的图像位图进行像素级处理与变换的场景。 |
| [image_packer_native.h](capi-image-packer-native-h.md) | 图片编码API。 |
| [picture_native.h](capi-picture-native-h.md) | 提供获取picture数据和信息的API。 |
| [image_native.h](capi-image-native-h.md) | 声明图像的剪辑矩形、大小和组件数据的接口函数。 |
| [image_common.h](capi-image-common-h.md) | 声明图像接口使用的公共枚举和结构体。 |
| [image_source_native.h](capi-image-source-native-h.md) | 图片解码API。 |
