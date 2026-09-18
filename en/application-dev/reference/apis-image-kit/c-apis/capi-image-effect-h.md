# image_effect.h

## Overview

Declares the functions for rendering image.

**Library**: libimage_effect.so

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Related module**: [ImageEffect](capi-imageeffect.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) | OH_ImageEffect | Define the new type name OH_ImageEffect for struct OH_ImageEffect |

### Function

| Name | Description |
| -- | -- |
| [OH_ImageEffect *OH_ImageEffect_Create(const char *name)](#oh_imageeffect_create) | Create an OH_ImageEffect instance. It should be noted that the life cycle of the OH_ImageEffect instance pointed to by the return value * needs to be manually released by [OH_ImageEffect_Release](capi-image-effect-h.md#oh_imageeffect_release) |
| [OH_EffectFilter *OH_ImageEffect_AddFilter(OH_ImageEffect *imageEffect, const char *filterName)](#oh_imageeffect_addfilter) | Create and add the OH_EffectFilter to the OH_ImageEffect |
| [ImageEffect_ErrorCode OH_ImageEffect_AddFilterByFilter(OH_ImageEffect *imageEffect, OH_EffectFilter *filter)](#oh_imageeffect_addfilterbyfilter) | Add the OH_EffectFilter to the OH_ImageEffect by the OH_EffectFilter instance pointer |
| [OH_EffectFilter *OH_ImageEffect_InsertFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)](#oh_imageeffect_insertfilter) | Create and add the OH_EffectFilter to the OH_ImageEffect by specified position |
| [ImageEffect_ErrorCode OH_ImageEffect_InsertFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, OH_EffectFilter *filter)](#oh_imageeffect_insertfilterbyfilter) | Insert the OH_EffectFilter to the OH_ImageEffect by the OH_EffectFilter instance pointer |
| [int32_t OH_ImageEffect_RemoveFilter(OH_ImageEffect *imageEffect, const char *filterName)](#oh_imageeffect_removefilter) | Remove all filters of the specified filter name |
| [ImageEffect_ErrorCode OH_ImageEffect_RemoveFilterByIndex(OH_ImageEffect *imageEffect, uint32_t index)](#oh_imageeffect_removefilterbyindex) | Remove the filter of the specified position |
| [OH_EffectFilter *OH_ImageEffect_ReplaceFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)](#oh_imageeffect_replacefilter) | Create and replace the OH_EffectFilter in the OH_ImageEffect by the filter name |
| [ImageEffect_ErrorCode OH_ImageEffect_ReplaceFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, OH_EffectFilter *filter)](#oh_imageeffect_replacefilterbyfilter) | Replace the OH_EffectFilter in the OH_ImageEffect by the OH_EffectFilter instance pointer |
| [int32_t OH_ImageEffect_GetFilterCount(OH_ImageEffect *imageEffect)](#oh_imageeffect_getfiltercount) | Get the number of the filters in OH_ImageEffect |
| [OH_EffectFilter *OH_ImageEffect_GetFilter(OH_ImageEffect *imageEffect, uint32_t index)](#oh_imageeffect_getfilter) | Get an OH_EffectFilter instance that add to OH_ImageEffect by the index |
| [ImageEffect_ErrorCode OH_ImageEffect_Configure(OH_ImageEffect *imageEffect, const char *key, const ImageEffect_Any *value)](#oh_imageeffect_configure) | Set configuration information to the OH_ImageEffect |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputSurface(OH_ImageEffect *imageEffect, OHNativeWindow *nativeWindow)](#oh_imageeffect_setoutputsurface) | Set the Surface to the image effect, this interface must be called before |
| [ImageEffect_ErrorCode OH_ImageEffect_GetInputSurface(OH_ImageEffect *imageEffect, OHNativeWindow **nativeWindow)](#oh_imageeffect_getinputsurface) | Get the input Surface from the image effect, this interface must be called after |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)](#oh_imageeffect_setinputpixelmap) | Set input pixelmap that contains the image information. It should be noted that the input pixel map will be directly rendered and modified if the output is not set |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)](#oh_imageeffect_setoutputpixelmap) | Set output pixelmap that contains the image information |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)](#oh_imageeffect_setinputnativebuffer) | Set input NativeBuffer that contains the image information. It should be noted that the input NativeBuffer will be directly rendered and modified if the output is not set |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)](#oh_imageeffect_setoutputnativebuffer) | Set output NativeBuffer that contains the image information |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputUri(OH_ImageEffect *imageEffect, const char *uri)](#oh_imageeffect_setinputuri) | Set input URI of the image. It should be noted that the image resource will be directly rendered and modified if the output is not set |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputUri(OH_ImageEffect *imageEffect, const char *uri)](#oh_imageeffect_setoutputuri) | Set output URI of the image |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)](#oh_imageeffect_setinputpicture) | Set input picture that contains the image information. It should be noted that the input picture will be directly rendered and modified if the output is not set |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)](#oh_imageeffect_setoutputpicture) | Set output picture that contains the image information |
| [ImageEffect_ErrorCode OH_ImageEffect_SetInputTextureId(OH_ImageEffect *imageEffect, int32_t textureId, int32_t colorSpace)](#oh_imageeffect_setinputtextureid) | Sets the ID of the input texture that contains the image information. |
| [ImageEffect_ErrorCode OH_ImageEffect_SetOutputTextureId(OH_ImageEffect *imageEffect, int32_t textureId)](#oh_imageeffect_setoutputtextureid) | Sets the ID of the output texture that contains the rendered image information. |
| [ImageEffect_ErrorCode OH_ImageEffect_Start(OH_ImageEffect *imageEffect)](#oh_imageeffect_start) | Render the filter effects that can be a single filter or a chain of filters |
| [ImageEffect_ErrorCode OH_ImageEffect_Stop(OH_ImageEffect *imageEffect)](#oh_imageeffect_stop) | Stop rendering the filter effects for next image frame data |
| [ImageEffect_ErrorCode OH_ImageEffect_Release(OH_ImageEffect *imageEffect)](#oh_imageeffect_release) | Clear the internal resources of the OH_ImageEffect and destroy the OH_ImageEffect instance |
| [ImageEffect_ErrorCode OH_ImageEffect_Save(OH_ImageEffect *imageEffect, char **info)](#oh_imageeffect_save) | Convert the OH_ImageEffect and the information of the filters in OH_ImageEffect to JSON string |
| [OH_ImageEffect *OH_ImageEffect_Restore(const char *info)](#oh_imageeffect_restore) | Create an OH_ImageEffect instance by deserializing the JSON string info |

## Function description

### OH_ImageEffect_Create()

```c
OH_ImageEffect *OH_ImageEffect_Create(const char *name)
```

**Description**

Create an OH_ImageEffect instance. It should be noted that the life cycle of the OH_ImageEffect instance pointed to by the return value * needs to be manually released by [OH_ImageEffect_Release](capi-image-effect-h.md#oh_imageeffect_release)

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | The name of image effect |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ImageEffect *](capi-imageeffect-oh-imageeffect.md) | Returns a pointer to an OH_ImageEffect instance if the execution is successful, otherwise returns nullptr |

### OH_ImageEffect_AddFilter()

```c
OH_EffectFilter *OH_ImageEffect_AddFilter(OH_ImageEffect *imageEffect, const char *filterName)
```

**Description**

Create and add the OH_EffectFilter to the OH_ImageEffect

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| const char *filterName | Indicates the name of the filter that can be customized by the developer or supported by the system |

**Returns**:

| Type | Description |
| -- | -- |
| OH_EffectFilter * | Returns a pointer to an OH_EffectFilter instance if the filter name is valid, otherwise returns nullptr |

### OH_ImageEffect_AddFilterByFilter()

```c
ImageEffect_ErrorCode OH_ImageEffect_AddFilterByFilter(OH_ImageEffect *imageEffect, OH_EffectFilter *filter)
```

**Description**

Add the OH_EffectFilter to the OH_ImageEffect by the OH_EffectFilter instance pointer

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_EffectFilter *filter | Indicates the filter instance that created by invoking OH_EffectFilter_Create |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer |

### OH_ImageEffect_InsertFilter()

```c
OH_EffectFilter *OH_ImageEffect_InsertFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)
```

**Description**

Create and add the OH_EffectFilter to the OH_ImageEffect by specified position

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter witch is created and added |
| const char *filterName | Indicates the name of the filter that can be customized by the developer or supported by the system |

**Returns**:

| Type | Description |
| -- | -- |
| OH_EffectFilter * | Returns a pointer to an OH_EffectFilter instance if the index and filter name is valid, otherwise returns  nullptr |

### OH_ImageEffect_InsertFilterByFilter()

```c
ImageEffect_ErrorCode OH_ImageEffect_InsertFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, OH_EffectFilter *filter)
```

**Description**

Insert the OH_EffectFilter to the OH_ImageEffect by the OH_EffectFilter instance pointer

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter witch is added |
| OH_EffectFilter *filter | Indicates the filter instance that created by invoking OH_EffectFilter_Create |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer or the index is invalid value |

### OH_ImageEffect_RemoveFilter()

```c
int32_t OH_ImageEffect_RemoveFilter(OH_ImageEffect *imageEffect, const char *filterName)
```

**Description**

Remove all filters of the specified filter name

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| const char *filterName | Indicates the name of the filter that can be customized by the developer or supported by the system |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the number of the filters that matches the specified filter name |

### OH_ImageEffect_RemoveFilterByIndex()

```c
ImageEffect_ErrorCode OH_ImageEffect_RemoveFilterByIndex(OH_ImageEffect *imageEffect, uint32_t index)
```

**Description**

Remove the filter of the specified position

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter witch is removed |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer or the index is invalid value |

### OH_ImageEffect_ReplaceFilter()

```c
OH_EffectFilter *OH_ImageEffect_ReplaceFilter(OH_ImageEffect *imageEffect, uint32_t index, const char *filterName)
```

**Description**

Create and replace the OH_EffectFilter in the OH_ImageEffect by the filter name

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter witch is created and replaced |
| const char *filterName | Indicates the name of the filter that can be customized by the developer or supported by the system |

**Returns**:

| Type | Description |
| -- | -- |
| OH_EffectFilter * | Returns a pointer to an OH_EffectFilter instance if the index and filter name is valid, otherwise returns  nullptr |

### OH_ImageEffect_ReplaceFilterByFilter()

```c
ImageEffect_ErrorCode OH_ImageEffect_ReplaceFilterByFilter(OH_ImageEffect *imageEffect, uint32_t index, OH_EffectFilter *filter)
```

**Description**

Replace the OH_EffectFilter in the OH_ImageEffect by the OH_EffectFilter instance pointer

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter witch is replaced |
| OH_EffectFilter *filter | Indicates the filter instance that created by invoking OH_EffectFilter_Create |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer or the index is invalid value |

### OH_ImageEffect_GetFilterCount()

```c
int32_t OH_ImageEffect_GetFilterCount(OH_ImageEffect *imageEffect)
```

**Description**

Get the number of the filters in OH_ImageEffect

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the number of the filters in OH_ImageEffect |

### OH_ImageEffect_GetFilter()

```c
OH_EffectFilter *OH_ImageEffect_GetFilter(OH_ImageEffect *imageEffect, uint32_t index)
```

**Description**

Get an OH_EffectFilter instance that add to OH_ImageEffect by the index

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| uint32_t index | Indicates the position of the OH_EffectFilter that add to OH_ImageEffect |

**Returns**:

| Type | Description |
| -- | -- |
| OH_EffectFilter * | Returns a pointer to an OH_EffectFilter instance if the index is valid, otherwise returns nullptr |

### OH_ImageEffect_Configure()

```c
ImageEffect_ErrorCode OH_ImageEffect_Configure(OH_ImageEffect *imageEffect, const char *key, const ImageEffect_Any *value)
```

**Description**

Set configuration information to the OH_ImageEffect

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| const char *key | Indicates the key of the configuration |
| const ImageEffect_Any *value | Indicates the value corresponding to the key of the configuration |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer.<br>{@link EFFECT_KEY_ERROR}, the key of the configuration parameter is invalid.<br>{@link EFFECT_PARAM_ERROR}, the value of the configuration parameter is invalid. |

### OH_ImageEffect_SetOutputSurface()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputSurface(OH_ImageEffect *imageEffect, OHNativeWindow *nativeWindow)
```

**Description**

Set the Surface to the image effect, this interface must be called before

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OHNativeWindow *nativeWindow | A pointer to a OHNativeWindow instance, see {@link OHNativeWindow} |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_GetInputSurface()

```c
ImageEffect_ErrorCode OH_ImageEffect_GetInputSurface(OH_ImageEffect *imageEffect, OHNativeWindow **nativeWindow)
```

**Description**

Get the input Surface from the image effect, this interface must be called after

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OHNativeWindow **nativeWindow | A pointer to a OHNativeWindow instance, see {@link OHNativeWindow} |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetInputPixelmap()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetInputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)
```

**Description**

Set input pixelmap that contains the image information. It should be noted that the input pixel map will be directly rendered and modified if the output is not set

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_PixelmapNative *pixelmap | Indicates the OH_PixelmapNative that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetOutputPixelmap()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputPixelmap(OH_ImageEffect *imageEffect, OH_PixelmapNative *pixelmap)
```

**Description**

Set output pixelmap that contains the image information

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_PixelmapNative *pixelmap | Indicates the OH_PixelmapNative that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetInputNativeBuffer()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetInputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)
```

**Description**

Set input NativeBuffer that contains the image information. It should be noted that the input NativeBuffer will be directly rendered and modified if the output is not set

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_NativeBuffer *nativeBuffer | Indicates the NativeBuffer that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetOutputNativeBuffer()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputNativeBuffer(OH_ImageEffect *imageEffect, OH_NativeBuffer *nativeBuffer)
```

**Description**

Set output NativeBuffer that contains the image information

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_NativeBuffer *nativeBuffer | Indicates the NativeBuffer that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetInputUri()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetInputUri(OH_ImageEffect *imageEffect, const char *uri)
```

**Description**

Set input URI of the image. It should be noted that the image resource will be directly rendered and modified if the output is not set

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| const char *uri | An URI for a image resource |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetOutputUri()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputUri(OH_ImageEffect *imageEffect, const char *uri)
```

**Description**

Set output URI of the image

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| const char *uri | An URI for a image resource |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetInputPicture()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetInputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)
```

**Description**

Set input picture that contains the image information. It should be noted that the input picture will be directly rendered and modified if the output is not set

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_PictureNative *picture | Indicates the OH_PictureNative that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetOutputPicture()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputPicture(OH_ImageEffect *imageEffect, OH_PictureNative *picture)
```

**Description**

Set output picture that contains the image information

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| OH_PictureNative *picture | Indicates the OH_PictureNative that contains the image information |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_SetInputTextureId()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetInputTextureId(OH_ImageEffect *imageEffect, int32_t textureId, int32_t colorSpace)
```

**Description**

Sets the ID of the input texture that contains the image information.

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| { | OH_ImageEffect } imageEffect Pointer to an instance of the OH_ImageEffect struct. |
| int32_t textureId | ID of the texture that contains the image information. This ID must be valid and have been bound bound to a texture of a GL_TEXTURE_2D type. |
| int32_t colorSpace | Color space of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the operation is successful; returns EFFECT_ERROR_PARAM_INVALID if the  parameter parameter is missing or incorrect. |

### OH_ImageEffect_SetOutputTextureId()

```c
ImageEffect_ErrorCode OH_ImageEffect_SetOutputTextureId(OH_ImageEffect *imageEffect, int32_t textureId)
```

**Description**

Sets the ID of the output texture that contains the rendered image information.

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Pointer to an instance of the OH_ImageEffect struct. |
| int32_t textureId | ID of the texture that contains the rendered image information. This ID must be valid. If it it is not bound to a texture, it will automatically be bound to a GL_TEXTURE_2D type. If the texture is already already bound and the size is inappropriate, the rendered result may be cropped or partially filled into into this texture. |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the operation is successful; returns EFFECT_ERROR_PARAM_INVALID if the  parameter parameter is missing or incorrect. |

### OH_ImageEffect_Start()

```c
ImageEffect_ErrorCode OH_ImageEffect_Start(OH_ImageEffect *imageEffect)
```

**Description**

Render the filter effects that can be a single filter or a chain of filters

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer.<br>{@link EFFECT_INPUT_OUTPUT_NOT_SUPPORTED}, the data types of the input and output images<br>to be processed are different.<br>{@link EFFECT_COLOR_SPACE_NOT_MATCH}, the color spaces of the input and output images are different.<br>{@link EFFECT_ALLOCATE_MEMORY_FAILED}, the buffer fails to be allocated. |

### OH_ImageEffect_Stop()

```c
ImageEffect_ErrorCode OH_ImageEffect_Stop(OH_ImageEffect *imageEffect)
```

**Description**

Stop rendering the filter effects for next image frame data

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_Release()

```c
ImageEffect_ErrorCode OH_ImageEffect_Release(OH_ImageEffect *imageEffect)
```

**Description**

Clear the internal resources of the OH_ImageEffect and destroy the OH_ImageEffect instance

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_Save()

```c
ImageEffect_ErrorCode OH_ImageEffect_Save(OH_ImageEffect *imageEffect, char **info)
```

**Description**

Convert the OH_ImageEffect and the information of the filters in OH_ImageEffect to JSON string

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageEffect](capi-imageeffect-oh-imageeffect.md) *imageEffect | Encapsulate OH_ImageEffect structure instance pointer |
| char **info | Indicates the serialized information that is obtained by converting the information of the filters in OH_ImageEffect to JSON string |

**Returns**:

| Type | Description |
| -- | -- |
| ImageEffect_ErrorCode | Returns EFFECT_SUCCESS if the execution is successful, otherwise returns a specific error code, refer to  {@link ImageEffect_ErrorCode}<br>{@link EFFECT_ERROR_PARAM_INVALID}, the input parameter is a null pointer. |

### OH_ImageEffect_Restore()

```c
OH_ImageEffect *OH_ImageEffect_Restore(const char *info)
```

**Description**

Create an OH_ImageEffect instance by deserializing the JSON string info

**System capability**: SystemCapability.Multimedia.ImageEffect.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *info | Indicates the serialized information that is obtained by converting the information of the filters in OH_ImageEffect to JSON string |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ImageEffect *](capi-imageeffect-oh-imageeffect.md) | Returns a pointer to an OH_ImageEffect instance if the execution is successful, otherwise returns nullptr |


