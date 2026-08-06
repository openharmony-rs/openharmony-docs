# OH_DecodingOptionsForPicture
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_DecodingOptionsForPicture
```

## 概述

Picture解码参数结构体。

使用[OH_DecodingOptionsForPicture_Create](capi-image-source-native-h.md#oh_decodingoptionsforpicture_create)函数创建OH_DecodingOptionsForPicture对象。

使用[OH_DecodingOptionsForPicture_Release](capi-image-source-native-h.md#oh_decodingoptionsforpicture_release)函数释放OH_DecodingOptionsForPicture对象。

资源管理：释放OH_ImageSourceNative或解码生成的OH_PictureNative对象，不会自动释放OH_DecodingOptionsForPicture对象。OH_DecodingOptionsForPicture释放后，不应继续传入Picture解码接口或调用其字段获取和设置接口。

OH_DecodingOptionsForPicture结构体内容和操作方式如下：

| 字段类型 | 字段名称 | 字段描述 | 字段默认值 | 字段获取函数 | 字段设置函数 |
| -------- | -------- | -------- | -------- | -------- | -------- |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype)数组 | desiredAuxiliaryPictures | 期望在Picture解码结果中包含的辅助图类型，可用于只解码调用方需要的增益图、深度图等辅助图。 | 空集合，即不指定任何辅助图类型；解码Picture时会按全部支持的辅助图类型处理。 | [OH_DecodingOptionsForPicture_GetDesiredAuxiliaryPictures](capi-image-source-native-h.md#oh_decodingoptionsforpicture_getdesiredauxiliarypictures) | [OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures](capi-image-source-native-h.md#oh_decodingoptionsforpicture_setdesiredauxiliarypictures) |

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

**相关开发指导：** [使用Image_NativeModule完成多图对象解码](../../media/image/image-source-picture-c.md)
