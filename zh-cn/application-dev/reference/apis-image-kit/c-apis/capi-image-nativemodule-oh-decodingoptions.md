# OH_DecodingOptions

```c
struct OH_DecodingOptions
```

## 概述

OH_DecodingOptions是native层封装的解码选项参数结构体，用于设置解码选项参数，在创建Pixelmap时作为入参传入，详细信息见[OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap)。<br>OH_DecodingOptions结构体不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>使用[OH_DecodingOptions_Create](capi-image-source-native-h.md#oh_decodingoptions_create)函数创建OH_DecodingOptions对象。<br>使用[OH_DecodingOptions_Release](capi-image-source-native-h.md#oh_decodingoptions_release)函数释放OH_DecodingOptions对象。<br>使用约束：OH_DecodingOptions用于配置PixelMap解码参数，通常作为[OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap)、[OH_ImageSourceNative_CreatePixelmapUsingAllocator](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmapusingallocator)或[OH_ImageSourceNative_CreatePixelmapList](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmaplist)的入参。使用前需通过[OH_DecodingOptions_Create](capi-image-source-native-h.md#oh_decodingoptions_create)创建对象；使用完成后，应调用[OH_DecodingOptions_Release](capi-image-source-native-h.md#oh_decodingoptions_release)释放对象。<br>资源管理：释放OH_ImageSourceNative或解码生成的OH_PixelmapNative对象，不会自动释放OH_DecodingOptions对象。OH_DecodingOptions释放后，不应继续传入解码接口或调用其字段获取和设置接口。<br>OH_DecodingOptions结构体内容和操作方式如下：

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_source_native.h](capi-image-source-native-h.md)

