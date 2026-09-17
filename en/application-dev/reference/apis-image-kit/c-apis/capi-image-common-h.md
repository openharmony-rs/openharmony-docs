# image_common.h

## Overview

The file declares the common enums and structs used by the image interface.

**Library**: libimage_common.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Image_Size](capi-image-nativemodule-image-size.md) | Image_Size | Declaration the image size. |
| [Image_Region](capi-image-nativemodule-image-region.md) | Image_Region | Declaration the image region. |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) | - | Define a PictureMetadata struct type, used for picture metadata. |
| [Image_String](capi-image-nativemodule-image-string.md) | Image_String | Defines the property string (in key-value format) of the image source. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Image_ErrorCode](#image_errorcode) | Image_ErrorCode | Enumerates the return values that may be used by the interface. |
| [Image_MetadataType](#image_metadatatype) | Image_MetadataType | Enumerates the metadata types. |
| [IMAGE_ALLOCATOR_MODE](#image_allocator_mode) | IMAGE_ALLOCATOR_MODE | Type of allocator used to allocate memory of a PixelMap. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_picturemetadata_create) | Creates the pointer to an OH_PictureMetadata struct. |
| [Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_getproperty) | Obtains a property of metadata based on the key. **value.data** obtained through this API lacks the string terminator **\0**. Please use it with caution. |
| [Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_getpropertywithnull) | Obtains the metadata value of an OH_PictureMetadata instance. The output **value.data** ends with the string terminator **\0**. |
| [Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)](#oh_picturemetadata_setproperty) | Sets a property of metadata based on the key. |
| [Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)](#oh_picturemetadata_setblobdata) | Sets blob data in the metadata. |
| [Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)](#oh_picturemetadata_getblobdatasize) | Obtains the size of the blob data in the metadata. |
| [Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)](#oh_picturemetadata_getblobdata) | Obtains blob data from the metadata. |
| [Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)](#oh_picturemetadata_release) | Releases the pointer to an OH_PictureMetadata struct. |
| [Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)](#oh_picturemetadata_clone) | Clones metadata. |

## Enum type description

### Image_ErrorCode

```c
enum Image_ErrorCode
```

**Description**

Enumerates the return values that may be used by the interface.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IMAGE_SUCCESS = 0 | operation success |
| IMAGE_BAD_PARAMETER = 401 | invalid parameter |
| OH_IMAGE_ERROR_NOT_SYSTEM_APPLICATION = 202 |  Permission verification failed. A non-system application calls a system API.<br>**Since**: 26.1.0 |
| IMAGE_UNSUPPORTED_MIME_TYPE = 7600101 | unsupported mime type |
| IMAGE_UNKNOWN_MIME_TYPE = 7600102 | unknown mime type |
| IMAGE_TOO_LARGE = 7600103 | too large data or image |
| IMAGE_GET_IMAGE_DATA_FAILED = 7600104 |  Failed to get image data.<br>**Since**: 23 |
| IMAGE_PIXELMAP_RELEASED = 7600105 |  PixelMap has been released.<br>**Since**: 26.0.0 |
| IMAGE_DMA_NOT_EXIST = 7600173 | @error DMA memory does not exist |
| IMAGE_DMA_OPERATION_FAILED = 7600174 | @error DMA operation failed |
| IMAGE_UNSUPPORTED_OPERATION = 7600201 | unsupported operations |
| IMAGE_UNSUPPORTED_METADATA = 7600202 | unsupported metadata |
| IMAGE_UNSUPPORTED_CONVERSION = 7600203 | unsupported conversion |
| IMAGE_INVALID_REGION = 7600204 | invalid region |
| IMAGE_UNSUPPORTED_MEMORY_FORMAT = 7600205 |  unsupported memory format<br>**Since**: 13 |
| IMAGE_INVALID_PARAMETER = 7600206 |  Invalid parameter.<br>**Since**: 19 |
| IMAGE_UNSUPPORTED_DATA_FORMAT = 7600207 |  Unsupported data format<br>**Since**: 22 |
| OH_IMAGE_ERROR_DECOMPOSE_FAILED = 7600208 |  the decomposition process failed.<br>**Since**: 26.1.0 |
| IMAGE_ALLOC_FAILED = 7600301 | failed to allocate memory |
| IMAGE_COPY_FAILED = 7600302 | memory copy failed |
| IMAGE_LOCK_UNLOCK_FAILED = 7600303 |  memory lock or unlock failed<br>**Since**: 15 |
| IMAGE_INIT_FAILED = 7600304 |  Initialization failed<br>**Since**: 22 |
| IMAGE_CREATE_PIXELMAP_FAILED = 7600305 |  Create PixelMap failed<br>**Since**: 22 |
| IMAGE_DATA_CONVERSION_FAILED = 7600306 |  Data conversion failed.<br>**Since**: 26.0.0 |
| IMAGE_ALLOCATOR_MODE_UNSUPPORTED = 7600501 |  unsupported allocator mode, e.g., use share memory to create a HDR image as only DMA supported hdr metadata.<br>**Since**: 20 |
| IMAGE_UNKNOWN_ERROR = 7600901 | unknown error |
| IMAGE_BAD_SOURCE = 7700101 | decode data source exception |
| IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE = 7700102 |  unsupported mime type<br>**Since**: 15 |
| IMAGE_SOURCE_TOO_LARGE = 7700103 |  image to large<br>**Since**: 15 |
| IMAGE_SOURCE_UNSUPPORTED_ALLOCATOR_TYPE = 7700201 |  unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata.<br>**Since**: 15 |
| IMAGE_SOURCE_UNSUPPORTED_METADATA = 7700202 |  Unsupported metadata. For example, the property key is not supported, or the property value is invalid.<br>**Since**: 23 |
| IMAGE_SOURCE_UNSUPPORTED_OPTIONS = 7700203 |  unsupported options, e.g, cannot convert image into desired pixel format.<br>**Since**: 15 |
| IMAGE_SOURCE_INVALID_PARAMETER = 7700204 |  Invalid parameter.<br>**Since**: 19 |
| IMAGE_DECODE_FAILED = 7700301 | decode failed |
| IMAGE_SOURCE_ALLOC_FAILED = 7700302 |  memory allocation failed<br>**Since**: 15 |
| IMAGE_PACKER_INVALID_PARAMETER = 7800202 |  Invalid parameter for ImagePacker.<br>**Since**: 19 |
| IMAGE_ENCODE_FAILED = 7800301 | encode failed |
| IMAGE_RECEIVER_INVALID_PARAMETER = 7900201 |  Invalid parameter for ImageReceiver.<br>**Since**: 20 |

### Image_MetadataType

```c
enum Image_MetadataType
```

**Description**

Enumerates the metadata types.

**Since**: 13

| Enum item | Description |
| -- | -- |
| EXIF_METADATA = 1 |  |
| FRAGMENT_METADATA = 2 |  |
| GIF_METADATA = 5 |  |

### IMAGE_ALLOCATOR_MODE

```c
enum IMAGE_ALLOCATOR_MODE
```

**Description**

Type of allocator used to allocate memory of a PixelMap.

**Since**: 20

| Enum item | Description |
| -- | -- |
| IMAGE_ALLOCATOR_MODE_AUTO = 0 |  |
| IMAGE_ALLOCATOR_MODE_DMA = 1 |  |
| IMAGE_ALLOCATOR_MODE_SHARED_MEMORY = 2 |  |


## Function description

### OH_PictureMetadata_Create()

```c
Image_ErrorCode OH_PictureMetadata_Create(Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**Description**

Creates the pointer to an OH_PictureMetadata struct.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Image_MetadataType](capi-image-common-h.md#image_metadatatype) metadataType | Metadata type. |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **metadata | Double pointer to the OH_PictureMetadata struct created. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): A parameter is incorrect. |

### OH_PictureMetadata_GetProperty()

```c
Image_ErrorCode OH_PictureMetadata_GetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**Description**

Obtains a property of metadata based on the key. **value.data** obtained through this API lacks the string terminator **\0**. Please use it with caution.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| [Image_String](capi-image-nativemodule-image-string.md) *key | Pointer to the key of the property. |
| [Image_String](capi-image-nativemodule-image-string.md) *value | Pointer to the value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): A parameter is incorrect.      <br>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode): The metadata type is not supported, or the metadata type and the      auxiliary picture type do not match. |

### OH_PictureMetadata_GetPropertyWithNull()

```c
Image_ErrorCode OH_PictureMetadata_GetPropertyWithNull(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**Description**

Obtains the metadata value of an OH_PictureMetadata instance. The output **value.data** ends with the string terminator **\0**.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| [Image_String](capi-image-nativemodule-image-string.md) *key | Pointer to the key of the property. |
| [Image_String](capi-image-nativemodule-image-string.md) *value | Pointer to the value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode): The metadata, key, or value parameter is a null pointer.      <br>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode): The metadata type is not supported, or the metadata type and the      auxiliary picture type do not match. |

### OH_PictureMetadata_SetProperty()

```c
Image_ErrorCode OH_PictureMetadata_SetProperty(OH_PictureMetadata *metadata, Image_String *key, Image_String *value)
```

**Description**

Sets a property of metadata based on the key.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| [Image_String](capi-image-nativemodule-image-string.md) *key | Pointer to the key of the property. |
| [Image_String](capi-image-nativemodule-image-string.md) *value | Pointer to the value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): A parameter is incorrect.      <br>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode): The metadata type is not supported, or the metadata type and the      auxiliary picture type do not match. |

### OH_PictureMetadata_SetBlobData()

```c
Image_ErrorCode OH_PictureMetadata_SetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)
```

**Description**

Sets blob data in the metadata.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| uint8_t *blob | Pointer to the blob data. |
| uint32_t blobSize | Size of the blob data. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) metadata is nullptr, or blob is nullptr, or blobSize is 0.</li>          <li>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) unsupported metadata type.</li>          <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) failed to set blob data.</li>          </ul> |

### OH_PictureMetadata_GetBlobDataSize()

```c
Image_ErrorCode OH_PictureMetadata_GetBlobDataSize(OH_PictureMetadata *metadata, uint32_t *blobSize)
```

**Description**

Obtains the size of the blob data in the metadata.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| uint32_t *blobSize | Pointer to the size of the blob data. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) metadata or blobSize is nullptr.</li>          <li>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) unsupported metadata type.</li>          </ul> |

### OH_PictureMetadata_GetBlobData()

```c
Image_ErrorCode OH_PictureMetadata_GetBlobData(OH_PictureMetadata *metadata, uint8_t *blob, uint32_t blobSize)
```

**Description**

Obtains blob data from the metadata.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |
| uint8_t *blob | Pointer to the blob data obtained. |
| uint32_t blobSize | Size of the blob data. The value must be greater than or equal to the value obtained by the OH_PictureMetadata_GetBlobSize method. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) metadata is nullptr, or blob is nullptr, or blobSize is 0, or blobSize              is less than metadata length.</li>          <li>[IMAGE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) unsupported metadata type.</li>          <li>[IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) failed to get blob data.</li>          </ul> |

### OH_PictureMetadata_Release()

```c
Image_ErrorCode OH_PictureMetadata_Release(OH_PictureMetadata *metadata)
```

**Description**

Releases the pointer to an OH_PictureMetadata struct.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *metadata | Pointer to an OH_PictureMetadata struct. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): A parameter is incorrect. |

### OH_PictureMetadata_Clone()

```c
Image_ErrorCode OH_PictureMetadata_Clone(OH_PictureMetadata *oldMetadata, OH_PictureMetadata **newMetadata)
```

**Description**

Clones metadata.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) *oldMetadata | Pointer to an OH_PictureMetadata struct. |
| [OH_PictureMetadata](capi-image-nativemodule-oh-picturemetadata.md) **newMetadata | Double pointer to the OH_PictureMetadata struct obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| [Image_ErrorCode](capi-image-common-h.md#image_errorcode) | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The operation is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): A parameter is incorrect.      <br>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode): The memory allocation fails.      <br>[IMAGE_COPY_FAILED](capi-image-common-h.md#image_errorcode): The memory copy fails. |


