# avtranscoder.h

## Overview

The file declares the native APIs provided by the AVTranscoder. You can use the APIs to transcode a source video file into a new video file.

**Library**: libavtranscoder.so

**Since**: 20

**Related module**: [AVTranscoder](capi-avtranscoder.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_AVTranscoder_Config *OH_AVTranscoderConfig_Create()](#oh_avtranscoderconfig_create) | Creates an instance of the transcoding configuration parameters. |
| [OH_AVErrCode OH_AVTranscoderConfig_Release(OH_AVTranscoder_Config* config)](#oh_avtranscoderconfig_release) | Releases the resources of the transcoding configuration parameters. After a successful call, the instance specified by **config** is released and set to nullptr. |
| [OH_AVErrCode OH_AVTranscoderConfig_SetSrcFD(OH_AVTranscoder_Config *config, int32_t srcFd, int64_t srcOffset, int64_t length)](#oh_avtranscoderconfig_setsrcfd) | Sets the file descriptor of the source video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstFD(OH_AVTranscoder_Config *config, int32_t dstFd)](#oh_avtranscoderconfig_setdstfd) | Sets the file descriptor of the output video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoType(OH_AVTranscoder_Config *config, const char *mimeType)](#oh_avtranscoderconfig_setdstvideotype) | Sets the encoding format of the output video for transcoding. Currently, only AVC and HEVC are supported. If the source video is in HEVC format, the default value is **HEVC**. Otherwise, the default value is **AVC**. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioType(OH_AVTranscoder_Config *config, const char *mimeType)](#oh_avtranscoderconfig_setdstaudiotype) | Sets the encoding format of the output audio for transcoding. Currently, only AAC is supported. If this parameter is not set, AAC is used by default. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstFileType(OH_AVTranscoder_Config *config, OH_AVOutputFormat mimeType)](#oh_avtranscoderconfig_setdstfiletype) | Sets the container format of the output video file for transcoding. Currently, only MP4 is supported. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)](#oh_avtranscoderconfig_setdstaudiobitrate) | Sets the bit rate of the output audio for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)](#oh_avtranscoderconfig_setdstvideobitrate) | Sets the bit rate of the output video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoResolution(OH_AVTranscoder_Config *config, int32_t width, int32_t height)](#oh_avtranscoderconfig_setdstvideoresolution) | Sets the resolution of the output video for transcoding, in px, where **width** is the width of the output video frame and **height** is the height of the output video frame. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). |
| [OH_AVTranscoder *OH_AVTranscoder_Create(void)](#oh_avtranscoder_create) | Creates an AVTranscoder instance. |
| [OH_AVErrCode OH_AVTranscoder_Prepare(OH_AVTranscoder *transcoder, OH_AVTranscoder_Config *config)](#oh_avtranscoder_prepare) | Sets the parameters for video transcoding and prepares for transcoding. This function must be called before [OH_AVTranscoder_Start](capi-avtranscoder-h.md#oh_avtranscoder_start). Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_PREPARED state. |
| [OH_AVErrCode OH_AVTranscoder_Start(OH_AVTranscoder *transcoder)](#oh_avtranscoder_start) | Starts transcoding. This function must be called after a successful call to [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_STARTED state. |
| [OH_AVErrCode OH_AVTranscoder_Pause(OH_AVTranscoder *transcoder)](#oh_avtranscoder_pause) | Pauses transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_STARTED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_PAUSED state. |
| [OH_AVErrCode OH_AVTranscoder_Resume(OH_AVTranscoder *transcoder)](#oh_avtranscoder_resume) | Resumes transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_PAUSED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_STARTED state again. |
| [OH_AVErrCode OH_AVTranscoder_Cancel(OH_AVTranscoder *transcoder)](#oh_avtranscoder_cancel) | Cancels transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_STARTED or AVTRANSCODER_PAUSED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_CANCELLED state. |
| [OH_AVErrCode OH_AVTranscoder_Release(OH_AVTranscoder *transcoder)](#oh_avtranscoder_release) | Releases an AVTranscoder instance. |
| [OH_AVErrCode OH_AVTranscoder_SetStateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnStateChange callback, void *userData)](#oh_avtranscoder_setstatecallback) | Registers a callback for transcoding state change events. This callback is invoked when the state of the transcoding process changes. An application can subscribe to only one transcoding state change event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called. |
| [OH_AVErrCode OH_AVTranscoder_SetErrorCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnError callback, void *userData)](#oh_avtranscoder_seterrorcallback) | Registers a callback for transcoding error events. This callback is invoked when an error occurs during the transcoding process. If this event is reported, call [OH_AVTranscoder_Release](capi-avtranscoder-h.md#oh_avtranscoder_release) to exit the transcoding. An application can subscribe to only one transcoding error event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called. |
| [OH_AVErrCode OH_AVTranscoder_SetProgressUpdateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnProgressUpdate callback, void *userData)](#oh_avtranscoder_setprogressupdatecallback) | Registers a callback for transcoding progress update events. This callback is invoked when the progress of the transcoding process is updated. An application can subscribe to only one transcoding error event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called. |
| [OH_AVErrCode OH_AVTranscoderConfig_EnableBFrame(OH_AVTranscoder_Config *config, bool enabled)](#oh_avtranscoderconfig_enablebframe) | Enables B-frame encoding for the output video during transcoding. For details about the constraints on B-frame video encoding, see {@link Constraints in B-Frame Video Encoding}. If the current environment does not meet these constraints, B-frames will be skipped, and encoding will proceed as if B-frame video encoding were not enabled. |

## Function description

### OH_AVTranscoderConfig_Create()

```c
OH_AVTranscoder_Config *OH_AVTranscoderConfig_Create()
```

**Description**

Creates an instance of the transcoding configuration parameters.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVTranscoder_Config * | Pointer to the OH_AVTranscoder_Config instance created. If the operation fails, nullptr is returned. |

### OH_AVTranscoderConfig_Release()

```c
OH_AVErrCode OH_AVTranscoderConfig_Release(OH_AVTranscoder_Config* config)
```

**Description**

Releases the resources of the transcoding configuration parameters. After a successful call, the instance specified by **config** is released and set to nullptr.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config* config | Pointer to an OH_AVTranscoder_Config instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The release operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr. |

### OH_AVTranscoderConfig_SetSrcFD()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetSrcFD(OH_AVTranscoder_Config *config, int32_t srcFd, int64_t srcOffset, int64_t length)
```

**Description**

Sets the file descriptor of the source video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance. |
| int32_t srcFd | Source file descriptor. |
| int64_t srcOffset | The offset into the file where the data to be read, in bytes. |
| int64_t length | The length in bytes of the data to be read |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the parameters related to the source video  file are incorrect. |

### OH_AVTranscoderConfig_SetDstFD()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstFD(OH_AVTranscoder_Config *config, int32_t dstFd)
```

**Description**

Sets the file descriptor of the output video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t dstFd | Destination file descriptor |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the output video file descriptor is invalid. |

### OH_AVTranscoderConfig_SetDstVideoType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoType(OH_AVTranscoder_Config *config, const char *mimeType)
```

**Description**

Sets the encoding format of the output video for transcoding. Currently, only AVC and HEVC are supported. If the source video is in HEVC format, the default value is **HEVC**. Otherwise, the default value is **AVC**. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| const char *mimeType | Destination video mime type. See native_avcodec_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of mimeType is not allowed. |

### OH_AVTranscoderConfig_SetDstAudioType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioType(OH_AVTranscoder_Config *config, const char *mimeType)
```

**Description**

Sets the encoding format of the output audio for transcoding. Currently, only AAC is supported. If this parameter is not set, AAC is used by default. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| const char *mimeType | Destination audio mime type. See native_avcodec_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of mimeType is not allowed. |

### OH_AVTranscoderConfig_SetDstFileType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstFileType(OH_AVTranscoder_Config *config, OH_AVOutputFormat mimeType)
```

**Description**

Sets the container format of the output video file for transcoding. Currently, only MP4 is supported. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| OH_AVOutputFormat mimeType | Destination file type. See native_avcodec_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of mimeType is invalid. |

### OH_AVTranscoderConfig_SetDstAudioBitrate()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)
```

**Description**

Sets the bit rate of the output audio for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t bitrate | Destination audio bitrate, in bit/s. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of bitrate is invalid. |

### OH_AVTranscoderConfig_SetDstVideoBitrate()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)
```

**Description**

Sets the bit rate of the output video for transcoding. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t bitrate | Destination video bitrate, in bit/s. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of bitrate is invalid. |

### OH_AVTranscoderConfig_SetDstVideoResolution()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoResolution(OH_AVTranscoder_Config *config, int32_t width, int32_t height)
```

**Description**

Sets the resolution of the output video for transcoding, in px, where **width** is the width of the output video frame and **height** is the height of the output video frame. This function must be called before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t width | Destination for video width, in px. |
| int32_t height | Destination for video height, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr, or the value of width or height is  invalid. |

### OH_AVTranscoder_Create()

```c
OH_AVTranscoder *OH_AVTranscoder_Create(void)
```

**Description**

Creates an AVTranscoder instance.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVTranscoder * | Pointer to the OH_AVTranscoder instance created. If the operation fails, nullptr is returned. |

### OH_AVTranscoder_Prepare()

```c
OH_AVErrCode OH_AVTranscoder_Prepare(OH_AVTranscoder *transcoder, OH_AVTranscoder_Config *config)
```

**Description**

Sets the parameters for video transcoding and prepares for transcoding. This function must be called before [OH_AVTranscoder_Start](capi-avtranscoder-h.md#oh_avtranscoder_start). Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_PREPARED state.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance, see {@link OH_AVTranscoder_Config} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The video transcoding parameters are set successfully, and the AVTranscoder enters the<br>AVTRANSCODER_PREPARED state.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Prepare operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Prepare operation is not allowed in the current state, or the format is not<br>supported.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_Start()

```c
OH_AVErrCode OH_AVTranscoder_Start(OH_AVTranscoder *transcoder)
```

**Description**

Starts transcoding. This function must be called after a successful call to [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare). Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_STARTED state.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: Transcoding starts successfully, and the AVTranscoder enters the AVTRANSCODER_STARTED state.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Start operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Start operation is not allowed in the current state.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_Pause()

```c
OH_AVErrCode OH_AVTranscoder_Pause(OH_AVTranscoder *transcoder)
```

**Description**

Pauses transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_STARTED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_PAUSED state.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: Transcoding is paused successfully, and the AVTranscoder enters the AVTRANSCODER_PAUSED state.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Pause operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Pause operation is not allowed in the current state.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_Resume()

```c
OH_AVErrCode OH_AVTranscoder_Resume(OH_AVTranscoder *transcoder)
```

**Description**

Resumes transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_PAUSED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_STARTED state again.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: Transcoding is resumed successfully, and the AVTranscoder enters the AVTRANSCODER_STARTED<br>state.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Resume operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Resume operation is not allowed in the current state.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_Cancel()

```c
OH_AVErrCode OH_AVTranscoder_Cancel(OH_AVTranscoder *transcoder)
```

**Description**

Cancels transcoding. This function must be called when the AVTranscoder is in the AVTRANSCODER_STARTED or AVTRANSCODER_PAUSED state. Upon a successful call to this function, the AVTranscoder enters the AVTRANSCODER_CANCELLED state.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: Transcoding is canceled successfully, and the AVTranscoder enters the AVTRANSCODER_CANCELLED<br>state.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Cancel operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Cancel operation is not allowed in the current state.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_Release()

```c
OH_AVErrCode OH_AVTranscoder_Release(OH_AVTranscoder *transcoder)
```

**Description**

Releases an AVTranscoder instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | AV_ERR_OK: The AVTranscoder instance is successfully released.  {@link AV_ERR_INVALID_VAL}: The input parameter transcoder is nullptr, or the Release operation fails.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The Release operation is not allowed in the current state.<br>AV_ERR_IO: An I/O access error occurs.<br>{@link AV_ERR_SERVICE_DIED}: The media service is stopped. |

### OH_AVTranscoder_SetStateCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetStateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnStateChange callback, void *userData)
```

**Description**

Registers a callback for transcoding state change events. This callback is invoked when the state of the transcoding process changes. An application can subscribe to only one transcoding state change event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |
| OH_AVTranscoder_OnStateChange callback | State callback function, see {@link OH_AVTranscoder_OnStateChange} |
| void *userData | Pointer to user specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The registration is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder or callback is nullptr. |

### OH_AVTranscoder_SetErrorCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetErrorCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnError callback, void *userData)
```

**Description**

Registers a callback for transcoding error events. This callback is invoked when an error occurs during the transcoding process. If this event is reported, call [OH_AVTranscoder_Release](capi-avtranscoder-h.md#oh_avtranscoder_release) to exit the transcoding. An application can subscribe to only one transcoding error event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |
| OH_AVTranscoder_OnError callback | Error callback function, see {@link OH_AVTranscoder_OnError} |
| void *userData | Pointer to user specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The registration is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder or callback is nullptr. |

### OH_AVTranscoder_SetProgressUpdateCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetProgressUpdateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnProgressUpdate callback, void *userData)
```

**Description**

Registers a callback for transcoding progress update events. This callback is invoked when the progress of the transcoding process is updated. An application can subscribe to only one transcoding error event. When the application initiates multiple subscriptions to this event, the last subscription is applied. The callback must be registered before [OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare) is called.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder *transcoder | Pointer to an OH_AVTranscoder instance |
| OH_AVTranscoder_OnProgressUpdate callback | Uri callback function, see {@link OH_AVTranscoder_OnProgressUpdate} |
| void *userData | Pointer to user specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The registration is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter transcoder or callback is nullptr. |

### OH_AVTranscoderConfig_EnableBFrame()

```c
OH_AVErrCode OH_AVTranscoderConfig_EnableBFrame(OH_AVTranscoder_Config *config, bool enabled)
```

**Description**

Enables B-frame encoding for the output video during transcoding. For details about the constraints on B-frame video encoding, see {@link Constraints in B-Frame Video Encoding}. If the current environment does not meet these constraints, B-frames will be skipped, and encoding will proceed as if B-frame video encoding were not enabled.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVTranscoder_Config *config | Pointer to an OH_AVTranscoder_Config instance |
| bool enabled | Whether enable B Frame. If this function is not called, B Frame is disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The setting is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter config is nullptr. |


