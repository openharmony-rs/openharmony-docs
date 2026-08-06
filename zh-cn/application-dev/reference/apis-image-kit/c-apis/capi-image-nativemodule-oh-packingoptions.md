# OH_PackingOptions

```c
struct OH_PackingOptions
```

## 概述

OH_PackingOptions是native层封装的图像编码选项结构体，不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>使用[OH_PackingOptions_Create](capi-image-packer-native-h.md#oh_packingoptions_create)函数创建OH_PackingOptions对象。<br>使用[OH_PackingOptions_Release](capi-image-packer-native-h.md#oh_packingoptions_release)函数释放OH_PackingOptions对象。<br>使用约束：OH_PackingOptions用于配置ImageSource、PixelMap或Picture编码参数。<br>资源管理：释放OH_ImagePackerNative对象不会自动释放OH_PackingOptions对象。OH_PackingOptions使用完成后，应调用[OH_PackingOptions_Release](capi-image-packer-native-h.md#oh_packingoptions_release)释放，释放后不应继续传入图像编码接口或调用其字段获取和设置接口。<br>OH_PackingOptions结构体内容和操作方式如下：<br>\| 字段类型 \| 字段名称 \| 字段描述 \| 字段获取函数 \| 字段设置函数 \|\| -- \| --
\| -- \| -- \| -- \|\| [Image_MimeType](capi-image-nativemodule-image-string.md) \| mimeType \| 目标编码格式的MIME类型。ImageSource或PixelMap编码支持`image/jpeg`、`image/webp`、`image/png`、`image/heic`或`image/heif`、`image/sdr_astc_4x4`、`image/sdr_sut_superfast_4x4`、`image/hdr_astc_4x4`；Picture编码支持`image/jpeg`、`image/heic`或`image/heif`。实际支持范围以[OH_ImagePackerNative_GetSupportedFormats](capi-image-packer-native-h.md#oh_imagepackernative_getsupportedformats)返回结果为准。 \|[OH_PackingOptions_GetMimeType](capi-image-packer-native-h.md#oh_packingoptions_getmimetype)、[OH_PackingOptions_GetMimeTypeWithNull](capi-image-packer-native-h.md#oh_packingoptions_getmimetypewithnull) \|[OH_PackingOptions_SetMimeType](capi-image-packer-native-h.md#oh_packingoptions_setmimetype) \|\| uint32_t \| quality \| 编码质量，实际编码效果取决于目标编码格式。 \|[OH_PackingOptions_GetQuality](capi-image-packer-native-h.md#oh_packingoptions_getquality) \| [OH_PackingOptions_SetQuality](capi-image-packer-native-h.md#oh_packingoptions_setquality) \|\| bool \| needsPackProperties \|是否需要编码图像属性，例如Exif。 \| [OH_PackingOptions_GetNeedsPackProperties](capi-image-packer-native-h.md#oh_packingoptions_getneedspackproperties) \|[OH_PackingOptions_SetNeedsPackProperties](capi-image-packer-native-h.md#oh_packingoptions_setneedspackproperties) \|\| int32_t \| desiredDynamicRange \| 编码时期望的图片动态范围，取值见[IMAGE_PACKER_DYNAMIC_RANGE](capi-image-packer-native-h.md#image_packer_dynamic_range)。 \| [OH_PackingOptions_GetDesiredDynamicRange](capi-image-packer-native-h.md#oh_packingoptions_getdesireddynamicrange) \|[OH_PackingOptions_SetDesiredDynamicRange](capi-image-packer-native-h.md#oh_packingoptions_setdesireddynamicrange) \|

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)

