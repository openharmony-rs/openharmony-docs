# OH_ImageSource_Info
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_ImageSource_Info
```

## 概述

OH_ImageSource_Info是native层封装的ImageSource信息结构体，OH_ImageSource_Info结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。

创建OH_ImageSource_Info对象使用[OH_ImageSourceInfo_Create](capi-image-source-native-h.md#oh_imagesourceinfo_create)函数。

释放OH_ImageSource_Info对象使用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)函数。调用该接口之后，与OH_ImageSourceInfo结构体相关的属性均会被释放。因此在调用该接口前，请务必确认相关属性已不再被需要或对相关属性已完成深拷贝操作。

OH_ImageSource_Info结构体内容和操作方式如下：

| 字段类型| 字段名称 | 字段描述 |操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| uint32_t | width | 图片宽度 | [OH_ImageSourceInfo_GetWidth](capi-image-source-native-h.md#oh_imagesourceinfo_getwidth) |获取图片的宽。|
| uint32_t | height | 图片高度 | [OH_ImageSourceInfo_GetHeight](capi-image-source-native-h.md#oh_imagesourceinfo_getheight) |获取图片的高。|
| bool | isHdr | 是否为高动态范围的信息 | [OH_ImageSourceInfo_GetDynamicRange](capi-image-source-native-h.md#oh_imagesourceinfo_getdynamicrange) |获取图片是否为高动态范围的信息。|
| [Image_MimeType](capi-image-nativemodule-image-string.md) | mimeType | 图片源的MIME类型 | [OH_ImageSourceInfo_GetMimetype](./capi-image-source-native-h.md#oh_imagesourceinfo_getmimetype) | 获取图片的MimeType。|

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

