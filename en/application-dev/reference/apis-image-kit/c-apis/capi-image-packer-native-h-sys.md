# image_packer_native.h(System API)

## Overview

The file declares the APIs for image encoding.

**Library**: libimage_packer.so

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 12

**System API:** This is a system API.

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_PackingOptions_GetNeedsPackDfxData(OH_PackingOptions *options, bool *needsPackDfxData)(System API)](#oh_packingoptions_getneedspackdfxdata) | Obtains the **needsPackDfxData** parameter in the OH_PackingOptions struct.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_PackingOptions_SetNeedsPackDfxData(OH_PackingOptions *options, bool needsPackDfxData)(System API)](#oh_packingoptions_setneedspackdfxdata) | Sets the **needsPackDfxData** parameter in the OH_PackingOptions struct.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_PackingOptions_SetC2paDataSize(OH_PackingOptions *options, uint32_t c2paDataSize)(System API)](#oh_packingoptions_setc2padatasize) | Sets the C2PA data size in the OH_PackingOptions struct. The default value is 0, indicating no reserved space is added.<br>**System API:** This is a system API. |
| [Image_ErrorCode OH_PackingOptions_GetC2paDataSize(const OH_PackingOptions *options, uint32_t *c2paDataSize)(System API)](#oh_packingoptions_getc2padatasize) | Obtains the C2PA data size in the OH_PackingOptions struct.<br>**System API:** This is a system API. |

## Function description

### OH_PackingOptions_GetNeedsPackDfxData()

```c
Image_ErrorCode OH_PackingOptions_GetNeedsPackDfxData(OH_PackingOptions *options, bool *needsPackDfxData)
```

**Description**

Obtains the **needsPackDfxData** parameter in the OH_PackingOptions struct.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | Pointer to an OH_PackingOptions struct. |
| bool *needsPackDfxData | Whether to encode image DFX data. The values include **true** (yes) and **false** (no). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options or needsPackDfxData is nullptr.</li>          </ul> |

### OH_PackingOptions_SetNeedsPackDfxData()

```c
Image_ErrorCode OH_PackingOptions_SetNeedsPackDfxData(OH_PackingOptions *options, bool needsPackDfxData)
```

**Description**

Sets the **needsPackDfxData** parameter in the OH_PackingOptions struct.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | Pointer to an OH_PackingOptions struct. |
| bool needsPackDfxData | Whether to encode image DFX data. The values include **true** (yes) and **false** (no). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li>          </ul> |

### OH_PackingOptions_SetC2paDataSize()

```c
Image_ErrorCode OH_PackingOptions_SetC2paDataSize(OH_PackingOptions *options, uint32_t c2paDataSize)
```

**Description**

Sets the C2PA data size in the OH_PackingOptions struct. The default value is 0, indicating no reserved space is added.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 26.0.1

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | [in] Pointer to an OH_PackingOptions struct. It must not be NULL. |
| uint32_t c2paDataSize | [in] Reserved space size for C2PA data, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>           <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the operation is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options is NULL.</li>          </ul> |

### OH_PackingOptions_GetC2paDataSize()

```c
Image_ErrorCode OH_PackingOptions_GetC2paDataSize(const OH_PackingOptions *options, uint32_t *c2paDataSize)
```

**Description**

Obtains the C2PA data size in the OH_PackingOptions struct.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Since**: 26.0.1

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_PackingOptions](capi-image-nativemodule-oh-packingoptions.md) *options | [in] Pointer to an OH_PackingOptions struct. It must not be NULL. |
| uint32_t *c2paDataSize | [out] Pointer to the C2PA data size obtained, in bytes. It must not be NULL. If the function fails, the content of c2paDataSize is unchanged. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>           <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the operation is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_PACKER_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options or c2paDataSize is NULL.</li>          </ul> |


