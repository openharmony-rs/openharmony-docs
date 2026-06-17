# OH_ImageRawData
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_ImageRawData OH_ImageRawData
```

## 概述

OH_ImageRawData用于承载图像中的原始数据。

使用[OH_ImageSourceNative_CreateImageRawData](capi-image-source-native-h.md#oh_imagesourcenative_createimagerawdata)函数从OH_ImageSourceNative对象中创建OH_ImageRawData对象。

使用[OH_ImageSourceNative_DestroyImageRawData](capi-image-source-native-h.md#oh_imagesourcenative_destroyimagerawdata)函数销毁OH_ImageRawData对象。

资源管理：OH_ImageRawData使用完成后，应调用[OH_ImageSourceNative_DestroyImageRawData](capi-image-source-native-h.md#oh_imagesourcenative_destroyimagerawdata)销毁。释放OH_ImageSourceNative对象不会自动销毁OH_ImageRawData对象，二者生命周期相互独立。通过[OH_ImageSourceNative_GetBufferFromRawData](capi-image-source-native-h.md#oh_imagesourcenative_getbufferfromrawdata)获取到的data指向OH_ImageRawData对象内部缓冲区，调用方不应对data调用free()。OH_ImageRawData对象销毁后，该data地址失效。如需在OH_ImageRawData对象销毁后继续使用数据，应在销毁前自行拷贝。

OH_ImageRawData结构体内容和操作方式如下：

| 字段类型 | 字段名称 | 字段描述 | 字段获取函数 |
| -- | -- | -- | -- |
| uint8_t * | data | 原始数据缓冲区首地址。 | [OH_ImageSourceNative_GetBufferFromRawData](capi-image-source-native-h.md#oh_imagesourcenative_getbufferfromrawdata) |
| size_t | length | 原始数据缓冲区长度。 | [OH_ImageSourceNative_GetBufferFromRawData](capi-image-source-native-h.md#oh_imagesourcenative_getbufferfromrawdata) |
| uint8_t | bitsPerPixel | 缓冲区数据中每个像素实际占用的位数。 | [OH_ImageSourceNative_GetBitsPerPixelFromRawData](capi-image-source-native-h.md#oh_imagesourcenative_getbitsperpixelfromrawdata) |

**起始版本：** 24

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)
