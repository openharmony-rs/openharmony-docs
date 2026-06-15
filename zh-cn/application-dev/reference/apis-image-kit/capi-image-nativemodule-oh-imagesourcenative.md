# OH_ImageSourceNative
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_ImageSourceNative
```

## 概述

OH_ImageSourceNative是native层封装的ImageSource结构体，用于创建图片数据。OH_ImageSourceNative结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。

有多种方式创建OH_ImageSourceNative，具体如下：

| 函数 | 描述 |
| -------- | -------- |
| [OH_ImageSourceNative_CreateFromUri](capi-image-source-native-h.md#oh_imagesourcenative_createfromuri) |通过uri创建OH_ImageSourceNative对象。|
| [OH_ImageSourceNative_CreateFromFd](capi-image-source-native-h.md#oh_imagesourcenative_createfromfd) |通过fd创建OH_ImageSourceNative对象。|
| [OH_ImageSourceNative_CreateFromData](capi-image-source-native-h.md#oh_imagesourcenative_createfromdata) |通过缓冲区数据创建OH_ImageSourceNative对象。|
| [OH_ImageSourceNative_CreateFromDataWithUserBuffer](capi-image-source-native-h.md#oh_imagesourcenative_createfromdatawithuserbuffer) |通过调用方传入的数据缓存创建OH_ImageSourceNative对象，创建过程中不拷贝该数据缓存。|
| [OH_ImageSourceNative_CreateFromRawFile](capi-image-source-native-h.md#oh_imagesourcenative_createfromrawfile) |通过图像资源文件的RawFileDescriptor创建OH_ImageSourceNative对象。|

使用[OH_ImageSourceNative_Release](capi-image-source-native-h.md#oh_imagesourcenative_release)函数释放OH_ImageSourceNative对象。

使用约束：使用OH_ImageSourceNative对象前，必须先通过上述接口创建对象；使用完成后，应调用[OH_ImageSourceNative_Release](capi-image-source-native-h.md#oh_imagesourcenative_release)释放对象。通过[OH_ImageSourceNative_CreateFromDataWithUserBuffer](capi-image-source-native-h.md#oh_imagesourcenative_createfromdatawithuserbuffer)创建对象时，在OH_ImageSourceNative对象生命周期内，调用方传入的数据缓存必须保持有效，不能被释放、复用或修改为其他图片数据。

资源管理：通过OH_ImageSourceNative解码或获取到的[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)、[OH_PictureNative](capi-image-nativemodule-oh-picturenative.md)、[OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md)对象由调用方分别管理。释放OH_ImageSourceNative对象不会自动释放这些对象，需要调用对应接口释放或销毁。

OH_ImageSourceNative结构体内容和操作方式如下：

| 字段类型| 字段名称 | 字段描述 |操作函数 | 函数描述 |
| -------- | -------- | -------- | -------- | -------- |
| int32_t | delayTimeList | 图像延迟时间数组。 | [OH_ImageSourceNative_GetDelayTimeList](capi-image-source-native-h.md#oh_imagesourcenative_getdelaytimelist) |获取图像延迟时间数组。 |
| OH_ImageSource_Info | info | ImageSource信息。 | [OH_ImageSourceNative_GetImageInfo](capi-image-source-native-h.md#oh_imagesourcenative_getimageinfo) |获取指定序号的图片信息。|
| Image_String | value | 图像属性值。 | [OH_ImageSourceNative_GetImageProperty](capi-image-source-native-h.md#oh_imagesourcenative_getimageproperty) |获取图片Exif指定属性键的值。|
| Image_String | value | 图像属性值。 | [OH_ImageSourceNative_ModifyImageProperty](capi-image-source-native-h.md#oh_imagesourcenative_modifyimageproperty) |通过指定的键修改图片Exif属性的值。|
| uint32_t | frameCount | 图像帧数。 | [OH_ImageSourceNative_GetFrameCount](capi-image-source-native-h.md#oh_imagesourcenative_getframecount) |获取图像帧数。|

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

**相关开发指导：** [使用Image_NativeModule完成图片解码](../../media/image/image-source-c.md)、[图片区域解码与下采样(C/C++)](../../media/image/image-region-and-downsampling-c.md)、[使用Image_NativeModule完成多图对象解码](../../media/image/image-source-picture-c.md)
