# image_source_native.h

## Overview

The file declares the APIs for image decoding.

**Library**: libimage_source.so

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) | - | The struct describes the image source, which is encapsulated at the native layer and is used to create image data. The struct cannot be directly operated. Instead, functions must be called to create and release the struct and operate the fields in the struct. |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) | - | The OH_ImageSource_Info struct describes the image source information encapsulated at the native layer. The struct cannot be directly operated. Instead, functions must be called to create and release the struct and operate the fields in the struct. |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) | - | The struct describes the decoding options for pictures. It is obtained by calling {@link OH_DecodingOptionsForPicture_Create}. |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) | - | The OH_DecodingOptions struct describes the decoding options encapsulated at the native layer. The struct is used to set decoding options and is passed in as an input parameter for creating a PixelMap. For details, see {@link OH_ImageSourceNative_CreatePixelmap}. |
| [OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md) | - | Defines raw data in an image. It is used in {@link OH_ImageSourceNative_CreateImageRawData}. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [IMAGE_DYNAMIC_RANGE](#image_dynamic_range) | IMAGE_DYNAMIC_RANGE | Enumerates the desired dynamic range for decoding. |
| [IMAGE_ALLOCATOR_TYPE](#image_allocator_type) | IMAGE_ALLOCATOR_TYPE | Enumerates the types of allocators used to allocate PixelMap memory. |
| [Image_CropAndScaleStrategy](#image_cropandscalestrategy) | Image_CropAndScaleStrategy | Enumerates the cropping and scaling strategies when **desiredSize** and **desiredRegion** are both specified.<br> If the **ImageCropAndScaleStrategy** parameter is not specified in [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) and both **desiredRegion** and **desiredSize** are set, the final decoding result may vary slightly due to differences in decoding algorithms used for different image formats.<br> For example, if the original image size is 200x200, and you specify **desiredSize:{width: 150, height: 150},<br>desiredRegion:{x: 0, y: 0, width: 100, height: 100}**, the expectation is to decode the top-left 1/4 region of the original image and then scale the pixelMap size to 150x150.<br> For JPEG and WebP images (as well as some DNG images that decode a JPEG preview within the file and therefore are treated as JPEG format), the system first performs downsampling. For instance, it might downsample by 7/8 and then crop the region based on a 175x175 image size. As a result, the final cropped region will be slightly larger than the top-left 1/4 of the original image.<br> For SVG images, which are vector-based and can be scaled without losing clarity, the system scales the image based on the ratio of **desiredSize** to the original image size and then crops the region. This results in a decoded region that may differ from the exact 1/4 region of the original image.<br> To ensure consistent results when both **desiredRegion** and **desiredSize** are set, set the **ImageCropAndScaleStrategy**<br>parameter to **CROP_FIRST**. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_ImageSourceInfo_Create(OH_ImageSource_Info **info)](#oh_imagesourceinfo_create) | Creates the pointer to an OH_ImageSource_Info object. |
| [Image_ErrorCode OH_ImageSourceInfo_GetWidth(OH_ImageSource_Info *info, uint32_t *width)](#oh_imagesourceinfo_getwidth) | Obtains the image width. |
| [Image_ErrorCode OH_ImageSourceInfo_GetHeight(OH_ImageSource_Info *info, uint32_t *height)](#oh_imagesourceinfo_getheight) | Obtains the image height. |
| [Image_ErrorCode OH_ImageSourceInfo_GetDynamicRange(OH_ImageSource_Info *info, bool *isHdr)](#oh_imagesourceinfo_getdynamicrange) | Obtains the dynamic range of an image. |
| [Image_ErrorCode OH_ImageSourceInfo_GetMimeType(OH_ImageSource_Info *info, Image_MimeType *mimetype)](#oh_imagesourceinfo_getmimetype) | Obtains the MIME type of an image source. |
| [Image_ErrorCode OH_ImageSourceInfo_Release(OH_ImageSource_Info *info)](#oh_imagesourceinfo_release) | Releases the pointer to an OH_ImageSource_Info object. |
| [Image_ErrorCode OH_DecodingOptions_Create(OH_DecodingOptions **options)](#oh_decodingoptions_create) | Creates the pointer to an OH_DecodingOptions object. |
| [Image_ErrorCode OH_DecodingOptions_GetPixelFormat(OH_DecodingOptions *options, int32_t *pixelFormat)](#oh_decodingoptions_getpixelformat) | Obtains the pixel format. |
| [Image_ErrorCode OH_DecodingOptions_SetPixelFormat(OH_DecodingOptions *options, int32_t pixelFormat)](#oh_decodingoptions_setpixelformat) | Sets the pixel format. |
| [Image_ErrorCode OH_DecodingOptions_GetIndex(OH_DecodingOptions *options, uint32_t *index)](#oh_decodingoptions_getindex) | Obtains the index of an image. |
| [Image_ErrorCode OH_DecodingOptions_SetIndex(OH_DecodingOptions *options, uint32_t index)](#oh_decodingoptions_setindex) | Sets the index for an image. |
| [Image_ErrorCode OH_DecodingOptions_GetRotate(OH_DecodingOptions *options, float *rotate)](#oh_decodingoptions_getrotate) | Obtains the rotation degree. |
| [Image_ErrorCode OH_DecodingOptions_SetRotate(OH_DecodingOptions *options, float rotate)](#oh_decodingoptions_setrotate) | Sets the rotation angle. |
| [Image_ErrorCode OH_DecodingOptions_GetDesiredSize(OH_DecodingOptions *options, Image_Size *desiredSize)](#oh_decodingoptions_getdesiredsize) | Obtains the desired output size. |
| [Image_ErrorCode OH_DecodingOptions_SetDesiredSize(OH_DecodingOptions *options, Image_Size *desiredSize)](#oh_decodingoptions_setdesiredsize) | Sets the desired output size. |
| [Image_ErrorCode OH_DecodingOptions_GetDesiredRegion(OH_DecodingOptions *options, Image_Region *desiredRegion)](#oh_decodingoptions_getdesiredregion) | Obtains the region to decode. Since the corresponding **SetDesiredRegion** function cannot meet the regional decoding requirements, starting from API version 19, you are advised to use [OH_DecodingOptions_GetCropRegion](capi-image-source-native-h.md#oh_decodingoptions_getcropregion) instead. |
| [Image_ErrorCode OH_DecodingOptions_SetDesiredRegion(OH_DecodingOptions *options, Image_Region *desiredRegion)](#oh_decodingoptions_setdesiredregion) | Sets the region to decode. The actual decoding will process the entire original image, without any regional decoding effect. Starting from API version 19, you are advised to use [OH_DecodingOptions_SetCropRegion](capi-image-source-native-h.md#oh_decodingoptions_setcropregion) instead. |
| [Image_ErrorCode OH_DecodingOptions_GetDesiredDynamicRange(OH_DecodingOptions *options, int32_t *desiredDynamicRange)](#oh_decodingoptions_getdesireddynamicrange) | Obtains the desired dynamic range configured during decoding. |
| [Image_ErrorCode OH_DecodingOptions_SetDesiredDynamicRange(OH_DecodingOptions *options, int32_t desiredDynamicRange)](#oh_decodingoptions_setdesireddynamicrange) | Sets the desired dynamic range during decoding. |
| [Image_ErrorCode OH_DecodingOptions_GetCropAndScaleStrategy(OH_DecodingOptions *options, int32_t *cropAndScaleStrategy)](#oh_decodingoptions_getcropandscalestrategy) | Obtains the cropping and scaling strategy used during decoding. |
| [Image_ErrorCode OH_DecodingOptions_SetCropAndScaleStrategy(OH_DecodingOptions *options, int32_t cropAndScaleStrategy)](#oh_decodingoptions_setcropandscalestrategy) | Sets the cropping and scaling strategy used during decoding. |
| [Image_ErrorCode OH_DecodingOptions_SetDesiredColorSpace(OH_DecodingOptions *options, int32_t colorSpace)](#oh_decodingoptions_setdesiredcolorspace) | Sets the desired color space for the decoding options. |
| [Image_ErrorCode OH_DecodingOptions_GetDesiredColorSpace(OH_DecodingOptions *options, int32_t *colorSpace)](#oh_decodingoptions_getdesiredcolorspace) | Obtains the color space set in the decoding options. |
| [Image_ErrorCode OH_DecodingOptions_SetCropRegion(OH_DecodingOptions *options, Image_Region *cropRegion)](#oh_decodingoptions_setcropregion) | Sets the cropping region in the decoding options. |
| [Image_ErrorCode OH_DecodingOptions_GetCropRegion(OH_DecodingOptions *options, Image_Region *cropRegion)](#oh_decodingoptions_getcropregion) | Obtains the cropping region in the decoding options. |
| [Image_ErrorCode OH_DecodingOptions_Release(OH_DecodingOptions *options)](#oh_decodingoptions_release) | Releases the pointer to an OH_DecodingOptions object. |
| [Image_ErrorCode OH_ImageSourceNative_CreateFromUri(char *uri, size_t uriSize, OH_ImageSourceNative **res)](#oh_imagesourcenative_createfromuri) | Creates the pointer to an OH_ImageSourceNative object based on a URI. |
| [Image_ErrorCode OH_ImageSourceNative_CreateFromFd(int32_t fd, OH_ImageSourceNative **res)](#oh_imagesourcenative_createfromfd) | Creates the pointer to an OH_ImageSourceNative object based on a file descriptor. |
| [Image_ErrorCode OH_ImageSourceNative_CreateFromData(uint8_t *data, size_t dataSize, OH_ImageSourceNative **res)](#oh_imagesourcenative_createfromdata) | Creates the pointer to an OH_ImageSourceNative object based on buffer data. The buffer data must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [OH_PixelmapNative_CreatePixelmap](capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap). |
| [Image_ErrorCode OH_ImageSourceNative_CreateFromDataWithUserBuffer(uint8_t *data, size_t datalength, OH_ImageSourceNative **imageSource)](#oh_imagesourcenative_createfromdatawithuserbuffer) | Creates an image source from data buffer. The data buffer is directly accessed by the image source object, and therefore the data buffer must remain accessible within the lifecycle of the image source object. |
| [Image_ErrorCode OH_ImageSourceNative_CreateFromRawFile(RawFileDescriptor *rawFile, OH_ImageSourceNative **res)](#oh_imagesourcenative_createfromrawfile) | Creates the pointer to an OH_ImageSourceNative object by using the raw file descriptor of an image resource file. |
| [Image_ErrorCode OH_ImageSourceNative_CreatePixelmap(OH_ImageSourceNative *source, OH_DecodingOptions *options, OH_PixelmapNative **pixelmap)](#oh_imagesourcenative_createpixelmap) | Creates the pointer to an OH_PixelmapNative object based on decoding options. |
| [Image_ErrorCode OH_ImageSourceNative_CreatePixelmapUsingAllocator(OH_ImageSourceNative *source, OH_DecodingOptions *options, IMAGE_ALLOCATOR_TYPE allocator, OH_PixelmapNative **pixelmap)](#oh_imagesourcenative_createpixelmapusingallocator) | Creates an OH_PixelmapNative object based on decoding options and memory type, where **allocatorType**<br>specifies the memory type of the PixelMap. By default, the system selects an appropriate memory type based on the image type, image size, and platform capability. When processing the returned PixelMap object, consider the impact of stride. |
| [Image_ErrorCode OH_ImageSourceNative_CreatePixelmapList(OH_ImageSourceNative *source, OH_DecodingOptions *options, OH_PixelmapNative *resVecPixMap[], size_t size)](#oh_imagesourcenative_createpixelmaplist) | Creates an array of OH_PixelmapNative objects based on decoding options. This function decodes all frames at once. If the number of frames is high or the size of individual frames is large, it can lead to significant memory usage. In these cases, you are advised to use the **Image** component for displaying animations. The **Image** component decodes frames one by one, which uses less memory than this function. |
| [Image_ErrorCode OH_ImageSourceNative_CreatePicture(OH_ImageSourceNative *source, OH_DecodingOptionsForPicture *options, OH_PictureNative **picture)](#oh_imagesourcenative_createpicture) | Creates the pointer to an OH_PictureNative object based on decoding options. |
| [Image_ErrorCode OH_ImageSourceNative_CreatePictureAtIndex(OH_ImageSourceNative *source, uint32_t index, OH_PictureNative **picture)](#oh_imagesourcenative_createpictureatindex) | Creates the pointer to an OH_PictureNative object at the specified index. |
| [Image_ErrorCode OH_ImageSourceNative_GetDelayTimeList(OH_ImageSourceNative *source, int32_t *delayTimeList, size_t size)](#oh_imagesourcenative_getdelaytimelist) | Obtains the image delay time list. |
| [Image_ErrorCode OH_ImageSourceNative_GetImageInfo(OH_ImageSourceNative *source, int32_t index, OH_ImageSource_Info *info)](#oh_imagesourcenative_getimageinfo) | Obtains the information about an image with a given index. |
| [Image_ErrorCode OH_ImageSourceNative_GetImageProperty(OH_ImageSourceNative *source, Image_String *key, Image_String *value)](#oh_imagesourcenative_getimageproperty) | Obtains the value of an image property. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyWithNull(OH_ImageSourceNative *source, Image_String *key, Image_String *value)](#oh_imagesourcenative_getimagepropertywithnull) | Obtains the value of an image property from an <b>ImageSource</b> object. The output value.data is null-terminated. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImageProperty(OH_ImageSourceNative *source, Image_String *key, Image_String *value)](#oh_imagesourcenative_modifyimageproperty) | Obtains the value of an image property. The output **value.data** is terminated with a string terminator. |
| [Image_ErrorCode OH_ImageSourceNative_GetFrameCount(OH_ImageSourceNative *source, uint32_t *frameCount)](#oh_imagesourcenative_getframecount) | Obtains the number of image frames. |
| [Image_ErrorCode OH_ImageSourceNative_Release(OH_ImageSourceNative *source)](#oh_imagesourcenative_release) | Releases the pointer to an OH_ImageSourceNative object. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_Create(OH_DecodingOptionsForPicture **options)](#oh_decodingoptionsforpicture_create) | Creates the pointer to an OH_DecodingOptionsForPicture object. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredAuxiliaryPictures(OH_DecodingOptionsForPicture *options, Image_AuxiliaryPictureType **desiredAuxiliaryPictures, size_t *length)](#oh_decodingoptionsforpicture_getdesiredauxiliarypictures) | Obtains desired auxiliary pictures in the decoding options (auxiliary pictures contained in **picture**<br>expected to be decoded.) |
| [Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures(OH_DecodingOptionsForPicture *options, Image_AuxiliaryPictureType *desiredAuxiliaryPictures, size_t length)](#oh_decodingoptionsforpicture_setdesiredauxiliarypictures) | Sets desired auxiliary pictures in the decoding options. |
| [Image_ErrorCode OH_DecodingOptionsForPicture_Release(OH_DecodingOptionsForPicture *options)](#oh_decodingoptionsforpicture_release) | Releases the pointer to an OH_DecodingOptionsForPicture object. |
| [Image_ErrorCode OH_ImageSourceNative_GetSupportedFormats(Image_MimeType** supportedFormats, size_t* length)](#oh_imagesourcenative_getsupportedformats) | Obtains the supported image formats that can be decoded. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyShort(OH_ImageSourceNative *source, Image_String *key, uint16_t *value)](#oh_imagesourcenative_getimagepropertyshort) | Obtains the value of an image property as short int type. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyLong(OH_ImageSourceNative *source, Image_String *key, uint32_t *value)](#oh_imagesourcenative_getimagepropertylong) | Obtains the value of an image property as long int type. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyDouble(OH_ImageSourceNative *source, Image_String *key, double *value)](#oh_imagesourcenative_getimagepropertydouble) | Obtains the value of an image property as double type. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyArraySize(OH_ImageSourceNative *source, Image_String *key, size_t *size)](#oh_imagesourcenative_getimagepropertyarraysize) | Gets the array length of an array type property or the string length of a string type property. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyString(OH_ImageSourceNative *source, Image_String *key, char *value, size_t size)](#oh_imagesourcenative_getimagepropertystring) | Obtains the value of an image property as string type. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyIntArray(OH_ImageSourceNative *source, Image_String *key, int32_t *value, size_t size)](#oh_imagesourcenative_getimagepropertyintarray) | Obtains the value of an image property as int array. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyDoubleArray(OH_ImageSourceNative *source, Image_String *key, double *value, size_t size)](#oh_imagesourcenative_getimagepropertydoublearray) | Obtains the value of an image property as double array. |
| [Image_ErrorCode OH_ImageSourceNative_GetImagePropertyBlob(OH_ImageSourceNative *source, Image_String *key, void *value, size_t size)](#oh_imagesourcenative_getimagepropertyblob) | Obtains the value of an image property as blob. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyShort(OH_ImageSourceNative *source, Image_String *key, uint16_t value)](#oh_imagesourcenative_modifyimagepropertyshort) | Modify the value of an image property as short int. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyLong(OH_ImageSourceNative *source, Image_String *key, uint32_t value)](#oh_imagesourcenative_modifyimagepropertylong) | Modify the value of an image property as long int. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyDouble(OH_ImageSourceNative *source, Image_String *key, double value)](#oh_imagesourcenative_modifyimagepropertydouble) | Modify the value of an image property as double. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyIntArray(OH_ImageSourceNative *source, Image_String *key, int32_t *value, size_t size)](#oh_imagesourcenative_modifyimagepropertyintarray) | Modify the value of an image property as int array. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyDoubleArray(OH_ImageSourceNative *source, Image_String *key, double *value, size_t size)](#oh_imagesourcenative_modifyimagepropertydoublearray) | Modify the value of an image property as double array. |
| [Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyBlob(OH_ImageSourceNative *source, Image_String *key, void *value, size_t size)](#oh_imagesourcenative_modifyimagepropertyblob) | Modify the value of an image property as blob. |
| [Image_ErrorCode OH_ImageSourceNative_CreateImageRawData(const OH_ImageSourceNative *source, OH_ImageRawData **rawData)](#oh_imagesourcenative_createimagerawdata) | Obtains rawData object from an image. The rawData object usually occupies a large amount of memory because it contains raw data from the camera. When the rawData object and the data it contains are not used, call the [OH_ImageSourceNative_DestroyImageRawData](capi-image-source-native-h.md#oh_imagesourcenative_destroyimagerawdata) method to destroy them in a timely manner. |
| [Image_ErrorCode OH_ImageSourceNative_GetBufferFromRawData(const OH_ImageRawData *rawData, uint8_t **data, size_t *length)](#oh_imagesourcenative_getbufferfromrawdata) | Gets binary data from the rawData object. |
| [Image_ErrorCode OH_ImageSourceNative_GetBitsPerPixelFromRawData(const OH_ImageRawData *rawData, uint8_t *bitsPerPixel)](#oh_imagesourcenative_getbitsperpixelfromrawdata) | Gets number of bits that each pixel actually occupies in the buffer data. |
| [Image_ErrorCode OH_ImageSourceNative_DestroyImageRawData(OH_ImageRawData *rawData)](#oh_imagesourcenative_destroyimagerawdata) | Destroys the rawData object. |

## Enum type description

### IMAGE_DYNAMIC_RANGE

```c
enum IMAGE_DYNAMIC_RANGE
```

**Description**

Enumerates the desired dynamic range for decoding.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

| Enum item | Description |
| -- | -- |
| IMAGE_DYNAMIC_RANGE_AUTO = 0 | Dynamic range depends on the image. |
| IMAGE_DYNAMIC_RANGE_SDR = 1 | Standard dynamic range. |
| IMAGE_DYNAMIC_RANGE_HDR = 2 | High dynamic range. |

### IMAGE_ALLOCATOR_TYPE

```c
enum IMAGE_ALLOCATOR_TYPE
```

**Description**

Enumerates the types of allocators used to allocate PixelMap memory.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 15

| Enum item | Description |
| -- | -- |
| IMAGE_ALLOCATOR_TYPE_AUTO = 0 | The system determines which memory to use to create the PixelMap. |
| IMAGE_ALLOCATOR_TYPE_DMA = 1 | Use DMA buffer to create the PixelMap. |
| IMAGE_ALLOCATOR_TYPE_SHARE_MEMORY = 2 | Use share memory to create the PixelMap. |

### Image_CropAndScaleStrategy

```c
enum Image_CropAndScaleStrategy
```

**Description**

Enumerates the cropping and scaling strategies when **desiredSize** and **desiredRegion** are both specified.<br> If the **ImageCropAndScaleStrategy** parameter is not specified in [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) and both **desiredRegion** and **desiredSize** are set, the final decoding result may vary slightly due to differences in decoding algorithms used for different image formats.<br> For example, if the original image size is 200x200, and you specify **desiredSize:{width: 150, height: 150},<br>desiredRegion:{x: 0, y: 0, width: 100, height: 100}**, the expectation is to decode the top-left 1/4 region of the original image and then scale the pixelMap size to 150x150.<br> For JPEG and WebP images (as well as some DNG images that decode a JPEG preview within the file and therefore are treated as JPEG format), the system first performs downsampling. For instance, it might downsample by 7/8 and then crop the region based on a 175x175 image size. As a result, the final cropped region will be slightly larger than the top-left 1/4 of the original image.<br> For SVG images, which are vector-based and can be scaled without losing clarity, the system scales the image based on the ratio of **desiredSize** to the original image size and then crops the region. This results in a decoded region that may differ from the exact 1/4 region of the original image.<br> To ensure consistent results when both **desiredRegion** and **desiredSize** are set, set the **ImageCropAndScaleStrategy**<br>parameter to **CROP_FIRST**.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 18

| Enum item | Description |
| -- | -- |
| IMAGE_CROP_AND_SCALE_STRATEGY_SCALE_FIRST = 1 |  |
| IMAGE_CROP_AND_SCALE_STRATEGY_CROP_FIRST = 2 |  |


## Function description

### OH_ImageSourceInfo_Create()

```c
Image_ErrorCode OH_ImageSourceInfo_Create(OH_ImageSource_Info **info)
```

**Description**

Creates the pointer to an OH_ImageSource_Info object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) **info | Double pointer to the OH_ImageSource_Info object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr.</li>          </ul> |

### OH_ImageSourceInfo_GetWidth()

```c
Image_ErrorCode OH_ImageSourceInfo_GetWidth(OH_ImageSource_Info *info, uint32_t *width)
```

**Description**

Obtains the image width.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to an OH_ImageSource_Info object. |
| uint32_t *width | Pointer to the image width, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr, or width is nullptr. |

### OH_ImageSourceInfo_GetHeight()

```c
Image_ErrorCode OH_ImageSourceInfo_GetHeight(OH_ImageSource_Info *info, uint32_t *height)
```

**Description**

Obtains the image height.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to an OH_ImageSource_Info object. |
| uint32_t *height | Pointer to the image height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr, or height is nullptr. |

### OH_ImageSourceInfo_GetDynamicRange()

```c
Image_ErrorCode OH_ImageSourceInfo_GetDynamicRange(OH_ImageSource_Info *info, bool *isHdr)
```

**Description**

Obtains the dynamic range of an image.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to an OH_ImageSource_Info object. |
| bool *isHdr | Pointer to a Boolean that specifies whether the HDR is used. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr, or isHdr is nullptr. |

### OH_ImageSourceInfo_GetMimeType()

```c
Image_ErrorCode OH_ImageSourceInfo_GetMimeType(OH_ImageSource_Info *info, Image_MimeType *mimetype)
```

**Description**

Obtains the MIME type of an image source.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to the OH_ImageSource_Info struct. |
| Image_MimeType *mimetype | Pointer to the MIME type of the image source. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr, or mimeType is nullptr. |

### OH_ImageSourceInfo_Release()

```c
Image_ErrorCode OH_ImageSourceInfo_Release(OH_ImageSource_Info *info)
```

**Description**

Releases the pointer to an OH_ImageSource_Info object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to an OH_ImageSource_Info object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr. |

### OH_DecodingOptions_Create()

```c
Image_ErrorCode OH_DecodingOptions_Create(OH_DecodingOptions **options)
```

**Description**

Creates the pointer to an OH_DecodingOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) **options | Double pointer to the OH_DecodingOptions object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | <ul>          <li>[IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.</li>          <li>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr.</li>          </ul> |

### OH_DecodingOptions_GetPixelFormat()

```c
Image_ErrorCode OH_DecodingOptions_GetPixelFormat(OH_DecodingOptions *options, int32_t *pixelFormat)
```

**Description**

Obtains the pixel format.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t *pixelFormat | Pointer to the pixel format. For details about the available options, see {@link PIXEL_FORMAT}. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or pixelFormat is nullptr. |

### OH_DecodingOptions_SetPixelFormat()

```c
Image_ErrorCode OH_DecodingOptions_SetPixelFormat(OH_DecodingOptions *options, int32_t pixelFormat)
```

**Description**

Sets the pixel format.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t pixelFormat | Pixel format. For details about the available options, see {@link PIXEL_FORMAT}. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_DecodingOptions_GetIndex()

```c
Image_ErrorCode OH_DecodingOptions_GetIndex(OH_DecodingOptions *options, uint32_t *index)
```

**Description**

Obtains the index of an image.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| uint32_t *index | Pointer to the index of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or index is nullptr. |

### OH_DecodingOptions_SetIndex()

```c
Image_ErrorCode OH_DecodingOptions_SetIndex(OH_DecodingOptions *options, uint32_t index)
```

**Description**

Sets the index for an image.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| uint32_t index | Index of the image. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_DecodingOptions_GetRotate()

```c
Image_ErrorCode OH_DecodingOptions_GetRotate(OH_DecodingOptions *options, float *rotate)
```

**Description**

Obtains the rotation degree.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| float *rotate | Pointer to the angle to rotate, in degrees. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or rotate is nullptr. |

### OH_DecodingOptions_SetRotate()

```c
Image_ErrorCode OH_DecodingOptions_SetRotate(OH_DecodingOptions *options, float rotate)
```

**Description**

Sets the rotation angle.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| float rotate | Angle to rotate, in degrees. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_DecodingOptions_GetDesiredSize()

```c
Image_ErrorCode OH_DecodingOptions_GetDesiredSize(OH_DecodingOptions *options, Image_Size *desiredSize)
```

**Description**

Obtains the desired output size.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| Image_Size *desiredSize | Pointer to the desired output size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or desiredSize is nullptr. |

### OH_DecodingOptions_SetDesiredSize()

```c
Image_ErrorCode OH_DecodingOptions_SetDesiredSize(OH_DecodingOptions *options, Image_Size *desiredSize)
```

**Description**

Sets the desired output size.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| Image_Size *desiredSize | Pointer to the desired output size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or desiredSize is nullptr. |

### OH_DecodingOptions_GetDesiredRegion()

```c
Image_ErrorCode OH_DecodingOptions_GetDesiredRegion(OH_DecodingOptions *options, Image_Region *desiredRegion)
```

**Description**

Obtains the region to decode. Since the corresponding **SetDesiredRegion** function cannot meet the regional decoding requirements, starting from API version 19, you are advised to use [OH_DecodingOptions_GetCropRegion](capi-image-source-native-h.md#oh_decodingoptions_getcropregion) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| Image_Region *desiredRegion | Pointer to the region to decode. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or desiredRegion is nullptr. |

### OH_DecodingOptions_SetDesiredRegion()

```c
Image_ErrorCode OH_DecodingOptions_SetDesiredRegion(OH_DecodingOptions *options, Image_Region *desiredRegion)
```

**Description**

Sets the region to decode. The actual decoding will process the entire original image, without any regional decoding effect. Starting from API version 19, you are advised to use [OH_DecodingOptions_SetCropRegion](capi-image-source-native-h.md#oh_decodingoptions_setcropregion) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| Image_Region *desiredRegion | Pointer to the region to decode. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options or desiredRegion is nullptr. |

### OH_DecodingOptions_GetDesiredDynamicRange()

```c
Image_ErrorCode OH_DecodingOptions_GetDesiredDynamicRange(OH_DecodingOptions *options, int32_t *desiredDynamicRange)
```

**Description**

Obtains the desired dynamic range configured during decoding.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t *desiredDynamicRange | Pointer to the desired dynamic range. For details about the available options, see [IMAGE_DYNAMIC_RANGE](capi-image-source-native-h.md#image_dynamic_range). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, or desiredDynamicRange is nullptr. |

### OH_DecodingOptions_SetDesiredDynamicRange()

```c
Image_ErrorCode OH_DecodingOptions_SetDesiredDynamicRange(OH_DecodingOptions *options, int32_t desiredDynamicRange)
```

**Description**

Sets the desired dynamic range during decoding.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t desiredDynamicRange | Desired dynamic range. For details about the available options, see [IMAGE_DYNAMIC_RANGE](capi-image-source-native-h.md#image_dynamic_range). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_DecodingOptions_GetCropAndScaleStrategy()

```c
Image_ErrorCode OH_DecodingOptions_GetCropAndScaleStrategy(OH_DecodingOptions *options, int32_t *cropAndScaleStrategy)
```

**Description**

Obtains the cropping and scaling strategy used during decoding.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t *cropAndScaleStrategy | Pointer to the cropping and scaling strategy that is executed when **desiredSize** and **desiredRegion** are both specified. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The execution is successful.       <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode): options or cropAndScaleStrategy is a null pointer. |

### OH_DecodingOptions_SetCropAndScaleStrategy()

```c
Image_ErrorCode OH_DecodingOptions_SetCropAndScaleStrategy(OH_DecodingOptions *options, int32_t cropAndScaleStrategy)
```

**Description**

Sets the cropping and scaling strategy used during decoding.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |
| int32_t cropAndScaleStrategy | Cropping and scaling strategy that is executed when **desiredSize** and **desiredRegion**<br>are both specified. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is a null pointer or cropAndScaleStrategy is not in the range of Image_CropAndScaleStrategy. |

### OH_DecodingOptions_SetDesiredColorSpace()

```c
Image_ErrorCode OH_DecodingOptions_SetDesiredColorSpace(OH_DecodingOptions *options, int32_t colorSpace)
```

**Description**

Sets the desired color space for the decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| int32_t colorSpace | Color space. For details, see {@link ColorSpaceName}. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options is a null pointer or colorSpace is not supported. |

### OH_DecodingOptions_GetDesiredColorSpace()

```c
Image_ErrorCode OH_DecodingOptions_GetDesiredColorSpace(OH_DecodingOptions *options, int32_t *colorSpace)
```

**Description**

Obtains the color space set in the decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| int32_t *colorSpace | Pointer to the color space. For details, see {@link ColorSpaceName}. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options or colorSpace is null pointer. |

### OH_DecodingOptions_SetCropRegion()

```c
Image_ErrorCode OH_DecodingOptions_SetCropRegion(OH_DecodingOptions *options, Image_Region *cropRegion)
```

**Description**

Sets the cropping region in the decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| Image_Region *cropRegion | Pointer to the cropping region. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options or cropRegion is null pointer. |

### OH_DecodingOptions_GetCropRegion()

```c
Image_ErrorCode OH_DecodingOptions_GetCropRegion(OH_DecodingOptions *options, Image_Region *cropRegion)
```

**Description**

Obtains the cropping region in the decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| Image_Region *cropRegion | Pointer to the cropping region. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if options or cropRegion is null pointer. |

### OH_DecodingOptions_Release()

```c
Image_ErrorCode OH_DecodingOptions_Release(OH_DecodingOptions *options)
```

**Description**

Releases the pointer to an OH_DecodingOptions object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to an OH_DecodingOptions object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) if options is a null pointer. |

### OH_ImageSourceNative_CreateFromUri()

```c
Image_ErrorCode OH_ImageSourceNative_CreateFromUri(char *uri, size_t uriSize, OH_ImageSourceNative **res)
```

**Description**

Creates the pointer to an OH_ImageSourceNative object based on a URI.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *uri | Pointer to the URI of the image source. Only file URIs or Base64 URIs are accepted. Currently, only absolute paths are supported. |
| size_t uriSize | URI length. |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) **res | Double pointer to the OH_ImageSourceNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) if uri is a null pointer. |

### OH_ImageSourceNative_CreateFromFd()

```c
Image_ErrorCode OH_ImageSourceNative_CreateFromFd(int32_t fd, OH_ImageSourceNative **res)
```

**Description**

Creates the pointer to an OH_ImageSourceNative object based on a file descriptor.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fd | File descriptor. |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) **res | Double pointer to the OH_ImageSourceNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) if fd is invalid. |

### OH_ImageSourceNative_CreateFromData()

```c
Image_ErrorCode OH_ImageSourceNative_CreateFromData(uint8_t *data, size_t dataSize, OH_ImageSourceNative **res)
```

**Description**

Creates the pointer to an OH_ImageSourceNative object based on buffer data. The buffer data must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [OH_PixelmapNative_CreatePixelmap](capi-pixelmap-native-h.md#oh_pixelmapnative_createpixelmap).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Pointer to the buffer data. |
| size_t dataSize | Size of the buffer. |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) **res | Double pointer to the OH_ImageSourceNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) if data is a null pointer or if dataSize is 0. |

### OH_ImageSourceNative_CreateFromDataWithUserBuffer()

```c
Image_ErrorCode OH_ImageSourceNative_CreateFromDataWithUserBuffer(uint8_t *data, size_t datalength, OH_ImageSourceNative **imageSource)
```

**Description**

Creates an image source from data buffer. The data buffer is directly accessed by the image source object, and therefore the data buffer must remain accessible within the lifecycle of the image source object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Pointer to the data buffer. |
| size_t datalength | Size of the data buffer. |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) **imageSource | Double pointer to the image source. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.       <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if data or imageSource is a null pointer or if datalength is 0. |

### OH_ImageSourceNative_CreateFromRawFile()

```c
Image_ErrorCode OH_ImageSourceNative_CreateFromRawFile(RawFileDescriptor *rawFile, OH_ImageSourceNative **res)
```

**Description**

Creates the pointer to an OH_ImageSourceNative object by using the raw file descriptor of an image resource file.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| RawFileDescriptor *rawFile | Pointer to the file descriptor of the raw file. |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) **res | Double pointer to the OH_ImageSourceNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) if rawFile is a null pointer. |

### OH_ImageSourceNative_CreatePixelmap()

```c
Image_ErrorCode OH_ImageSourceNative_CreatePixelmap(OH_ImageSourceNative *source, OH_DecodingOptions *options, OH_PixelmapNative **pixelmap)
```

**Description**

Creates the pointer to an OH_PixelmapNative object based on decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| OH_PixelmapNative **pixelmap | Double pointer to the OH_PixelmapNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_OPTIONS](capi-image-common-h.md#image_errorcode) unsupported options,          e.g, cannot convert image into desired pixel format. |

### OH_ImageSourceNative_CreatePixelmapUsingAllocator()

```c
Image_ErrorCode OH_ImageSourceNative_CreatePixelmapUsingAllocator(OH_ImageSourceNative *source, OH_DecodingOptions *options, IMAGE_ALLOCATOR_TYPE allocator, OH_PixelmapNative **pixelmap)
```

**Description**

Creates an OH_PixelmapNative object based on decoding options and memory type, where **allocatorType**<br>specifies the memory type of the PixelMap. By default, the system selects an appropriate memory type based on the image type, image size, and platform capability. When processing the returned PixelMap object, consider the impact of stride.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| [IMAGE_ALLOCATOR_TYPE](capi-image-source-native-h.md#image_allocator_type) allocator | Memory type used by the returned PixelMap. |
| OH_PixelmapNative **pixelmap | Double pointer to the OH_PixelmapNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Result code. |

### OH_ImageSourceNative_CreatePixelmapList()

```c
Image_ErrorCode OH_ImageSourceNative_CreatePixelmapList(OH_ImageSourceNative *source, OH_DecodingOptions *options, OH_PixelmapNative *resVecPixMap[], size_t size)
```

**Description**

Creates an array of OH_PixelmapNative objects based on decoding options. This function decodes all frames at once. If the number of frames is high or the size of individual frames is large, it can lead to significant memory usage. In these cases, you are advised to use the **Image** component for displaying animations. The **Image** component decodes frames one by one, which uses less memory than this function.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| [OH_DecodingOptions](capi-image-nativemodule-oh-decodingoptions.md) *options | Pointer to the decoding options. |
| OH_PixelmapNative *resVecPixMap[] | Indicates a pointer array to the <b>Pixelmap</b> objects obtained at the C++ native layer. It cannot be a null pointer. |
| size_t size | Size of the array. You can use [OH_ImageSourceNative_GetFrameCount](capi-image-source-native-h.md#oh_imagesourcenative_getframecount) to obtain the size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or options is nullptr, or resVecPixMap is nullptr. |

### OH_ImageSourceNative_CreatePicture()

```c
Image_ErrorCode OH_ImageSourceNative_CreatePicture(OH_ImageSourceNative *source, OH_DecodingOptionsForPicture *options, OH_PictureNative **picture)
```

**Description**

Creates the pointer to an OH_PictureNative object based on decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to the decoding options. |
| OH_PictureNative **picture | Double pointer to the OH_PictureNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or picture is nullptr.      <br>[IMAGE_DECODE_FAILED](capi-image-common-h.md#image_errorcode) decode failed. |

### OH_ImageSourceNative_CreatePictureAtIndex()

```c
Image_ErrorCode OH_ImageSourceNative_CreatePictureAtIndex(OH_ImageSourceNative *source, uint32_t index, OH_PictureNative **picture)
```

**Description**

Creates the pointer to an OH_PictureNative object at the specified index.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| uint32_t index | Index of the image. |
| OH_PictureNative **picture | Double pointer to the OH_PictureNative object created at the C++ local layer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode): The execution is successful.<br>    <br>[IMAGE_BAD_SOURCE](capi-image-common-h.md#image_errorcode): The data source is abnormal.<br>    <br>{@link IMAGE_SOURCE_UNSUPPORTED_MIMETYPE}: The image format is unsupported.<br>    <br>[IMAGE_SOURCE_TOO_LARGE](capi-image-common-h.md#image_errorcode): The image is too large.<br>    <br>[IMAGE_SOURCE_UNSUPPORTED_OPTIONS](capi-image-common-h.md#image_errorcode): The operation is not supported, for example, invalid index.<br>    <br>[IMAGE_DECODE_FAILED](capi-image-common-h.md#image_errorcode): Decoding fails. |

### OH_ImageSourceNative_GetDelayTimeList()

```c
Image_ErrorCode OH_ImageSourceNative_GetDelayTimeList(OH_ImageSourceNative *source, int32_t *delayTimeList, size_t size)
```

**Description**

Obtains the image delay time list.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| int32_t *delayTimeList | Pointer to the delay time list obtained. It cannot be a null pointer. |
| size_t size | Size of the delay time list. You can use [OH_ImageSourceNative_GetFrameCount](capi-image-source-native-h.md#oh_imagesourcenative_getframecount) to obtain the size. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or delayTimeList is nullptr. |

### OH_ImageSourceNative_GetImageInfo()

```c
Image_ErrorCode OH_ImageSourceNative_GetImageInfo(OH_ImageSourceNative *source, int32_t index, OH_ImageSource_Info *info)
```

**Description**

Obtains the information about an image with a given index.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| int32_t index | Index of an image. For a GIF image, the value range is [0, N-1], where N indicates the number of GIF frames. For an image with only one frame, you can pass in **0**. |
| [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md) *info | Pointer to the image information obtained, which is an OH_ImageSource_Info struct. For details, see [OH_ImageSource_Info](capi-image-nativemodule-oh-imagesource-info.md). |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or info is nullptr, or failed to get image info. |

### OH_ImageSourceNative_GetImageProperty()

```c
Image_ErrorCode OH_ImageSourceNative_GetImageProperty(OH_ImageSourceNative *source, Image_String *key, Image_String *value)
```

**Description**

Obtains the value of an image property.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| Image_String *key | Pointer to the property key. For details, see [Image_String](capi-image-nativemodule-image-string.md). For details about the value range of **key**, see the definition of {@link OHOS_IMAGE_PROPERTY_XXX}<br>    . The memory must be released after the image source is used. For details, see [OH_ImageSourceNative_Release](capi-image-source-native-h.md#oh_imagesourcenative_release). |
| Image_String *value | Pointer to the value obtained. You can pass in a null pointer with the size set to zero. In this case, the system will allocate memory, but you must release the memory after use. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or key is nullptr, or value is nullptr.      <br>[IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) allocate memory failed.      <br>[IMAGE_COPY_FAILED](capi-image-common-h.md#image_errorcode) copy memory failed. |

### OH_ImageSourceNative_GetImagePropertyWithNull()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyWithNull(OH_ImageSourceNative *source, Image_String *key, Image_String *value)
```

**Description**

Obtains the value of an image property from an <b>ImageSource</b> object. The output value.data is null-terminated.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to ImageSource. |
| Image_String *key | Pointer to the property key. |
| Image_String *value | Pointer to the property value. Output Parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr. |

### OH_ImageSourceNative_ModifyImageProperty()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImageProperty(OH_ImageSourceNative *source, Image_String *key, Image_String *value)
```

**Description**

Obtains the value of an image property. The output **value.data** is terminated with a string terminator.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| Image_String *key | Pointer to the property key. |
| Image_String *value | Pointer to the value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or key is nullptr, or value is nullptr,          or failed to modify image property because of invalid parameters. |

### OH_ImageSourceNative_GetFrameCount()

```c
Image_ErrorCode OH_ImageSourceNative_GetFrameCount(OH_ImageSourceNative *source, uint32_t *frameCount)
```

**Description**

Obtains the number of image frames.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |
| uint32_t *frameCount | Indicates a pointer to the number of frames obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr, or frameCount is nullptr. |

### OH_ImageSourceNative_Release()

```c
Image_ErrorCode OH_ImageSourceNative_Release(OH_ImageSourceNative *source)
```

**Description**

Releases the pointer to an OH_ImageSourceNative object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to an OH_ImageSourceNative object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) source is nullptr. |

### OH_DecodingOptionsForPicture_Create()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_Create(OH_DecodingOptionsForPicture **options)
```

**Description**

Creates the pointer to an OH_DecodingOptionsForPicture object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) **options | Double pointer to the OH_DecodingOptionsForPicture object created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_DecodingOptionsForPicture_GetDesiredAuxiliaryPictures()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_GetDesiredAuxiliaryPictures(OH_DecodingOptionsForPicture *options, Image_AuxiliaryPictureType **desiredAuxiliaryPictures, size_t *length)
```

**Description**

Obtains desired auxiliary pictures in the decoding options (auxiliary pictures contained in **picture**<br>expected to be decoded.)

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to an OH_DecodingOptionsForPicture object. |
| Image_AuxiliaryPictureType **desiredAuxiliaryPictures | Double pointer to the desired auxiliary pictures. |
| size_t *length | Length of the desired auxiliary pictures. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, desiredAuxiliaryPictures is nullptr,          or length is invalid. |

### OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_SetDesiredAuxiliaryPictures(OH_DecodingOptionsForPicture *options, Image_AuxiliaryPictureType *desiredAuxiliaryPictures, size_t length)
```

**Description**

Sets desired auxiliary pictures in the decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to an OH_DecodingOptionsForPicture object. |
| Image_AuxiliaryPictureType *desiredAuxiliaryPictures | Pointer to the desired auxiliary pictures. |
| size_t length | Length of the desired auxiliary pictures. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr, desiredAuxiliaryPictures is nullptr,          or length is invalid. |

### OH_DecodingOptionsForPicture_Release()

```c
Image_ErrorCode OH_DecodingOptionsForPicture_Release(OH_DecodingOptionsForPicture *options)
```

**Description**

Releases the pointer to an OH_DecodingOptionsForPicture object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DecodingOptionsForPicture](capi-image-nativemodule-oh-decodingoptionsforpicture.md) *options | Pointer to an OH_DecodingOptionsForPicture object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) options is nullptr. |

### OH_ImageSourceNative_GetSupportedFormats()

```c
Image_ErrorCode OH_ImageSourceNative_GetSupportedFormats(Image_MimeType** supportedFormats, size_t* length)
```

**Description**

Obtains the supported image formats that can be decoded.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Image_MimeType** supportedFormats | Double pointer to the supported image formats. |
| size_t* length | Pointer to the size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if <b>supportedFormats</b> or <b>length</b> is empty. |

### OH_ImageSourceNative_GetImagePropertyShort()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyShort(OH_ImageSourceNative *source, Image_String *key, uint16_t *value)
```

**Description**

Obtains the value of an image property as short int type.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| uint16_t *value | Query result. Output Parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a short int value. |

### OH_ImageSourceNative_GetImagePropertyLong()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyLong(OH_ImageSourceNative *source, Image_String *key, uint32_t *value)
```

**Description**

Obtains the value of an image property as long int type.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| uint32_t *value | Query result. Output Parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a long int value. |

### OH_ImageSourceNative_GetImagePropertyDouble()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyDouble(OH_ImageSourceNative *source, Image_String *key, double *value)
```

**Description**

Obtains the value of an image property as double type.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| double *value | Query result. Output Parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a double value. |

### OH_ImageSourceNative_GetImagePropertyArraySize()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyArraySize(OH_ImageSourceNative *source, Image_String *key, size_t *size)
```

**Description**

Gets the array length of an array type property or the string length of a string type property.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| size_t *size | Array length for an array type property, string length for a string type property. Output Parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or size is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a array\string value. |

### OH_ImageSourceNative_GetImagePropertyString()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyString(OH_ImageSourceNative *source, Image_String *key, char *value, size_t size)
```

**Description**

Obtains the value of an image property as string type.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| char *value | Query result. Output Parameter. The caller needs to manage memory application and release. |
| size_t size | String length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key, value or size is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a string value. |

### OH_ImageSourceNative_GetImagePropertyIntArray()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyIntArray(OH_ImageSourceNative *source, Image_String *key, int32_t *value, size_t size)
```

**Description**

Obtains the value of an image property as int array.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| int32_t *value | Query result. Output Parameter. The caller needs to manage memory application and release. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key, value or size is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a int array. |

### OH_ImageSourceNative_GetImagePropertyDoubleArray()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyDoubleArray(OH_ImageSourceNative *source, Image_String *key, double *value, size_t size)
```

**Description**

Obtains the value of an image property as double array.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| double *value | Query result. Output Parameter. The caller needs to manage memory application and release. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key, value or size is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a double array. |

### OH_ImageSourceNative_GetImagePropertyBlob()

```c
Image_ErrorCode OH_ImageSourceNative_GetImagePropertyBlob(OH_ImageSourceNative *source, Image_String *key, void *value, size_t size)
```

**Description**

Obtains the value of an image property as blob.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is queried. |
| Image_String *key | The property to be queried. |
| void *value | Query result. Output Parameter. The caller needs to manage memory application and release. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key, value or size is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a blob. |

### OH_ImageSourceNative_ModifyImagePropertyShort()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyShort(OH_ImageSourceNative *source, Image_String *key, uint16_t value)
```

**Description**

Modify the value of an image property as short int.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| uint16_t value | The value set to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a short int. |

### OH_ImageSourceNative_ModifyImagePropertyLong()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyLong(OH_ImageSourceNative *source, Image_String *key, uint32_t value)
```

**Description**

Modify the value of an image property as long int.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| uint32_t value | The value set to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a long int. |

### OH_ImageSourceNative_ModifyImagePropertyDouble()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyDouble(OH_ImageSourceNative *source, Image_String *key, double value)
```

**Description**

Modify the value of an image property as double.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| double value | The value set to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a double. |

### OH_ImageSourceNative_ModifyImagePropertyIntArray()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyIntArray(OH_ImageSourceNative *source, Image_String *key, int32_t *value, size_t size)
```

**Description**

Modify the value of an image property as int array.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| int32_t *value | The value set to the property. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not an int array. |

### OH_ImageSourceNative_ModifyImagePropertyDoubleArray()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyDoubleArray(OH_ImageSourceNative *source, Image_String *key, double *value, size_t size)
```

**Description**

Modify the value of an image property as double array.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| double *value | The value set to the property. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a double array. |

### OH_ImageSourceNative_ModifyImagePropertyBlob()

```c
Image_ErrorCode OH_ImageSourceNative_ModifyImagePropertyBlob(OH_ImageSourceNative *source, Image_String *key, void *value, size_t size)
```

**Description**

Modify the value of an image property as blob.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | ImageSource from which the property is modified. |
| Image_String *key | The property to be modified. |
| void *value | The value set to the property. |
| size_t size | Array length. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if source, key or value is nullptr.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) if query image property of current mimetype is not supported.      <br>[IMAGE_SOURCE_UNSUPPORTED_METADATA](capi-image-common-h.md#image_errorcode) if indicated metadata doesn't exist, or is not a blob. |

### OH_ImageSourceNative_CreateImageRawData()

```c
Image_ErrorCode OH_ImageSourceNative_CreateImageRawData(const OH_ImageSourceNative *source, OH_ImageRawData **rawData)
```

**Description**

Obtains rawData object from an image. The rawData object usually occupies a large amount of memory because it contains raw data from the camera. When the rawData object and the data it contains are not used, call the [OH_ImageSourceNative_DestroyImageRawData](capi-image-source-native-h.md#oh_imagesourcenative_destroyimagerawdata) method to destroy them in a timely manner.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ImageSourceNative](capi-image-nativemodule-oh-imagesourcenative.md) *source | Pointer to the image source. |
| [OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md) **rawData | Double pointer to the rawData object obtained after decoding. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_BAD_SOURCE](capi-image-common-h.md#image_errorcode) Bad source.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if the rawData object is invalid.      <br>[IMAGE_SOURCE_UNSUPPORTED_MIME_TYPE](capi-image-common-h.md#image_errorcode) Unsupported MIME type. |

### OH_ImageSourceNative_GetBufferFromRawData()

```c
Image_ErrorCode OH_ImageSourceNative_GetBufferFromRawData(const OH_ImageRawData *rawData, uint8_t **data, size_t *length)
```

**Description**

Gets binary data from the rawData object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md) *rawData | Pointer to the rawData object. |
| uint8_t **data | Pointer to the binary buffer data. |
| size_t *length | Pointer to the length of data obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if the rawData object is invalid. |

### OH_ImageSourceNative_GetBitsPerPixelFromRawData()

```c
Image_ErrorCode OH_ImageSourceNative_GetBitsPerPixelFromRawData(const OH_ImageRawData *rawData, uint8_t *bitsPerPixel)
```

**Description**

Gets number of bits that each pixel actually occupies in the buffer data.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md) *rawData | Pointer to the rawData object. |
| uint8_t *bitsPerPixel | Pointer to the bitsPerPixel obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if the rawData object is invalid. |

### OH_ImageSourceNative_DestroyImageRawData()

```c
Image_ErrorCode OH_ImageSourceNative_DestroyImageRawData(OH_ImageRawData *rawData)
```

**Description**

Destroys the rawData object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageRawData](capi-image-nativemodule-oh-imagerawdata.md) *rawData | Pointer to the rawData object. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      <br>[IMAGE_SOURCE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) if the rawData object is invalid. |


