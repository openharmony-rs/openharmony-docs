# image_source_native.h(System API)

## Overview

The file declares the APIs for image decoding.

**Library**: libimage_source.so

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**System API:** This is a system API.

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ImageSource_SVGResourceLimitLevel(System API)](#oh_imagesource_svgresourcelimitlevel) | OH_ImageSource_SVGResourceLimitLevel | Indicates the enumeration of SVG resource restriction levels. Higher levels allow fewer resources to be used when parsing and rendering SVG images. System resource limits are enforced regardless of the level specified.**System API:** This is a system API. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_ImageSourceNative_SetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel level)(System API)](#oh_imagesourcenative_setsvgresourcelimitlevel) | Sets the SVG resource limit level for the image source. This only takes effect for SVG format images. For non-SVG images, this function has no effect. Must be called before [OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap) to ensure the limit takes effect on both DOM parsing and rendering stages.**System API:** This is a system API. |
| [Image_ErrorCode OH_ImageSourceNative_GetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel *level)(System API)](#oh_imagesourcenative_getsvgresourcelimitlevel) | Gets the SVG resource limit level of the image source.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool *needsDecodeDfxData)(System API)](#oh_decodingoptionsforpicture_getneedsdecodedfxdata) | Obtains the **needsDecodeDfxData** parameter in the decoding options.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool needsDecodeDfxData)(System API)](#oh_decodingoptionsforpicture_setneedsdecodedfxdata) | Sets the **needsDecodeDfxData** parameter in the decoding options.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size *desiredSizeForMainPixelmap)(System API)](#oh_decodingoptionsforpicture_getdesiredsizeformainpixelmap) | Gets the desiredSizeForMainPixelMap number for DecodingOptionsForPicture struct.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size desiredSizeForMainPixelmap)(System API)](#oh_decodingoptionsforpicture_setdesiredsizeformainpixelmap) | Sets the desiredSizeForMainPixelMap number for DecodingOptionsForPicture struct.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT *desiredPixelFormat)(System API)](#oh_decodingoptionsforpicture_getdesiredpixelformat) | Get pixelFormat number for DecodingOptionsForPicture struct.**System API:** This is a system API. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT desiredPixelFormat)(System API)](#oh_decodingoptionsforpicture_setdesiredpixelformat) | Set pixelFormat number for DecodingOptionsForPicture struct.**System API:** This is a system API. |
| [Image_ErrorCode OH_ImageSourceNative_ReadImageMetadataByType(OH_ImageSourceNative *source, uint32_t index, Image_MetadataType *metadataTypes, size_t typeCount, OH_PictureMetadata **outMetadataArray, size_t *metadataCount)(System API)](#oh_imagesourcenative_readimagemetadatabytype) | Read metadata of the image source, use metadatatype to specify metadata of interest. If metadataType is not specified, all supported metadata will be returned.**System API:** This is a system API. |

## Enum type description

### OH_ImageSource_SVGResourceLimitLevel

```c
enum OH_ImageSource_SVGResourceLimitLevel
```

**Description**

Indicates the enumeration of SVG resource restriction levels. Higher levels allow fewer resources to be used when parsing and rendering SVG images. System resource limits are enforced regardless of the level specified.

**Since**: 26.1.0

**System API:** This is a system API.

| Enum item | Description |
| -- | -- |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_NONE = 0 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_LOW = 1 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_MEDIUM = 2 |  |
| OH_IMAGESOURCE_SVG_RESOURCE_LIMIT_LEVEL_HIGH = 3 |  |


## Function description

### OH_ImageSourceNative_SetSvgResourceLimitLevel()

```c
Image_ErrorCode OH_ImageSourceNative_SetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel level)
```

**Description**

Sets the SVG resource limit level for the image source. This only takes effect for SVG format images. For non-SVG images, this function has no effect. Must be called before [OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap) to ensure the limit takes effect on both DOM parsing and rendering stages.

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Indicates a pointer to the image source. |
| [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel) level | Indicates the SVG resource limit level. For details, see [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION} if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} source is nullptr.</li>          </ul> |

### OH_ImageSourceNative_GetSvgResourceLimitLevel()

```c
Image_ErrorCode OH_ImageSourceNative_GetSvgResourceLimitLevel(OH_ImageSourceNative *source, OH_ImageSource_SVGResourceLimitLevel *level)
```

**Description**

Gets the SVG resource limit level of the image source.

**Since**: 26.1.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Indicates a pointer to the image source. |
| [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel) *level | Indicates the pointer to receive the SVG resource limit level. For details, see [OH_ImageSource_SVGResourceLimitLevel](capi-image-source-native-h.md#oh_imagesource_svgresourcelimitlevel). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION} if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} source or level is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool *needsDecodeDfxData)
```

**Description**

Obtains the **needsDecodeDfxData** parameter in the decoding options.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to an OH_DecodingOptionsForPicture object. |
| bool *needsDecodeDfxData | Whether to decode image DFX data. The values include **true** (yes) and **false** (no). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options or needsDecodeDfxData is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetNeedsDecodeDfxData(OH_DecodingOptionsForPicture *options, bool needsDecodeDfxData)
```

**Description**

Sets the **needsDecodeDfxData** parameter in the decoding options.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to an OH_DecodingOptionsForPicture object. |
| bool needsDecodeDfxData | Whether to decode image DFX data. The values include **true** (yes) and **false** (no). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size *desiredSizeForMainPixelmap)
```

**Description**

Gets the desiredSizeForMainPixelMap number for DecodingOptionsForPicture struct.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | The OH_DecodingOptionsForPicture pointer will be operated. |
| Image_Size *desiredSizeForMainPixelmap | On output, the number of main pixelMap desiredSize. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredSizeForMainPixelmap(OH_DecodingOptionsForPicture *options, Image_Size desiredSizeForMainPixelmap)
```

**Description**

Sets the desiredSizeForMainPixelMap number for DecodingOptionsForPicture struct.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | The OH_DecodingOptionsForPicture pointer will be operated. |
| Image_Size desiredSizeForMainPixelmap | the number of main pixelMap desiredSize. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT *desiredPixelFormat)
```

**Description**

Get pixelFormat number for DecodingOptionsForPicture struct.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | The OH_DecodingOptionsForPicture pointer will be operated. |
| PIXEL_FORMAT *desiredPixelFormat | the number of image pixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options is nullptr.</li>          </ul> |

### OH_DecodingOptionsForPicture_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredPixelFormat(OH_DecodingOptionsForPicture *options, PIXEL_FORMAT desiredPixelFormat)
```

**Description**

Set pixelFormat number for DecodingOptionsForPicture struct.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | The OH_DecodingOptionsForPicture pointer will be operated. |
| PIXEL_FORMAT desiredPixelFormat | Image pixel format. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} options is nullptr.</li>          </ul> |

### OH_ImageSourceNative_ReadImageMetadataByType()

```c
Image_ErrorCode OH_ImageSourceNative_ReadImageMetadataByType(OH_ImageSourceNative *source, uint32_t index, Image_MetadataType *metadataTypes, size_t typeCount, OH_PictureMetadata **outMetadataArray, size_t *metadataCount)
```

**Description**

Read metadata of the image source, use metadatatype to specify metadata of interest. If metadataType is not specified, all supported metadata will be returned.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to the image source. |
| uint32_t index | Image index. |
| Image_MetadataType *metadataTypes | Metadata types of interest. |
| size_t typeCount | Count of metadataTypes. |
| OH_PictureMetadata **outMetadataArray | Output parameter used to receive a metadata array allocated by this function. The caller is required to release this object. |
| size_t *metadataCount | Number of OH_PictureMetadata elements returned in outMetadataArray. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link IMAGE_SOURCE_INVALID_PARAMETER} if source, outMetadataArray or metadataCount is nullptr.</li><br>        <li>{@link IMAGE_SOURCE_UNSUPPORTED_METADATA} if metadata doesn't exist, or types are unsupported.</li><br>        <li>{@link IMAGE_SOURCE_ALLOC_FAILED} memory allocation failed.</li>          </ul> |


