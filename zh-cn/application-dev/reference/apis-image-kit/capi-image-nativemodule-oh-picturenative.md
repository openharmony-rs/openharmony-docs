# OH_PictureNative
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_PictureNative
```

## 概述

Picture结构体类型，用于执行picture相关操作。

Picture为多图对象结构体，包含主图、辅助图和元数据。

主图包含图像的大部分信息，主要用于显示图像内容。

辅助图用于存储与主图相关但不同的数据，展示图像更丰富的信息。

元数据一般用来存储关于图像文件的信息。

有多种方式创建OH_PictureNative，具体如下：

| 函数 | 描述 |
| -------- | -------- |
| [OH_ImageSourceNative_CreatePicture](capi-image-source-native-h.md#oh_imagesourcenative_createpicture) | 通过图片解码创建OH_PictureNative对象。 |
| [OH_ImageSourceNative_CreatePictureAtIndex](capi-image-source-native-h.md#oh_imagesourcenative_createpictureatindex) | 通过指定序号的图片解码创建OH_PictureNative对象。 |
| [OH_PictureNative_CreatePicture](capi-picture-native-h.md#oh_picturenative_createpicture) | 通过主图OH_PixelmapNative对象创建OH_PictureNative对象。 |

使用[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)函数释放OH_PictureNative对象。

使用约束：使用OH_PictureNative对象前，需先创建对象；使用完成后，应调用[OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release)释放对象。通过[OH_ImageSourceNative_CreatePicture](capi-image-source-native-h.md#oh_imagesourcenative_createpicture)或[OH_ImageSourceNative_CreatePictureAtIndex](capi-image-source-native-h.md#oh_imagesourcenative_createpictureatindex)解码Picture时，图片源格式需支持Picture解码。通过[OH_PictureNative_CreatePicture](capi-picture-native-h.md#oh_picturenative_createpicture)创建Picture时，mainPixelmap和picture均不能为空指针。

资源管理：释放OH_ImageSourceNative对象不会自动释放已创建的OH_PictureNative对象。通过OH_PictureNative获取到的OH_PixelmapNative、OH_AuxiliaryPictureNative和OH_PictureMetadata对象由调用方管理，使用完成后需分别调用[OH_PixelmapNative_Destroy](capi-pixelmap-native-h.md#oh_pixelmapnative_destroy)、[OH_AuxiliaryPictureNative_Release](capi-picture-native-h.md#oh_auxiliarypicturenative_release)和[OH_PictureMetadata_Release](capi-image-common-h.md#oh_picturemetadata_release)释放。获取PixelMap、辅助图或元数据的接口返回失败时，输出参数的内容不能在后续流程中继续使用。

OH_PictureNative结构体内容和操作方式如下：

| 字段类型 | 字段名称 | 字段描述 | 操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| OH_PixelmapNative | mainPixelmap | Picture主图。 | [OH_PictureNative_GetMainPixelmap](capi-picture-native-h.md#oh_picturenative_getmainpixelmap) | 获取主图的OH_PixelmapNative对象。 |
| OH_PixelmapNative | hdrPixelmap | HDR合成图。 | [OH_PictureNative_GetHdrComposedPixelmap](capi-picture-native-h.md#oh_picturenative_gethdrcomposedpixelmap) | 获取HDR合成后的OH_PixelmapNative对象。 |
| OH_PixelmapNative | hdrPixelmap | HDR合成图。 | [OH_PictureNative_GetHdrComposedPixelmapWithOptions](capi-picture-native-h.md#oh_picturenative_gethdrcomposedpixelmapwithoptions) | 按OH_ComposeOptions配置获取HDR合成后的OH_PixelmapNative对象。 |
| OH_PixelmapNative | gainmapPixelmap | 增益图。 | [OH_PictureNative_GetGainmapPixelmap](capi-picture-native-h.md#oh_picturenative_getgainmappixelmap) | 获取增益图的OH_PixelmapNative对象。 |
| OH_AuxiliaryPictureNative | auxiliaryPicture | 辅助图。 | [OH_PictureNative_SetAuxiliaryPicture](capi-picture-native-h.md#oh_picturenative_setauxiliarypicture) | 设置辅助图。 |
| OH_AuxiliaryPictureNative | auxiliaryPicture | 辅助图。 | [OH_PictureNative_GetAuxiliaryPicture](capi-picture-native-h.md#oh_picturenative_getauxiliarypicture) | 根据类型获取辅助图。 |
| OH_PictureMetadata | metadata | 主图元数据。 | [OH_PictureNative_GetMetadata](capi-picture-native-h.md#oh_picturenative_getmetadata) | 获取主图的元数据。 |
| OH_PictureMetadata | metadata | 主图元数据。 | [OH_PictureNative_SetMetadata](capi-picture-native-h.md#oh_picturenative_setmetadata) | 设置主图的元数据。 |

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [picture_native.h](capi-picture-native-h.md)

**相关开发指导：** [使用Image_NativeModule完成多图对象解码](../../media/image/image-source-picture-c.md)
