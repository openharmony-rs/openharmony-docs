# avmetadata_extractor.h

## Overview

The file declares the AVMetadataExtractor APIs. You can use the APIs to obtain metadata from media assets.

**Library**: libavmetadata_extractor.so

**Since**: 18

**Related module**: [AVMetadataExtractor](capi-avmetadataextractor.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) | OH_AVMetadataExtractor | The struct describes the OH_AVMetadataExtractor type. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVFormat *OH_AVMetadataExtractor_GetTrackDescription(OH_AVMetadataExtractor *extractor, uint32_t index)](#oh_avmetadataextractor_gettrackdescription) | - | Obtains the track description of a specified index from the media source. This function must be used after resources are set. |
| [OH_AVFormat *OH_AVMetadataExtractor_GetCustomInfo(OH_AVMetadataExtractor *extractor)](#oh_avmetadataextractor_getcustominfo) | - | Obtains custom metadata from the media source. This function must be used after resources are set. |
| [OH_AVErrCode OH_AVMetadataExtractor_SetMediaSource(OH_AVMetadataExtractor *extractor, OH_AVMediaSource *source)](#oh_avmetadataextractor_setmediasource) | - | Sets the media source for the extractor. |
| [OH_AVMetadataExtractor* OH_AVMetadataExtractor_Create(void)](#oh_avmetadataextractor_create) | - | Creates an **OH_AVMetadataExtractor** instance. |
| [OH_AVErrCode OH_AVMetadataExtractor_SetFDSource(OH_AVMetadataExtractor* extractor, int32_t fd, int64_t offset, int64_t size)](#oh_avmetadataextractor_setfdsource) | - | Sets a data source based on the media file descriptor. |
| [OH_AVErrCode OH_AVMetadataExtractor_FetchMetadata(OH_AVMetadataExtractor* extractor, OH_AVFormat* avMetadata)](#oh_avmetadataextractor_fetchmetadata) | - | Obtains metadata from a media asset. This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource). |
| [OH_AVErrCode OH_AVMetadataExtractor_FetchAlbumCover(OH_AVMetadataExtractor* extractor, OH_PixelmapNative** pixelMap)](#oh_avmetadataextractor_fetchalbumcover) | - | Obtains the cover of an audio album. This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource). |
| [OH_AVErrCode OH_AVMetadataExtractor_FetchFrameByTime(OH_AVMetadataExtractor *extractor, int64_t timeUs, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_PixelmapNative** pixelMap)](#oh_avmetadataextractor_fetchframebytime) | - | Extracts an image at a specified time point from the video source. This function must be used after resources are set. |
| [typedef void (\*OH_AVMetadataExtractor_OnFrameFetched)(OH_AVMetadataExtractor *extractor, const OH_AVMetadataExtractor_FrameInfo* frameInfo, OH_AVErrCode code, void *userData)](#oh_avmetadataextractor_onframefetched) | OH_AVMetadataExtractor_OnFrameFetched | Defines a callback used to obtain the frames captured by **AVMetadataExtractor**. Note: **frameInfo** is automatically released after the callback. However, you need to use {@link OH_PixelmapNative_Destroy} to release **<br>frameInfo.image** to avoid memory leaks. |
| [OH_AVErrCode OH_AVMetadataExtractor_FetchFramesByTimes(OH_AVMetadataExtractor *extractor, int64_t timesUs[], uint16_t timesUsSize, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_AVMetadataExtractor_OnFrameFetched onFrameInfoCallback, void* userData)](#oh_avmetadataextractor_fetchframesbytimes) | - | Extracts images at multiple specified time points from the video source asynchronously. This function must be used after resources are set. |
| [void OH_AVMetadataExtractor_CancelAllFetchFrames(OH_AVMetadataExtractor *extractor)](#oh_avmetadataextractor_cancelallfetchframes) | - | Cancels all batch image obtaining operations initiated by [OH_AVMetadataExtractor_FetchFramesByTimes](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchframesbytimes). If this function is called, the pending fetch operation is canceled and the result is marked as canceled in the [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) callback. |
| [OH_AVErrCode OH_AVMetadataExtractor_Release(OH_AVMetadataExtractor* extractor)](#oh_avmetadataextractor_release) | - | Releases the resources used by the **OH_AVMetadataExtractor** instance and destroys the instance. |
| [OH_AVMetadataExtractor_OutputParam* OH_AVMetadataExtractor_OutputParam_Create()](#oh_avmetadataextractor_outputparam_create) | - | Creates an **OH_AVMetadataExtractor_OutputParam** instance. |
| [void OH_AVMetadataExtractor_OutputParam_Destroy(OH_AVMetadataExtractor_OutputParam* outputParam)](#oh_avmetadataextractor_outputparam_destroy) | - | Releases the **OH_AVMetadataExtractor_OutputParam** instance. |
| [bool OH_AVMetadataExtractor_OutputParam_SetSize(OH_AVMetadataExtractor_OutputParam* outputParam, int32_t width, int32_t height)](#oh_avmetadataextractor_outputparam_setsize) | - | Sets the expected output size of the **OH_AVMetadataExtractor_OutputParam** instance. If **width** or **<br>height** is less than 0, the original width or height is used. If **width** or **height** is 0, the aspect ratio is maintained and the image is scaled proportionally. If both **width** and **height** are greater than 0, they are used to scale the image. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AVMetadataExtractor_OnFrameFetched)(OH_AVMetadataExtractor *extractor, const OH_AVMetadataExtractor_FrameInfo* frameInfo, OH_AVErrCode code, void *userData) | Defines a callback used to obtain the frames captured by **AVMetadataExtractor**. Note: **frameInfo** is automatically released after the callback. However, you need to use {@link OH_PixelmapNative_Destroy} to release **<br>frameInfo.image** to avoid memory leaks.<br>**Since**: 23 |

## Function description

### OH_AVMetadataExtractor_GetTrackDescription()

```c
OH_AVFormat *OH_AVMetadataExtractor_GetTrackDescription(OH_AVMetadataExtractor *extractor, uint32_t index)
```

**Description**

Obtains the track description of a specified index from the media source. This function must be used after resources are set.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| uint32_t index | Index of the track description to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Returns a pointer to an OH_AVFormat instance containing track description for success, nullptr for failure.  Possible failure causes: extractor is nullptr, no source set, or format is unsupported.  Note: User need release OH_AVFormat by [OH_AVFormat_Destroy](capi-native-avformat-h.md#oh_avformat_destroy) after use. |

### OH_AVMetadataExtractor_GetCustomInfo()

```c
OH_AVFormat *OH_AVMetadataExtractor_GetCustomInfo(OH_AVMetadataExtractor *extractor)
```

**Description**

Obtains custom metadata from the media source. This function must be used after resources are set.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Returns a pointer to an OH_AVFormat instance containing custom metadata for success, nullptr for failure.  Possible failure causes: extractor is nullptr, no source set, or custom info not found.  Note: User need release OH_AVFormat by [OH_AVFormat_Destroy](capi-native-avformat-h.md#oh_avformat_destroy) after use. |

### OH_AVMetadataExtractor_SetMediaSource()

```c
OH_AVErrCode OH_AVMetadataExtractor_SetMediaSource(OH_AVMetadataExtractor *extractor, OH_AVMediaSource *source)
```

**Description**

Sets the media source for the extractor.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| OH_AVMediaSource *source | Media source to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): input extractor is nullptr or input source is invalid. |

### OH_AVMetadataExtractor_Create()

```c
OH_AVMetadataExtractor* OH_AVMetadataExtractor_Create(void)
```

**Description**

Creates an **OH_AVMetadataExtractor** instance.

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVMetadataExtractor*](capi-avmetadataextractor-oh-avmetadataextractor.md) | Returns a pointer to an OH_AVMetadataExtractor instance for success, nullptr for failure  Possible failure causes: failed to HstEngineFactory::CreateAVMetadataHelperEngine. |

### OH_AVMetadataExtractor_SetFDSource()

```c
OH_AVErrCode OH_AVMetadataExtractor_SetFDSource(OH_AVMetadataExtractor* extractor, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets a data source based on the media file descriptor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| int32_t fd | File descriptor of the media source. |
| int64_t offset | Offset of the media source in the file descriptor. |
| int64_t size | Size of the media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): input extractor is nullptr or input param is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): operation not allowed.  [AV_ERR_NO_MEMORY](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): internal memory allocation failed. |

### OH_AVMetadataExtractor_FetchMetadata()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchMetadata(OH_AVMetadataExtractor* extractor, OH_AVFormat* avMetadata)
```

**Description**

Obtains metadata from a media asset. This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| OH_AVFormat* avMetadata | Pointer to the **OH_AVFormat** instance, which contains the obtained metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): input extractor is nullptr or input param is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): operation not allowed.  [AV_ERR_UNSUPPORTED_FORMAT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): format is unsupported.  [AV_ERR_NO_MEMORY](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): internal memory allocation failed.  [AV_ERR_IO_CLEARTEXT_NOT_PERMITTED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): http cleartext traffic is not permitted. Add since api 23. |

### OH_AVMetadataExtractor_FetchAlbumCover()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchAlbumCover(OH_AVMetadataExtractor* extractor, OH_PixelmapNative** pixelMap)
```

**Description**

Obtains the cover of an audio album. This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| OH_PixelmapNative** pixelMap | Double pointer to the album cover obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): input extractor is nullptr or input param is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): operation not allowed.  [AV_ERR_UNSUPPORTED_FORMAT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): format is unsupported.  [AV_ERR_NO_MEMORY](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): internal memory allocation failed. |

### OH_AVMetadataExtractor_FetchFrameByTime()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchFrameByTime(OH_AVMetadataExtractor *extractor, int64_t timeUs, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_PixelmapNative** pixelMap)
```

**Description**

Extracts an image at a specified time point from the video source. This function must be used after resources are set.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| int64_t timeUs | Time (in microseconds) at which an image is extracted from the video resource. |
| OH_AVMedia_SeekMode seekMode | Seek mode that defines the relationship between the specified time and the key frame. For details, see [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode). |
| const OH_AVMetadataExtractor_OutputParam* outputParam | Output parameter of the image, for example, the height or width of the image. For details, see [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md). If this parameter is a null pointer, the original size of the video is used. Note: You need to use {@link OH_PixelmapNative_Destroy} to release the pixel map after using it. |
| OH_PixelmapNative** pixelMap | Used to receive images extracted from the video source. For details, see {@link OH_PixelmapNative}. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the input param is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): operation not allowed.  [AV_ERR_UNSUPPORTED_FORMAT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): format is unsupported.  [AV_ERR_SERVICE_DIED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the service died.  [AV_ERR_IO_CLEARTEXT_NOT_PERMITTED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): http cleartext traffic is not permitted. |

### OH_AVMetadataExtractor_OnFrameFetched()

```c
typedef void (*OH_AVMetadataExtractor_OnFrameFetched)(OH_AVMetadataExtractor *extractor, const OH_AVMetadataExtractor_FrameInfo* frameInfo, OH_AVErrCode code, void *userData)
```

**Description**

Defines a callback used to obtain the frames captured by **AVMetadataExtractor**. Note: **frameInfo** is automatically released after the callback. However, you need to use {@link OH_PixelmapNative_Destroy} to release **<br>frameInfo.image** to avoid memory leaks.

**Since**: 23

### OH_AVMetadataExtractor_FetchFramesByTimes()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchFramesByTimes(OH_AVMetadataExtractor *extractor, int64_t timesUs[], uint16_t timesUsSize, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_AVMetadataExtractor_OnFrameFetched onFrameInfoCallback, void* userData)
```

**Description**

Extracts images at multiple specified time points from the video source asynchronously. This function must be used after resources are set.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |
| int64_t timesUs[] | The times array expected to fetch picture from the video resource. The unit is microsecond(us). |
| uint16_t timesUsSize | Length of the time point array. |
| OH_AVMedia_SeekMode seekMode | Seek mode that defines the relationship between the specified time and the key frame. For details, see [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode). |
| const OH_AVMetadataExtractor_OutputParam* outputParam | Output parameter of the image, for example, the height or width of the image. For details, see [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md). If this parameter is a null pointer, the original video size is used for the obtained frame. |
| [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) onFrameInfoCallback | Callback function invoked after each frame is extracted or fails to be extracted. |
| void* userData | Pointer to the user-defined data passed to the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the input param is invalid.  [AV_ERR_SERVICE_DIED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the service died.  [AV_ERR_IO_CLEARTEXT_NOT_PERMITTED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): http cleartext traffic is not permitted.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): operation not allowed. Returned by onFrameInfoCallback.  [AV_ERR_UNSUPPORTED_FORMAT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): format is unsupported. Returned by onFrameInfoCallback.  [AV_ERR_TIMEOUT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is times out. Returned by onFrameInfoCallback. |

### OH_AVMetadataExtractor_CancelAllFetchFrames()

```c
void OH_AVMetadataExtractor_CancelAllFetchFrames(OH_AVMetadataExtractor *extractor)
```

**Description**

Cancels all batch image obtaining operations initiated by [OH_AVMetadataExtractor_FetchFramesByTimes](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchframesbytimes). If this function is called, the pending fetch operation is canceled and the result is marked as canceled in the [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the **OH_AVMetadataExtractor** instance. |

### OH_AVMetadataExtractor_Release()

```c
OH_AVErrCode OH_AVMetadataExtractor_Release(OH_AVMetadataExtractor* extractor)
```

**Description**

Releases the resources used by the **OH_AVMetadataExtractor** instance and destroys the instance.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the **OH_AVMetadataExtractor** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): the execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): input extractor is nullptr or input param is invalid. |

### OH_AVMetadataExtractor_OutputParam_Create()

```c
OH_AVMetadataExtractor_OutputParam* OH_AVMetadataExtractor_OutputParam_Create()
```

**Description**

Creates an **OH_AVMetadataExtractor_OutputParam** instance.

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVMetadataExtractor_OutputParam* | The new OH_AVMetadataExtractor_OutputParam instance. |

### OH_AVMetadataExtractor_OutputParam_Destroy()

```c
void OH_AVMetadataExtractor_OutputParam_Destroy(OH_AVMetadataExtractor_OutputParam* outputParam)
```

**Description**

Releases the **OH_AVMetadataExtractor_OutputParam** instance.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVMetadataExtractor_OutputParam* outputParam | Pointer to the **OH_AVMetadataExtractor_OutputParam** instance. |

### OH_AVMetadataExtractor_OutputParam_SetSize()

```c
bool OH_AVMetadataExtractor_OutputParam_SetSize(OH_AVMetadataExtractor_OutputParam* outputParam, int32_t width, int32_t height)
```

**Description**

Sets the expected output size of the **OH_AVMetadataExtractor_OutputParam** instance. If **width** or **<br>height** is less than 0, the original width or height is used. If **width** or **height** is 0, the aspect ratio is maintained and the image is scaled proportionally. If both **width** and **height** are greater than 0, they are used to scale the image.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVMetadataExtractor_OutputParam* outputParam | Pointer to the **OH_AVMetadataExtractor_OutputParam** instance. |
| int32_t width | Expected width of the output image, which can be scaled if necessary. |
| int32_t height | Expected height of the output image, which can be scaled if necessary. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | The return value is TRUE for success, FALSE for failure.  Possible failure causes: outputParam is nullptr. |


