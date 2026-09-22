# image_source_mdk.h

## Overview

Declares APIs for decoding an image source into a pixel map.

**Library**: libimage_source_ndk.z.so

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 8

**Related module**: [Image](capi-image.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OhosImageRegion](capi-image-ohosimageregion.md) | - | Defines the region of the image source to decode. It is used in {@link OhosImageDecodingOps}, {@link OH_ImageSource_CreatePixelMap}, and<br>{@link OH_ImageSource_CreatePixelMapList}. |
| [OhosImageSourceOps](capi-image-ohosimagesourceops.md) | - | Defines image source options information {@link OH_ImageSource_Create} and {@link OH_ImageSource_CreateIncremental}. |
| [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) | - | Defines the options for decoding the image source. It is used in {@link OH_ImageSource_CreatePixelMap} and {@link OH_ImageSource_CreatePixelMapList}. |
| [OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md) | - | Defines the image source information, which is obtained by calling {@link OH_ImageSource_GetImageInfo}. |
| [OhosImageSource](capi-image-ohosimagesource.md) | - | Defines the input resource of the image source. It is obtained by calling {@link OH_ImageSource_Create}. Only one type of resource is accepted at a time. |
| [OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md) | - | Defines the delay time list of the image source. It is obtained by calling {@link OH_ImageSource_GetDelayTime}. |
| [OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md) | - | Defines image source supported format string. {@link OhosImageSourceSupportedFormatList} and {@link OH_ImageSource_GetSupportedFormats} |
| [OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md) | - | Defines the format string list supported by the image source. It is obtained by calling {@link OH_ImageSource_GetSupportedFormats}. |
| [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md) | - | Defines the property string (in key-value format) of the image source. It is used in {@link OH_ImageSource_GetImageProperty} and {@link OH_ImageSource_ModifyImageProperty}. |
| [OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md) | - | Defines the update data of the image source. It is obtained by calling {@link OH_ImageSource_UpdateData}. |
| [ImageSourceNative_](capi-image-imagesourcenative-.md) | - | Defines a native image source object for the image source APIs. |

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_ImageSource_Create(napi_env env, struct OhosImageSource* src, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_create) | Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified [OhosImageSource](capi-image-ohosimagesource.md) and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.(Deprecated in API11) |
| [int32_t OH_ImageSource_CreateFromUri(napi_env env, char* uri, size_t size, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromuri) | Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source URI and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. |
| [int32_t OH_ImageSource_CreateFromFd(napi_env env, int32_t fd, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromfd) | Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source file descriptor and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. |
| [int32_t OH_ImageSource_CreateFromData(napi_env env, uint8_t* data, size_t dataSize, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromdata) | Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source data and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. |
| [int32_t OH_ImageSource_CreateFromRawFile(napi_env env, RawFileDescriptor rawFile, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromrawfile) | Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified raw file's file descriptor and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. |
| [int32_t OH_ImageSource_CreateIncremental(napi_env env, struct OhosImageSource* source, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createincremental) | Creates an incremental <b>ImageSource</b> object at the JavaScript native layer based on the specified [OhosImageSource](capi-image-ohosimagesource.md) and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. The image source data will be updated through [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).(Deprecated in API11) |
| [int32_t OH_ImageSource_CreateIncrementalFromData(napi_env env, uint8_t* data, size_t dataSize, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createincrementalfromdata) | Creates an incremental <b>ImageSource</b> object at the JavaScript native layer based on the specified image source data and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. The image source data will be updated through [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata). |
| [int32_t OH_ImageSource_GetSupportedFormats(struct OhosImageSourceSupportedFormatList* res)](#oh_imagesource_getsupportedformats) | Obtains all supported decoding formats. |
| [ImageSourceNative* OH_ImageSource_InitNative(napi_env env, napi_value source)](#oh_imagesource_initnative) | Converts an {@link ImageSource} object at the JavaScript native layer to an <b>ImageSourceNative</b> object at the C++ native layer. |
| [int32_t OH_ImageSource_CreatePixelMap(const ImageSourceNative* native, struct OhosImageDecodingOps* ops, napi_value *res)](#oh_imagesource_createpixelmap) | Decodes an <b>ImageSource</b> object to obtain a <b>PixelMap</b> object at the JavaScript native layer based on the specified [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) struct. |
| [int32_t OH_ImageSource_CreatePixelMapList(const ImageSourceNative* native, struct OhosImageDecodingOps* ops, napi_value *res)](#oh_imagesource_createpixelmaplist) | Decodes an <b>ImageSource</b> to obtain all the <b>PixelMap</b> objects at the JavaScript native layer based on the specified [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) struct. |
| [int32_t OH_ImageSource_GetDelayTime(const ImageSourceNative* native, struct OhosImageSourceDelayTimeList* res)](#oh_imagesource_getdelaytime) | Obtains the delay time list from some <b>ImageSource</b> objects (such as GIF image sources). |
| [int32_t OH_ImageSource_GetFrameCount(const ImageSourceNative* native, uint32_t *res)](#oh_imagesource_getframecount) | Obtains the number of frames from an <b>ImageSource</b> object. |
| [int32_t OH_ImageSource_GetImageInfo(const ImageSourceNative* native, int32_t index, struct OhosImageSourceInfo* info)](#oh_imagesource_getimageinfo) | Obtains image source information from an <b>ImageSource</b> object by index. |
| [int32_t OH_ImageSource_GetImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)](#oh_imagesource_getimageproperty) | Obtains the value of an image property from an <b>ImageSource</b> object. |
| [int32_t OH_ImageSource_ModifyImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)](#oh_imagesource_modifyimageproperty) | Modifies the value of an image property of an <b>ImageSource</b> object. |
| [int32_t OH_ImageSource_UpdateData(const ImageSourceNative* native, struct OhosImageSourceUpdateData* data)](#oh_imagesource_updatedata) | Updates the data of an <b>ImageSource</b> object. |
| [int32_t OH_ImageSource_Release(ImageSourceNative* native)](#oh_imagesource_release) | Releases an <b>ImageSourceNative</b> object. |

### Variable

| Name | Description |
| -- | -- |
| static const char *OHOS_IMAGE_PROPERTY_BITS_PER_SAMPLE = "BitsPerSample" | Defines a pointer to bits per sample, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_ORIENTATION = "Orientation" | Defines a pointer to the orientation, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_IMAGE_LENGTH = "ImageLength" | Defines a pointer to the image length, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_IMAGE_WIDTH = "ImageWidth" | Defines a pointer to the image width, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_GPS_LATITUDE = "GPSLatitude" | Defines a pointer to the GPS latitude, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_GPS_LONGITUDE = "GPSLongitude" | Defines a pointer to the GPS longitude, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_GPS_LATITUDE_REF = "GPSLatitudeRef" | Defines a pointer to the GPS latitude reference information, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_GPS_LONGITUDE_REF = "GPSLongitudeRef" | Defines a pointer to the GPS longitude reference information, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_DATE_TIME_ORIGINAL = "DateTimeOriginal" | Defines a pointer to the created date and time, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_EXPOSURE_TIME = "ExposureTime" | Defines a pointer to the exposure time, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_SCENE_TYPE = "SceneType" | Defines a pointer to the scene type, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_ISO_SPEED_RATINGS = "ISOSpeedRatings" | Defines a pointer to the ISO speed ratings, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_F_NUMBER = "FNumber" | Defines a pointer to the f-number of the image, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |
| static const char *OHOS_IMAGE_PROPERTY_COMPRESSED_BITS_PER_PIXEL = "CompressedBitsPerPixel" | Defines a pointer to the compressed bits per pixel, one of the image properties. It is used in [OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty) and [OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty). Add static keyword since API 12, it is used to limit the scope of the constant to a single file.<br>**Since**: 10 |

## Function description

### OH_ImageSource_Create()

```c
int32_t OH_ImageSource_Create(napi_env env, struct OhosImageSource* src, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified [OhosImageSource](capi-image-ohosimagesource.md) and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Deprecated**: 11

**Replaced by**: image#OH_ImageSource_CreateFromData

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the Java Native Interface (JNI) environment. |
| [struct OhosImageSource](capi-image-ohosimagesource.md)* src | Indicates a pointer to the input resource of the image source. For details, see [OhosImageSource](capi-image-ohosimagesource.md). |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SOURCE_DATA_INCOMPLETE - if image source data incomplete.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SOURCE_DATA - if image source data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_TOO_LARGE - if image data too large.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FILE_DAMAGED - if file damaged.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FILE_FD_ERROR - if file fd is bad.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_STREAM_SIZE_ERROR - if stream bad.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SEEK_FAILED - if seek file failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PEEK_FAILED - if peek file failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FREAD_FAILED - if read file failed. |

**Reference**:

[OhosImageSource](capi-image-ohosimagesource.md), [OhosImageSourceOps](capi-image-ohosimagesourceops.md)


### OH_ImageSource_CreateFromUri()

```c
int32_t OH_ImageSource_CreateFromUri(napi_env env, char* uri, size_t size, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source URI and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the Java Native Interface (JNI) environment. |
| char* uri | Indicates a pointer to the image source URI. Only a file URI or Base64 URI is accepted. |
| size_t size | Indicates the length of the image source URI. |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[OhosImageSourceOps](capi-image-ohosimagesourceops.md)


### OH_ImageSource_CreateFromFd()

```c
int32_t OH_ImageSource_CreateFromFd(napi_env env, int32_t fd, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source file descriptor and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the Java Native Interface (JNI) environment. |
| int32_t fd | Indicates the image source file descriptor. |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[OhosImageSourceOps](capi-image-ohosimagesourceops.md)


### OH_ImageSource_CreateFromData()

```c
int32_t OH_ImageSource_CreateFromData(napi_env env, uint8_t* data, size_t dataSize, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified image source data and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the Java Native Interface (JNI) environment. |
| uint8_t* data | Indicates a pointer to the image source data. Only a formatted packet data or Base64 data is accepted. |
| size_t dataSize | Indicates the size of the image source data. |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[OhosImageSourceOps](capi-image-ohosimagesourceops.md)


### OH_ImageSource_CreateFromRawFile()

```c
int32_t OH_ImageSource_CreateFromRawFile(napi_env env, RawFileDescriptor rawFile, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an <b>ImageSource</b> object at the JavaScript native layer based on the specified raw file's file descriptor and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the Java Native Interface (JNI) environment. |
| RawFileDescriptor rawFile | Indicates the raw file's file descriptor. |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[OhosImageSourceOps](capi-image-ohosimagesourceops.md)


### OH_ImageSource_CreateIncremental()

```c
int32_t OH_ImageSource_CreateIncremental(napi_env env, struct OhosImageSource* source, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an incremental <b>ImageSource</b> object at the JavaScript native layer based on the specified [OhosImageSource](capi-image-ohosimagesource.md) and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. The image source data will be updated through [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Deprecated**: 11

**Replaced by**: image#OH_ImageSource_CreateIncrementalFromData

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the JNI environment. |
| src | Indicates a pointer to the input resource of the image source. Only the buffer type is accepted. For details, see [OhosImageSource](capi-image-ohosimagesource.md). |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SOURCE_DATA_INCOMPLETE - if image source data incomplete.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SOURCE_DATA - if image source data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_TOO_LARGE - if image data too large.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FILE_DAMAGED - if file damaged.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FILE_FD_ERROR - if file fd is bad.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_STREAM_SIZE_ERROR - if stream bad.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SEEK_FAILED - if seek file failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PEEK_FAILED - if peek file failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_FREAD_FAILED - if read file failed. |

**Reference**:

[OhosImageSource](capi-image-ohosimagesource.md), [OhosImageSourceOps](capi-image-ohosimagesourceops.md), [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata)


### OH_ImageSource_CreateIncrementalFromData()

```c
int32_t OH_ImageSource_CreateIncrementalFromData(napi_env env, uint8_t* data, size_t dataSize, struct OhosImageSourceOps* ops, napi_value *res)
```

**Description**

Creates an incremental <b>ImageSource</b> object at the JavaScript native layer based on the specified image source data and [OhosImageSourceOps](capi-image-ohosimagesourceops.md) structs. The image source data will be updated through [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the JNI environment. |
| uint8_t* data | Indicates a pointer to the image source data. Only a formatted packet data or Base64 data is accepted. |
| size_t dataSize | Indicates the size of the image source data. |
| [struct OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | Indicates a pointer to the options for creating the image source. For details, see [OhosImageSourceOps](capi-image-ohosimagesourceops.md). |
| napi_value *res | Indicates a pointer to the <b>ImageSource</b> object created at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter. |

**Reference**:

[OhosImageSourceOps](capi-image-ohosimagesourceops.md), [OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata)


### OH_ImageSource_GetSupportedFormats()

```c
int32_t OH_ImageSource_GetSupportedFormats(struct OhosImageSourceSupportedFormatList* res)
```

**Description**

Obtains all supported decoding formats.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md)* res | Indicates a pointer to the <b>OhosImageSourceSupportedFormatList</b> struct. When the input <b>supportedFormatList</b> is a null pointer and <b>size</b> is 0, the size of the supported formats is returned through <b>size</b> in <b>res</b>. To obtain all formats, a space larger than <b>size</b> is required. In addition, sufficient space must be reserved for each format supported. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CHECK_FORMAT_ERROR - if decode fail. |

**Reference**:

[OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md), [OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md)


### OH_ImageSource_InitNative()

```c
ImageSourceNative* OH_ImageSource_InitNative(napi_env env, napi_value source)
```

**Description**

Converts an {@link ImageSource} object at the JavaScript native layer to an <b>ImageSourceNative</b> object at the C++ native layer.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Indicates a pointer to the JNI environment. |
| napi_value source | Indicates a pointer to the <b>ImageSource</b> object at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| [ImageSourceNative*](capi-image-imagesourcenative-.md) | Returns a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object if the operation is successful;  returns a null pointer otherwise. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OH_ImageSource_Release](capi-image-source-mdk-h.md#oh_imagesource_release)


### OH_ImageSource_CreatePixelMap()

```c
int32_t OH_ImageSource_CreatePixelMap(const ImageSourceNative* native, struct OhosImageDecodingOps* ops, napi_value *res)
```

**Description**

Decodes an <b>ImageSource</b> object to obtain a <b>PixelMap</b> object at the JavaScript native layer based on the specified [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) struct.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)* ops | Indicates a pointer to the options for decoding the image source. For details, see [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md). |
| napi_value *res | Indicates a pointer to the <b>PixelMap</b> object obtained at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_ENCODER_FAILED - if create encoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CHECK_FORMAT_ERROR - if check format failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST - if sharememory error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL - if sharememory data abnormal.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MALLOC_ABNORMAL - if image malloc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INIT_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CROP - if crop error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ENCODE_FAILED - if image add pixel map fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_UNSUPPORT - if image hardware decode unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_FAILED - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_IPC - if ipc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALPHA_TYPE_ERROR - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALLOCATER_TYPE_ERROR - if hard decode failed. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)


### OH_ImageSource_CreatePixelMapList()

```c
int32_t OH_ImageSource_CreatePixelMapList(const ImageSourceNative* native, struct OhosImageDecodingOps* ops, napi_value *res)
```

**Description**

Decodes an <b>ImageSource</b> to obtain all the <b>PixelMap</b> objects at the JavaScript native layer based on the specified [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) struct.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)* ops | Indicates a pointer to the options for decoding the image source. For details, see [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md). |
| napi_value *res | Indicates a pointer to the <b>PixelMap</b> objects obtained at the JavaScript native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_ENCODER_FAILED - if create encoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CHECK_FORMAT_ERROR - if check format failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST - if sharememory error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL - if sharememory data abnormal.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MALLOC_ABNORMAL - if image malloc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INIT_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CROP - if crop error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ENCODE_FAILED - if image add pixel map fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_UNSUPPORT - if image hardware decode unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_FAILED - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_IPC - if ipc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALPHA_TYPE_ERROR - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALLOCATER_TYPE_ERROR - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)


### OH_ImageSource_GetDelayTime()

```c
int32_t OH_ImageSource_GetDelayTime(const ImageSourceNative* native, struct OhosImageSourceDelayTimeList* res)
```

**Description**

Obtains the delay time list from some <b>ImageSource</b> objects (such as GIF image sources).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md)* res | Indicates a pointer to the delay time list obtained. For details, see [OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md). When the input <b>delayTimeList</b> is a null pointer and <b>size</b> is <b>0</b>, the size of the delay time list is returned through <b>size</b> in <b>res</b>. To obtain the complete delay time list, a space greater than <b>size</b> is required. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md)


### OH_ImageSource_GetFrameCount()

```c
int32_t OH_ImageSource_GetFrameCount(const ImageSourceNative* native, uint32_t *res)
```

**Description**

Obtains the number of frames from an <b>ImageSource</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| uint32_t *res | Indicates a pointer to the number of frames obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md)


### OH_ImageSource_GetImageInfo()

```c
int32_t OH_ImageSource_GetImageInfo(const ImageSourceNative* native, int32_t index, struct OhosImageSourceInfo* info)
```

**Description**

Obtains image source information from an <b>ImageSource</b> object by index.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| int32_t index | Indicates the index of the frame. |
| [struct OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md)* info | Indicates a pointer to the image source information obtained. For details, see [OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md)


### OH_ImageSource_GetImageProperty()

```c
int32_t OH_ImageSource_GetImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)
```

**Description**

Obtains the value of an image property from an <b>ImageSource</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* key | Indicates a pointer to the property. For details, see [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md). |
| [struct OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* value | Indicates a pointer to the property value obtained. If the input <b>value</b> is a null pointer and <b>size</b> is <b>0</b>, the size of the property value is returned through <b>size</b> in <b>value</b>. To obtain the complete property value, a space greater than <b>size</b> is required. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)


### OH_ImageSource_ModifyImageProperty()

```c
int32_t OH_ImageSource_ModifyImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)
```

**Description**

Modifies the value of an image property of an <b>ImageSource</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* key | Indicates a pointer to the property. For details, see [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md). |
| [struct OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* value | Indicates a pointer to the new value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_EXIF_UNSUPPORT - if image decode exif unsupport.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PROPERTY_NOT_EXIST - if image property not exist. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)


### OH_ImageSource_UpdateData()

```c
int32_t OH_ImageSource_UpdateData(const ImageSourceNative* native, struct OhosImageSourceUpdateData* data)
```

**Description**

Updates the data of an <b>ImageSource</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |
| [struct OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md)* data | Indicates a pointer to the update data. For details, see [OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_FAILED - if decode fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_HEAD_ABNORMAL - if image decode head error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_DECODER_FAILED - if create decoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CREATE_ENCODER_FAILED - if create encoder failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CHECK_FORMAT_ERROR - if check format failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_THIRDPART_SKIA_ERROR - if skia error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST - if sharememory error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL - if sharememory data abnormal.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DECODE_ABNORMAL - if image decode error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_MALLOC_ABNORMAL - if image malloc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_UNSUPPORT - if image init error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INIT_ABNORMAL - if image input data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_CROP - if crop error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_UNKNOWN_FORMAT - if image unknown format.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_REGISTER_FAILED - if register plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_PLUGIN_CREATE_FAILED - if create plugin fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ENCODE_FAILED - image add pixel map fail.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_UNSUPPORT - if image hardware decode unsupported.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_HW_DECODE_FAILED - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ERR_IPC - if ipc error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INDEX_INVALID - if invalid index.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALPHA_TYPE_ERROR - if hard decode failed.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_ALLOCATER_TYPE_ERROR - if hard decode failed. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md)


### OH_ImageSource_Release()

```c
int32_t OH_ImageSource_Release(ImageSourceNative* native)
```

**Description**

Releases an <b>ImageSourceNative</b> object.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ImageSourceNative](capi-image-imagesourcenative-.md)* native | Indicates a pointer to the [ImageSourceNative](capi-image-imagesourcenative-.md) object at the C++ native layer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_SUCCESS - if the operation is successful.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_BAD_PARAMETER - if bad parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_JNI_ENV_ABNORMAL - if Abnormal JNI environment.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_INVALID_PARAMETER - if invalid parameter.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_GET_DATA_ABNORMAL - if image get data error.  returns [IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode) IMAGE_RESULT_DATA_ABNORMAL - if image input data error. |

**Reference**:

[ImageSourceNative](capi-image-imagesourcenative-.md), [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create), [OH_ImageSource_CreateIncremental](capi-image-source-mdk-h.md#oh_imagesource_createincremental)



