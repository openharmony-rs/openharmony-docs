# pixelmap_native.h

## Overview

Declares the APIs that can access a pixel map.

**Library**: libpixelmap.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Pixelmap_HdrStaticMetadata](capi-image-nativemodule-oh-pixelmap-hdrstaticmetadata.md) | OH_Pixelmap_HdrStaticMetadata | Value for HDR_STATIC_METADATA. |
| [OH_Pixelmap_HdrDynamicMetadata](capi-image-nativemodule-oh-pixelmap-hdrdynamicmetadata.md) | OH_Pixelmap_HdrDynamicMetadata | Value for HDR_DYNAMIC_METADATA. |
| [OH_Pixelmap_HdrGainmapMetadata](capi-image-nativemodule-oh-pixelmap-hdrgainmapmetadata.md) | OH_Pixelmap_HdrGainmapMetadata | Value for HDR_GAINMAP_METADATA. |
| [OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md) | OH_Pixelmap_HdrMetadataValue | Value for HDR_METADATA_KEY. Corresponding relationship with HDR_METADATA_KEY. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) | - | Define a Pixelmap struct type, used for pixelmap pointer controls. |
| [OH_NativeBuffer](capi-image-nativemodule-oh-nativebuffer.md) | - | Define a native buffer type, used for retrieving a native buffer. |
| [OH_NativeColorSpaceManager](capi-image-nativemodule-oh-nativecolorspacemanager.md) | OH_NativeColorSpaceManager | Define a native ColorSpaceManager type, used for retrieving a native ColorSpaceManager. |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) | - | Defines the options used for creating a pixel map. |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) | - | Defines the pixel map information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PIXELMAP_ALPHA_TYPE](#pixelmap_alpha_type) | PIXELMAP_ALPHA_TYPE | Define a pixelmap alpha type. |
| [OH_PixelmapNative_AntiAliasingLevel](#oh_pixelmapnative_antialiasinglevel) | OH_PixelmapNative_AntiAliasingLevel | Defines the anti-aliasing level. |
| [OH_Pixelmap_HdrMetadataKey](#oh_pixelmap_hdrmetadatakey) | OH_Pixelmap_HdrMetadataKey | Enumerates the HDR metadata types that need to be stored in Pixelmap. |
| [OH_Pixelmap_HdrMetadataType](#oh_pixelmap_hdrmetadatatype) | OH_Pixelmap_HdrMetadataType | Value for HDR_METADATA_TYPE. |

### Function

| Name | Description |
| -- | -- |
| [Image_ErrorCode OH_PixelmapInitializationOptions_Create(OH_Pixelmap_InitializationOptions **options)](#oh_pixelmapinitializationoptions_create) | Create a for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetWidth(OH_Pixelmap_InitializationOptions *options, uint32_t *width)](#oh_pixelmapinitializationoptions_getwidth) | Get width number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetWidth(OH_Pixelmap_InitializationOptions *options, uint32_t width)](#oh_pixelmapinitializationoptions_setwidth) | Set width number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetHeight(OH_Pixelmap_InitializationOptions *options, uint32_t *height)](#oh_pixelmapinitializationoptions_getheight) | Get height number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetHeight(OH_Pixelmap_InitializationOptions *options, uint32_t height)](#oh_pixelmapinitializationoptions_setheight) | Set height number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t *pixelFormat)](#oh_pixelmapinitializationoptions_getpixelformat) | Get pixelFormat number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t pixelFormat)](#oh_pixelmapinitializationoptions_setpixelformat) | Set pixelFormat number for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetSrcPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t *srcpixelFormat)](#oh_pixelmapinitializationoptions_getsrcpixelformat) | Get pixelFormat number for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetSrcPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t srcpixelFormat)](#oh_pixelmapinitializationoptions_setsrcpixelformat) | Set pixelFormat number for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetRowStride(OH_Pixelmap_InitializationOptions *options, int32_t *rowStride)](#oh_pixelmapinitializationoptions_getrowstride) | Get rowStride for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetRowStride(OH_Pixelmap_InitializationOptions *options, int32_t rowStride)](#oh_pixelmapinitializationoptions_setrowstride) | Set rowStride number for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetAlphaType(OH_Pixelmap_InitializationOptions *options, int32_t *alphaType)](#oh_pixelmapinitializationoptions_getalphatype) | Get alphaType number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetAlphaType(OH_Pixelmap_InitializationOptions *options, int32_t alphaType)](#oh_pixelmapinitializationoptions_setalphatype) | Set alphaType number for InitializationOtions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_GetEditable(OH_Pixelmap_InitializationOptions *options, bool *editable)](#oh_pixelmapinitializationoptions_geteditable) | Get editable for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_SetEditable(OH_Pixelmap_InitializationOptions *options, bool editable)](#oh_pixelmapinitializationoptions_seteditable) | Set editable for InitializationOptions struct. |
| [Image_ErrorCode OH_PixelmapInitializationOptions_Release(OH_Pixelmap_InitializationOptions *options)](#oh_pixelmapinitializationoptions_release) | delete InitializationOtions pointer. |
| [Image_ErrorCode OH_PixelmapImageInfo_Create(OH_Pixelmap_ImageInfo **info)](#oh_pixelmapimageinfo_create) | Create imageinfo struct . |
| [Image_ErrorCode OH_PixelmapImageInfo_GetWidth(OH_Pixelmap_ImageInfo *info, uint32_t *width)](#oh_pixelmapimageinfo_getwidth) | Get width number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetHeight(OH_Pixelmap_ImageInfo *info, uint32_t *height)](#oh_pixelmapimageinfo_getheight) | Get height number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetAlphaMode(OH_Pixelmap_ImageInfo *info, int32_t *alphaMode)](#oh_pixelmapimageinfo_getalphamode) | Get alphaMode number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetRowStride(OH_Pixelmap_ImageInfo *info, uint32_t *rowStride)](#oh_pixelmapimageinfo_getrowstride) | Get rowStride number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetPixelFormat(OH_Pixelmap_ImageInfo *info, int32_t *pixelFormat)](#oh_pixelmapimageinfo_getpixelformat) | Get pixelFormat number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetAlphaType(OH_Pixelmap_ImageInfo *info, int32_t *alphaType)](#oh_pixelmapimageinfo_getalphatype) | Get alphaType number for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_GetDynamicRange(OH_Pixelmap_ImageInfo *info, bool *isHdr)](#oh_pixelmapimageinfo_getdynamicrange) | Get isHdr boolean for imageinfo struct. |
| [Image_ErrorCode OH_PixelmapImageInfo_Release(OH_Pixelmap_ImageInfo *info)](#oh_pixelmapimageinfo_release) | Delete imageinfo struct pointer. |
| [Image_ErrorCode OH_PixelmapNative_CreatePixelmap(uint8_t *data, size_t dataLength, OH_Pixelmap_InitializationOptions *options, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createpixelmap) | Creates a <b>PixelMap</b> object. |
| [Image_ErrorCode OH_PixelmapNative_CreatePixelmapUsingAllocator(uint8_t *data, size_t dataLength, OH_Pixelmap_InitializationOptions *options, IMAGE_ALLOCATOR_MODE allocator, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createpixelmapusingallocator) | Creates a pixelmap based on options [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md), the memory type used by the pixelmap can be specified by allocatorType [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the pixelmap returned by this interface, please always consider the impact of stride. |
| [Image_ErrorCode OH_PixelmapNative_ConvertPixelmapNativeToNapi(napi_env env, OH_PixelmapNative *pixelmapNative, napi_value *pixelmapNapi)](#oh_pixelmapnative_convertpixelmapnativetonapi) | Convert a native <b>PixelMap</b> object to <b>PixelMap</b> napi object. |
| [Image_ErrorCode OH_PixelmapNative_ConvertPixelmapNativeFromNapi(napi_env env, napi_value pixelmapNapi, OH_PixelmapNative **pixelmapNative)](#oh_pixelmapnative_convertpixelmapnativefromnapi) | Convert a <b>PixelMap</b> napi object to native <b>PixelMap</b> object. |
| [Image_ErrorCode OH_PixelmapNative_ReadPixels(OH_PixelmapNative *pixelmap, uint8_t *destination, size_t *bufferSize)](#oh_pixelmapnative_readpixels) | Reads data of this pixel map to an Buffer. If this pixel map is created in the BGRA_8888 format, the data read is the same as the original data. |
| [Image_ErrorCode OH_PixelmapNative_WritePixels(OH_PixelmapNative *pixelmap, uint8_t *source, size_t bufferSize)](#oh_pixelmapnative_writepixels) | Reads image data in an Buffer and writes the data to a Pixelmap object. |
| [Image_ErrorCode OH_PixelmapNative_ReadPixelsFromArea(OH_PixelmapNative *pixelmap, Image_PositionArea *area)](#oh_pixelmapnative_readpixelsfromarea) | Reads data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format. |
| [Image_ErrorCode OH_PixelmapNative_WritePixelsToArea(OH_PixelmapNative *pixelmap, Image_PositionArea *area)](#oh_pixelmapnative_writepixelstoarea) | Writes data from a buffer to a certain area of the PixelMap. The source data should be in BGRA_8888 format. |
| [Image_ErrorCode OH_PixelmapNative_GetArgbPixels(OH_PixelmapNative *pixelmap, uint8_t *destination, size_t *bufferSize)](#oh_pixelmapnative_getargbpixels) | Get argb pixel buffer from pixelmap. |
| [Image_ErrorCode OH_PixelmapNative_ToSdr(OH_PixelmapNative *pixelmap)](#oh_pixelmapnative_tosdr) | Convert [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) to standard dynamic range. |
| [Image_ErrorCode OH_PixelmapNative_GetImageInfo(OH_PixelmapNative *pixelmap, OH_Pixelmap_ImageInfo *imageInfo)](#oh_pixelmapnative_getimageinfo) | Obtains pixel map information of this image. |
| [Image_ErrorCode OH_PixelmapNative_SetOpacity(OH_PixelmapNative *pixelmap, float value)](#oh_pixelmapnative_setopacity) | Sets opacity of the PixelMap. Every pixel will be set to the same opacity value. |
| [Image_ErrorCode OH_PixelmapNative_Opacity(OH_PixelmapNative *pixelmap, float rate)](#oh_pixelmapnative_opacity) | Sets an opacity rate for this image pixel map. It is recommended to use [OH_PixelmapNative_SetOpacity](capi-pixelmap-native-h.md#oh_pixelmapnative_setopacity). |
| [Image_ErrorCode OH_PixelmapNative_ApplyScale(OH_PixelmapNative *pixelmap, float scaleX, float scaleY)](#oh_pixelmapnative_applyscale) | Scales the PixelMap in the horizontal and/or vertical dimensions. |
| [Image_ErrorCode OH_PixelmapNative_Scale(OH_PixelmapNative *pixelmap, float scaleX, float scaleY)](#oh_pixelmapnative_scale) | Scales this image based on the input width and height. It is recommended to use [OH_PixelmapNative_ApplyScale](capi-pixelmap-native-h.md#oh_pixelmapnative_applyscale). |
| [Image_ErrorCode OH_PixelmapNative_ApplyScaleWithAntiAliasing(OH_PixelmapNative *pixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)](#oh_pixelmapnative_applyscalewithantialiasing) | Scales the PixelMap in the horizontal and/or vertical dimensions with anti-aliasing. |
| [Image_ErrorCode OH_PixelmapNative_ScaleWithAntiAliasing(OH_PixelmapNative *pixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)](#oh_pixelmapnative_scalewithantialiasing) | Scales this image based on the input width and height with anti-aliasing. It is recommended to use [OH_PixelmapNative_ApplyScaleWithAntiAliasing](capi-pixelmap-native-h.md#oh_pixelmapnative_applyscalewithantialiasing). |
| [Image_ErrorCode OH_PixelmapNative_CreateScaledPixelMap(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap, float scaleX, float scaleY)](#oh_pixelmapnative_createscaledpixelmap) | Create a scaled pixelmap based on the source pixelmap and the input width and height. |
| [Image_ErrorCode OH_PixelmapNative_CreateScaledPixelMapWithAntiAliasing(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)](#oh_pixelmapnative_createscaledpixelmapwithantialiasing) | Create a scaled pixelmap based on the source pixelmap and the input width and height with anti-aliasing. |
| [Image_ErrorCode OH_PixelmapNative_ApplyTranslate(OH_PixelmapNative *pixelmap, float x, float y)](#oh_pixelmapnative_applytranslate) | Repositions the PixelMap in the horizontal and/or vertical directions. |
| [Image_ErrorCode OH_PixelmapNative_Translate(OH_PixelmapNative *pixelmap, float x, float y)](#oh_pixelmapnative_translate) | Translates this image based on the input coordinates. It is recommended to use [OH_PixelmapNative_ApplyTranslate](capi-pixelmap-native-h.md#oh_pixelmapnative_applytranslate). |
| [Image_ErrorCode OH_PixelmapNative_CreateAlphaPixelmap(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap)](#oh_pixelmapnative_createalphapixelmap) | Creates a PixelMap with only alpha channel from the source PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_Clone(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap)](#oh_pixelmapnative_clone) | Clones a PixelMap from the source PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_CreateCroppedAndScaledPixelMap(OH_PixelmapNative *srcPixelmap, Image_Region *region, Image_Scale *scale, OH_PixelmapNative_AntiAliasingLevel level, OH_PixelmapNative **dstPixelmap)](#oh_pixelmapnative_createcroppedandscaledpixelmap) | Creates a cropped and then scaled PixelMap based on the source PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_ApplyRotate(OH_PixelmapNative *pixelmap, float angle)](#oh_pixelmapnative_applyrotate) | Rotates the PixelMap. Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees. |
| [Image_ErrorCode OH_PixelmapNative_Rotate(OH_PixelmapNative *pixelmap, float angle)](#oh_pixelmapnative_rotate) | Rotates this image based on the input angle. It is recommended to use [OH_PixelmapNative_ApplyRotate](capi-pixelmap-native-h.md#oh_pixelmapnative_applyrotate). |
| [Image_ErrorCode OH_PixelmapNative_ApplyFlip(OH_PixelmapNative *pixelmap, bool shouldFlipHorizontally, bool shouldFlipVertically)](#oh_pixelmapnative_applyflip) | Flips the PixelMap in the horizontal and/or vertical directions. |
| [Image_ErrorCode OH_PixelmapNative_Flip(OH_PixelmapNative *pixelmap, bool shouldFlipHorizontally, bool shouldFlipVertically)](#oh_pixelmapnative_flip) | Flips this image horizontally or vertically, or both. It is recommended to use [OH_PixelmapNative_ApplyFlip](capi-pixelmap-native-h.md#oh_pixelmapnative_applyflip). |
| [Image_ErrorCode OH_PixelmapNative_ApplyCrop(OH_PixelmapNative *pixelmap, Image_Region *region)](#oh_pixelmapnative_applycrop) | Crops the PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_Crop(OH_PixelmapNative *pixelmap, Image_Region *region)](#oh_pixelmapnative_crop) | Crops this image based on the input size. It is recommended to use [OH_PixelmapNative_ApplyCrop](capi-pixelmap-native-h.md#oh_pixelmapnative_applycrop). |
| [Image_ErrorCode OH_PixelmapNative_Release(OH_PixelmapNative *pixelmap)](#oh_pixelmapnative_release) | Releases an <b>OH_Pixelmap</b> object. |
| [Image_ErrorCode OH_PixelmapNative_Destroy(OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_destroy) | Destroys an <b>OH_PixelmapNative</b> object and deallocates its resources. |
| [Image_ErrorCode OH_PixelmapNative_ConvertAlphaType(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative *dstPixelmap, const bool toPremul)](#oh_pixelmapnative_convertalphatype) | Converts the alpha type of the PixelMap to either premultiplied or unpremultiplied. The conversion only supports pixel formats that have an alpha channel, except RGBA_F16. |
| [Image_ErrorCode OH_PixelmapNative_ConvertAlphaFormat(OH_PixelmapNative* srcpixelmap, OH_PixelmapNative* dstpixelmap, const bool isPremul)](#oh_pixelmapnative_convertalphaformat) | Converting images to alpha format It is recommended to use [OH_PixelmapNative_ConvertAlphaType](capi-pixelmap-native-h.md#oh_pixelmapnative_convertalphatype). |
| [Image_ErrorCode OH_PixelmapNative_CreateEmptyPixelmap(OH_Pixelmap_InitializationOptions *options, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createemptypixelmap) | Create a empty <b>PixelMap</b> object. |
| [Image_ErrorCode OH_PixelmapNative_CreateEmptyPixelmapUsingAllocator(OH_Pixelmap_InitializationOptions *options, IMAGE_ALLOCATOR_MODE allocator, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createemptypixelmapusingallocator) | Creates a empty pixelmap based on options [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md), the memory type used by the pixelmap can be specified by allocatorType [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the pixelmap returned by this interface, please always consider the impact of stride. |
| [Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromSurface(const char *surfaceId, size_t length, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createpixelmapfromsurface) | Creates a PixelMap from a Surface with the Surface ID. |
| [Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromSurfaceWithTransformation(const char *surfaceId, size_t length, bool transformEnabled, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createpixelmapfromsurfacewithtransformation) | Creates a PixelMap object based on the ID of a Surface with transformation. |
| [Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromNativeBuffer(OH_NativeBuffer *nativeBuffer, OH_PixelmapNative **pixelmap)](#oh_pixelmapnative_createpixelmapfromnativebuffer) | Creates a PixelMap from a native buffer. |
| [Image_ErrorCode OH_PixelmapNative_GetMetadata(OH_PixelmapNative *pixelmap, OH_Pixelmap_HdrMetadataKey key, OH_Pixelmap_HdrMetadataValue **value)](#oh_pixelmapnative_getmetadata) | Get metadata. |
| [Image_ErrorCode OH_PixelmapNative_SetMetadata(OH_PixelmapNative *pixelmap, OH_Pixelmap_HdrMetadataKey key, OH_Pixelmap_HdrMetadataValue *value)](#oh_pixelmapnative_setmetadata) | Set metadata. |
| [Image_ErrorCode OH_PixelmapNative_GetNativeBuffer(OH_PixelmapNative *pixelmap, OH_NativeBuffer **nativeBuffer)](#oh_pixelmapnative_getnativebuffer) | Get the native buffer from the PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_GetColorSpaceNative(OH_PixelmapNative *pixelmap, OH_NativeColorSpaceManager **colorSpaceNative)](#oh_pixelmapnative_getcolorspacenative) | Get the native colorspace from the PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_SetColorSpaceNative(OH_PixelmapNative *pixelmap, OH_NativeColorSpaceManager *colorSpaceNative)](#oh_pixelmapnative_setcolorspacenative) | Set the native colorspace for the PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_SetMemoryName(OH_PixelmapNative *pixelmap, char *name, size_t *size)](#oh_pixelmapnative_setmemoryname) | Set pixelmap memory name. |
| [Image_ErrorCode OH_PixelmapNative_GetByteCount(OH_PixelmapNative *pixelmap, uint32_t *byteCount)](#oh_pixelmapnative_getbytecount) | Get the total number of bytes occupied by all pixels in the Pixelmap, without any padding. |
| [Image_ErrorCode OH_PixelmapNative_GetAllocationByteCount(OH_PixelmapNative *pixelmap, uint32_t *allocationByteCount)](#oh_pixelmapnative_getallocationbytecount) | Get the size of the allocated memory used to store this pixelmap's pixels. |
| [Image_ErrorCode OH_PixelmapNative_AccessPixels(OH_PixelmapNative *pixelmap, void **addr)](#oh_pixelmapnative_accesspixels) | Obtains the memory address of a PixelMap and locks the memory. When the memory is locked, any operation that modifies or releases the PixelMap will fail and return [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode). |
| [Image_ErrorCode OH_PixelmapNative_UnaccessPixels(OH_PixelmapNative *pixelmap)](#oh_pixelmapnative_unaccesspixels) | Unlocks the memory of the PixelMap data. This function is used with [OH_PixelmapNative_AccessPixels](capi-pixelmap-native-h.md#oh_pixelmapnative_accesspixels) in pairs. |
| [Image_ErrorCode OH_PixelmapNative_GetUniqueId(OH_PixelmapNative *pixelmap, uint32_t *uniqueId)](#oh_pixelmapnative_getuniqueid) | Gets the unique ID of a PixelMap. |
| [Image_ErrorCode OH_PixelmapNative_IsReleased(OH_PixelmapNative *pixelmap, bool *released)](#oh_pixelmapnative_isreleased) | Checks whether the PixelMap has been released. |

## Enum type description

### PIXELMAP_ALPHA_TYPE

```c
enum PIXELMAP_ALPHA_TYPE
```

**Description**

Define a pixelmap alpha type.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| PIXELMAP_ALPHA_TYPE_UNKNOWN = 0 | Unknown format |
| PIXELMAP_ALPHA_TYPE_OPAQUE = 1 | Opaque format |
| PIXELMAP_ALPHA_TYPE_PREMULTIPLIED = 2 | Premultiplied format |
| PIXELMAP_ALPHA_TYPE_UNPREMULTIPLIED = 3 | Unpremultiplied format |

### OH_PixelmapNative_AntiAliasingLevel

```c
enum OH_PixelmapNative_AntiAliasingLevel
```

**Description**

Defines the anti-aliasing level.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_PixelmapNative_AntiAliasing_NONE = 0 | Nearest-neighbor interpolation algorithm |
| OH_PixelmapNative_AntiAliasing_LOW = 1 | Bilinear interpolation algorithm |
| OH_PixelmapNative_AntiAliasing_MEDIUM = 2 | Bilinear interpolation algorithm with mipmap linear filtering |
| OH_PixelmapNative_AntiAliasing_HIGH = 3 | Cubic interpolation algorithm |

### OH_Pixelmap_HdrMetadataKey

```c
enum OH_Pixelmap_HdrMetadataKey
```

**Description**

Enumerates the HDR metadata types that need to be stored in Pixelmap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| HDR_METADATA_TYPE = 0 | Indicate the types of metadata that image needs to use. |
| HDR_STATIC_METADATA = 1 | Static metadata key. |
| HDR_DYNAMIC_METADATA = 2 | Dynamic metadata key. |
| HDR_GAINMAP_METADATA = 3 | Gainmap metadata key. |

### OH_Pixelmap_HdrMetadataType

```c
enum OH_Pixelmap_HdrMetadataType
```

**Description**

Value for HDR_METADATA_TYPE.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| HDR_METADATA_TYPE_NONE = 0 | No metadata. |
| HDR_METADATA_TYPE_BASE = 1 | Indicates that metadata will be used for the base image. |
| HDR_METADATA_TYPE_GAINMAP = 2 | Indicates that metadata will be used for the gainmap image. |
| HDR_METADATA_TYPE_ALTERNATE = 3 | Indicates that metadata will be used for the alternate image. |


## Function description

### OH_PixelmapInitializationOptions_Create()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_Create(OH_Pixelmap_InitializationOptions **options)
```

**Description**

Create a for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) **options | The InitializationOtions pointer will be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter is nullptr or          create OH_Pixelmap_InitializationOptions object failed. |

### OH_PixelmapInitializationOptions_GetWidth()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetWidth(OH_Pixelmap_InitializationOptions *options, uint32_t *width)
```

**Description**

Get width number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| uint32_t *width | the number of image width. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options or width is null. |

### OH_PixelmapInitializationOptions_SetWidth()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetWidth(OH_Pixelmap_InitializationOptions *options, uint32_t width)
```

**Description**

Set width number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| uint32_t width | the number of image width. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapInitializationOptions_GetHeight()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetHeight(OH_Pixelmap_InitializationOptions *options, uint32_t *height)
```

**Description**

Get height number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| uint32_t *height | the number of image height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options or height is null. |

### OH_PixelmapInitializationOptions_SetHeight()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetHeight(OH_Pixelmap_InitializationOptions *options, uint32_t height)
```

**Description**

Set height number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| uint32_t height | the number of image height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapInitializationOptions_GetPixelFormat()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t *pixelFormat)
```

**Description**

Get pixelFormat number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| int32_t *pixelFormat | the number of image pixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options or pixelFormat is null. |

### OH_PixelmapInitializationOptions_SetPixelFormat()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t pixelFormat)
```

**Description**

Set pixelFormat number for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t pixelFormat | the number of image pixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapInitializationOptions_GetSrcPixelFormat()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetSrcPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t *srcpixelFormat)
```

**Description**

Get pixelFormat number for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t *srcpixelFormat | the number of image srcpixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options or srcpixelFormat is null. |

### OH_PixelmapInitializationOptions_SetSrcPixelFormat()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetSrcPixelFormat(OH_Pixelmap_InitializationOptions *options, int32_t srcpixelFormat)
```

**Description**

Set pixelFormat number for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t srcpixelFormat | the number of image srcpixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapInitializationOptions_GetRowStride()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetRowStride(OH_Pixelmap_InitializationOptions *options, int32_t *rowStride)
```

**Description**

Get rowStride for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t *rowStride | the rowStride of image buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if rowStride is null.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error, maybe options is released. |

### OH_PixelmapInitializationOptions_SetRowStride()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetRowStride(OH_Pixelmap_InitializationOptions *options, int32_t rowStride)
```

**Description**

Set rowStride number for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t rowStride | the rowStride of image buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if rowStride does not match width.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error, maybe options is released. |

### OH_PixelmapInitializationOptions_GetAlphaType()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetAlphaType(OH_Pixelmap_InitializationOptions *options, int32_t *alphaType)
```

**Description**

Get alphaType number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| int32_t *alphaType | the number of image alphaType. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options or alphaType is null. |

### OH_PixelmapInitializationOptions_SetAlphaType()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetAlphaType(OH_Pixelmap_InitializationOptions *options, int32_t alphaType)
```

**Description**

Set alphaType number for InitializationOtions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |
| int32_t alphaType | the number of image alphaType. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapInitializationOptions_GetEditable()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_GetEditable(OH_Pixelmap_InitializationOptions *options, bool *editable)
```

**Description**

Get editable for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| bool *editable | The boolean value representing the editable status. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if options or editable is invalid. |

### OH_PixelmapInitializationOptions_SetEditable()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_SetEditable(OH_Pixelmap_InitializationOptions *options, bool editable)
```

**Description**

Set editable for InitializationOptions struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOptions pointer will be operated. |
| bool editable | The boolean value representing the editable status. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if options is invalid. |

### OH_PixelmapInitializationOptions_Release()

```c
Image_ErrorCode OH_PixelmapInitializationOptions_Release(OH_Pixelmap_InitializationOptions *options)
```

**Description**

delete InitializationOtions pointer.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | The InitializationOtions pointer will be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null. |

### OH_PixelmapImageInfo_Create()

```c
Image_ErrorCode OH_PixelmapImageInfo_Create(OH_Pixelmap_ImageInfo **info)
```

**Description**

Create imageinfo struct .

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) **info | The imageinfo pointer will be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter is nullptr or          create OH_Pixelmap_ImageInfo object failed. |

### OH_PixelmapImageInfo_GetWidth()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetWidth(OH_Pixelmap_ImageInfo *info, uint32_t *width)
```

**Description**

Get width number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| uint32_t *width | The number of imageinfo width. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or width is null. |

### OH_PixelmapImageInfo_GetHeight()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetHeight(OH_Pixelmap_ImageInfo *info, uint32_t *height)
```

**Description**

Get height number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| uint32_t *height | The number of imageinfo height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or height is null. |

### OH_PixelmapImageInfo_GetAlphaMode()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetAlphaMode(OH_Pixelmap_ImageInfo *info, int32_t *alphaMode)
```

**Description**

Get alphaMode number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| int32_t *alphaMode | The number of imageinfo alphaMode. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Image functions result code.      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) info is nullptr, or alphaMode is nullptr. |

### OH_PixelmapImageInfo_GetRowStride()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetRowStride(OH_Pixelmap_ImageInfo *info, uint32_t *rowStride)
```

**Description**

Get rowStride number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| uint32_t *rowStride | The number of imageinfo rowStride. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or rowStride is null. |

### OH_PixelmapImageInfo_GetPixelFormat()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetPixelFormat(OH_Pixelmap_ImageInfo *info, int32_t *pixelFormat)
```

**Description**

Get pixelFormat number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| int32_t *pixelFormat | The number of imageinfo pixelFormat. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or pixelFormat is null. |

### OH_PixelmapImageInfo_GetAlphaType()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetAlphaType(OH_Pixelmap_ImageInfo *info, int32_t *alphaType)
```

**Description**

Get alphaType number for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |
| int32_t *alphaType | The number of imageinfo alphaType. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or alphaType is null. |

### OH_PixelmapImageInfo_GetDynamicRange()

```c
Image_ErrorCode OH_PixelmapImageInfo_GetDynamicRange(OH_Pixelmap_ImageInfo *info, bool *isHdr)
```

**Description**

Get isHdr boolean for imageinfo struct.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. Pointer connot be null. |
| bool *isHdr | Whether the image has a high dynamic range. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info or isHdr is null. |

### OH_PixelmapImageInfo_Release()

```c
Image_ErrorCode OH_PixelmapImageInfo_Release(OH_Pixelmap_ImageInfo *info)
```

**Description**

Delete imageinfo struct pointer.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *info | The imageinfo pointer will be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if info is null. |

### OH_PixelmapNative_CreatePixelmap()

```c
Image_ErrorCode OH_PixelmapNative_CreatePixelmap(uint8_t *data, size_t dataLength, OH_Pixelmap_InitializationOptions *options, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a <b>PixelMap</b> object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Color buffer in BGRA_8888 format. |
| size_t dataLength | Color buffer size in BGRA_8888 format. |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | IPixel properties, including the alpha type, size, pixel format, and editable. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | Pixelmap pointer for created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Possible causes:          if data or options is null or failed to create pixelmap due to invalid options. |

### OH_PixelmapNative_CreatePixelmapUsingAllocator()

```c
Image_ErrorCode OH_PixelmapNative_CreatePixelmapUsingAllocator(uint8_t *data, size_t dataLength, OH_Pixelmap_InitializationOptions *options, IMAGE_ALLOCATOR_MODE allocator, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a pixelmap based on options [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md), the memory type used by the pixelmap can be specified by allocatorType [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the pixelmap returned by this interface, please always consider the impact of stride.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *data | Input color buffer in BGRA_8888 format by default. |
| size_t dataLength | Length of input buffer in bytes. |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | Pixelmap initialization properties including size, pixel format, alpha type, and editable flags. |
| IMAGE_ALLOCATOR_MODE allocator | Indicate which memory type will be used by the returned pixelmap. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | Output parameter receiving the created pixelmap object pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If the param is nullptr or invalid.          [IMAGE_TOO_LARGE](capi-image-common-h.md#image_errorcode) too large data or image.          [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) unsupported operations.          [IMAGE_DMA_OPERATION_FAILED](capi-image-common-h.md#image_errorcode) DMA operation failed.          [IMAGE_ALLOCATOR_MODE_UNSUPPORTED](capi-image-common-h.md#image_errorcode) unsupported allocator mode, e.g.,          use share memory to create a HDR image as only DMA supported hdr metadata. |

### OH_PixelmapNative_ConvertPixelmapNativeToNapi()

```c
Image_ErrorCode OH_PixelmapNative_ConvertPixelmapNativeToNapi(napi_env env, OH_PixelmapNative *pixelmapNative, napi_value *pixelmapNapi)
```

**Description**

Convert a native <b>PixelMap</b> object to <b>PixelMap</b> napi object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmapNative | Indicates a pointer to the <b>PixelMap</b> object created at the native layer. |
| napi_value *pixelmapNapi | the <b>PixelMap</b> pointer will be converted. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Image functions result code.      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) pixelmapNative is nullptr |

### OH_PixelmapNative_ConvertPixelmapNativeFromNapi()

```c
Image_ErrorCode OH_PixelmapNative_ConvertPixelmapNativeFromNapi(napi_env env, napi_value pixelmapNapi, OH_PixelmapNative **pixelmapNative)
```

**Description**

Convert a <b>PixelMap</b> napi object to native <b>PixelMap</b> object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates the NAPI environment pointer. |
| napi_value pixelmapNapi | Indicates napi <b>PixelMap</b> object. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmapNative | Indicates native <b>PixelMap</b> pointer to created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Image functions result code.      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.      [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) pixelmapNative is nullptr, or pixelmapNapi is not a PixelMap |

### OH_PixelmapNative_ReadPixels()

```c
Image_ErrorCode OH_PixelmapNative_ReadPixels(OH_PixelmapNative *pixelmap, uint8_t *destination, size_t *bufferSize)
```

**Description**

Reads data of this pixel map to an Buffer. If this pixel map is created in the BGRA_8888 format, the data read is the same as the original data.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| uint8_t *destination | Buffer to which the image pixel map data will be written. |
| size_t *bufferSize | Buffer size to which the image pixel map data will be written. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) Parameter error. Possible causes:          1.Parameter is nullptr          2.pixelmap's inner pixelmap is nullptr.          3.Parameter bufferSize is less than the actual data size.          [IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) Internal unknown error, e.g.          memory copy failed or pixelmap's attributes are incorrect. |

### OH_PixelmapNative_WritePixels()

```c
Image_ErrorCode OH_PixelmapNative_WritePixels(OH_PixelmapNative *pixelmap, uint8_t *source, size_t bufferSize)
```

**Description**

Reads image data in an Buffer and writes the data to a Pixelmap object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| uint8_t *source | Buffer from which the image data will be read. |
| size_t bufferSize | Buffer size from which the image data will be read. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) if the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) Parameter error. Possible causes:          1.Parameter is nullptr          2.pixelmap's inner pixelmap is nullptr.          3.Parameter bufferSize is less than the actual data size.          [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) If the pixelmap is not editable.          [IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) Internal unknown error, e.g.          memory copy failed or pixelmap's attributes are incorrect. |

### OH_PixelmapNative_ReadPixelsFromArea()

```c
Image_ErrorCode OH_PixelmapNative_ReadPixelsFromArea(OH_PixelmapNative *pixelmap, Image_PositionArea *area)
```

**Description**

Reads data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap to be read. |
| Image_PositionArea *area | Area of the PixelMap to read the data. Data will be read and copied into area->pixels. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. pixelmap or area is incorrect.          [IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) Internal unknown error, e.g. unsupported pixel format. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_WritePixelsToArea()

```c
Image_ErrorCode OH_PixelmapNative_WritePixelsToArea(OH_PixelmapNative *pixelmap, Image_PositionArea *area)
```

**Description**

Writes data from a buffer to a certain area of the PixelMap. The source data should be in BGRA_8888 format.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap to be written. |
| Image_PositionArea *area | Area of the PixelMap to write the data. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. pixelmap or area is incorrect.          [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) If the PixelMap is not editable.          [IMAGE_UNKNOWN_ERROR](capi-image-common-h.md#image_errorcode) Internal unknown error, e.g. unsupported pixel format. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetArgbPixels()

```c
Image_ErrorCode OH_PixelmapNative_GetArgbPixels(OH_PixelmapNative *pixelmap, uint8_t *destination, size_t *bufferSize)
```

**Description**

Get argb pixel buffer from pixelmap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| uint8_t *destination | Buffer to which the image pixel map data will be written. |
| size_t *bufferSize | Buffer size to which the image pixel map data will be written. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, destination and bufferSize are incorrect.          [IMAGE_UNSUPPORTED_CONVERSION](capi-image-common-h.md#image_errorcode) If format does not support conversion to argb or conversion failed.          [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) If device has no memory.          [IMAGE_COPY_FAILED](capi-image-common-h.md#image_errorcode) If memory copy failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_ToSdr()

```c
Image_ErrorCode OH_PixelmapNative_ToSdr(OH_PixelmapNative *pixelmap)
```

**Description**

Convert [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) to standard dynamic range.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. Pointer connot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - The operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - Parameter error.Possible causes:Parameter verification failed.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNSUPPORTED_OPERATION - Unsupported operation.Pixelmap can't be converted. |

### OH_PixelmapNative_GetImageInfo()

```c
Image_ErrorCode OH_PixelmapNative_GetImageInfo(OH_PixelmapNative *pixelmap, OH_Pixelmap_ImageInfo *imageInfo)
```

**Description**

Obtains pixel map information of this image.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| [OH_Pixelmap_ImageInfo](capi-image-nativemodule-oh-pixelmap-imageinfo.md) *imageInfo | Indicates the pointer to the image information. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr.          3.imageInfo is nullptr. |

### OH_PixelmapNative_SetOpacity()

```c
Image_ErrorCode OH_PixelmapNative_SetOpacity(OH_PixelmapNative *pixelmap, float value)
```

**Description**

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be modified. |
| float value | The target opacity value to be set. The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming more transparent as it approaches 0.0. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter.          Possible causes: 1. The rate is out of range. 2. The parameter is null.      [IMAGE_UNSUPPORTED_DATA_FORMAT](capi-image-common-h.md#image_errorcode) Unsupported data format. Possible cause: Alpha type is not supported. |

### OH_PixelmapNative_Opacity()

```c
Image_ErrorCode OH_PixelmapNative_Opacity(OH_PixelmapNative *pixelmap, float rate)
```

**Description**

Sets an opacity rate for this image pixel map. It is recommended to use [OH_PixelmapNative_SetOpacity](capi-pixelmap-native-h.md#oh_pixelmapnative_setopacity).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| float rate | Opacity rate to set. The value ranges from 0 to 1. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_ApplyScale()

```c
Image_ErrorCode OH_PixelmapNative_ApplyScale(OH_PixelmapNative *pixelmap, float scaleX, float scaleY)
```

**Description**

Scales the PixelMap in the horizontal and/or vertical dimensions.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be scaled. |
| float scaleX | The scale ratio of width. |
| float scaleY | The scale ratio of height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: The parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory.          Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

### OH_PixelmapNative_Scale()

```c
Image_ErrorCode OH_PixelmapNative_Scale(OH_PixelmapNative *pixelmap, float scaleX, float scaleY)
```

**Description**

Scales this image based on the input width and height. It is recommended to use [OH_PixelmapNative_ApplyScale](capi-pixelmap-native-h.md#oh_pixelmapnative_applyscale).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| float scaleX | Scaling ratio of the width. |
| float scaleY | Scaling ratio of the height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_ApplyScaleWithAntiAliasing()

```c
Image_ErrorCode OH_PixelmapNative_ApplyScaleWithAntiAliasing(OH_PixelmapNative *pixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)
```

**Description**

Scales the PixelMap in the horizontal and/or vertical dimensions with anti-aliasing.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be scaled. |
| float scaleX | The scale ratio of width. |
| float scaleY | The scale ratio of height. |
| [OH_PixelmapNative_AntiAliasingLevel](capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel) level | The anti-aliasing algorithm to be used. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: The parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory.          Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

### OH_PixelmapNative_ScaleWithAntiAliasing()

```c
Image_ErrorCode OH_PixelmapNative_ScaleWithAntiAliasing(OH_PixelmapNative *pixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)
```

**Description**

Scales this image based on the input width and height with anti-aliasing. It is recommended to use [OH_PixelmapNative_ApplyScaleWithAntiAliasing](capi-pixelmap-native-h.md#oh_pixelmapnative_applyscalewithantialiasing).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| float scaleX | Scaling ratio of the width. |
| float scaleY | Scaling ratio of the height. |
| [OH_PixelmapNative_AntiAliasingLevel](capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel) level | The anti-aliasing algorithm to be used. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if invalid parameter, x and y are incorrect.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_TOO_LARGE - if image is too large.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_ALLOC_FAILED - if device has no memory.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_UNKNOWN_ERROR - inner unknown error, maybe source pixelmap is released. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_CreateScaledPixelMap()

```c
Image_ErrorCode OH_PixelmapNative_CreateScaledPixelMap(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap, float scaleX, float scaleY)
```

**Description**

Create a scaled pixelmap based on the source pixelmap and the input width and height.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source native pixelmap. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **dstPixelmap | The destination native pixelmap for create. |
| float scaleX | Scaling ratio of the width. |
| float scaleY | Scaling ratio of the height. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If the param is nullptr or invalid. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_CreateScaledPixelMapWithAntiAliasing()

```c
Image_ErrorCode OH_PixelmapNative_CreateScaledPixelMapWithAntiAliasing(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap, float scaleX, float scaleY, OH_PixelmapNative_AntiAliasingLevel level)
```

**Description**

Create a scaled pixelmap based on the source pixelmap and the input width and height with anti-aliasing.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source native pixelmap. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **dstPixelmap | The destination native pixelmap for create. |
| float scaleX | Scaling ratio of the width. |
| float scaleY | Scaling ratio of the height. |
| [OH_PixelmapNative_AntiAliasingLevel](capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel) level | The anti-aliasing algorithm to be used. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If the param is nullptr or invalid.          [IMAGE_TOO_LARGE](capi-image-common-h.md#image_errorcode) If image is too large.          [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) If device has no memory. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_ApplyTranslate()

```c
Image_ErrorCode OH_PixelmapNative_ApplyTranslate(OH_PixelmapNative *pixelmap, float x, float y)
```

**Description**

Repositions the PixelMap in the horizontal and/or vertical directions.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be translated. |
| float x | The distance in pixels to move in the horizontal direction. |
| float y | The distance in pixels to move in the vertical direction. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: The parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory.          Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

### OH_PixelmapNative_Translate()

```c
Image_ErrorCode OH_PixelmapNative_Translate(OH_PixelmapNative *pixelmap, float x, float y)
```

**Description**

Translates this image based on the input coordinates. It is recommended to use [OH_PixelmapNative_ApplyTranslate](capi-pixelmap-native-h.md#oh_pixelmapnative_applytranslate).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| float x | The distance to be translate in the X direction. |
| float y | The distance to be translate in the Y direction. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_CreateAlphaPixelmap()

```c
Image_ErrorCode OH_PixelmapNative_CreateAlphaPixelmap(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap)
```

**Description**

Creates a PixelMap with only alpha channel from the source PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source PixelMap. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **dstPixelmap | The target PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. srcPixelmap or dstPixelmap is incorrect. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_Clone()

```c
Image_ErrorCode OH_PixelmapNative_Clone(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative **dstPixelmap)
```

**Description**

Clones a PixelMap from the source PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source PixelMap to be cloned. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **dstPixelmap | The target PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. srcPixelmap or dstPixelmap is incorrect.          [IMAGE_UNSUPPORTED_DATA_FORMAT](capi-image-common-h.md#image_errorcode) If the pixel format is unsupported.          [IMAGE_TOO_LARGE](capi-image-common-h.md#image_errorcode) If the PixelMap size is too large.          [IMAGE_INIT_FAILED](capi-image-common-h.md#image_errorcode) If the PixelMap initialization failed.          [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) If the copying of PixelMap data failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_CreateCroppedAndScaledPixelMap()

```c
Image_ErrorCode OH_PixelmapNative_CreateCroppedAndScaledPixelMap(OH_PixelmapNative *srcPixelmap, Image_Region *region, Image_Scale *scale, OH_PixelmapNative_AntiAliasingLevel level, OH_PixelmapNative **dstPixelmap)
```

**Description**

Creates a cropped and then scaled PixelMap based on the source PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source PixelMap. |
| Image_Region *region | The crop region. |
| Image_Scale *scale | The scale ratio of width and height. |
| [OH_PixelmapNative_AntiAliasingLevel](capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel) level | The anti-aliasing algorithm to be used. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **dstPixelmap | The target PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. srcPixelmap, region, scale, or dstPixelmap is                                      incorrect.          [IMAGE_UNSUPPORTED_DATA_FORMAT](capi-image-common-h.md#image_errorcode) If the pixel format is unsupported.          [IMAGE_TOO_LARGE](capi-image-common-h.md#image_errorcode) If the PixelMap size is too large.          [IMAGE_INIT_FAILED](capi-image-common-h.md#image_errorcode) If the PixelMap initialization failed.          [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) If the copying of PixelMap data failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_ApplyRotate()

```c
Image_ErrorCode OH_PixelmapNative_ApplyRotate(OH_PixelmapNative *pixelmap, float angle)
```

**Description**

Rotates the PixelMap. Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be rotated. |
| float angle | The rotation angle in degrees. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: The parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory.          Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

### OH_PixelmapNative_Rotate()

```c
Image_ErrorCode OH_PixelmapNative_Rotate(OH_PixelmapNative *pixelmap, float angle)
```

**Description**

Rotates this image based on the input angle. It is recommended to use [OH_PixelmapNative_ApplyRotate](capi-pixelmap-native-h.md#oh_pixelmapnative_applyrotate).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| float angle | Angle to rotate. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_ApplyFlip()

```c
Image_ErrorCode OH_PixelmapNative_ApplyFlip(OH_PixelmapNative *pixelmap, bool shouldFlipHorizontally, bool shouldFlipVertically)
```

**Description**

Flips the PixelMap in the horizontal and/or vertical directions.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be flipped. |
| bool shouldFlipHorizontally | Whether to flip horizontally. |
| bool shouldFlipVertically | Whether to flip vertically. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: The parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory. Possible cause: The system is out of memory. |

### OH_PixelmapNative_Flip()

```c
Image_ErrorCode OH_PixelmapNative_Flip(OH_PixelmapNative *pixelmap, bool shouldFlipHorizontally, bool shouldFlipVertically)
```

**Description**

Flips this image horizontally or vertically, or both. It is recommended to use [OH_PixelmapNative_ApplyFlip](capi-pixelmap-native-h.md#oh_pixelmapnative_applyflip).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| bool shouldFlipHorizontally | Whether to flip the image horizontally. |
| bool shouldFlipVertically | Whether to flip the image vertically. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_ApplyCrop()

```c
Image_ErrorCode OH_PixelmapNative_ApplyCrop(OH_PixelmapNative *pixelmap, Image_Region *region)
```

**Description**

Crops the PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | Pointer of the PixelMap to be cropped. |
| Image_Region *region | Pointer of the region to crop. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) The PixelMap has been released.      [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation because the PixelMap is locked.      [IMAGE_INVALID_REGION](capi-image-common-h.md#image_errorcode) The specified region is invalid or out of range.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter. Possible cause: Any parameter is null.      [IMAGE_ALLOC_FAILED](capi-image-common-h.md#image_errorcode) Failed to allocate memory.          Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

### OH_PixelmapNative_Crop()

```c
Image_ErrorCode OH_PixelmapNative_Crop(OH_PixelmapNative *pixelmap, Image_Region *region)
```

**Description**

Crops this image based on the input size. It is recommended to use [OH_PixelmapNative_ApplyCrop](capi-pixelmap-native-h.md#oh_pixelmapnative_applycrop).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |
| Image_Region *region | Area size, read according to area. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - The operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode)  - Parameter error.Possible causes:          1.pixelmap is nullptr.          2.region is nullptr.          3.pixelmap's inner pixelmap is nullptr. |

### OH_PixelmapNative_Release()

```c
Image_ErrorCode OH_PixelmapNative_Release(OH_PixelmapNative *pixelmap)
```

**Description**

Releases an <b>OH_Pixelmap</b> object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer will be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if either:          1.Pixelmap is nullptr.          2.It's inner pixelmap is nullptr.          3.Pixelmap is not allowed to release. |

### OH_PixelmapNative_Destroy()

```c
Image_ErrorCode OH_PixelmapNative_Destroy(OH_PixelmapNative **pixelmap)
```

**Description**

Destroys an <b>OH_PixelmapNative</b> object and deallocates its resources.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | A pointer to the OH_PixelmapNative pointer to destroy. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if pixelmap is null or pixelmap is null. |

### OH_PixelmapNative_ConvertAlphaType()

```c
Image_ErrorCode OH_PixelmapNative_ConvertAlphaType(OH_PixelmapNative *srcPixelmap, OH_PixelmapNative *dstPixelmap, const bool toPremul)
```

**Description**

Converts the alpha type of the PixelMap to either premultiplied or unpremultiplied. The conversion only supports pixel formats that have an alpha channel, except RGBA_F16.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *srcPixelmap | The source PixelMap containing pixel data to be converted. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *dstPixelmap | An empty destination PixelMap that must have the same properties (width, height, pixel format, etc.) as the source PixelMap, except that its alpha type must be opposite to that of the source (premultiplied vs. unpremultiplied). The converted pixel data will be written into this PixelMap. |
| const bool toPremul | Specifies the conversion direction. If true, converts from unpremultiplied to premultiplied alpha; if false, converts from premultiplied to unpremultiplied alpha. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:      [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) The operation is successful.      [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get image data.          Possible cause: Internal data is corrupted. Please check the logs for detailed information.      [IMAGE_PIXELMAP_RELEASED](capi-image-common-h.md#image_errorcode) Either PixelMap has been released.      [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter.          Possible causes: 1. Either PixelMap does not meet the requirements. 2. Any parameter is null.      [IMAGE_UNSUPPORTED_DATA_FORMAT](capi-image-common-h.md#image_errorcode) Unsupported pixel format for either PixelMap. |

### OH_PixelmapNative_ConvertAlphaFormat()

```c
Image_ErrorCode OH_PixelmapNative_ConvertAlphaFormat(OH_PixelmapNative* srcpixelmap, OH_PixelmapNative* dstpixelmap, const bool isPremul)
```

**Description**

Converting images to alpha format It is recommended to use [OH_PixelmapNative_ConvertAlphaType](capi-pixelmap-native-h.md#oh_pixelmapnative_convertalphatype).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)* srcpixelmap | The source pixel map pointer will be operated. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)* dstpixelmap | The destination pixel map pointer will be operated. |
| const bool isPremul | Whether it is pre-multiplied, true for prediction, false for non-pre-multiplied. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if either:          1.srcpixelmap or dstpixelmap is null pointer.          2.Their inner pixelmap structures are unavailable. |

### OH_PixelmapNative_CreateEmptyPixelmap()

```c
Image_ErrorCode OH_PixelmapNative_CreateEmptyPixelmap(OH_Pixelmap_InitializationOptions *options, OH_PixelmapNative **pixelmap)
```

**Description**

Create a empty <b>PixelMap</b> object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | IPixel properties, including the alpha type, size, pixel format, and editable. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | Pixelmap pointer for created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) - if the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) - if options is null or          failed to create pixelmap due to invalid options. |

### OH_PixelmapNative_CreateEmptyPixelmapUsingAllocator()

```c
Image_ErrorCode OH_PixelmapNative_CreateEmptyPixelmapUsingAllocator(OH_Pixelmap_InitializationOptions *options, IMAGE_ALLOCATOR_MODE allocator, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a empty pixelmap based on options [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md), the memory type used by the pixelmap can be specified by allocatorType [IMAGE_ALLOCATOR_MODE](capi-image-common-h.md#image_errorcode). By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the pixelmap returned by this interface, please always consider the impact of stride.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Pixelmap_InitializationOptions](capi-image-nativemodule-oh-pixelmap-initializationoptions.md) *options | Pixelmap initialization properties including size, pixel format, alpha type, and editable flags. |
| IMAGE_ALLOCATOR_MODE allocator | Indicate which memory type will be used by the returned pixelmap. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | Output parameter receiving the created pixelmap object pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If the param is nullptr or invalid.          [IMAGE_TOO_LARGE](capi-image-common-h.md#image_errorcode) too large data or image.          [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) unsupported operations.          [IMAGE_ALLOCATOR_MODE_UNSUPPORTED](capi-image-common-h.md#image_errorcode) unsupported allocator mode, e.g., use          share memory to create a HDR image as only DMA supported hdr metadata. |

### OH_PixelmapNative_CreatePixelmapFromSurface()

```c
Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromSurface(const char *surfaceId, size_t length, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a PixelMap from a Surface with the Surface ID.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *surfaceId | The Surface ID. |
| size_t length | Length of the Surface ID. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | The PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. surfaceId or pixelmap is incorrect.          [IMAGE_CREATE_PIXELMAP_FAILED](capi-image-common-h.md#image_errorcode) If the PixelMap creation failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_CreatePixelmapFromSurfaceWithTransformation()

```c
Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromSurfaceWithTransformation(const char *surfaceId, size_t length, bool transformEnabled, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a PixelMap object based on the ID of a Surface with transformation.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *surfaceId | ID of the Surface. |
| size_t length | Length of the Surface ID. |
| bool transformEnabled | Whether to inverse transform the PixelMap to cancel out the transformation from the Surface. If true, the PixelMap will be transformed by the same amount from the Surface but in a reversed direction; if false, the PixelMap will not be transformed. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | The PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) Operation is successful.          [IMAGE_INVALID_PARAMETER](capi-image-common-h.md#image_errorcode) Invalid parameter, e.g. surfaceId or pixelmap is incorrect.          [IMAGE_UNSUPPORTED_OPERATION](capi-image-common-h.md#image_errorcode) Unsupported operation, e.g. on cross-platform.          [IMAGE_GET_IMAGE_DATA_FAILED](capi-image-common-h.md#image_errorcode) Failed to get the data from Surface.          [IMAGE_CREATE_PIXELMAP_FAILED](capi-image-common-h.md#image_errorcode) Failed to create the PixelMap. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_CreatePixelmapFromNativeBuffer()

```c
Image_ErrorCode OH_PixelmapNative_CreatePixelmapFromNativeBuffer(OH_NativeBuffer *nativeBuffer, OH_PixelmapNative **pixelmap)
```

**Description**

Creates a PixelMap from a native buffer.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBuffer](capi-image-nativemodule-oh-nativebuffer.md) *nativeBuffer | The native buffer. |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) **pixelmap | The PixelMap to be created. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. nativeBuffer or pixelmap is incorrect.          [IMAGE_CREATE_PIXELMAP_FAILED](capi-image-common-h.md#image_errorcode) If the PixelMap creation failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetMetadata()

```c
Image_ErrorCode OH_PixelmapNative_GetMetadata(OH_PixelmapNative *pixelmap, OH_Pixelmap_HdrMetadataKey key, OH_Pixelmap_HdrMetadataValue **value)
```

**Description**

Get metadata.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| [OH_Pixelmap_HdrMetadataKey](capi-pixelmap-native-h.md#oh_pixelmap_hdrmetadatakey) key | Type of metadata. |
| [OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md) **value | Value of metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if invalid parameter, key and value are incorrect.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_DMA_NOT_EXIST - if DMA memory does not exist.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_COPY_FAILED - if memory copy failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_SetMetadata()

```c
Image_ErrorCode OH_PixelmapNative_SetMetadata(OH_PixelmapNative *pixelmap, OH_Pixelmap_HdrMetadataKey key, OH_Pixelmap_HdrMetadataValue *value)
```

**Description**

Set metadata.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| [OH_Pixelmap_HdrMetadataKey](capi-pixelmap-native-h.md#oh_pixelmap_hdrmetadatakey) key | Type of metadata. |
| [OH_Pixelmap_HdrMetadataValue](capi-image-nativemodule-oh-pixelmap-hdrmetadatavalue.md) *value | Value of metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if invalid parameter, key and value are incorrect.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_DMA_NOT_EXIST - if DMA memory does not exist.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_COPY_FAILED - if memory copy failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetNativeBuffer()

```c
Image_ErrorCode OH_PixelmapNative_GetNativeBuffer(OH_PixelmapNative *pixelmap, OH_NativeBuffer **nativeBuffer)
```

**Description**

Get the native buffer from the PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap to get the native buffer from. |
| [OH_NativeBuffer](capi-image-nativemodule-oh-nativebuffer.md) **nativeBuffer | The native buffer to retrieve. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_BAD_PARAMETER - if invalid parameter, pixelmap or nativeBuffer is null.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_DMA_NOT_EXIST - if DMA memory dose not exist.  returns [Image_ErrorCode](capi-image-common-h.md#image_errorcode) IMAGE_DMA_OPERATION_FAILED - if operations related to DMA memory has failed. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetColorSpaceNative()

```c
Image_ErrorCode OH_PixelmapNative_GetColorSpaceNative(OH_PixelmapNative *pixelmap, OH_NativeColorSpaceManager **colorSpaceNative)
```

**Description**

Get the native colorspace from the PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The native pixelmap to get the native colorspace from. |
| [OH_NativeColorSpaceManager](capi-image-nativemodule-oh-nativecolorspacemanager.md) **colorSpaceNative | The native colorspace to retrieve. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) The param of pixelmap or colorSpaceNative is nullptr or invalid. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_SetColorSpaceNative()

```c
Image_ErrorCode OH_PixelmapNative_SetColorSpaceNative(OH_PixelmapNative *pixelmap, OH_NativeColorSpaceManager *colorSpaceNative)
```

**Description**

Set the native colorspace for the PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The native pixelmap to set the native colorspace for. |
| [OH_NativeColorSpaceManager](capi-image-nativemodule-oh-nativecolorspacemanager.md) *colorSpaceNative | The native colorspace to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the execution is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) The param of pixelmap or colorSpaceNative is nullptr or invalid. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_SetMemoryName()

```c
Image_ErrorCode OH_PixelmapNative_SetMemoryName(OH_PixelmapNative *pixelmap, char *name, size_t *size)
```

**Description**

Set pixelmap memory name.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| char *name | The pointer of name that needs to be set. |
| size_t *size | The size of name size that needs to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, name and size are incorrect.          [IMAGE_UNSUPPORTED_MEMORY_FORMAT](capi-image-common-h.md#image_errorcode) If memory format is unsupported. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetByteCount()

```c
Image_ErrorCode OH_PixelmapNative_GetByteCount(OH_PixelmapNative *pixelmap, uint32_t *byteCount)
```

**Description**

Get the total number of bytes occupied by all pixels in the Pixelmap, without any padding.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| uint32_t *byteCount | The total number of bytes to be retrieved. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, pixelmap or byteCount are invalid. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetAllocationByteCount()

```c
Image_ErrorCode OH_PixelmapNative_GetAllocationByteCount(OH_PixelmapNative *pixelmap, uint32_t *allocationByteCount)
```

**Description**

Get the size of the allocated memory used to store this pixelmap's pixels.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The Pixelmap pointer to be operated. |
| uint32_t *allocationByteCount | The size of the allocated memory. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, pixelmap or allocationByteCount are invalid. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_AccessPixels()

```c
Image_ErrorCode OH_PixelmapNative_AccessPixels(OH_PixelmapNative *pixelmap, void **addr)
```

**Description**

Obtains the memory address of a PixelMap and locks the memory. When the memory is locked, any operation that modifies or releases the PixelMap will fail and return [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode).

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap pointer to be operated. |
| void **addr | The double pointer to the memory address of the PixelMap. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, pixelmap or addr are invalid.          [IMAGE_LOCK_UNLOCK_FAILED](capi-image-common-h.md#image_errorcode) If memory failed to be locked. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_UnaccessPixels()

```c
Image_ErrorCode OH_PixelmapNative_UnaccessPixels(OH_PixelmapNative *pixelmap)
```

**Description**

Unlocks the memory of the PixelMap data. This function is used with [OH_PixelmapNative_AccessPixels](capi-pixelmap-native-h.md#oh_pixelmapnative_accesspixels) in pairs.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap pointer to be operated. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If invalid parameter, pixelmap is invalid.          [IMAGE_LOCK_UNLOCK_FAILED](capi-image-common-h.md#image_errorcode) If memory failed to be unlocked. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_GetUniqueId()

```c
Image_ErrorCode OH_PixelmapNative_GetUniqueId(OH_PixelmapNative *pixelmap, uint32_t *uniqueId)
```

**Description**

Gets the unique ID of a PixelMap.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap to retrieve the unique ID. |
| uint32_t *uniqueId | The resulting unique ID. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. pixelmap or uniqueId is incorrect. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)


### OH_PixelmapNative_IsReleased()

```c
Image_ErrorCode OH_PixelmapNative_IsReleased(OH_PixelmapNative *pixelmap, bool *released)
```

**Description**

Checks whether the PixelMap has been released.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md) *pixelmap | The PixelMap to check. |
| bool *released | The resulting release status. |

**Returns**:

| Type | Description |
| -- | -- |
| Image_ErrorCode | Function result code:          [IMAGE_SUCCESS](capi-image-common-h.md#image_errorcode) If the operation is successful.          [IMAGE_BAD_PARAMETER](capi-image-common-h.md#image_errorcode) If any parameter is invalid, e.g. pixelmap or released is incorrect. |

**Reference**:

[OH_PixelmapNative](capi-image-nativemodule-oh-pixelmapnative.md)



