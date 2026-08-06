# OH_ImageSource_Info

```c
struct OH_ImageSource_Info
```

## 概述

OH_ImageSource_Info是native层封装的ImageSource信息结构体，OH_ImageSource_Info结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>使用[OH_ImageSourceInfo_Create](capi-image-source-native-h.md#oh_imagesourceinfo_create)函数创建OH_ImageSource_Info对象。<br>使用[OH_ImageSourceNative_GetImageInfo](capi-image-source-native-h.md#oh_imagesourcenative_getimageinfo)函数将OH_ImageSourceNative中的图像信息写入创建好的OH_ImageSource_Info对象。<br>使用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)函数释放OH_ImageSource_Info对象。<br>使用约束：OH_ImageSource_Info对象通常配合[OH_ImageSourceNative_GetImageInfo](capi-image-source-native-h.md#oh_imagesourcenative_getimageinfo)使用，用于承载指定序号图片的宽、高、动态范围和MIME类型等信息。使用前需通过[OH_ImageSourceInfo_Create](capi-image-source-native-h.md#oh_imagesourceinfo_create)创建对象；使用完成后，应调用[OH_ImageSourceInfo_Release](capi-image-source-native-h.md#oh_imagesourceinfo_release)释放对象。<br>OH_ImageSource_Info结构体内容和操作方式如下：

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

