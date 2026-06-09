# OH_ImageSource_Info
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_ImageSource_Info
```

## 概述

OH_ImageSource_Info是native层封装的ImageSource信息结构体，OH_ImageSource_Info结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。

使用[OH_ImageSourceInfo_Create](capi-image-source-native-h.md#oh_imagesourceinfo_create)函数创建OH_ImageSource_Info对象。

使用[OH_ImageSourceNative_GetImageInfo](capi-image-source-native-h.md#oh_imagesourcenative_getimageinfo)函数将OH_ImageSourceNative中的图像信息写入创建好的OH_ImageSource_Info对象。

使用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)函数释放OH_ImageSource_Info对象。

使用约束：OH_ImageSource_Info对象通常配合[OH_ImageSourceNative_GetImageInfo](capi-image-source-native-h.md#oh_imagesourcenative_getimageinfo)使用，用于承载指定序号图片的宽、高、动态范围和MIME类型等信息。使用前需通过[OH_ImageSourceInfo_Create](capi-image-source-native-h.md#oh_imagesourceinfo_create)创建对象；使用完成后，应调用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)释放对象。

OH_ImageSource_Info结构体内容和操作方式如下：

| 字段类型| 字段名称 | 字段描述 |操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| uint32_t | width | 图片宽度。 | [OH_ImageSourceInfo_GetWidth](capi-image-source-native-h.md#oh_imagesourceinfo_getwidth) |获取图片的宽。|
| uint32_t | height | 图片高度。 | [OH_ImageSourceInfo_GetHeight](capi-image-source-native-h.md#oh_imagesourceinfo_getheight) |获取图片的高。|
| bool | isHdr | 是否为高动态范围（HDR）的信息。 | [OH_ImageSourceInfo_GetDynamicRange](capi-image-source-native-h.md#oh_imagesourceinfo_getdynamicrange) |获取图片是否为高动态范围的信息。|
| [Image_MimeType](capi-image-nativemodule-image-string.md) | mimeType | 图片源的MIME类型。 | [OH_ImageSourceInfo_GetMimeType](./capi-image-source-native-h.md#oh_imagesourceinfo_getmimetype) | 获取图片的MimeType。|

> **说明：**
>
> 通过[OH_ImageSourceInfo_GetMimeType](capi-image-source-native-h.md#oh_imagesourceinfo_getmimetype)获取到的mimeType.data指向OH_ImageSource_Info对象内部持有的内存。调用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)释放OH_ImageSource_Info后，该地址会失效；如需在释放后继续使用MIME类型数据，应在释放前自行深拷贝。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

**相关开发指导：** [使用Image_NativeModule完成图片解码](../../media/image/image-source-c.md)、[图片区域解码与下采样(C/C++)](../../media/image/image-region-and-downsampling-c.md)
