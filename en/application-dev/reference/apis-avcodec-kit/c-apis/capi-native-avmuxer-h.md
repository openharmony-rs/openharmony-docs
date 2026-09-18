# native_avmuxer.h

## Overview

The file declares the native APIs used for audio and video multiplexing.

**Include**: <multimedia/player_framework/native_avmuxer.h>

**Library**: libnative_media_avmuxer.so

**System capability**: SystemCapability.Multimedia.Media.Muxer

**Since**: 10

**Related module**: [AVMuxer](capi-avmuxer.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) | OH_AVMuxer | The struct describes a native object for the muxer interface. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVMuxer *OH_AVMuxer_Create(int32_t fd, OH_AVOutputFormat format)](#oh_avmuxer_create) | Creates an OH_AVMuxer instance by using the file descriptor and container format. |
| [OH_AVErrCode OH_AVMuxer_SetRotation(OH_AVMuxer *muxer, int32_t rotation)](#oh_avmuxer_setrotation) | Sets the rotation angle (clockwise), which must be 0, 90, 180, or 270, of an output video. This function must be called before [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start). |
| [OH_AVErrCode OH_AVMuxer_SetFormat(OH_AVMuxer *muxer, OH_AVFormat *format)](#oh_avmuxer_setformat) | Set format to the muxer. |
| [OH_AVErrCode OH_AVMuxer_AddTrack(OH_AVMuxer *muxer, int32_t *trackIndex, OH_AVFormat *trackFormat)](#oh_avmuxer_addtrack) | Adds an audio or video track to a muxer. Each time this function is called, an audio or video track is added to the muxer. This function must be called before [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start). |
| [OH_AVErrCode OH_AVMuxer_Start(OH_AVMuxer *muxer)](#oh_avmuxer_start) | Starts a muxer. This function must be called after [OH_AVMuxer_AddTrack](capi-native-avmuxer-h.md#oh_avmuxer_addtrack) and before [OH_AVMuxer_WriteSample](capi-native-avmuxer-h.md#oh_avmuxer_writesample). |
| [OH_AVErrCode OH_AVMuxer_WriteSample(OH_AVMuxer *muxer, uint32_t trackIndex, OH_AVMemory *sample, OH_AVCodecBufferAttr info)](#oh_avmuxer_writesample) | Writes a sample to a muxer. This function must be called after [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start) and before [OH_AVMuxer_Stop](capi-native-avmuxer-h.md#oh_avmuxer_stop). The caller must write the sample to the correct audio or video track based on the timing in **info**.(Deprecated in API11) |
| [OH_AVErrCode OH_AVMuxer_WriteSampleBuffer(OH_AVMuxer *muxer, uint32_t trackIndex, const OH_AVBuffer *sample)](#oh_avmuxer_writesamplebuffer) | Writes a sample to a muxer. This function must be called after [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start) and before [OH_AVMuxer_Stop](capi-native-avmuxer-h.md#oh_avmuxer_stop). The caller must write the sample to the correct audio or video track based on the timing in **sample**. |
| [OH_AVErrCode OH_AVMuxer_Stop(OH_AVMuxer *muxer)](#oh_avmuxer_stop) | Stops a muxer. Once the muxer is stopped, it cannot be restarted. |
| [OH_AVErrCode OH_AVMuxer_Destroy(OH_AVMuxer *muxer)](#oh_avmuxer_destroy) | Clears internal resources and destroys an OH_AVMuxer instance.<br> Do not repeatedly destroy the instance. Otherwise, the program may crash. |

## Function description

### OH_AVMuxer_Create()

```c
OH_AVMuxer *OH_AVMuxer_Create(int32_t fd, OH_AVOutputFormat format)
```

**Description**

Creates an OH_AVMuxer instance by using the file descriptor and container format.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t fd | File descriptor (FD). You must open the file in read/write mode (O_RDWR) and close the file after using it. |
| OH_AVOutputFormat format | Format of the multiplexed output file. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVMuxer *](capi-avmuxer-oh-avmuxer.md) | Pointer to the OH_AVMuxer instance created. You must call [OH_AVMuxer_Destroy](capi-native-avmuxer-h.md#oh_avmuxer_destroy) to destroy the      instance when it is no longer needed. |

### OH_AVMuxer_SetRotation()

```c
OH_AVErrCode OH_AVMuxer_SetRotation(OH_AVMuxer *muxer, int32_t rotation)
```

**Description**

Sets the rotation angle (clockwise), which must be 0, 90, 180, or 270, of an output video. This function must be called before [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |
| int32_t rotation | Angle to set. The value must be 0, 90, 180, or 270. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null or the value of rotation is invalid.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence. |

### OH_AVMuxer_SetFormat()

```c
OH_AVErrCode OH_AVMuxer_SetFormat(OH_AVMuxer *muxer, OH_AVFormat *format)
```

**Description**

Set format to the muxer.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance |
| OH_AVFormat *format | OH_AVFormat handle pointer contain format |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: the muxer or format is invalid<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: not permit to call the interface, it was called in invalid state |

### OH_AVMuxer_AddTrack()

```c
OH_AVErrCode OH_AVMuxer_AddTrack(OH_AVMuxer *muxer, int32_t *trackIndex, OH_AVFormat *trackFormat)
```

**Description**

Adds an audio or video track to a muxer. Each time this function is called, an audio or video track is added to the muxer. This function must be called before [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |
| int32_t *trackIndex | Pointer to the index of the media track. The index will be used in the [OH_AVMuxer_WriteSample](capi-native-avmuxer-h.md#oh_avmuxer_writesample) function. If the media track is added, the index value is greater than or equal to 0; otherwise, the value is less than 0. |
| OH_AVFormat *trackFormat | Pointer to an OH_AVFormat instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null, or the track index or track format is invalid.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence.<br>    <br>{@link AV_ERR_UNSUPPORT}: The MIME type is not supported.<br>    <br>{@link AV_ERR_NO_MEMORY}: Memory allocation fails.<br>    <br>{@link AV_ERR_UNKNOWN}: An unknown error occurs. |

### OH_AVMuxer_Start()

```c
OH_AVErrCode OH_AVMuxer_Start(OH_AVMuxer *muxer)
```

**Description**

Starts a muxer. This function must be called after [OH_AVMuxer_AddTrack](capi-native-avmuxer-h.md#oh_avmuxer_addtrack) and before [OH_AVMuxer_WriteSample](capi-native-avmuxer-h.md#oh_avmuxer_writesample).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence.<br>    <br>{@link AV_ERR_UNKNOWN}: An unknown error occurs. |

### OH_AVMuxer_WriteSample()

```c
OH_AVErrCode OH_AVMuxer_WriteSample(OH_AVMuxer *muxer, uint32_t trackIndex, OH_AVMemory *sample, OH_AVCodecBufferAttr info)
```

**Description**

Writes a sample to a muxer. This function must be called after [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start) and before [OH_AVMuxer_Stop](capi-native-avmuxer-h.md#oh_avmuxer_stop). The caller must write the sample to the correct audio or video track based on the timing in **info**.

**Since**: 10

**Deprecated**: 11

**Replaced by**: OH_AVMuxer_WriteSampleBuffer

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |
| uint32_t trackIndex | Index of the audio or video track corresponding to the data. |
| OH_AVMemory *sample | Pointer to the data obtained after encoding or demultiplexing. |
| OH_AVCodecBufferAttr info | Sample description. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null, or the track index, sample, or info is invalid.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence.<br>    <br>{@link AV_ERR_NO_MEMORY}: Memory allocation fails.<br>    <br>{@link AV_ERR_UNKNOWN}: An unknown error occurs. |

### OH_AVMuxer_WriteSampleBuffer()

```c
OH_AVErrCode OH_AVMuxer_WriteSampleBuffer(OH_AVMuxer *muxer, uint32_t trackIndex, const OH_AVBuffer *sample)
```

**Description**

Writes a sample to a muxer. This function must be called after [OH_AVMuxer_Start](capi-native-avmuxer-h.md#oh_avmuxer_start) and before [OH_AVMuxer_Stop](capi-native-avmuxer-h.md#oh_avmuxer_stop). The caller must write the sample to the correct audio or video track based on the timing in **sample**.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |
| uint32_t trackIndex | Index of the audio or video track corresponding to the data. |
| const OH_AVBuffer *sample | Pointer to the data and properties obtained after encoding or demultiplexing. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null, or the track index or sample is invalid.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence.<br>    <br>{@link AV_ERR_NO_MEMORY}: Memory allocation fails.<br>    <br>{@link AV_ERR_UNKNOWN}: An unknown error occurs. |

### OH_AVMuxer_Stop()

```c
OH_AVErrCode OH_AVMuxer_Stop(OH_AVMuxer *muxer)
```

**Description**

Stops a muxer. Once the muxer is stopped, it cannot be restarted.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The function is called out of sequence. |

### OH_AVMuxer_Destroy()

```c
OH_AVErrCode OH_AVMuxer_Destroy(OH_AVMuxer *muxer)
```

**Description**

Clears internal resources and destroys an OH_AVMuxer instance.<br> Do not repeatedly destroy the instance. Otherwise, the program may crash.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVMuxer](capi-avmuxer-oh-avmuxer.md) *muxer | Pointer to an OH_AVMuxer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The muxer pointer is null. |


