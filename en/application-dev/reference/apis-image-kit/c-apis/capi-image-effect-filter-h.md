# image_effect_filter.h

## Overview

Declares the functions for setting filter parameters, registering custom filter and filter lookup information.

**Library**: libimage_effect.so

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Related module**: [ImageEffect](capi-imageeffect.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) | OH_EffectFilter | Define the new type name OH_EffectFilter for struct OH_EffectFilter |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) | OH_EffectFilterInfo | Define the new type name OH_EffectFilterInfo for struct OH_EffectFilterInfo |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) | OH_EffectBufferInfo | Define the new type name OH_EffectBufferInfo for struct OH_EffectBufferInfo |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ImageEffect_DataType](#imageeffect_datatype) | ImageEffect_DataType | Enumerates the data type |
| [ImageEffect_Format](#imageeffect_format) | ImageEffect_Format | Enumerates the pixel format type |
| [ImageEffect_BufferType](#imageeffect_buffertype) | ImageEffect_BufferType | Enumerates the effect buffer type |

### Macro

| Name | Description |
| -- | -- |
| OH_EFFECT_BRIGHTNESS_FILTER "Brightness" | Define the brightness filter name that contain the parameter matched with the key refer to OH_EFFECT_FILTER_INTENSITY_KEY and the value refer to {@link ImageEffect_Any} that contain the data type of [EFFECT_DATA_TYPE_FLOAT](capi-image-effect-filter-h.md#imageeffect_datatype)<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| OH_EFFECT_CONTRAST_FILTER "Contrast" | Define the contrast filter name that contain the parameter matched with the key refer to OH_EFFECT_FILTER_INTENSITY_KEY and the value refer to {@link ImageEffect_Any} that contain the data type of [EFFECT_DATA_TYPE_FLOAT](capi-image-effect-filter-h.md#imageeffect_datatype)<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| OH_EFFECT_CROP_FILTER "Crop" | Define the crop filter name that contain the parameter matched with the key refer to OH_EFFECT_FILTER_REGION_KEY and the value refer to {@link ImageEffect_Any} that contain the data type of<br>[EFFECT_DATA_TYPE_PTR](capi-image-effect-filter-h.md#imageeffect_datatype) for {@link ImageEffect_Region}<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| OH_EFFECT_FILTER_INTENSITY_KEY "FilterIntensity" | Define the key that means intensity<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| OH_EFFECT_FILTER_REGION_KEY "FilterRegion" | Define the key that means region and matches the value ref to {@link ImageEffect_Any} contain the data type of<br>[EFFECT_DATA_TYPE_PTR](capi-image-effect-filter-h.md#imageeffect_datatype) for {@link ImageEffect_Region}<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_EffectFilterInfo *OH_EffectFilterInfo_Create()](#oh_effectfilterinfo_create) | - | Create an OH_EffectFilterInfo instance. It should be noted that the life cycle of the OH_EffectFilterInfo instance pointed to by the return value * needs to be manually released by [OH_EffectFilterInfo_Release](capi-image-effect-filter-h.md#oh_effectfilterinfo_release) |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_SetFilterName(OH_EffectFilterInfo *info, const char *name)](#oh_effectfilterinfo_setfiltername) | - | Set the filter name for OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_GetFilterName(OH_EffectFilterInfo *info, char **name)](#oh_effectfilterinfo_getfiltername) | - | Get the filter name from OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_SetSupportedBufferTypes(OH_EffectFilterInfo *info, uint32_t size, ImageEffect_BufferType *bufferTypeArray)](#oh_effectfilterinfo_setsupportedbuffertypes) | - | Set the supported buffer types for OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_GetSupportedBufferTypes(OH_EffectFilterInfo *info, uint32_t *size, ImageEffect_BufferType **bufferTypeArray)](#oh_effectfilterinfo_getsupportedbuffertypes) | - | Get the supported buffer types from OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_SetSupportedFormats(OH_EffectFilterInfo *info, uint32_t size, ImageEffect_Format *formatArray)](#oh_effectfilterinfo_setsupportedformats) | - | Set the supported formats for OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_GetSupportedFormats(OH_EffectFilterInfo *info, uint32_t *size, ImageEffect_Format **formatArray)](#oh_effectfilterinfo_getsupportedformats) | - | Get the supported formats from OH_EffectFilterInfo structure |
| [ImageEffect_ErrorCode OH_EffectFilterInfo_Release(OH_EffectFilterInfo *info)](#oh_effectfilterinfo_release) | - | Clear the internal resources of the OH_EffectFilterInfo and destroy the OH_EffectFilterInfo instance |
| [OH_EffectBufferInfo *OH_EffectBufferInfo_Create()](#oh_effectbufferinfo_create) | - | Create an OH_EffectBufferInfo instance. It should be noted that the life cycle of the OH_EffectBufferInfo instance pointed to by the return value * needs to be manually released by [OH_EffectBufferInfo_Release](capi-image-effect-filter-h.md#oh_effectbufferinfo_release) |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetAddr(OH_EffectBufferInfo *info, void *addr)](#oh_effectbufferinfo_setaddr) | - | Set access to the address of the image in memory |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetAddr(OH_EffectBufferInfo *info, void **addr)](#oh_effectbufferinfo_getaddr) | - | Provide direct access to the address of the image in memory for rendering the filter effects |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetWidth(OH_EffectBufferInfo *info, int32_t width)](#oh_effectbufferinfo_setwidth) | - | Set the width of the image in pixels |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetWidth(OH_EffectBufferInfo *info, int32_t *width)](#oh_effectbufferinfo_getwidth) | - | Get the width of the image in pixels |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetHeight(OH_EffectBufferInfo *info, int32_t height)](#oh_effectbufferinfo_setheight) | - | Set the height of the image in pixels |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetHeight(OH_EffectBufferInfo *info, int32_t *height)](#oh_effectbufferinfo_getheight) | - | Get the height of the image in pixels |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetRowSize(OH_EffectBufferInfo *info, int32_t rowSize)](#oh_effectbufferinfo_setrowsize) | - | Set number of bytes per row for the image |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetRowSize(OH_EffectBufferInfo *info, int32_t *rowSize)](#oh_effectbufferinfo_getrowsize) | - | Get number of bytes per row for the image |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetEffectFormat(OH_EffectBufferInfo *info, ImageEffect_Format format)](#oh_effectbufferinfo_seteffectformat) | - | Set the format of the image for OH_EffectBufferInfo |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetEffectFormat(OH_EffectBufferInfo *info, ImageEffect_Format *format)](#oh_effectbufferinfo_geteffectformat) | - | Get the format of the image from OH_EffectBufferInfo |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetTimestamp(OH_EffectBufferInfo *info, int64_t timestamp)](#oh_effectbufferinfo_settimestamp) | - | Set the timestamp of the image for OH_EffectBufferInfo |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetTimestamp(OH_EffectBufferInfo *info, int64_t *timestamp)](#oh_effectbufferinfo_gettimestamp) | - | Get the timestamp of the image from OH_EffectBufferInfo |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_SetTextureId(OH_EffectBufferInfo *info, int32_t textureId)](#oh_effectbufferinfo_settextureid) | - | Sets the texture ID of the image for an OH_EffectBufferInfo struct. |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_GetTextureId(OH_EffectBufferInfo *info, int32_t *textureId)](#oh_effectbufferinfo_gettextureid) | - | Obtains the texture ID of an image from an OH_EffectBufferInfo struct. |
| [ImageEffect_ErrorCode OH_EffectBufferInfo_Release(OH_EffectBufferInfo *info)](#oh_effectbufferinfo_release) | - | Clear the internal resources of the OH_EffectBufferInfo and destroy the OH_EffectBufferInfo instance |
| [typedef bool (\*OH_EffectFilterDelegate_SetValue)(OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value)](#oh_effectfilterdelegate_setvalue) | OH_EffectFilterDelegate_SetValue | When executing the method of [OH_EffectFilter_SetValue](capi-image-effect-filter-h.md#oh_effectfilter_setvalue) for the delegate filter, the function pointer will be called for checking the parameters is valid for the delegate filter |
| [typedef void (\*OH_EffectFilterDelegate_PushData)(OH_EffectFilter *filter, OH_EffectBufferInfo *info)](#oh_effectfilterdelegate_pushdata) | OH_EffectFilterDelegate_PushData | Actively execute this callback function at the end of invoking the method of [OH_EffectFilterDelegate_Render](capi-image-effect-filter-h.md#oh_effectfilterdelegate_render) for passing possible new OH_EffectBufferInfo to the next filter. It should be noted that when passing new OH_EffectBufferInfo, the buffer in OH_EffectBufferInfo needs to be manually released after the execution of the function ends |
| [typedef bool (\*OH_EffectFilterDelegate_Render)(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)](#oh_effectfilterdelegate_render) | OH_EffectFilterDelegate_Render | When the method of OH_ImageEffect_Start is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for rendering the delegate filter effects |
| [typedef bool (\*OH_EffectFilterDelegate_Save)(OH_EffectFilter *filter, char **info)](#oh_effectfilterdelegate_save) | OH_EffectFilterDelegate_Save | When the method of OH_ImageEffect_Save is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for serializing the delegate filter parameters |
| [typedef OH_EffectFilter *(\*OH_EffectFilterDelegate_Restore)(const char *info)](#oh_effectfilterdelegate_restore) | OH_EffectFilterDelegate_Restore | When the method of OH_ImageEffect_Restore is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for deserializing the delegate filter parameters |
| [OH_EffectFilter *OH_EffectFilter_Create(const char *name)](#oh_effectfilter_create) | - | Create an OH_EffectFilter instance. It should be noted that the life cycle of the OH_EffectFilter instance pointed to by the return value * needs to be manually released by [OH_EffectFilter_Release](capi-image-effect-filter-h.md#oh_effectfilter_release) |
| [ImageEffect_ErrorCode OH_EffectFilter_SetValue(OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value)](#oh_effectfilter_setvalue) | - | Set the filter parameter. It can be set multiple parameters by invoking this function multiple times |
| [ImageEffect_ErrorCode OH_EffectFilter_GetValue(OH_EffectFilter *filter, const char *key, ImageEffect_Any *value)](#oh_effectfilter_getvalue) | - | Get the filter parameter |
| [ImageEffect_ErrorCode OH_EffectFilter_Register(const OH_EffectFilterInfo *info, const ImageEffect_FilterDelegate *delegate)](#oh_effectfilter_register) | - | Register the delegate filter |
| [ImageEffect_FilterNames *OH_EffectFilter_LookupFilters(const char *key)](#oh_effectfilter_lookupfilters) | - | Lookup for the filter names that matches the lookup condition. It should be noted that the allocated memory of ImageEffect_FilterNames can be manually released by invoking [OH_EffectFilter_ReleaseFilterNames](capi-image-effect-filter-h.md#oh_effectfilter_releasefilternames) if need |
| [void OH_EffectFilter_ReleaseFilterNames()](#oh_effectfilter_releasefilternames) | - | Clear the internal cached resources of the ImageEffect_FilterNames |
| [ImageEffect_ErrorCode OH_EffectFilter_LookupFilterInfo(const char *name, OH_EffectFilterInfo *info)](#oh_effectfilter_lookupfilterinfo) | - | Lookup for the capabilities that supported by the filter |
| [ImageEffect_ErrorCode OH_EffectFilter_Render(OH_EffectFilter *filter, OH_PixelmapNative *inputPixelmap, OH_PixelmapNative *outputPixelmap)](#oh_effectfilter_render) | - | Render the filter effects. The function is designed to support the same input and output image |
| [ImageEffect_ErrorCode OH_EffectFilter_RenderWithTextureId(OH_EffectFilter *filter, int32_t inputTextureId, int32_t outputTextureId, int32_t colorSpace)](#oh_effectfilter_renderwithtextureid) | - | Applies the filter effect using texture IDs. This function does not support using the same texture for for both input and output. |
| [ImageEffect_ErrorCode OH_EffectFilter_Release(OH_EffectFilter *filter)](#oh_effectfilter_release) | - | Clear the internal resources of the OH_EffectFilter and destroy the OH_EffectFilter instance |

### Variable

| Name | Description |
| -- | -- |
| bool (*OH_EffectFilterDelegate_SetValue)(OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value) | When executing the method of [OH_EffectFilter_SetValue](capi-image-effect-filter-h.md#oh_effectfilter_setvalue) for the delegate filter, the function pointer will be called for checking the parameters is valid for the delegate filter<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| void (*OH_EffectFilterDelegate_PushData)(OH_EffectFilter *filter, OH_EffectBufferInfo *info) | Actively execute this callback function at the end of invoking the method of [OH_EffectFilterDelegate_Render](capi-image-effect-filter-h.md#oh_effectfilterdelegate_render) for passing possible new OH_EffectBufferInfo to the next filter. It should be noted that when passing new OH_EffectBufferInfo, the buffer in OH_EffectBufferInfo needs to be manually released after the execution of the function ends<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| bool (*OH_EffectFilterDelegate_Render)(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData) | When the method of OH_ImageEffect_Start is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for rendering the delegate filter effects<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| bool (*OH_EffectFilterDelegate_Save)(OH_EffectFilter *filter, char **info) | When the method of OH_ImageEffect_Save is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for serializing the delegate filter parameters<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |
| OH_EffectFilter *(*OH_EffectFilterDelegate_Restore)(const char *info) | When the method of OH_ImageEffect_Restore is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for deserializing the delegate filter parameters<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.ImageEffect.Core |

## Enum type description

### ImageEffect_DataType

```c
enum ImageEffect_DataType
```

**Description**

Enumerates the data type

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_DATA_TYPE_UNKNOWN = 0 | unknown data type |
| EFFECT_DATA_TYPE_INT32 = 1 | int32_t data type |
| EFFECT_DATA_TYPE_FLOAT = 2 | float data type |
| EFFECT_DATA_TYPE_DOUBLE = 3 | double data type |
| EFFECT_DATA_TYPE_CHAR = 4 | char data type |
| EFFECT_DATA_TYPE_LONG = 5 | long data type |
| EFFECT_DATA_TYPE_BOOL = 6 | bool data type |
| EFFECT_DATA_TYPE_PTR = 7 | point data type |

### ImageEffect_Format

```c
enum ImageEffect_Format
```

**Description**

Enumerates the pixel format type

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_PIXEL_FORMAT_UNKNOWN = 0 | Unknown pixel format |
| EFFECT_PIXEL_FORMAT_RGBA8888 = 1 | RGBA8888 pixel format |
| EFFECT_PIXEL_FORMAT_NV21 = 2 | NV21 pixel format |
| EFFECT_PIXEL_FORMAT_NV12 = 3 | NV12 pixel format |
| EFFECT_PIXEL_FORMAT_RGBA1010102 = 4 | RGBA 10bit pixel format |
| EFFECT_PIXEL_FORMAT_YCBCR_P010 = 5 | YCBCR420 semi-planar 10bit pixel format |
| EFFECT_PIXEL_FORMAT_YCRCB_P010 = 6 | YCRCB420 semi-planar 10bit pixel format |

### ImageEffect_BufferType

```c
enum ImageEffect_BufferType
```

**Description**

Enumerates the effect buffer type

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_BUFFER_TYPE_UNKNOWN = 0 | Unknown buffer type |
| EFFECT_BUFFER_TYPE_PIXEL = 1 | Pixel buffer type |
| EFFECT_BUFFER_TYPE_TEXTURE = 2 | Texture buffer type |


## Function description

### OH_EffectFilterInfo_Create()

```c
OH_EffectFilterInfo *OH_EffectFilterInfo_Create()
```

**Description**

Create an OH_EffectFilterInfo instance. It should be noted that the life cycle of the OH_EffectFilterInfo instance pointed to by the return value * needs to be manually released by [OH_EffectFilterInfo_Release](capi-image-effect-filter-h.md#oh_effectfilterinfo_release)

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_EffectFilterInfo *](capi-imageeffect-oh-effectfilterinfo.md) | Returns a pointer to an OH_EffectFilterInfo instance if the execution is successful, otherwise returns  nullptr |

### OH_EffectFilterInfo_SetFilterName()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_SetFilterName(OH_EffectFilterInfo *info, const char *name)
```

**Description**

Set the filter name for OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| const char *name | Indicates the filter name |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_GetFilterName()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_GetFilterName(OH_EffectFilterInfo *info, char **name)
```

**Description**

Get the filter name from OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| char **name | Indicates the filter name |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_SetSupportedBufferTypes()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_SetSupportedBufferTypes(OH_EffectFilterInfo *info, uint32_t size, ImageEffect_BufferType *bufferTypeArray)
```

**Description**

Set the supported buffer types for OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| uint32_t size | The size of [ImageEffect_BufferType](capi-image-effect-filter-h.md#imageeffect_buffertype) that can be supported |
| [ImageEffect_BufferType](capi-image-effect-filter-h.md#imageeffect_buffertype) *bufferTypeArray | Array of [ImageEffect_BufferType](capi-image-effect-filter-h.md#imageeffect_buffertype) that can be supported |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_GetSupportedBufferTypes()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_GetSupportedBufferTypes(OH_EffectFilterInfo *info, uint32_t *size, ImageEffect_BufferType **bufferTypeArray)
```

**Description**

Get the supported buffer types from OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| uint32_t *size | The size of {@link OH_EffectBufferInfoType} that can be supported |
| [ImageEffect_BufferType](capi-image-effect-filter-h.md#imageeffect_buffertype) **bufferTypeArray | Array of {@link OH_EffectBufferInfoType} that can be supported |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_SetSupportedFormats()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_SetSupportedFormats(OH_EffectFilterInfo *info, uint32_t size, ImageEffect_Format *formatArray)
```

**Description**

Set the supported formats for OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| uint32_t size | The size of [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) that can be supported |
| [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) *formatArray | Array of [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) that can be supported |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_GetSupportedFormats()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_GetSupportedFormats(OH_EffectFilterInfo *info, uint32_t *size, ImageEffect_Format **formatArray)
```

**Description**

Get the supported formats from OH_EffectFilterInfo structure

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |
| uint32_t *size | The size of [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) that can be supported |
| [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) **formatArray | Array of [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) that can be supported |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterInfo_Release()

```c
ImageEffect_ErrorCode OH_EffectFilterInfo_Release(OH_EffectFilterInfo *info)
```

**Description**

Clear the internal resources of the OH_EffectFilterInfo and destroy the OH_EffectFilterInfo instance

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Encapsulate OH_EffectFilterInfo structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_Create()

```c
OH_EffectBufferInfo *OH_EffectBufferInfo_Create()
```

**Description**

Create an OH_EffectBufferInfo instance. It should be noted that the life cycle of the OH_EffectBufferInfo instance pointed to by the return value * needs to be manually released by [OH_EffectBufferInfo_Release](capi-image-effect-filter-h.md#oh_effectbufferinfo_release)

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_EffectBufferInfo *](capi-imageeffect-oh-effectbufferinfo.md) | Returns a pointer to an OH_EffectBufferInfo instance if the execution is successful, otherwise returns  nullptr |

### OH_EffectBufferInfo_SetAddr()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetAddr(OH_EffectBufferInfo *info, void *addr)
```

**Description**

Set access to the address of the image in memory

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| void *addr | Indicates the address of the image in memory |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetAddr()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetAddr(OH_EffectBufferInfo *info, void **addr)
```

**Description**

Provide direct access to the address of the image in memory for rendering the filter effects

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| void **addr | Indicates the address of the image in memory |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetWidth()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetWidth(OH_EffectBufferInfo *info, int32_t width)
```

**Description**

Set the width of the image in pixels

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t width | Indicates the width of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetWidth()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetWidth(OH_EffectBufferInfo *info, int32_t *width)
```

**Description**

Get the width of the image in pixels

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t *width | Indicates the width of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetHeight()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetHeight(OH_EffectBufferInfo *info, int32_t height)
```

**Description**

Set the height of the image in pixels

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t height | Indicates the height of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetHeight()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetHeight(OH_EffectBufferInfo *info, int32_t *height)
```

**Description**

Get the height of the image in pixels

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t *height | Indicates the height of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetRowSize()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetRowSize(OH_EffectBufferInfo *info, int32_t rowSize)
```

**Description**

Set number of bytes per row for the image

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t rowSize | Indicates number of bytes per row |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetRowSize()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetRowSize(OH_EffectBufferInfo *info, int32_t *rowSize)
```

**Description**

Get number of bytes per row for the image

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int32_t *rowSize | Indicates number of bytes per row |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetEffectFormat()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetEffectFormat(OH_EffectBufferInfo *info, ImageEffect_Format format)
```

**Description**

Set the format of the image for OH_EffectBufferInfo

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) format | Indicates [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetEffectFormat()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetEffectFormat(OH_EffectBufferInfo *info, ImageEffect_Format *format)
```

**Description**

Get the format of the image from OH_EffectBufferInfo

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) *format | Indicates [ImageEffect_Format](capi-image-effect-filter-h.md#imageeffect_format) of the image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetTimestamp()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetTimestamp(OH_EffectBufferInfo *info, int64_t timestamp)
```

**Description**

Set the timestamp of the image for OH_EffectBufferInfo

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int64_t timestamp | Indicates the timestamp of the image frame data for the OHNativeWindow input type. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_GetTimestamp()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetTimestamp(OH_EffectBufferInfo *info, int64_t *timestamp)
```

**Description**

Get the timestamp of the image from OH_EffectBufferInfo

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |
| int64_t *timestamp | Indicates the timestamp of the image frame data for the OHNativeWindow input type. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectBufferInfo_SetTextureId()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_SetTextureId(OH_EffectBufferInfo *info, int32_t textureId)
```

**Description**

Sets the texture ID of the image for an OH_EffectBufferInfo struct.

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Pointer to an instance of the OH_EffectBufferInfo struct. |
| int32_t textureId | Pointer to the texture ID of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the operation is successful; returns EFFECT_ERROR_PARAM_INVALID if the  parameter parameter is missing. |

### OH_EffectBufferInfo_GetTextureId()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_GetTextureId(OH_EffectBufferInfo *info, int32_t *textureId)
```

**Description**

Obtains the texture ID of an image from an OH_EffectBufferInfo struct.

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Pointer to an instance of the OH_EffectBufferInfo struct. |
| int32_t *textureId | Texture ID of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the operation is successful; returns EFFECT_ERROR_PARAM_INVALID if the  parameter parameter is missing. |

### OH_EffectBufferInfo_Release()

```c
ImageEffect_ErrorCode OH_EffectBufferInfo_Release(OH_EffectBufferInfo *info)
```

**Description**

Clear the internal resources of the OH_EffectBufferInfo and destroy the OH_EffectBufferInfo instance

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) *info | Encapsulate OH_EffectBufferInfo structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilterDelegate_SetValue()

```c
typedef bool (*OH_EffectFilterDelegate_SetValue)(OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value)
```

**Description**

When executing the method of [OH_EffectFilter_SetValue](capi-image-effect-filter-h.md#oh_effectfilter_setvalue) for the delegate filter, the function pointer will be called for checking the parameters is valid for the delegate filter

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) \*filter | Encapsulate OH_EffectFilter structure instance pointer |
| const char \*key | Indicates the key of the filter |
| const ImageEffect_Any \*value | Indicates the value corresponding to the key of the filter |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the parameter is valid, otherwise returns false |

### OH_EffectFilterDelegate_PushData()

```c
typedef void (*OH_EffectFilterDelegate_PushData)(OH_EffectFilter *filter, OH_EffectBufferInfo *info)
```

**Description**

Actively execute this callback function at the end of invoking the method of [OH_EffectFilterDelegate_Render](capi-image-effect-filter-h.md#oh_effectfilterdelegate_render) for passing possible new OH_EffectBufferInfo to the next filter. It should be noted that when passing new OH_EffectBufferInfo, the buffer in OH_EffectBufferInfo needs to be manually released after the execution of the function ends

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) \*filter | Encapsulate OH_EffectFilter structure instance pointer |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) \*info | Indicates the information of the image, such as width, height, etc. See [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) |

### OH_EffectFilterDelegate_Render()

```c
typedef bool (*OH_EffectFilterDelegate_Render)(OH_EffectFilter *filter, OH_EffectBufferInfo *info, OH_EffectFilterDelegate_PushData pushData)
```

**Description**

When the method of OH_ImageEffect_Start is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for rendering the delegate filter effects

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) \*filter | Encapsulate OH_EffectFilter structure instance pointer |
| [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) \*info | Indicates the information of the image, such as width, height, etc. See [OH_EffectBufferInfo](capi-imageeffect-oh-effectbufferinfo.md) |
| [OH_EffectFilterDelegate_PushData](capi-image-effect-filter-h.md#oh_effectfilterdelegate_pushdata) pushData | Indicates the callback function for passing possible new OH_EffectBufferInfo to the next filter. See [OH_EffectFilterDelegate_PushData](capi-image-effect-filter-h.md#oh_effectfilterdelegate_pushdata) |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if this function point is executed successfully, otherwise returns false |

### OH_EffectFilterDelegate_Save()

```c
typedef bool (*OH_EffectFilterDelegate_Save)(OH_EffectFilter *filter, char **info)
```

**Description**

When the method of OH_ImageEffect_Save is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for serializing the delegate filter parameters

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) \*filter | Encapsulate OH_EffectFilter structure instance pointer |
| char \*\*info | Indicates the serialized information that is obtained by converting the delegate filter parameters to JSON string |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if this function point is executed successfully, otherwise returns false |

### OH_EffectFilterDelegate_Restore()

```c
typedef OH_EffectFilter *(*OH_EffectFilterDelegate_Restore)(const char *info)
```

**Description**

When the method of OH_ImageEffect_Restore is executed on delegate filter that is contained in OH_ImageEffect, the function pointer will be called for deserializing the delegate filter parameters

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char \*info | Indicates the serialized information that is obtained by converting the delegate filter parameters to JSON string |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_EffectFilter *](capi-imageeffect-oh-effectfilter.md) | Returns a pointer to an OH_EffectFilter instance if the execution is successful, otherwise returns nullptr |

### OH_EffectFilter_Create()

```c
OH_EffectFilter *OH_EffectFilter_Create(const char *name)
```

**Description**

Create an OH_EffectFilter instance. It should be noted that the life cycle of the OH_EffectFilter instance pointed to by the return value * needs to be manually released by [OH_EffectFilter_Release](capi-image-effect-filter-h.md#oh_effectfilter_release)

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Indicates the filter name. For example, see {@link OH_EFFECT_BRIGHTNESS_FILTER} |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_EffectFilter *](capi-imageeffect-oh-effectfilter.md) | Returns a pointer to an OH_EffectFilter instance if the execution is successful, otherwise returns nullptr |

### OH_EffectFilter_SetValue()

```c
ImageEffect_ErrorCode OH_EffectFilter_SetValue(OH_EffectFilter *filter, const char *key, const ImageEffect_Any *value)
```

**Description**

Set the filter parameter. It can be set multiple parameters by invoking this function multiple times

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | Encapsulate OH_EffectFilter structure instance pointer |
| const char *key | Indicates the key of the filter. For example, see {@link OH_EFFECT_FILTER_INTENSITY_KEY} |
| const ImageEffect_Any *value | Indicates the value corresponding to the key of the filter |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer.<br>{@link EFFECT_KEY_ERROR}, the key of the filter parameter is invalid.<br>{@link EFFECT_PARAM_ERROR}, the value of the filter parameter is invalid. |

### OH_EffectFilter_GetValue()

```c
ImageEffect_ErrorCode OH_EffectFilter_GetValue(OH_EffectFilter *filter, const char *key, ImageEffect_Any *value)
```

**Description**

Get the filter parameter

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | Encapsulate OH_EffectFilter structure instance pointer |
| const char *key | Indicates the key of the filter |
| ImageEffect_Any *value | Indicates the value corresponding to the key of the filter |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer.<br>{@link EFFECT_KEY_ERROR}, the key of the filter parameter is invalid. |

### OH_EffectFilter_Register()

```c
ImageEffect_ErrorCode OH_EffectFilter_Register(const OH_EffectFilterInfo *info, const ImageEffect_FilterDelegate *delegate)
```

**Description**

Register the delegate filter

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Indicates the capabilities supported by delegate filter, see [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) |
| const ImageEffect_FilterDelegate *delegate | A collection of all callback functions, see {@link ImageEffect_FilterDelegate} |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilter_LookupFilters()

```c
ImageEffect_FilterNames *OH_EffectFilter_LookupFilters(const char *key)
```

**Description**

Lookup for the filter names that matches the lookup condition. It should be noted that the allocated memory of ImageEffect_FilterNames can be manually released by invoking [OH_EffectFilter_ReleaseFilterNames](capi-image-effect-filter-h.md#oh_effectfilter_releasefilternames) if need

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *key | Indicates the lookup condition |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_FilterNames * | Returns Filter name array that matches the key, see {@link ImageEffect_FilterNames} |

### OH_EffectFilter_ReleaseFilterNames()

```c
void OH_EffectFilter_ReleaseFilterNames()
```

**Description**

Clear the internal cached resources of the ImageEffect_FilterNames

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

### OH_EffectFilter_LookupFilterInfo()

```c
ImageEffect_ErrorCode OH_EffectFilter_LookupFilterInfo(const char *name, OH_EffectFilterInfo *info)
```

**Description**

Lookup for the capabilities that supported by the filter

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | Indicates the filter name |
| [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) *info | Indicates the capabilities supported by the filter, see [OH_EffectFilterInfo](capi-imageeffect-oh-effectfilterinfo.md) |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilter_Render()

```c
ImageEffect_ErrorCode OH_EffectFilter_Render(OH_EffectFilter *filter, OH_PixelmapNative *inputPixelmap, OH_PixelmapNative *outputPixelmap)
```

**Description**

Render the filter effects. The function is designed to support the same input and output image

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | Encapsulate OH_EffectFilter structure instance pointer |
| OH_PixelmapNative *inputPixelmap | Indicates the input image |
| OH_PixelmapNative *outputPixelmap | Indicates the output image |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_EffectFilter_RenderWithTextureId()

```c
ImageEffect_ErrorCode OH_EffectFilter_RenderWithTextureId(OH_EffectFilter *filter, int32_t inputTextureId, int32_t outputTextureId, int32_t colorSpace)
```

**Description**

Applies the filter effect using texture IDs. This function does not support using the same texture for for both input and output.

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | Pointer to an instance of the OH_EffectFilter struct. |
| int32_t inputTextureId | ID of the input texture. This ID must be valid and bound to a texture of the GL_TEXTURE_2D GL_TEXTURE_2D type. |
| int32_t outputTextureId | ID of the output texture. This ID must be valid. If it is not bound to a texture, it will will automatically be bound to a GL_TEXTURE_2D type. If the texture is already bound and the size is inappropriate, inappropriate, the rendered result may be cropped or partially filled into this texture. |
| int32_t colorSpace | Color space of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the operation is successful; returns EFFECT_ERROR_PARAM_INVALID if the  parameter parameter is missing. |

### OH_EffectFilter_Release()

```c
ImageEffect_ErrorCode OH_EffectFilter_Release(OH_EffectFilter *filter)
```

**Description**

Clear the internal resources of the OH_EffectFilter and destroy the OH_EffectFilter instance

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_EffectFilter](capi-imageeffect-oh-effectfilter.md) *filter | Encapsulate OH_EffectFilter structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |


