# OH_PackingOptions

```c
struct OH_PackingOptions
```

## 概述

OH_PackingOptions是native层封装的图像编码选项结构体，不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>使用 {@link OH_PackingOptions_Create}函数创建OH_PackingOptions对象。<br>使用{@link OH_PackingOptions_Release}<br>函数释放OH_PackingOptions对象。<br>使用约束：OH_PackingOptions用于配置ImageSource、PixelMap或Picture编码参数。<br>资源管理：<br>释放OH_ImagePackerNative对象不会自动释放OH_PackingOptions对象。OH_PackingOptions使用完成后，应调用{@link OH_PackingOptions_Release}释放，<br>释放后不应继续传入图像编码接口或调用其字段获取和设置接口。<br>OH_PackingOptions结构体内容和操作方式如下：<br>\| 字段类型 \| 字段名称 \| 字段描述 \| 字段获取函数 \| 字段设置函数 \|\| -- \| --<br>\| -- \| -- \| -- \|\| {@link Image_MimeType} \| mimeType \| 目标编码格式的MIME类型。ImageSource或PixelMap编码支持`image/jpeg`、`image/webp`<br>、`image/png`、`image/heic`或`image/heif`、`image/sdr_astc_4x4`、`image/sdr_sut_superfast_4x4`、`image/hdr_astc_4x4`；<br>Picture编码支持`image/jpeg`、`image/heic`或`image/heif`。实际支持范围以{@link OH_ImagePackerNative_GetSupportedFormats}返回结果为准。 \|<br>{@link OH_PackingOptions_GetMimeType}、{@link OH_PackingOptions_GetMimeTypeWithNull} \|<br>{@link OH_PackingOptions_SetMimeType} \|\| uint32_t \| quality \| 编码质量，实际编码效果取决于目标编码格式。 \|<br>{@link OH_PackingOptions_GetQuality} \| {@link OH_PackingOptions_SetQuality} \|\| bool \| needsPackProperties \|<br>是否需要编码图像属性，例如Exif。 \| {@link OH_PackingOptions_GetNeedsPackProperties} \|<br>{@link OH_PackingOptions_SetNeedsPackProperties} \|\| int32_t \| desiredDynamicRange \| 编码时期望的图片动态范围，取值见<br>{@link IMAGE_PACKER_DYNAMIC_RANGE}。 \| {@link OH_PackingOptions_GetDesiredDynamicRange} \|<br>{@link OH_PackingOptions_SetDesiredDynamicRange} \|

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)

