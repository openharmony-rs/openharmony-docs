# image_source_native.h（系统接口）

## 概述

图片解码API。

**库：** libimage_source.so

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 12

**系统接口：** 此接口为系统接口。

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ImageSource_SVGResourceLimitLevel（系统接口）](#oh_imagesource_svgresourcelimitlevel) | OH_ImageSource_SVGResourceLimitLevel | SVG资源限制级别的枚举。 级别越高，解析和渲染SVG图片时允许使用的资源越少。 无论指定哪个级别，系统资源限制都会生效。<br>**系统接口：** 此接口为系统接口。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Image_ErrorCode OH_ImageSourceNative_SetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel level)（系统接口）](#oh_imagesourcenative_setsvgresourcelimitlevel) | 设置图像源的SVG资源限制级别。 仅对SVG格式图片生效。对于非SVG图片，此函数无效果。 必须在[OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap)之前调用，以确保限制在DOM解析和渲染阶段均生效。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_ImageSourceNative_GetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel *level)（系统接口）](#oh_imagesourcenative_getsvgresourcelimitlevel) | 获取图像源的SVG资源限制级别。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool *needsDecodeDfxData)（系统接口）](#oh_decodingoptionsforpicture_getneedsdecodedfxdata) | 获取解码选项中的needsDecodeDfxData参数。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool needsDecodeDfxData)（系统接口）](#oh_decodingoptionsforpicture_setneedsdecodedfxdata) | 设置解码选项中的needsDecodeDfxData参数。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size *desiredSizeForMainPixelmap)（系统接口）](#oh_decodingoptionsforpicture_getdesiredsizeformainpixelmap) | 获取DecodingOptionsForPicture结构体中的主图期望尺寸。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size desiredSizeForMainPixelmap)（系统接口）](#oh_decodingoptionsforpicture_setdesiredsizeformainpixelmap) | 设置DecodingOptionsForPicture结构体中的主图期望尺寸。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT *desiredPixelFormat)（系统接口）](#oh_decodingoptionsforpicture_getdesiredpixelformat) | 获取DecodingOptionsForPicture结构体中的像素格式。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT desiredPixelFormat)（系统接口）](#oh_decodingoptionsforpicture_setdesiredpixelformat) | 设置DecodingOptionsForPicture结构体中的像素格式。<br>**系统接口：** 此接口为系统接口。 |
| [Image_ErrorCode OH_ImageSourceNative_ReadImageMetadataByType(OH_ImageSourceNative *source, uint32_t index, Image_MetadataType *metadataTypes, size_t typeCount, OH_PictureMetadata **outMetadataArray, size_t *metadataCount)（系统接口）](#oh_imagesourcenative_readimagemetadatabytype) | 读取图像源的元数据，使用metadataTypes参数指定要读取的元数据类型。如果未指定metadataTypes，将返回所有支持的元数据。<br>**系统接口：** 此接口为系统接口。 |

## 枚举类型说明

### OH_ImageSource_SVGResourceLimitLevel

```c
enum OH_ImageSource_SVGResourceLimitLevel
```

**描述：**

SVG资源限制级别的枚举。 级别越高，解析和渲染SVG图片时允许使用的资源越少。 无论指定哪个级别，系统资源限制都会生效。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

| 枚举项 | 描述 |
| -- | -- |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_NONE = 0 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_LOW = 1 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_MEDIUM = 2 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_HIGH = 3 |  |


## 函数说明

### OH_ImageSourceNative_SetSvgResourceLimitLevel()

```c
Image_ErrorCode OH_ImageSourceNative_SetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel level)
```

**描述：**

设置图像源的SVG资源限制级别。 仅对SVG格式图片生效。对于非SVG图片，此函数无效果。 必须在[OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap)之前调用，以确保限制在DOM解析和渲染阶段均生效。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | 指向图像源的指针。 |
| [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h-sys.md#oh_imagesource_svgresourcelimitlevel) level | SVG资源限制级别。详见[OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) 执行成功。</li>          <li>[OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION](capi-image-common-h.md#image_errorcode) 非系统应用调用此系统接口。</li>          <li>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) source为空指针。</li>          </ul> |

### OH_ImageSourceNative_GetSvgResourceLimitLevel()

```c
Image_ErrorCode OH_ImageSourceNative_GetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel *level)
```

**描述：**

获取图像源的SVG资源限制级别。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | 指向图像源的指针。 |
| [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h-sys.md#oh_imagesource_svgresourcelimitlevel) *level | 用于接收SVG资源限制级别的指针。 详见[OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) 执行成功。</li>          <li>[OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION](capi-image-common-h.md#image_errorcode) 非系统应用调用此系统接口。</li>          <li>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) source或level为空指针。</li>          </ul> |

### OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool *needsDecodeDfxData)
```

**描述：**

获取解码选项中的needsDecodeDfxData参数。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| bool *needsDecodeDfxData | 图像DFX数据是否需要解码。true表示图像DFX数据需要解码，false表示图像DFX数据不需要解码。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options或needsDecodeDfxData为空指针。</li>      <br></ul> |

### OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool needsDecodeDfxData)
```

**描述：**

设置解码选项中的needsDecodeDfxData参数。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| bool needsDecodeDfxData | 图像DFX数据是否需要解码。true表示图像DFX数据需要解码，false表示图像DFX数据不需要解码。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size *desiredSizeForMainPixelmap)
```

**描述：**

获取DecodingOptionsForPicture结构体中的主图期望尺寸。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| Image_Size *desiredSizeForMainPixelmap | 主图的期望尺寸。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size desiredSizeForMainPixelmap)
```

**描述：**

设置DecodingOptionsForPicture结构体中的主图期望尺寸。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| Image_Size desiredSizeForMainPixelmap | 主图的期望尺寸。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_DecodingOptionsForPicture_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT *desiredPixelFormat)
```

**描述：**

获取DecodingOptionsForPicture结构体中的像素格式。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| PIXEL_FORMAT *desiredPixelFormat | 解码选项中的像素格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_DecodingOptionsForPicture_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT desiredPixelFormat)
```

**描述：**

设置DecodingOptionsForPicture结构体中的像素格式。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | 指向OH_DecodingOptionsForPicture结构体的指针。 |
| PIXEL_FORMAT desiredPixelFormat | 解码选项中的像素格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：options为空指针。</li>      <br></ul> |

### OH_ImageSourceNative_ReadImageMetadataByType()

```c
Image_ErrorCode OH_ImageSourceNative_ReadImageMetadataByType(OH_ImageSourceNative *source, uint32_t index, Image_MetadataType *metadataTypes, size_t typeCount, OH_PictureMetadata **outMetadataArray, size_t *metadataCount)
```

**描述：**

读取图像源的元数据，使用metadataTypes参数指定要读取的元数据类型。如果未指定metadataTypes，将返回所有支持的元数据。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | 指向图像源的指针。 |
| uint32_t index | 图片索引。 |
| Image_MetadataType *metadataTypes | 指定的元数据类型。 |
| size_t typeCount | 指定的元数据类型的数量。 |
| OH_PictureMetadata **outMetadataArray | 输出参数，用于接收本函数分配的元数据数组。使用完成后调用者需要释放该对象。 |
| size_t *metadataCount | 输出的元数据数组中返回的OH_PictureMetadata元素数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| Image_ErrorCode | <ul>      <br><li>IMAGE_SUCCESS：执行成功。</li>      <br><li>202：非系统应用程序调用该接口则返回此错误码。</li>      <br><li>IMAGE_SOURCE_INVALID_PARAMETER：source、outMetadataArray或metadataCount为空指针。</li>      <br><li>IMAGE_SOURCE_UNSUPPORTED_METADATA：元数据不存在，或类型不支持。</li>      <br><li>IMAGE_SOURCE_ALLOC_FAILED：内存分配失败。</li>      <br></ul> |


