# OH_ImageNative
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--SE: @liyang_bryan-->
<!--TSE: @xchaosioda-->

## 概述

为图像接口定义native层图像对象的别名。

此结构体内容不可直接操作，采用函数调用方式操作具体字段，结构体内容和操作方式如下：

| 字段类型| 字段名称 | 字段描述 |操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| Image_Size| imageSize | 图像大小 |[OH_ImageNative_GetImageSize](capi-image-native-h.md#oh_imagenative_getimagesize) | 获取 OH_ImageNative 对象的 Image_Size 信息。|
| uint32_t | types |组件类型，用于描述图像颜色分量。 |[OH_ImageNative_GetComponentTypes](capi-image-native-h.md#oh_imagenative_getcomponenttypes) | 获取 OH_ImageNative 对象的组件列表信息。 |
| OH_NativeBuffer | nativeBuffer | 组件缓冲区|[OH_ImageNative_GetByteBuffer](capi-image-native-h.md#oh_imagenative_getbytebuffer) | 获取 OH_ImageNative 对象中某个组件类型所对应的缓冲区。|
| size_t | bufferSize | 缓冲区的大小 | [OH_ImageNative_GetBufferSize](capi-image-native-h.md#oh_imagenative_getbuffersize) | 获取 OH_ImageNative 对象中某个组件类型所对应的缓冲区的大小。|
| int32_t | rowStride | 像素行宽 | [OH_ImageNative_GetRowStride](capi-image-native-h.md#oh_imagenative_getrowstride) | 获取 OH_ImageNative 对象中某个组件类型所对应的像素行宽。 |
| int32_t | pixelStride | 像素大小 | [OH_ImageNative_GetPixelStride](capi-image-native-h.md#oh_imagenative_getpixelstride) | 获取 OH_ImageNative 对象中某个组件类型所对应的像素大小。 |

释放OH_ImageNative对象使用[OH_ImageNative_Release](capi-image-native-h.md#oh_imagenative_release)函数。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_native.h](capi-image-native-h.md)

