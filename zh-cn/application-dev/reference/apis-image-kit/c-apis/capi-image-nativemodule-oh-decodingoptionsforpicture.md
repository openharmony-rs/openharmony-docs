# OH_DecodingOptionsForPicture

```c
typedef struct OH_DecodingOptionsForPicture OH_DecodingOptionsForPicture
```

## 概述

Picture解码参数结构体。<br>使用[OH_DecodingOptionsForPicture_Create](capi-image-source-native-h.md#oh_decodingoptionsforpicture_create)函数创建OH_DecodingOptionsForPicture对象。<br>使用[OH_DecodingOptionsForPicture_Release](capi-image-source-native-h.md#oh_decodingoptionsforpicture_release)函数释放OH_DecodingOptionsForPicture对象。<br>资源管理：释放OH_ImageSourceNative或解码生成的OH_PictureNative对象，不会自动释放OH_DecodingOptionsForPicture对象。OH_DecodingOptionsForPicture释放后，不应继续传入Picture解码接口或调用其字段获取和设置接口。<br>OH_DecodingOptionsForPicture结构体内容和操作方式如下：

**起始版本：** 13

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

