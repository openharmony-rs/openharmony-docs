# picture_native.h(System API)

## Overview

The file declares the APIs for obtaining picture data and information.

**Library**: libpicture.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 13

**System API:** This is a system API.

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_DecomposeOptions(System API)](capi-image-nativemodule-oh-decomposeoptions-sys.md) | OH_DecomposeOptions | **OH_DecomposeOptions** is the HDR decomposition option struct encapsulated at the native layer. It is used to specify parameters used for HDR decomposition, such as the target pixel format.<br>**System API:** This is a system API. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)(System API)](#oh_auxiliarypicturenative_createusingallocator) | Creates an OH_AuxiliaryPictureNative object with a specified memory type. By default, the system selects the memory type based on the image type, image size, platform capability, and other factors. When processing the auxiliary picture returned by this API, always consider the impact of stride. If **data** is null or **dataLength**<br>is less than or equal to 0, the auxiliary picture will not be initialized.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)(System API)](#oh_decomposeoptions_create) | Creates an OH_DecomposeOptions object.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)(System API)](#oh_decomposeoptions_setisfullsizegainmap) | Sets whether to generate a full-size gainmap.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)(System API)](#oh_decomposeoptions_getisfullsizegainmap) | Gets whether to generate a full-size gainmap.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)(System API)](#oh_decomposeoptions_setdesiredpixelformat) | Sets the desired pixel format of the SDR pixel map generated after HDR decomposition.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)(System API)](#oh_decomposeoptions_getdesiredpixelformat) | Gets the desired pixel format of the SDR pixel map generated after HDR decomposition.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)(System API)](#oh_decomposeoptions_release) | Releases an OH_DecomposeOptions object.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)(System API)](#oh_picturenative_decomposetopicture) | Decomposes an HDR pixel map into a Picture object which contains an SDR pixel map and a gainmap.<br>**System API:** This is a system API. |

## Function description

### OH_AuxiliaryPictureNative_CreateUsingAllocator()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**Description**

Creates an OH_AuxiliaryPictureNative object with a specified memory type. By default, the system selects the memory type based on the image type, image size, platform capability, and other factors. When processing the auxiliary picture returned by this API, always consider the impact of stride. If **data** is null or **dataLength**<br>is less than or equal to 0, the auxiliary picture will not be initialized.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Pointer to the image data. |
| uint32_t dataLength | Length of the image data. |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the basic information of the auxiliary picture. |
| IMAGE_ALLOCATOR_MODE allocator | Memory type used by the auxiliary picture. For details about the available options, see [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | Double pointer to the OH_AuxiliaryPictureNative object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) info or auxiliaryPicture is nullptr, or allocator is invalid,          or the size is invalid, or the type is unsupported, or dataLength is smaller than required.</li>          <li>[IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE](capi-image-common-h.md#image_errorcode) unsupported allocator type,          e.g., use share memory create a gainmap as only DMA supported hdr metadata.</li>          <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li>          </ul> |

### OH_DecomposeOptions_Create()

```c
Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)
```

**Description**

Creates an OH_DecomposeOptions object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) **outOwnedOptions | The pointer to an OH_DecomposeOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) outOwnedOptions is nullptr.</li>          <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_DecomposeOptions_SetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)
```

**Description**

Sets whether to generate a full-size gainmap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |
| bool isFullSizeGainmap | Whether to generate a full-size gainmap. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_DecomposeOptions_GetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)
```

**Description**

Gets whether to generate a full-size gainmap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |
| bool *isFullSizeGainmap | Pointer to the value indicating whether to generate a full-size gainmap. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options or isFullSizeGainmap is nullptr.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_DecomposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)
```

**Description**

Sets the desired pixel format of the SDR pixel map generated after HDR decomposition.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |
| int32_t desiredPixelFormat | The desired pixel format of the generated SDR pixel map, which can be set to RGBA_8888, NV12, or NV21. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li>          <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) desiredPixelFormat is not supported.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_DecomposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)
```

**Description**

Gets the desired pixel format of the SDR pixel map generated after HDR decomposition.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |
| int32_t *desiredPixelFormat | Pointer to the desired pixel format of the generated SDR pixel map. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options or desiredPixelFormat is nullptr.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_DecomposeOptions_Release()

```c
Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)
```

**Description**

Releases an OH_DecomposeOptions object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_PictureNative_DecomposeToPicture()

```c
Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)
```

**Description**

Decomposes an HDR pixel map into a Picture object which contains an SDR pixel map and a gainmap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_PixelmapNative *hdrPixelmap | The HDR pixel map to be decomposed. |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | Options used to control HDR decomposition. This parameter is mandatory. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **outOwnedPicture | Pointer to the created Picture object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li><br>        <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) hdrPixelmap, options, or outOwnedPicture is nullptr.</li><br>        <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) the pixel map is not supported for decomposition.</li><br>        <li>{@link IMAGE_DECOMPOSE_FAILED} the decomposition process failed.</li><br>        <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |


