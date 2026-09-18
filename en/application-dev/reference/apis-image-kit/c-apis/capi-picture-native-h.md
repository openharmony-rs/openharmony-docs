# picture_native.h

## Overview

The file declares the APIs for obtaining picture data and information.

**Library**: libpicture.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_PictureNative_AuxiliaryPictureCopyItem](capi-image-nativemodule-oh-picturenative-auxiliarypicturecopyitem.md) | OH_PictureNative_AuxiliaryPictureCopyItem | This structure is used to specify an auxiliary picture copy rule when creating a deep copy of a PictureNative object. It describes how to copy an auxiliary picture from one type to another. |
| [OH_PictureNative_MetadataCopyItem](capi-image-nativemodule-oh-picturenative-metadatacopyitem.md) | OH_PictureNative_MetadataCopyItem | This structure is used to specify a metadata copy rule when creating a deep copy of a PictureNative object. It describes how to copy metadata from one type to another. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) | - | The struct is used to perform operations related to the picture. |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) | - | The struct describes the auxiliary picture, which is used to perform operations related to the auxiliary picture. |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) | - | The struct describes the auxiliary picture information, which is used to perform operations related to the auxiliary picture information. |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) | OH_ComposeOptions | **OH_ComposeOptions** is the HDR composition option struct encapsulated at the native layer. It is used to specify parameters used for HDR composition, such as the target pixel format. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Image_AuxiliaryPictureType](#image_auxiliarypicturetype) | Image_AuxiliaryPictureType | Type of the auxiliary picture. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_ComposeOptions_Create(OH_ComposeOptions **options)](#oh_composeoptions_create) | Creates an **OH_ComposeOptions** instance. |
| [Image_ErrorCode OH_ComposeOptions_SetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT desiredPixelFormat)](#oh_composeoptions_setdesiredpixelformat) | Sets the pixel format in **OH_ComposeOptions**. |
| [Image_ErrorCode OH_ComposeOptions_GetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT *desiredPixelFormat)](#oh_composeoptions_getdesiredpixelformat) | Obtains the pixel format in **OH_ComposeOptions**. |
| [Image_ErrorCode OH_ComposeOptions_Release(OH_ComposeOptions *options)](#oh_composeoptions_release) | Releases the pointer to **OH_ComposeOptions**. |
| [Image_ErrorCode OH_PictureNative_CreatePicture(OH_PixelmapNative *mainPixelmap, OH_PictureNative **picture)](#oh_picturenative_createpicture) | Creates the pointer to an OH_PictureNative object. |
| [Image_ErrorCode OH_PictureNative_GetMainPixelmap(OH_PictureNative *picture, OH_PixelmapNative **mainPixelmap)](#oh_picturenative_getmainpixelmap) | Obtains the pointer to the OH_PixelmapNative object of a main picture. |
| [Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmap(OH_PictureNative *picture, OH_PixelmapNative **hdrPixelmap)](#oh_picturenative_gethdrcomposedpixelmap) | Obtains the pointer to the OH_PixelmapNative object of an HDR picture. |
| [Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmapWithOptions(OH_PictureNative *picture, OH_ComposeOptions *options, OH_PixelmapNative **hdrPixelmap)](#oh_picturenative_gethdrcomposedpixelmapwithoptions) | Obtains the pointer to **OH_PixelmapNative** of an HDR picture based on **OH_ComposeOptions**. |
| [Image_ErrorCode OH_PictureNative_GetGainmapPixelmap(OH_PictureNative *picture, OH_PixelmapNative **gainmapPixelmap)](#oh_picturenative_getgainmappixelmap) | Obtains the pointer to the OH_PixelmapNative object of a gain map. |
| [Image_ErrorCode OH_PictureNative_SetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative *auxiliaryPicture)](#oh_picturenative_setauxiliarypicture) | Sets an auxiliary picture. |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)](#oh_picturenative_getauxiliarypicture) | Obtains an auxiliary picture by type. |
| [Image_ErrorCode OH_PictureNative_GetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_picturenative_getmetadata) | Obtains the metadata of a main picture. |
| [Image_ErrorCode OH_PictureNative_SetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)](#oh_picturenative_setmetadata) | Sets the metadata for a main picture. |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureCount(OH_PictureNative *picture, uint32_t *count)](#oh_picturenative_getauxiliarypicturecount) | Obtains the number of auxiliary pictures in a Picture object. |
| [Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureTypes(OH_PictureNative *picture, Image_AuxiliaryPictureType *auxiliaryPictureTypes, uint32_t *count)](#oh_picturenative_getauxiliarypicturetypes) | Obtains the types of auxiliary pictures in a Picture object. |
| [Image_ErrorCode OH_PictureNative_GetMetadataCount(OH_PictureNative *picture, uint32_t *count)](#oh_picturenative_getmetadatacount) | Obtains the number of metadata entries in a Picture object. |
| [Image_ErrorCode OH_PictureNative_GetMetadataTypes(OH_PictureNative *picture, Image_MetadataType *metadataTypes, uint32_t *count)](#oh_picturenative_getmetadatatypes) | Obtains the types of metadata in a Picture object. |
| [Image_ErrorCode OH_PictureNative_RemoveAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type)](#oh_picturenative_removeauxiliarypicture) | Removes an auxiliary picture from a Picture object. |
| [Image_ErrorCode OH_PictureNative_RemoveMetadata(OH_PictureNative *picture, Image_MetadataType type)](#oh_picturenative_removemetadata) | Removes metadata from a Picture object. |
| [Image_ErrorCode OH_PictureNative_DeepCopyWithItems(OH_PictureNative *source, const OH_PictureNative_AuxiliaryPictureCopyItem *auxiliaryPictureCopyItems, uint32_t auxiliaryPictureCopyCount, const OH_PictureNative_MetadataCopyItem *metadataCopyItems, uint32_t metadataCopyCount, Image_AuxiliaryPictureType *sourceAuxPictureAsMainPixelMap, OH_PictureNative **picture)](#oh_picturenative_deepcopywithitems) | Creates a deep copy of a PictureNative object with specified auxiliary pictures and metadata copied to specified destination types. |
| [Image_ErrorCode OH_PictureNative_Release(OH_PictureNative *picture)](#oh_picturenative_release) | Releases the pointer to an OH_PictureNative object. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_Create(uint8_t *data, size_t dataLength, Image_Size *size, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)](#oh_auxiliarypicturenative_create) | Creates the pointer to an OH_AuxiliaryPictureNative object. This API supports only continuous pixel data whose {@link pixel format} is BGRA_8888 and creates an auxiliary picture in RGBA_8888 format. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_WritePixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *source, size_t bufferSize)](#oh_auxiliarypicturenative_writepixels) | Reads pixels in the buffer and writes the result to an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_ReadPixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *destination, size_t *bufferSize)](#oh_auxiliarypicturenative_readpixels) | Reads pixels of an auxiliary picture and writes the result to the buffer. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetType(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_AuxiliaryPictureType *type)](#oh_auxiliarypicturenative_gettype) | Obtains the type of an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo **info)](#oh_auxiliarypicturenative_getinfo) | Obtains the information of an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_SetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo *info)](#oh_auxiliarypicturenative_setinfo) | Sets the information for an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_GetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)](#oh_auxiliarypicturenative_getmetadata) | Obtains the metadata of an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_SetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)](#oh_auxiliarypicturenative_setmetadata) | Sets the metadata for an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_AcquirePixelmap(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_PixelmapNative **pixelmap)](#oh_auxiliarypicturenative_acquirepixelmap) | Obtains the OH_PixelmapNative object of an auxiliary picture. |
| [Image_ErrorCode OH_AuxiliaryPictureNative_Release(OH_AuxiliaryPictureNative *picture)](#oh_auxiliarypicturenative_release) | Releases the pointer to an OH_AuxiliaryPictureNative object. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_Create(OH_AuxiliaryPictureInfo **info)](#oh_auxiliarypictureinfo_create) | Creates an OH_AuxiliaryPictureInfo object. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType *type)](#oh_auxiliarypictureinfo_gettype) | Obtains the auxiliary picture type in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType type)](#oh_auxiliarypictureinfo_settype) | Sets the auxiliary picture type in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)](#oh_auxiliarypictureinfo_getsize) | Obtains the image size in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)](#oh_auxiliarypictureinfo_setsize) | Sets the image size in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t *rowStride)](#oh_auxiliarypictureinfo_getrowstride) | Obtains the row stride in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t rowStride)](#oh_auxiliarypictureinfo_setrowstride) | Sets the row stride in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_GetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT *pixelFormat)](#oh_auxiliarypictureinfo_getpixelformat) | Obtains the pixel format in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_SetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT pixelFormat)](#oh_auxiliarypictureinfo_setpixelformat) | Sets the pixel format in **OH_AuxiliaryPictureInfo**. |
| [Image_ErrorCode OH_AuxiliaryPictureInfo_Release(OH_AuxiliaryPictureInfo *info)](#oh_auxiliarypictureinfo_release) | Releases the pointer to an OH_AuxiliaryPictureInfo object. |

## Enum type description

### Image_AuxiliaryPictureType

```c
enum Image_AuxiliaryPictureType
```

**Description**

Type of the auxiliary picture.

**Since**: 13

| Enum item | Description |
| -- | -- |
| AUXILIARY_PICTURE_TYPE_GAINMAP = 1 | Gainmap |
| AUXILIARY_PICTURE_TYPE_DEPTH_MAP = 2 | Depth map |
| AUXILIARY_PICTURE_TYPE_UNREFOCUS_MAP = 3 | Unrefocus map |
| AUXILIARY_PICTURE_TYPE_LINEAR_MAP = 4 | Linear map |
| AUXILIARY_PICTURE_TYPE_FRAGMENT_MAP = 5 | Fragment map |


## Function description

### OH_ComposeOptions_Create()

```c
Image_ErrorCode OH_ComposeOptions_Create(OH_ComposeOptions **options)
```

**Description**

Creates an **OH_ComposeOptions** instance.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) **options | Pointer to **OH_ComposeOptions**. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} options is nullptr. |

### OH_ComposeOptions_SetDesiredPixelFormat()

```c
Image_ErrorCode OH_ComposeOptions_SetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT desiredPixelFormat)
```

**Description**

Sets the pixel format in **OH_ComposeOptions**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | Pointer to **OH_ComposeOptions**. |
| PIXEL_FORMAT desiredPixelFormat | Pixel format. The RGBA_1010102, YCBCR_P010, and YCRCB_P010 formats are supported. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} options is nullptr, or desiredPixelFormat is not supported. |

### OH_ComposeOptions_GetDesiredPixelFormat()

```c
Image_ErrorCode OH_ComposeOptions_GetDesiredPixelFormat(OH_ComposeOptions *options, PIXEL_FORMAT *desiredPixelFormat)
```

**Description**

Obtains the pixel format in **OH_ComposeOptions**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | Pointer to **OH_ComposeOptions**. |
| PIXEL_FORMAT *desiredPixelFormat | Pixel format in the composition options. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} options is nullptr,or desiredPixelFormat is nullptr. |

### OH_ComposeOptions_Release()

```c
Image_ErrorCode OH_ComposeOptions_Release(OH_ComposeOptions *options)
```

**Description**

Releases the pointer to **OH_ComposeOptions**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | Pointer to **OH_ComposeOptions**. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} options is nullptr. |

### OH_PictureNative_CreatePicture()

```c
Image_ErrorCode OH_PictureNative_CreatePicture(OH_PixelmapNative *mainPixelmap, OH_PictureNative **picture)
```

**Description**

Creates the pointer to an OH_PictureNative object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_PixelmapNative *mainPixelmap | Pointer to the OH_PixelmapNative object of the main picture. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **picture | Double pointer to the OH_PictureNative object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} mainPixelmap is nullptr, or picture is nullptr. |

### OH_PictureNative_GetMainPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetMainPixelmap(OH_PictureNative *picture, OH_PixelmapNative **mainPixelmap)
```

**Description**

Obtains the pointer to the OH_PixelmapNative object of a main picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| OH_PixelmapNative **mainPixelmap | Double pointer to the OH_PixelmapNative object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or mainPixelmap is nullptr. |

### OH_PictureNative_GetHdrComposedPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmap(OH_PictureNative *picture, OH_PixelmapNative **hdrPixelmap)
```

**Description**

Obtains the pointer to the OH_PixelmapNative object of an HDR picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| OH_PixelmapNative **hdrPixelmap | Double pointer to the OH_PixelmapNative object of the HDR picture. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or hdrPixelmap is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_OPERATION} Unsupported operation, e.g. the picture does not has a gainmap. |

### OH_PictureNative_GetHdrComposedPixelmapWithOptions()

```c
Image_ErrorCode OH_PictureNative_GetHdrComposedPixelmapWithOptions(OH_PictureNative *picture, OH_ComposeOptions *options, OH_PixelmapNative **hdrPixelmap)
```

**Description**

Obtains the pointer to **OH_PixelmapNative** of an HDR picture based on **OH_ComposeOptions**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| [OH_ComposeOptions](capi-image-nativemodule-oh-composeoptions.md) *options | Pointer to **OH_ComposeOptions**. |
| OH_PixelmapNative **hdrPixelmap | Pointer to **OH_PixelmapNative** of the obtained HDR picture. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or hdrPixelmap is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_OPERATION} Unsupported operation, e.g. the picture does not has a gainmap. |

### OH_PictureNative_GetGainmapPixelmap()

```c
Image_ErrorCode OH_PictureNative_GetGainmapPixelmap(OH_PictureNative *picture, OH_PixelmapNative **gainmapPixelmap)
```

**Description**

Obtains the pointer to the OH_PixelmapNative object of a gain map.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| OH_PixelmapNative **gainmapPixelmap | Double pointer to the OH_PixelmapNative object of the gain map. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or gainmapPixelmap is nullptr. |

### OH_PictureNative_SetAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_SetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative *auxiliaryPicture)
```

**Description**

Sets an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | Type of the auxiliary picture. |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or auxiliaryPicture is nullptr, or the type is invalid. |

### OH_PictureNative_GetAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**Description**

Obtains an auxiliary picture by type.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | Type of the auxiliary picture. |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | Double pointer to the OH_AuxiliaryPictureNative object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or auxiliaryPicture is nullptr, or the type is invalid. |

### OH_PictureNative_GetMetadata()

```c
Image_ErrorCode OH_PictureNative_GetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**Description**

Obtains the metadata of a main picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| Image_MetadataType metadataType | Metadata type. |
| OH_PictureMetadata **metadata | Double pointer to the metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or metadata is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_METADATA} unsupported metadata type. |

### OH_PictureNative_SetMetadata()

```c
Image_ErrorCode OH_PictureNative_SetMetadata(OH_PictureNative *picture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)
```

**Description**

Sets the metadata for a main picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| Image_MetadataType metadataType | Metadata type. |
| OH_PictureMetadata *metadata | Pointer to the metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr, or metadata is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_METADATA} unsupported metadata type. |

### OH_PictureNative_GetAuxiliaryPictureCount()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureCount(OH_PictureNative *picture, uint32_t *count)
```

**Description**

Obtains the number of auxiliary pictures in a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| uint32_t *count | Pointer to the number of auxiliary pictures. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture or count is nullptr, or fail to get the picture.</li>          </ul> |

### OH_PictureNative_GetAuxiliaryPictureTypes()

```c
Image_ErrorCode OH_PictureNative_GetAuxiliaryPictureTypes(OH_PictureNative *picture, Image_AuxiliaryPictureType *auxiliaryPictureTypes, uint32_t *count)
```

**Description**

Obtains the types of auxiliary pictures in a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *auxiliaryPictureTypes | Pointer to the array that receives the auxiliary picture types. |
| uint32_t *count | On input, the size of auxiliaryPictureTypes array. On output, the actual number of auxiliary pictures. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture, auxiliaryPictureTypes, or count is nullptr,          or fail to get the picture, or count is smaller than required.</li>          </ul> |

### OH_PictureNative_GetMetadataCount()

```c
Image_ErrorCode OH_PictureNative_GetMetadataCount(OH_PictureNative *picture, uint32_t *count)
```

**Description**

Obtains the number of metadata entries in a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| uint32_t *count | Pointer to the number of metadata entries. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture or count is nullptr, or fail to get the picture.</li>          </ul> |

### OH_PictureNative_GetMetadataTypes()

```c
Image_ErrorCode OH_PictureNative_GetMetadataTypes(OH_PictureNative *picture, Image_MetadataType *metadataTypes, uint32_t *count)
```

**Description**

Obtains the types of metadata in a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| Image_MetadataType *metadataTypes | Pointer to the array that receives the metadata types. |
| uint32_t *count | On input, the size of metadataTypes array. On output, the actual number of metadata entries. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture, metadataTypes, or count is nullptr,          or fail to get the picture, or count is smaller than required.</li>          </ul> |

### OH_PictureNative_RemoveAuxiliaryPicture()

```c
Image_ErrorCode OH_PictureNative_RemoveAuxiliaryPicture(OH_PictureNative *picture, Image_AuxiliaryPictureType type)
```

**Description**

Removes an auxiliary picture from a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | Type of the auxiliary picture to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the auxiliary picture was successfully removed or did not exist.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture is nullptr, or fail to get the picture,          or the type is invalid.</li>          </ul> |

### OH_PictureNative_RemoveMetadata()

```c
Image_ErrorCode OH_PictureNative_RemoveMetadata(OH_PictureNative *picture, Image_MetadataType type)
```

**Description**

Removes metadata from a Picture object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |
| Image_MetadataType type | Type of the metadata to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the metadata was successfully removed or did not exist.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} picture is nullptr, or fail to get the picture.</li><br>        <li>{@link IMAGE_UNSUPPORTED_METADATA} unsupported metadata type.</li>          </ul> |

### OH_PictureNative_DeepCopyWithItems()

```c
Image_ErrorCode OH_PictureNative_DeepCopyWithItems(OH_PictureNative *source, const OH_PictureNative_AuxiliaryPictureCopyItem *auxiliaryPictureCopyItems, uint32_t auxiliaryPictureCopyCount, const OH_PictureNative_MetadataCopyItem *metadataCopyItems, uint32_t metadataCopyCount, Image_AuxiliaryPictureType *sourceAuxPictureAsMainPixelMap, OH_PictureNative **picture)
```

**Description**

Creates a deep copy of a PictureNative object with specified auxiliary pictures and metadata copied to specified destination types.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *source | The source PictureNative object to be copied. Must not be NULL. |
| [const OH_PictureNative_AuxiliaryPictureCopyItem](capi-image-nativemodule-oh-picturenative-auxiliarypicturecopyitem.md) *auxiliaryPictureCopyItems | An array describing the auxiliary pictures to copy, including source and destination auxiliary picture types. Can be NULL if auxiliaryPictureCopyCount is 0. |
| uint32_t auxiliaryPictureCopyCount | The number of items in auxiliaryPictureCopyItems. |
| [const OH_PictureNative_MetadataCopyItem](capi-image-nativemodule-oh-picturenative-metadatacopyitem.md) *metadataCopyItems | An array describing the metadata entries to copy, including source and destination metadata types. Can be NULL if metadataCopyCount is 0. |
| uint32_t metadataCopyCount | The number of items in metadataCopyItems. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *sourceAuxPictureAsMainPixelMap | Specifies an auxiliary picture type in the source picture to be used as the main pixel map in the copied picture. Can be NULL if the original main pixel map should be used. |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) **picture | Output parameter used to receive the newly created PictureNative object. The caller is responsible for releasing it when it is no longer needed. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} if source or picture is nullptr, or counts mismatch,<br>        or fail to get the source picture, or Count is not zero but corresponding array is nullptr.</li><br>        <li>{@link IMAGE_ALLOC_FAILED} memory allocation failed.</li>          </ul> |

### OH_PictureNative_Release()

```c
Image_ErrorCode OH_PictureNative_Release(OH_PictureNative *picture)
```

**Description**

Releases the pointer to an OH_PictureNative object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](capi-image-nativemodule-oh-picturenative.md) *picture | Pointer to an OH_PictureNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr. |

### OH_AuxiliaryPictureNative_Create()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_Create(uint8_t *data, size_t dataLength, Image_Size *size, Image_AuxiliaryPictureType type, OH_AuxiliaryPictureNative **auxiliaryPicture)
```

**Description**

Creates the pointer to an OH_AuxiliaryPictureNative object. This API supports only continuous pixel data whose {@link pixel format} is BGRA_8888 and creates an auxiliary picture in RGBA_8888 format.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Pointer to the image data. |
| size_t dataLength | Length of the image data. |
| Image_Size *size | Pointer to the size of the auxiliary picture. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | Type of the auxiliary picture. |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) **auxiliaryPicture | Double pointer to the OH_AuxiliaryPictureNative object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} data is nullptr, or dataLength is invalid, or size is nullptr, or the type          is invalid, or auxiliaryPicture is nullptr. |

### OH_AuxiliaryPictureNative_WritePixels()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_WritePixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *source, size_t bufferSize)
```

**Description**

Reads pixels in the buffer and writes the result to an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| uint8_t *source | Pixels to be written. |
| size_t bufferSize | Buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or source is nullptr, or the bufferSize is invalid.<br>    <br>{@link IMAGE_ALLOC_FAILED} memory alloc failed.<br>    <br>{@link IMAGE_COPY_FAILED} memory copy failed. |

### OH_AuxiliaryPictureNative_ReadPixels()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_ReadPixels(OH_AuxiliaryPictureNative *auxiliaryPicture, uint8_t *destination, size_t *bufferSize)
```

**Description**

Reads pixels of an auxiliary picture and writes the result to the buffer.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| uint8_t *destination | Pointer to the buffer to which the pixels of the auxiliary data will be written. |
| size_t *bufferSize | Pointer to the buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or destination is nullptr,<br>        or the bufferSize is invalid.<br>    <br>{@link IMAGE_ALLOC_FAILED} memory alloc failed.<br>    <br>{@link IMAGE_COPY_FAILED} memory copy failed. |

### OH_AuxiliaryPictureNative_GetType()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetType(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_AuxiliaryPictureType *type)
```

**Description**

Obtains the type of an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *type | Pointer to the auxiliary picture type. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or type is nullptr. |

### OH_AuxiliaryPictureNative_GetInfo()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo **info)
```

**Description**

Obtains the information of an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) **info | Double pointer to the auxiliary picture information. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or info is nullptr. |

### OH_AuxiliaryPictureNative_SetInfo()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_SetInfo(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_AuxiliaryPictureInfo *info)
```

**Description**

Sets the information for an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the auxiliary picture information. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or info is nullptr. |

### OH_AuxiliaryPictureNative_GetMetadata()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_GetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata **metadata)
```

**Description**

Obtains the metadata of an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| Image_MetadataType metadataType | Metadata type. |
| OH_PictureMetadata **metadata | Double pointer to the metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or metadata is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_METADATA} unsupported metadata type, or the metadata type does not match the          auxiliary picture type. |

### OH_AuxiliaryPictureNative_SetMetadata()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_SetMetadata(OH_AuxiliaryPictureNative *auxiliaryPicture, Image_MetadataType metadataType, OH_PictureMetadata *metadata)
```

**Description**

Sets the metadata for an auxiliary picture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| Image_MetadataType metadataType | Metadata type. |
| OH_PictureMetadata *metadata | Pointer to the metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} auxiliaryPicture is nullptr, or metadata is nullptr.<br>    <br>{@link IMAGE_UNSUPPORTED_METADATA} unsupported metadata type, or the metadata type does not match the          auxiliary picture type. |

### OH_AuxiliaryPictureNative_AcquirePixelmap()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_AcquirePixelmap(OH_AuxiliaryPictureNative *auxiliaryPicture, OH_PixelmapNative **pixelmap)
```

**Description**

Obtains the OH_PixelmapNative object of an auxiliary picture.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *auxiliaryPicture | Pointer to an OH_AuxiliaryPictureNative object. |
| OH_PixelmapNative **pixelmap | Double pointer to the OH_PixelmapNative object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>{@link IMAGE_SUCCESS} if the execution is successful.</li><br>        <li>{@link IMAGE_INVALID_PARAMETER} auxiliaryPicture is nullptr, or pixelmap is nullptr.</li><br>        <li>{@link IMAGE_GET_IMAGE_DATA_FAILED} fail to get the auxiliary picture or its pixelmap content.</li><br>        <li>{@link IMAGE_ALLOC_FAILED} memory allocation failed.</li>          </ul> |

### OH_AuxiliaryPictureNative_Release()

```c
Image_ErrorCode OH_AuxiliaryPictureNative_Release(OH_AuxiliaryPictureNative *picture)
```

**Description**

Releases the pointer to an OH_AuxiliaryPictureNative object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureNative](capi-image-nativemodule-oh-auxiliarypicturenative.md) *picture | Pointer to an OH_AuxiliaryPictureNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} picture is nullptr. |

### OH_AuxiliaryPictureInfo_Create()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_Create(OH_AuxiliaryPictureInfo **info)
```

**Description**

Creates an OH_AuxiliaryPictureInfo object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) **info | Double pointer to the OH_AuxiliaryPictureInfo object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr. |

### OH_AuxiliaryPictureInfo_GetType()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType *type)
```

**Description**

Obtains the auxiliary picture type in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) *type | Pointer to the type of the auxiliary picture. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or type is nullptr. |

### OH_AuxiliaryPictureInfo_SetType()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetType(OH_AuxiliaryPictureInfo *info, Image_AuxiliaryPictureType type)
```

**Description**

Sets the auxiliary picture type in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) type | Type of the auxiliary picture. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or type is invalid. |

### OH_AuxiliaryPictureInfo_GetSize()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)
```

**Description**

Obtains the image size in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| Image_Size *size | Pointer to the size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or size is nullptr. |

### OH_AuxiliaryPictureInfo_SetSize()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetSize(OH_AuxiliaryPictureInfo *info, Image_Size *size)
```

**Description**

Sets the image size in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| Image_Size *size | Pointer to the size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or size is nullptr. |

### OH_AuxiliaryPictureInfo_GetRowStride()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t *rowStride)
```

**Description**

Obtains the row stride in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| uint32_t *rowStride | Pointer to the row stride, which is the number of bytes from one row of pixels in memory to the next row of pixels in memory. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or rowStride is nullptr. |

### OH_AuxiliaryPictureInfo_SetRowStride()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetRowStride(OH_AuxiliaryPictureInfo *info, uint32_t rowStride)
```

**Description**

Sets the row stride in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| uint32_t rowStride | Row stride, which is the number of bytes from one row of pixels in memory to the next row of pixels in memory. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or rowStride is nullptr. |

### OH_AuxiliaryPictureInfo_GetPixelFormat()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_GetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT *pixelFormat)
```

**Description**

Obtains the pixel format in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| PIXEL_FORMAT *pixelFormat | Pointer to the pixel format obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr, or pixelFormat is nullptr. |

### OH_AuxiliaryPictureInfo_SetPixelFormat()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_SetPixelFormat(OH_AuxiliaryPictureInfo *info, PIXEL_FORMAT pixelFormat)
```

**Description**

Sets the pixel format in **OH_AuxiliaryPictureInfo**.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |
| PIXEL_FORMAT pixelFormat | Pixel format. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr. |

### OH_AuxiliaryPictureInfo_Release()

```c
Image_ErrorCode OH_AuxiliaryPictureInfo_Release(OH_AuxiliaryPictureInfo *info)
```

**Description**

Releases the pointer to an OH_AuxiliaryPictureInfo object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AuxiliaryPictureInfo](capi-image-nativemodule-oh-auxiliarypictureinfo.md) *info | Pointer to the OH_AuxiliaryPictureInfo object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | {@link IMAGE_SUCCESS} if the execution is successful.<br>    <br>{@link IMAGE_BAD_PARAMETER} info is nullptr. |


