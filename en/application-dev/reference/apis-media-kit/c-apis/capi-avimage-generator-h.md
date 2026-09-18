# avimage_generator.h

## Overview

The file declares the AVImageGenerator APIs. You can use the APIs to extract video frames at given time points from videos.

**Library**: libavimage_generator.so

**Since**: 18

**Related module**: [AVImageGenerator](capi-avimagegenerator.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVImageGenerator](capi-avimagegenerator-oh-avimagegenerator.md) | OH_AVImageGenerator | The OH_AVImageGenerator struct describes the type used for generating video frames at specified timestamps. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVImageGenerator* OH_AVImageGenerator_Create(void)](#oh_avimagegenerator_create) | Creates an OH_AVImageGenerator instance, which is used to generate video frames at given time points. |
| [OH_AVErrCode OH_AVImageGenerator_SetFDSource(OH_AVImageGenerator* generator, int32_t fd, int64_t offset, int64_t size)](#oh_avimagegenerator_setfdsource) | Sets a data source based on the media file descriptor. |
| [OH_AVErrCode OH_AVImageGenerator_FetchFrameByTime(OH_AVImageGenerator* generator, int64_t timeUs, OH_AVImageGenerator_QueryOptions options, OH_PixelmapNative** pixelMap)](#oh_avimagegenerator_fetchframebytime) | Extracts a video frame at a given time from a video. |
| [OH_AVErrCode OH_AVImageGenerator_Release(OH_AVImageGenerator* generator)](#oh_avimagegenerator_release) | Releases the resources used by the OH_AVImageGenerator instance and destroys the instance. |

## Function description

### OH_AVImageGenerator_Create()

```c
OH_AVImageGenerator* OH_AVImageGenerator_Create(void)
```

**Description**

Creates an OH_AVImageGenerator instance, which is used to generate video frames at given time points.

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVImageGenerator*](capi-avimagegenerator-oh-avimagegenerator.md) | Returns a pointer to an OH_AVImageGenerator instance for success, nullptr for failure.  Possible failure causes: HstEngineFactory failed to CreateAVMetadataHelperEngine. |

### OH_AVImageGenerator_SetFDSource()

```c
OH_AVErrCode OH_AVImageGenerator_SetFDSource(OH_AVImageGenerator* generator, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets a data source based on the media file descriptor.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVImageGenerator](capi-avimagegenerator-oh-avimagegenerator.md)* generator | Pointer to the OH_AVImageGenerator instance. |
| int32_t fd | File descriptor of the media source. |
| int64_t offset | Offset of the media source in the file descriptor. |
| int64_t size | Size of the media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  {@link AV_ERR_OK}: the execution is successful.<br>{@link AV_ERR_INVALID_VAL}: input generator is nullptr or input param is invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: operation not allowed.<br>{@link AV_ERR_NO_MEMORY}: internal memory allocation failed. |

### OH_AVImageGenerator_FetchFrameByTime()

```c
OH_AVErrCode OH_AVImageGenerator_FetchFrameByTime(OH_AVImageGenerator* generator, int64_t timeUs, OH_AVImageGenerator_QueryOptions options, OH_PixelmapNative** pixelMap)
```

**Description**

Extracts a video frame at a given time from a video.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVImageGenerator](capi-avimagegenerator-oh-avimagegenerator.md)* generator | Pointer to the OH_AVImageGenerator instance. |
| int64_t timeUs | Time point of the video frame to be extracted in the video, in μs. |
| OH_AVImageGenerator_QueryOptions options | Mappings between the given time points and video frames. |
| OH_PixelmapNative** pixelMap | Double pointer to the video frame object obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  {@link AV_ERR_OK}: the execution is successful.<br>{@link AV_ERR_INVALID_VAL}: input generator is nullptr or input param is invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: operation not allowed.<br>{@link AV_ERR_UNSUPPORTED_FORMAT}: format is unsupported.<br>{@link AV_ERR_NO_MEMORY}: internal memory allocation failed. |

### OH_AVImageGenerator_Release()

```c
OH_AVErrCode OH_AVImageGenerator_Release(OH_AVImageGenerator* generator)
```

**Description**

Releases the resources used by the OH_AVImageGenerator instance and destroys the instance.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVImageGenerator](capi-avimagegenerator-oh-avimagegenerator.md)* generator | Pointer to the OH_AVImageGenerator instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.  {@link AV_ERR_OK}: the execution is successful.<br>{@link AV_ERR_INVALID_VAL}: input generator is nullptr or input param is invalid. |


