# image_common.h(System API)

## Overview

The file declares the common enums and structs used by the image interface.

**Library**: libimage_common.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**System API:** This is a system API.

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_PictureMetadata_GetMetadataByType(OH_PictureMetadata **metadatas, uint32_t metadataCount, int32_t type, OH_PictureMetadata *metadata)(System API)](#oh_picturemetadata_getmetadatabytype) | Obtains the PictureMetadata object matching the specified type from the PictureMetadata array.**System API:** This is a system API. |
| [Image_ErrorCode OH_PictureMetadatas_Release(OH_PictureMetadata **metadatas, uint32_t metadatasCount)(System API)](#oh_picturemetadatas_release) | Releases an array of OH_PictureMetadata objects.**System API:** This is a system API. |

## Function description

### OH_PictureMetadata_GetMetadataByType()

```c
Image_ErrorCode OH_PictureMetadata_GetMetadataByType(OH_PictureMetadata **metadatas, uint32_t metadataCount, int32_t type, OH_PictureMetadata *metadata)
```

**Description**

Obtains the PictureMetadata object matching the specified type from the PictureMetadata array.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadatas | Pointer to the PictureMetadata array. |
| uint32_t metadataCount | Length of the PictureMetadata array. |
| int32_t type | Target metadata type to be matched. |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to the output PictureMetadata object, which stores the matched content. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the operation is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if metadatas/metadata is nullptr or metadataCount is 0.</li>          </ul> |

### OH_PictureMetadatas_Release()

```c
Image_ErrorCode OH_PictureMetadatas_Release(OH_PictureMetadata **metadatas, uint32_t metadatasCount)
```

**Description**

Releases an array of OH_PictureMetadata objects.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadatas | Pointer to a OH_PictureMetadata array. |
| uint32_t metadatasCount | The length of the OH_PictureMetadata array. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>202 if a non-system application calls this system API.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) metadatas is nullptr, or metadatasCount is 0.</li>          </ul> |


