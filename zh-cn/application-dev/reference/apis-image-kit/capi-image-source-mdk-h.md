# image_source_mdk.h

## 概述

声明将ImageSource解码成像素位图的方法。

**库：** libimage_source_ndk.z.so

**引用文件：** <multimedia/image_framework/image_source_mdk.h>

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OhosImageRegion](capi-image-ohosimageregion.md) | - | 定义图像源解码的范围选项。是[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)的成员变量。 |
| [ImageSourceNative_](capi-image-imagesourcenative-.md) | ImageSourceNative | 为图像源方法定义native层图像源对象。 |
| [OhosImageSourceOps](capi-image-ohosimagesourceops.md) | - | 定义图像源选项信息。此选项给[OH_ImageSource_Create](#oh_imagesource_create)和[OH_ImageSource_CreateIncremental](#oh_imagesource_createincremental)接口使用。 |
| [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md) | - | 定义图像源解码选项。此选项给[OH_ImageSource_CreatePixelMap](#oh_imagesource_createpixelmap)和[OH_ImageSource_CreatePixelMapList](#oh_imagesource_createpixelmaplist)接口使用。 |
| [OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md) | - | 定义图像源信息，由[OH_ImageSource_GetImageInfo](#oh_imagesource_getimageinfo)获取。 |
| [OhosImageSource](capi-image-ohosimagesource.md) | - | 定义图像源输入资源，每次仅接收一种类型。由[OH_ImageSource_Create](#oh_imagesource_create)获取。 |
| [OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md) | - | 定义图像源延迟时间列表。由[OH_ImageSource_GetDelayTime](#oh_imagesource_getdelaytime)获取。 |
| [OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md) | - | 定义图像源支持的格式字符串。此选项给[OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md)和[OH_ImageSource_GetSupportedFormats](#oh_imagesource_getsupportedformats)接口使用。 |
| [OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md) | - | 定义图像源支持的格式字符串列表。由[OH_ImageSource_GetSupportedFormats](#oh_imagesource_getsupportedformats)获取。 |
| [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md) | - | 定义图像源属性键值字符串。此选项给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。 |
| [OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md) | - | 定义图像源更新数据选项，由[OH_ImageSource_UpdateData](#oh_imagesource_updatedata)获取。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_ImageSource_Create(napi_env env, struct OhosImageSource* src, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_create) | 通过给定的信息OhosImageSource和OhosImageSourceOps结构体，获取JavaScript native层API ImageSource对象。 |
| [int32_t OH_ImageSource_CreateFromUri(napi_env env, char* uri, size_t size,struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromuri) | 通过给定的标识符URI和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。 |
| [int32_t OH_ImageSource_CreateFromFd(napi_env env, int32_t fd,struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromfd) | 通过给定的文件描述符fd和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。 |
| [int32_t OH_ImageSource_CreateFromData(napi_env env, uint8_t* data, size_t dataSize,struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromdata) | 通过给定的图像源缓冲区资源data和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。 |
| [int32_t OH_ImageSource_CreateFromRawFile(napi_env env, RawFileDescriptor rawFile,struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createfromrawfile) | 通过给定的资源描述符[RawFileDescriptor](../apis-localization-kit/capi-rawfile-rawfiledescriptor.md)和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。 |
| [int32_t OH_ImageSource_CreateIncremental(napi_env env, struct OhosImageSource* source, struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createincremental) | 通过给定的信息[OhosImageSource](capi-image-ohosimagesource.md)和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构，获取增量类型的JavaScript Native API ImageSource对象，图像数据应通过[OH_ImageSource_UpdateData](#oh_imagesource_updatedata)更新。|
| [int32_t OH_ImageSource_CreateIncrementalFromData(napi_env env, uint8_t* data, size_t dataSize,struct OhosImageSourceOps* ops, napi_value *res)](#oh_imagesource_createincrementalfromdata) | 通过给定的图像源缓冲区资源data和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取增量类型的JavaScript Native API ImageSource对象，图像数据应通过[OH_ImageSource_UpdateData](#oh_imagesource_updatedata)更新。 |
| [int32_t OH_ImageSource_GetSupportedFormats(struct OhosImageSourceSupportedFormatList* res)](#oh_imagesource_getsupportedformats) | 获取所有支持的解码格式元标记。 |
| [ImageSourceNative* OH_ImageSource_InitNative(napi_env env, napi_value source)](#oh_imagesource_initnative) | 从输入JavaScript native层ImageSource对象中，转换成[ImageSourceNative](capi-image-imagesourcenative-.md)值。 |
| [int32_t OH_ImageSource_CreatePixelMap(const ImageSourceNative* native,struct OhosImageDecodingOps* ops, napi_value *res)](#oh_imagesource_createpixelmap) | 通过一个给定的选项[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)结构体，从ImageSource中解码JavaScript native层PixelMap对象。 |
| [int32_t OH_ImageSource_CreatePixelMapList(const ImageSourceNative* native,struct OhosImageDecodingOps* ops, napi_value *res)](#oh_imagesource_createpixelmaplist) | 通过一个给定的选项[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)结构体结构体，从ImageSource中解码所有的JavaScript native层PixelMap对象列表。 |
| [int32_t OH_ImageSource_GetDelayTime(const ImageSourceNative* native,struct OhosImageSourceDelayTimeList* res)](#oh_imagesource_getdelaytime) | 从ImageSource（如GIF图像源）获取延迟时间列表。 |
| [int32_t OH_ImageSource_GetFrameCount(const ImageSourceNative* native, uint32_t *res)](#oh_imagesource_getframecount) | 从ImageSource中获取帧计数。 |
| [int32_t OH_ImageSource_GetImageInfo(const ImageSourceNative* native, int32_t index,struct OhosImageSourceInfo* info)](#oh_imagesource_getimageinfo) | 通过索引从ImageSource获取图像源信息。 |
| [int32_t OH_ImageSource_GetImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)](#oh_imagesource_getimageproperty) | 通过关键字从ImageSource中获取图像源属性。 |
| [int32_t OH_ImageSource_UpdateData(const ImageSourceNative* native, struct OhosImageSourceUpdateData* data)](#oh_imagesource_updatedata) | 为了增量类型的ImageSource更新源数据。 |
| [int32_t OH_ImageSource_Release(ImageSourceNative* native)](#oh_imagesource_release) | 释放native层图像源 <b>ImageSourceNative</b>。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| const char* OHOS_IMAGE_PROPERTY_BITS_PER_SAMPLE = "BitsPerSample" | 定义每个样本比特的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_ORIENTATION = "Orientation" | 定义方向的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_IMAGE_LENGTH = "ImageLength" | 定义图像长度的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_IMAGE_WIDTH = "ImageWidth" | 定义图像宽度的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_GPS_LATITUDE = "GPSLatitude" | 定义GPS纬度的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_GPS_LONGITUDE = "GPSLongitude" | 定义GPS经度的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_GPS_LATITUDE_REF = "GPSLatitudeRef" | 定义GPS纬度参考的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_GPS_LONGITUDE_REF = "GPSLongitudeRef" | 定义GPS经度参考的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_DATE_TIME_ORIGINAL = "DateTimeOriginal" | 定义初始日期时间的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_EXPOSURE_TIME = "ExposureTime" | 定义曝光时间的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_SCENE_TYPE = "SceneType" | 定义场景类型的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_ISO_SPEED_RATINGS = "ISOSpeedRatings" | 定义ISO速度等级的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_F_NUMBER = "FNumber" | 定义FNumber的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |
| const char* OHOS_IMAGE_PROPERTY_COMPRESSED_BITS_PER_PIXEL = "CompressedBitsPerPixel" | 定义每个像素的压缩比特的图像属性关键字。<br>此标签给[OH_ImageSource_GetImageProperty](#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](#oh_imagesource_modifyimageproperty)接口使用。<br>**起始版本：** 10 |

## 函数说明

### OH_ImageSource_Create()

```
int32_t OH_ImageSource_Create(napi_env env, struct OhosImageSource* src, struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的信息OhosImageSource和OhosImageSourceOps结构体，获取JavaScript native层API ImageSource对象。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [OH_ImageSource_CreateFromUri](#oh_imagesource_createfromuri)，[OH_ImageSource_CreateFromFd](#oh_imagesource_createfromfd)，[OH_ImageSource_CreateFromData](#oh_imagesource_createfromdata)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| struct OhosImageSource* src | 表明创建一个图像源的信息。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br>IMAGE_RESULT_BAD_PARAMETER：参数错误。<br>IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br>IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br>IMAGE_RESULT_SOURCE_DATA_INCOMPLETE：图像源数据不完整。<br>IMAGE_RESULT_SOURCE_DATA：图像源数据错误。<br>IMAGE_RESULT_GET_DATA_ABNORMAL：图像获取数据错误。<br>IMAGE_RESULT_TOO_LARGE：图像数据太大。<br>IMAGE_RESULT_DECODE_FAILED：解码失败。<br>IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br>IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：图像解码EXIF不支持。<br>IMAGE_RESULT_PROPERTY_NOT_EXIST：图像属性不存在。<br>IMAGE_RESULT_FILE_DAMAGED：文件损坏。<br>IMAGE_RESULT_FILE_FD_ERROR：文件FD错误。<br>IMAGE_RESULT_STREAM_SIZE_ERROR：数据流错误。<br>IMAGE_RESULT_SEEK_FAILED：查找文件失败。<br>IMAGE_RESULT_PEEK_FAILED：速览文件失败。<br>IMAGE_RESULT_FREAD_FAILED：读取文件失败。 |

### OH_ImageSource_CreateFromUri()

```
int32_t OH_ImageSource_CreateFromUri(napi_env env, char* uri, size_t size,struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的标识符URI和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| char* uri | 表明图像源资源标识符，接受文件资源或者base64资源。当前文件资源只支持绝对路径。 |
| size_t size | 表明图像源资源URI的长度。|
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |

### OH_ImageSource_CreateFromFd()

```
int32_t OH_ImageSource_CreateFromFd(napi_env env, int32_t fd,struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的文件描述符fd和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| int32_t fd | 表明图像源文件资源描述符。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |

### OH_ImageSource_CreateFromData()

```
int32_t OH_ImageSource_CreateFromData(napi_env env, uint8_t* data, size_t dataSize,struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的图像源缓冲区资源data和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| uint8_t* data | 表明图像源缓冲区资源，接受格式化包缓冲区或者base64缓冲区。 |
| size_t dataSize | 表明图像源缓冲区资源大小。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |

### OH_ImageSource_CreateFromRawFile()

```
int32_t OH_ImageSource_CreateFromRawFile(napi_env env, RawFileDescriptor rawFile,struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的资源描述符[RawFileDescriptor](../apis-localization-kit/capi-rawfile-rawfiledescriptor.md)和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取JavaScript native层API ImageSource对象。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| [RawFileDescriptor](../apis-localization-kit/capi-rawfile-rawfiledescriptor.md) rawFile | 表明图像源资源描述符。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |


### OH_ImageSource_CreateIncremental()

```
int32_t OH_ImageSource_CreateIncremental(napi_env env, struct OhosImageSource* source, struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的信息[OhosImageSource](capi-image-ohosimagesource.md)和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构，获取增量类型的JavaScript Native API ImageSource对象，图像数据应通过[OH_ImageSource_UpdateData](#oh_imagesource_updatedata)更新。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [OH_ImageSource_CreateIncrementalFromData](#oh_imagesource_createincrementalfromdata)


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| struct [OhosImageSource](capi-image-ohosimagesource.md)* source | 表明创建一个图像源的信息，只接收缓冲区类型。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |

### OH_ImageSource_CreateIncrementalFromData()

```
int32_t OH_ImageSource_CreateIncrementalFromData(napi_env env, uint8_t* data, size_t dataSize,struct OhosImageSourceOps* ops, napi_value *res)
```

**描述**

通过给定的图像源缓冲区资源data和[OhosImageSourceOps](capi-image-ohosimagesourceops.md)结构体，获取增量类型的JavaScript Native API ImageSource对象，图像数据应通过[OH_ImageSource_UpdateData](#oh_imagesource_updatedata)更新。

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| uint8_t* data | 表明图像源缓冲区资源，接受格式化包缓冲区或者base64缓冲区。 |
| size_t dataSize | 表明图像源缓冲区资源大小。 |
| struct [OhosImageSourceOps](capi-image-ohosimagesourceops.md)* ops | 表明创建一个图像源的选项。 |
| napi_value *res | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。 |

### OH_ImageSource_GetSupportedFormats()

```
int32_t OH_ImageSource_GetSupportedFormats(struct OhosImageSourceSupportedFormatList* res)
```

**描述**

获取所有支持的解码格式元标记。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| struct OhosImageSourceSupportedFormatList* res | 表明指向[OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md)结构的列表指针。<br>当supportedFormatList为nullptr并且size以res为0作为输入时，它将以ressize返回支持的格式大小。<br>为了获得所有的格式标记，它需要比supportedFormatList中的结果大小大的足够空间，还需要为[OhosImageSourceSupportedFormat](capi-image-ohosimagesourcesupportedformat.md)项目中的每个格式提供足够的空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_CHECK_FORMAT_ERROR：检查格式不对。 |

### OH_ImageSource_InitNative()

```
ImageSourceNative* OH_ImageSource_InitNative(napi_env env, napi_value source)
```

**描述**

从输入JavaScript native层ImageSource对象中，转换成[ImageSourceNative](capi-image-imagesourcenative-.md)值。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| napi_env env | 表明JNI环境的指针。 |
| napi_value source | 表明JavaScript native层API ImageSource对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ImageSourceNative](capi-image-imagesourcenative-.md)* | 如果操作成功返回[ImageSourceNative](capi-image-imagesourcenative-.md)指针；如果操作失败，返回空指针。 |

**参考：**

[OH_ImageSource_Release](#oh_imagesource_release)

### OH_ImageSource_CreatePixelMap()

```
int32_t OH_ImageSource_CreatePixelMap(const ImageSourceNative* native,struct OhosImageDecodingOps* ops, napi_value *res)
```

**描述**

通过一个给定的选项[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)结构体，从ImageSource中解码JavaScript native层PixelMap对象。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)* ops | 表明为了解码图像源的选项。 |
| napi_value *res | 表明JavaScript native层PixelMap对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_CREATE_ENCODER_FAILED：创建编码器失败。<br> IMAGE_RESULT_CHECK_FORMAT_ERROR：检查格式不对。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST：共享内存错误。<br> IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL：共享内存数据异常。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_MALLOC_ABNORMAL：图像错误。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_INIT_ABNORMAL：图片输入数据错误。<br> IMAGE_RESULT_CROP：裁剪错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_ENCODE_FAILED：增加位图失败。<br> IMAGE_RESULT_HW_DECODE_UNSUPPORT：不支持图片硬解码。<br> IMAGE_RESULT_HW_DECODE_FAILED：硬解码失败。<br>IMAGE_RESULT_ERR_IPC：ipc失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_ALPHA_TYPE_ERROR：硬解码失败。<br> IMAGE_RESULT_ALLOCATER_TYPE_ERROR：硬解码失败。 |

### OH_ImageSource_CreatePixelMapList()

```
int32_t OH_ImageSource_CreatePixelMapList(const ImageSourceNative* native,struct OhosImageDecodingOps* ops, napi_value *res)
```

**描述**

通过一个给定的选项[OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)结构体，从ImageSource中解码所有的JavaScript native层PixelMap对象列表。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md)* ops | 表明为了解码图像源的选项。 |
| napi_value *res | 表明JavaScript native层PixelMap列表对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_CREATE_ENCODER_FAILED：创建编码器失败。<br> IMAGE_RESULT_CHECK_FORMAT_ERROR：检查格式不对。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST：共享内存错误。<br> IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL：共享内存数据异常。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_MALLOC_ABNORMAL：图像错误。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_INIT_ABNORMAL：图片输入数据错误。<br> IMAGE_RESULT_CROP：裁剪错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_ENCODE_FAILED：增加位图失败。<br> IMAGE_RESULT_HW_DECODE_UNSUPPORT：不支持图片硬解码。<br> IMAGE_RESULT_HW_DECODE_FAILED：硬解码失败。<br>IMAGE_RESULT_ERR_IPC：ipc失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_ALPHA_TYPE_ERROR：硬解码失败。<br> IMAGE_RESULT_ALLOCATER_TYPE_ERROR：硬解码失败。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_GetDelayTime()

```
int32_t OH_ImageSource_GetDelayTime(const ImageSourceNative* native,struct OhosImageSourceDelayTimeList* res)
```

**描述**

从ImageSource（如GIF图像源）获取延迟时间列表。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageSourceDelayTimeList](capi-image-ohosimagesourcedelaytimelist.md)* res | 表明延迟时间列表OhosImageSourceDelayTimeList的指针。<br>当输入的res中delayTimeList是空指针并且size是0时，将通过res的size中返回延迟时间列表大小为了获取延迟时间，需要比返回的delayTimeList大小值大的足够空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_GetFrameCount()

```
int32_t OH_ImageSource_GetFrameCount(const ImageSourceNative* native, uint32_t *res)
```

**描述**

从ImageSource中获取帧计数。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| uint32_t *res | 表明帧计数的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_GetImageInfo()

```
int32_t OH_ImageSource_GetImageInfo(const ImageSourceNative* native, int32_t index,struct OhosImageSourceInfo* info)
```

**描述**

通过索引从ImageSource获取图像源信息。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| int32_t index | 表明帧计数的指针。 |
| struct [OhosImageSourceInfo](capi-image-ohosimagesourceinfo.md)* info | 表明图像源信息OhosImageSourceInfo的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br>OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_GetImageProperty()

```
int32_t OH_ImageSource_GetImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)
```

**描述**

通过关键字从ImageSource中获取图像源属性。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* key | 表明属性关键字OhosImageSourceProperty的指针。 |
| struct [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* value | 表明作为结果的属性值OhosImageSourceProperty的指针。当输入的value中value是空指针并且size是0时，将通过value中的size返回属性值的大小。为了获取属性值，需要比value中的结果大小大的足够的空间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br> OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_ModifyImageProperty()

```
int32_t OH_ImageSource_ModifyImageProperty(const ImageSourceNative* native, struct OhosImageSourceProperty* key, struct OhosImageSourceProperty* value)
```

**描述**

通过关键字为ImageSource修改图像源属性。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* key | 表明属性关键字OhosImageSourceProperty的指针。 |
| struct [OhosImageSourceProperty](capi-image-ohosimagesourceproperty.md)* value | 为了修改表明属性值OhosImageSourceProperty的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br> OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：skia错误。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_DECODE_EXIF_UNSUPPORT：解码的EXIF不支持。<br> IMAGE_RESULT_PROPERTY_NOT_EXIST：图片属性不存在。 |

### OH_ImageSource_UpdateData()

```
int32_t OH_ImageSource_UpdateData(const ImageSourceNative* native, struct OhosImageSourceUpdateData* data)
```

**描述**

为了增量类型的ImageSource更新源数据。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |
| struct [OhosImageSourceUpdateData](capi-image-ohosimagesourceupdatedata.md)* data | 表明更新数据信息OhosImageSourceUpdateData的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br> OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DECODE_FAILED：解码失败。<br> IMAGE_RESULT_DECODE_HEAD_ABNORMAL：图像解码头错误。<br> IMAGE_RESULT_CREATE_DECODER_FAILED：创建解码器失败。<br> IMAGE_RESULT_CREATE_ENCODER_FAILED：创建编码器失败。<br> IMAGE_RESULT_CHECK_FORMAT_ERROR：检查格式不对。<br> IMAGE_RESULT_THIRDPART_SKIA_ERROR：Skia第三方库出错。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。<br> IMAGE_RESULT_ERR_SHAMEM_NOT_EXIST：共享内存不存在。<br> IMAGE_RESULT_ERR_SHAMEM_DATA_ABNORMAL：共享内存数据异常。<br> IMAGE_RESULT_DECODE_ABNORMAL：图片解码异常。<br> IMAGE_RESULT_MALLOC_ABNORMAL：图像内存分配异常。<br> IMAGE_RESULT_DATA_UNSUPPORT：图片初始化错误。<br> IMAGE_RESULT_INIT_ABNORMAL：图片输入数据错误。<br> IMAGE_RESULT_CROP：裁剪失败。<br> IMAGE_RESULT_UNKNOWN_FORMAT：图片格式未知。<br> IMAGE_RESULT_PLUGIN_REGISTER_FAILED：注册插件失败。<br> IMAGE_RESULT_PLUGIN_CREATE_FAILED：创建插件失败。<br> IMAGE_RESULT_ENCODE_FAILED：增加位图失败。<br> IMAGE_RESULT_HW_DECODE_UNSUPPORT：不支持图片硬解码。<br> IMAGE_RESULT_HW_DECODE_FAILED：硬解码失败。<br> IMAGE_RESULT_ERR_IPC：IPC操作失败。<br> IMAGE_RESULT_INDEX_INVALID：索引无效。<br> IMAGE_RESULT_ALPHA_TYPE_ERROR：Alpha类型错误。<br> IMAGE_RESULT_ALLOCATER_TYPE_ERROR：内存分配器类型错误。 |

### OH_ImageSource_Release()

```
int32_t OH_ImageSource_Release(ImageSourceNative* native)
```

**描述**

释放native层图像源ImageSourceNative。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ImageSourceNative](capi-image-imagesourcenative-.md)* native | 表明native层ImageSourceNative值的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 参考[IRNdkErrCode](capi-image-mdk-common-h.md#irndkerrcode)：<br> OHOS_IMAGE_RESULT_SUCCESS：操作成功。<br> IMAGE_RESULT_BAD_PARAMETER：参数错误。<br> IMAGE_RESULT_JNI_ENV_ABNORMAL：JNI 环境异常。<br> IMAGE_RESULT_INVALID_PARAMETER：参数无效。<br> IMAGE_RESULT_GET_DATA_ABNORMAL：获取图片数据异常。<br> IMAGE_RESULT_DATA_ABNORMAL：输入图片数据错误。 |

**参考：**

[OH_ImageSource_Create](#oh_imagesource_create), [OH_ImageSource_CreateIncremental](#oh_imagesource_createincremental)


