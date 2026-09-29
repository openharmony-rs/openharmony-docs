# picture_native.h(System API)

## Overview

The file declares the APIs for obtaining picture data and information.

**Library**: libpicture.so

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
| [Image_ErrorCode OH_PictureNative_ConvertPictureNativeToNapi(napi_env env, OH_PictureNative *pictureNative, napi_value *outPictureNapi)(System API)](#oh_picturenative_convertpicturenativetonapi) | Converts an [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) object to an ArkTS <b>Picture</b> object represented by a napi_value. The returned ArkTS Picture object holds its own strong reference to the same underlying Picture as pictureNative. This function does not copy the main image, auxiliary pictures, or metadata.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_PictureNative_ConvertPictureNativeFromNapi(napi_env env, napi_value pictureNapi, OH_PictureNative **outOwnedPictureNative)(System API)](#oh_picturenative_convertpicturenativefromnapi) | Converts an ArkTS <b>Picture</b> object represented by a napi_value to an [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) object. The returned OH_PictureNative object and pictureNapi share the same underlying Picture object. This function does not copy the main image, auxiliary pictures, or metadata.<br>**System API:** This is a system API. |

## Function description

### OH_AuxiliaryPictureNative_CreateUsingAllocator()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_CreateUsingAllocator(uint8_t *data, uint32_t dataLength, OH_AuxiliaryPictureInfo *info, IMAGE_ALLOCATOR_MODE allocator, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**Description**

Creates an OH_AuxiliaryPictureNative object with a specified memory type. By default, the system selects the memory type based on the image type, image size, platform capability, and other factors. When processing the auxiliary picture returned by this API, always consider the impact of stride. If **data** is null or **dataLength**<br>is less than or equal to 0, the auxiliary picture will not be initialized.

**Since**: 26.0.0

**Resource release**: picture_native/OH_AuxiliaryPictureNative_Release {auxiliaryPicture}

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Pointer to the image data. |
| uint32_t dataLength | Length of the image data. |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the basic information of the auxiliary picture. |
| [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_allocator_mode) allocator | Memory type used by the auxiliary picture. For details about the available options, see [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | Double pointer to the OH_AuxiliaryPictureNative object created. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>202 if a non-system application calls this system API.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) info or auxiliaryPicture is nullptr, or allocator is invalid, or the size is invalid, or the type is unsupported, or dataLength is smaller than required.</li> <li>[IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE](capi-image-common-h.md#image_errorcode) unsupported allocator type, e.g., use share memory create a gainmap as only DMA supported hdr metadata.</li> <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li> </ul> |

### OH_DecomposeOptions_Create()

```c
Image_ErrorCode OH_DecomposeOptions_Create(OH_DecomposeOptions **outOwnedOptions)
```

**Description**

Creates an OH_DecomposeOptions object.

**Since**: 26.0.0

**Resource release**: picture_native/OH_DecomposeOptions_Release {outOwnedOptions}

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) **outOwnedOptions | The pointer to an OH_DecomposeOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) outOwnedOptions is nullptr.</li> <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_DecomposeOptions_SetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_SetIsFullSizeGainmap(OH_DecomposeOptions *options, bool isFullSizeGainmap)
```

**Description**

Sets whether to generate a full-size gainmap.

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
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_DecomposeOptions_GetIsFullSizeGainmap()

```c
Image_ErrorCode OH_DecomposeOptions_GetIsFullSizeGainmap(OH_DecomposeOptions *options, bool *isFullSizeGainmap)
```

**Description**

Gets whether to generate a full-size gainmap.

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
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options or isFullSizeGainmap is nullptr.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_DecomposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_SetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t desiredPixelFormat)
```

**Description**

Sets the desired pixel format of the SDR pixel map generated after HDR decomposition.

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
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li> <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) desiredPixelFormat is not supported.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_DecomposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_DecomposeOptions_GetDesiredPixelFormat(OH_DecomposeOptions *options, int32_t *desiredPixelFormat)
```

**Description**

Gets the desired pixel format of the SDR pixel map generated after HDR decomposition.

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
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options or desiredPixelFormat is nullptr.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_DecomposeOptions_Release()

```c
Image_ErrorCode OH_DecomposeOptions_Release(OH_DecomposeOptions *options)
```

**Description**

Releases an OH_DecomposeOptions object.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | The pointer to an OH_DecomposeOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_PictureNative_DecomposeToPicture()

```c
Image_ErrorCode OH_PictureNative_DecomposeToPicture(OH_PixelmapNative *hdrPixelmap, OH_DecomposeOptions *options, OH_PictureNative **outOwnedPicture)
```

**Description**

Decomposes an HDR pixel map into a Picture object which contains an SDR pixel map and a gainmap.

**Since**: 26.0.0

**Resource release**: picture_native/OH_PictureNative_Release {outOwnedPicture}

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *hdrPixelmap | The HDR pixel map to be decomposed. |
| [OH_DecomposeOptions](capi-image-nativemodule-oh-decomposeoptions-sys.md) *options | Options used to control HDR decomposition. This parameter is mandatory. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **outOwnedPicture | Pointer to the created Picture object. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) hdrPixelmap, options, or outOwnedPicture is nullptr.</li> <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) the pixel map is not supported for decomposition.</li> <li>IMAGE_DECOMPOSE_FAILED the decomposition process failed.</li> <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) memory allocation failed.</li> <li>202 if a non-system application calls this system API.</li> </ul> |

### OH_PictureNative_ConvertPictureNativeToNapi()

```c
Image_ErrorCode OH_PictureNative_ConvertPictureNativeToNapi(napi_env env, OH_PictureNative *pictureNative, napi_value *outPictureNapi)
```

**Description**

Converts an [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) object to an ArkTS <b>Picture</b> object represented by a napi_value. The returned ArkTS Picture object holds its own strong reference to the same underlying Picture as pictureNative. This function does not copy the main image, auxiliary pictures, or metadata.

**Since**: 26.0.1

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | [in] The N-API environment in which the ArkTS Picture object is created. This parameter must not be nullptr. This function must be called on the thread associated with env. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *pictureNative | [in] Pointer to the OH_PictureNative object to convert. The pointer must not be nullptr, and the object must contain a valid underlying Picture. This function does not release or take ownership of pictureNative. Releasing pictureNative after a successful conversion does not invalidate the created ArkTS Picture object. |
| napi_value *outPictureNapi | [out] Pointer to a napi_value that receives a handle to the created ArkTS Picture object. The pointer must not be nullptr. The output value is valid only when IMAGE_SUCCESS is returned. Do not use the output value if the conversion fails. The handle is subject to N-API handle-scope rules. The lifetime of the ArkTS Picture object is governed by its release API and the runtime's garbage collection. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the conversion is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if env, pictureNative, or outPictureNapi is nullptr.</li> <li>[IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) if creation of the ArkTS Picture object fails.</li> <li>[OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION](capi-image-common-h.md#image_errorcode) if system API is called by a non-system application.</li> </ul> |

### OH_PictureNative_ConvertPictureNativeFromNapi()

```c
Image_ErrorCode OH_PictureNative_ConvertPictureNativeFromNapi(napi_env env, napi_value pictureNapi, OH_PictureNative **outOwnedPictureNative)
```

**Description**

Converts an ArkTS <b>Picture</b> object represented by a napi_value to an [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) object. The returned OH_PictureNative object and pictureNapi share the same underlying Picture object. This function does not copy the main image, auxiliary pictures, or metadata.

**Since**: 26.0.1

**Resource release**: picture_native/OH_PictureNative_Release {outOwnedPictureNative}

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | [in] The N-API environment to which pictureNapi belongs. This parameter must not be nullptr. This function must be called on the thread associated with env. |
| napi_value pictureNapi | [in] A valid napi_value handle to the ArkTS Picture object to convert. The object must belong to env and must not have been explicitly released. This function does not release or take ownership of the input ArkTS Picture object. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **outOwnedPictureNative | [out] Pointer to an OH_PictureNative pointer variable that receives the newly created native object. The pointer must not be nullptr. The output variable is left unchanged on failure. The caller owns the OH_PictureNative object and must release it by calling [OH_PictureNative_Release](capi-picture-native-h.md#oh_picturenative_release) when it is no longer needed. Explicit release or garbage collection of the input ArkTS Picture object after a successful conversion does not invalidate the created OH_PictureNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul> <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the operation is successful.</li> <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if env, pictureNapi, or outOwnedPictureNative is nullptr, pictureNapi is not an ArkTS Picture object, or the ArkTS Picture object has been released.</li> <li>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) if memory allocation fails.</li> <li>[IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) if an N-API operation fails while inspecting pictureNapi in env.</li> <li>[OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION](capi-image-common-h.md#image_errorcode) if a non-system application calls this system API.</li> </ul> |


