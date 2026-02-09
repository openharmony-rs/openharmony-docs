# avmetadata_extractor.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the AVMetadataExtractor APIs. You can use the APIs to obtain metadata from media assets.

**File to include**: <multimedia/player_framework/avmetadata_extractor.h>

**Library**: libavmetadata_extractor.so

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Related module**: [AVMetadataExtractor](capi-avmetadataextractor.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) | OH_AVMetadataExtractor | Describes the OH_AVMetadataExtractor.|

### Functions

| Name| Description|
| -- | -- |
| [OH_AVMetadataExtractor_OutputParam* OH_AVMetadataExtractor_OutputParam_Create()](#oh_avmetadataextractor_outputparam_create) | Creates an **OH_AVMetadataExtractor_OutputParam** instance.|
| [void OH_AVMetadataExtractor_OutputParam_Destroy(OH_AVMetadataExtractor_OutputParam* outputParam)](#oh_avmetadataextractor_outputparam_destroy) | Releases the **OH_AVMetadataExtractor_OutputParam** instance.|
| [bool OH_AVMetadataExtractor_OutputParam_SetSize(OH_AVMetadataExtractor_OutputParam* outputParam, int32_t width, int32_t height)](#oh_avmetadataextractor_outputparam_setsize) | Sets the expected output size of the **OH_AVMetadataExtractor_OutputParam** instance. If **width** or **height** is less than 0, the original width or height is used. If **width** or **height** is 0, the aspect ratio is maintained and the image is scaled proportionally. If both **width** and **height** are greater than 0, they are used to scale the image.|
| [OH_AVErrCode OH_AVMetadataExtractor_FetchFrameByTime(OH_AVMetadataExtractor *extractor, int64_t timeUs, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_PixelmapNative** pixelMap)](#oh_avmetadataextractor_fetchframebytime) | Extracts an image at a specified time point from the video source. This function must be used after resources are set.|
| [typedef void (\*OH_AVMetadataExtractor_OnFrameFetched)(OH_AVMetadataExtractor *extractor, const OH_AVMetadataExtractor_FrameInfo* frameInfo, OH_AVErrCode code, void* userData)](#oh_avmetadataextractor_onframefetched) | Defines a callback used to obtain the frames captured by **AVMetadataExtractor**. Note: **frameInfo** is automatically released after the callback. However, you need to use [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to release **frameInfo.image** to avoid memory leaks.|
| [OH_AVErrCode OH_AVMetadataExtractor_FetchFramesByTimes(OH_AVMetadataExtractor *extractor, int64_t timeUs[], uint16_t timesUsSize, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_AVMetadataExtractor_OnFrameFetched onFrameInfoCallback, void* userData)](#oh_avmetadataextractor_fetchframesbytimes) | Extracts images at multiple specified time points from the video source asynchronously. This function must be used after resources are set.|
| [void OH_AVMetadataExtractor_CancelAllFetchFrames(OH_AVMetadataExtractor *extractor)](#oh_avmetadataextractor_cancelallfetchframes) | Cancels all batch image obtaining operations initiated by [OH_AVMetadataExtractor_FetchFramesByTimes](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchframesbytimes). If this function is called, the pending fetch operation is canceled and the result is marked as canceled in the [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) callback.|
| [OH_AVFormat *OH_AVMetadataExtractor_GetTrackDescription(OH_AVMetadataExtractor *extractor, uint32_t index)](#oh_avmetadataextractor_gettrackdescription) | Obtains the track description of a specified index from the media source. This function must be used after resources are set.|
| [OH_AVFormat *OH_AVMetadataExtractor_GetCustomInfo(OH_AVMetadataExtractor *extractor)](#oh_avmetadataextractor_getcustominfo) | Obtains custom metadata from the media source. This function must be used after resources are set.|
| [OH_AVErrCode OH_AVMetadataExtractor_SetMediaSource(OH_AVMetadataExtractor *extractor, OH_AVMediaSource *source)](#oh_avmetadataextractor_setmediasource) | Sets the media source for the extractor.|
| [OH_AVMetadataExtractor* OH_AVMetadataExtractor_Create(void)](#oh_avmetadataextractor_create) | Creates an OH_AVMetadataExtractor instance.|
| [OH_AVErrCode OH_AVMetadataExtractor_SetFDSource(OH_AVMetadataExtractor* extractor, int32_t fd, int64_t offset, int64_t size)](#oh_avmetadataextractor_setfdsource) | Sets a data source based on the media file descriptor.|
| [OH_AVErrCode OH_AVMetadataExtractor_FetchMetadata(OH_AVMetadataExtractor* extractor, OH_AVFormat* avMetadata)](#oh_avmetadataextractor_fetchmetadata) | Obtains metadata from a media asset.<br>        This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).|
| [OH_AVErrCode OH_AVMetadataExtractor_FetchAlbumCover(OH_AVMetadataExtractor* extractor, OH_PixelmapNative** pixelMap)](#oh_avmetadataextractor_fetchalbumcover) | Obtains the cover of an audio album.<br>        This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).|
| [OH_AVErrCode OH_AVMetadataExtractor_Release(OH_AVMetadataExtractor* extractor)](#oh_avmetadataextractor_release) | Releases the resources used by the OH_AVMetadataExtractor instance and destroys the instance.|

## Function Description

### OH_AVMetadataExtractor_OutputParam_Create()

```c
OH_AVMetadataExtractor_OutputParam* OH_AVMetadataExtractor_OutputParam_Create()
```

**Description**

Creates an **OH_AVMetadataExtractor_OutputParam** instance.

**Since**: 23

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md) * | Pointer to the **OH_AVMetadataExtractor_OutputParam** instance.|

### OH_AVMetadataExtractor_OutputParam_Destroy()

```c
void OH_AVMetadataExtractor_OutputParam_Destroy(OH_AVMetadataExtractor_OutputParam* outputParam)
```

**Description**

Releases the **OH_AVMetadataExtractor_OutputParam** instance.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md)* outputParam | Pointer to the **OH_AVMetadataExtractor_OutputParam** instance.|

### OH_AVMetadataExtractor_OutputParam_SetSize()

```c
bool OH_AVMetadataExtractor_OutputParam_SetSize(OH_AVMetadataExtractor_OutputParam* outputParam, int32_t width, int32_t height)
```

**Description**

Sets the expected output size of the **OH_AVMetadataExtractor_OutputParam** instance. If **width** or **height** is less than 0, the original width or height is used. If **width** or **height** is 0, the aspect ratio is maintained and the image is scaled proportionally. If both **width** and **height** are greater than 0, they are used to scale the image.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md)* outputParam | Pointer to the **OH_AVMetadataExtractor_OutputParam** instance.|
| int32_t width | Expected width of the output image, which can be scaled if necessary.|
| int32_t height | Expected height of the output image, which can be scaled if necessary.|

**Return value**

| Type| Description|
| -- | -- |
| bool | **true** if the operation is successful; **false** otherwise.<br>     Possible cause: **outputParam** is a null pointer.|

### OH_AVMetadataExtractor_FetchFrameByTime()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchFrameByTime(OH_AVMetadataExtractor *extractor, int64_t timeUs, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_PixelmapNative** pixelMap)
```

**Description**

Extracts an image at a specified time point from the video source. This function must be used after resources are set.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|
| int64_t timeUs | Time (in microseconds) at which an image is extracted from the video resource.|
| [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode) seekMode | Seek mode that defines the relationship between the specified time and the key frame. For details, see [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode).|
| [const OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md)* outputParam | Output parameter of the image, for example, the height or width of the image. For details, see [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md). If this parameter is a null pointer, the original size of the video is used. Note: You need to use [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to release the pixel map after using it.|
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelMap | Used to receive images extracted from the video source. For details, see [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md).|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.<br>         **AV_ERR_UNSUPPORTED_FORMAT**: The format is not supported.<br>         **AV_ERR_SERVICE_DIED**: The service is terminated.<br>         **AV_ERR_IO_CLEARTEXT_NOT_PERMITTED**: Plaintext HTTP traffic is not allowed.|

### OH_AVMetadataExtractor_OnFrameFetched()

```c
typedef void (*OH_AVMetadataExtractor_OnFrameFetched)(OH_AVMetadataExtractor *extractor, const OH_AVMetadataExtractor_FrameInfo* frameInfo, OH_AVErrCode code, void* userData)
```

**Description**

Defines a callback used to obtain the frames captured by **AVMetadataExtractor**. Note: **frameInfo** is automatically released after the callback. However, you need to use [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to release **frameInfo.image** to avoid memory leaks.

**Since**: 23

### OH_AVMetadataExtractor_FetchFramesByTimes()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchFramesByTimes(OH_AVMetadataExtractor *extractor, int64_t timeUs[], uint16_t timesUsSize, OH_AVMedia_SeekMode seekMode, const OH_AVMetadataExtractor_OutputParam* outputParam, OH_AVMetadataExtractor_OnFrameFetched onFrameInfoCallback, void* userData)
```

**Description**

Extracts images at multiple specified time points from the video source asynchronously. This function must be used after resources are set.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|
| int64_t timeUs[] | Time point array (in microseconds) when images are extracted from the video source.|
| uint16_t timesUsSize | Length of the time point array.|
| [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode) seekMode | Seek mode that defines the relationship between the specified time and the key frame. For details, see [OH_AVMedia_SeekMode](capi-avmedia-base-h.md#oh_avmedia_seekmode).|
| [const OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md)* outputParam | Output parameter of the image, for example, the height or width of the image. For details, see [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md). If this parameter is a null pointer, the original video size is used for the obtained frame.|
| [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) onFrameInfoCallback | Callback function invoked after each frame is extracted or fails to be extracted.|
| void* userData | Pointer to the user-defined data passed to the callback function.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter is invalid.<br>         **AV_ERR_SERVICE_DIED**: The service is terminated.<br>         **AV_ERR_IO_CLEARTEXT_NOT_PERMITTED**: Plaintext HTTP traffic is not allowed.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. This error code is returned by **onFrameInfoCallback**.<br>         **AV_ERR_UNSUPPORTED_FORMAT**: The format is not supported. This error code is returned by **onFrameInfoCallback**.<br>         **AV_ERR_TIMEOUT**: The execution times out. This error code is returned by **onFrameInfoCallback**.|

### OH_AVMetadataExtractor_CancelAllFetchFrames()

```c
void OH_AVMetadataExtractor_CancelAllFetchFrames(OH_AVMetadataExtractor *extractor)
```

**Description**

Cancels all batch image obtaining operations initiated by [OH_AVMetadataExtractor_FetchFramesByTimes](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchframesbytimes). If this function is called, the pending fetch operation is canceled and the result is marked as canceled in the [OH_AVMetadataExtractor_OnFrameFetched](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_onframefetched) callback.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|

### OH_AVMetadataExtractor_GetTrackDescription()

```c
OH_AVFormat *OH_AVMetadataExtractor_GetTrackDescription(OH_AVMetadataExtractor *extractor, uint32_t index)
```

**Description**

Obtains the track description of a specified index from the media source. This function must be used after resources are set.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|
| uint32_t index | Index of the track description to be obtained.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the **OH_AVFormat** instance that contains the track description if the operation is successful; null pointer otherwise.<br>         The possible causes of an operation failure are as follows:<br>         1. The **extractor** is a null pointer.<br>         2. The media source is not set.<br>         3. The format is not supported.<br>         Note: You need to use [OH_AVFormat_Destroy](../apis-avcodec-kit/capi-native-avformat-h.md#oh_avformat_destroy) to release the **OH_AVFormat** instance after using it.|

### OH_AVMetadataExtractor_GetCustomInfo()

```c
OH_AVFormat *OH_AVMetadataExtractor_GetCustomInfo(OH_AVMetadataExtractor *extractor)
```

**Description**

Obtains custom metadata from the media source. This function must be used after resources are set.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the **OH_AVFormat** instance that contains custom metadata if the operation is successful; null pointer otherwise.<br>         The possible causes of an operation failure are as follows:<br>         1. The **extractor** is a null pointer.<br>         2. The media source is not set.<br>         3. The custom information is not found.<br>         Note: You need to use [OH_AVFormat_Destroy](../apis-avcodec-kit/capi-native-avformat-h.md#oh_avformat_destroy) to release the **OH_AVFormat** instance after using it.|

### OH_AVMetadataExtractor_SetMediaSource()

```c
OH_AVErrCode OH_AVMetadataExtractor_SetMediaSource(OH_AVMetadataExtractor *extractor, OH_AVMediaSource *source)
```

**Description**

Sets the media source for the extractor.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md) *extractor | Pointer to the OH_AVMetadataExtractor instance.|
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Media source to be set.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input **extractor** is a null pointer or the **source** is invalid.|

### OH_AVMetadataExtractor_Create()

```c
OH_AVMetadataExtractor* OH_AVMetadataExtractor_Create(void)
```

**Description**

Creates an OH_AVMetadataExtractor instance.

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* | Pointer to the OH_AVMetadataExtractor instance created if the operation is successful; nullptr otherwise.<br>         Possible cause of failures: **HstEngineFactory::CreateAVMetadataHelperEngine** fails to run.|

### OH_AVMetadataExtractor_SetFDSource()

```c
OH_AVErrCode OH_AVMetadataExtractor_SetFDSource(OH_AVMetadataExtractor* extractor, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets a data source based on the media file descriptor.

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the OH_AVMetadataExtractor instance.|
| int32_t fd | File descriptor of the media source.|
| int64_t offset | Offset of the media source in the file descriptor.|
| int64_t size | Size of the media source.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **extractor** is nullptr or a parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is forbidden.<br>         **AV_ERR_NO_MEMORY**: Internal memory allocation failed.|

### OH_AVMetadataExtractor_FetchMetadata()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchMetadata(OH_AVMetadataExtractor* extractor, OH_AVFormat* avMetadata)
```

**Description**

Obtains metadata from a media asset.<br>        This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the OH_AVMetadataExtractor instance.|
| [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md)* avMetadata | Pointer to the OH_AVFormat instance, which contains the obtained metadata.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **extractor** is nullptr or a parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is forbidden.<br>         **AV_ERR_UNSUPPORTED_FORMAT**: The format is not supported.<br>         **AV_ERR_NO_MEMORY**: Internal memory allocation failed.|

### OH_AVMetadataExtractor_FetchAlbumCover()

```c
OH_AVErrCode OH_AVMetadataExtractor_FetchAlbumCover(OH_AVMetadataExtractor* extractor, OH_PixelmapNative** pixelMap)
```

**Description**

Obtains the cover of an audio album.<br>        This function must be called after [OH_AVMetadataExtractor_SetFDSource](capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource).

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the OH_AVMetadataExtractor instance.|
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelMap | Double pointer to the album cover obtained.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **extractor** is nullptr or a parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is forbidden.<br>         **AV_ERR_UNSUPPORTED_FORMAT**: The format is not supported.<br>         **AV_ERR_NO_MEMORY**: Internal memory allocation failed.|

### OH_AVMetadataExtractor_Release()

```c
OH_AVErrCode OH_AVMetadataExtractor_Release(OH_AVMetadataExtractor* extractor)
```

**Description**

Releases the resources used by the OH_AVMetadataExtractor instance and destroys the instance.

**System capability**: SystemCapability.Multimedia.Media.AVMetadataExtractor

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVMetadataExtractor](capi-avmetadataextractor-oh-avmetadataextractor.md)* extractor | Pointer to the OH_AVMetadataExtractor instance.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **extractor** is nullptr or a parameter is invalid.|
