# lowpower_video_sink.h

## Overview

The file declares the native APIs provided by the LowPowerVideoSink. You can use the APIs to implement low- power video playback.

**Library**: liblowpower_avsink.so

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Related module**: [LowPowerVideoSink](capi-lowpowervideosink.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_LowPowerVideoSink* OH_LowPowerVideoSink_CreateByMime(const char* mime)](#oh_lowpowervideosink_createbymime) | Creates an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_Configure(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)](#oh_lowpowervideosink_configure) | Configures an OH_LowPowerVideoSink instance. This function must be called before [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare). |
| [OH_AVErrCode OH_LowPowerVideoSink_SetParameter(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)](#oh_lowpowervideosink_setparameter) | Sets parameters for an OH_LowPowerVideoSink instance. The parameters can be dynamically set after [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare). |
| [OH_AVErrCode OH_LowPowerVideoSink_GetParameter(OH_LowPowerVideoSink* sink, OH_AVFormat* format)](#oh_lowpowervideosink_getparameter) | Obtains the parameters of an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_SetVideoSurface(OH_LowPowerVideoSink* sink, const OHNativeWindow* surface)](#oh_lowpowervideosink_setvideosurface) | Sets the rendering window for an OH_LowPowerVideoSink instance. This function must be called before [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare). |
| [OH_AVErrCode OH_LowPowerVideoSink_Prepare(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_prepare) | Prepares an OH_LowPowerVideoSink instance for decoding and rendering. This function must be called after [OH_LowPowerVideoSink_SetSyncAudioSink](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_setsyncaudiosink). |
| [OH_AVErrCode OH_LowPowerVideoSink_StartDecoder(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_startdecoder) | Starts an OH_LowPowerVideoSink instance for decoding. This function must be called after [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare) or if no video is playing, after [OH_LowPowerVideoSink_SetTargetStartFrame](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_settargetstartframe). |
| [OH_AVErrCode OH_LowPowerVideoSink_RenderFirstFrame(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_renderfirstframe) | Renders the first frame decoded by an OH_LowPowerVideoSink instance. This function must be called after [OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder). |
| [OH_AVErrCode OH_LowPowerVideoSink_StartRenderer(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_startrenderer) | Starts an OH_LowPowerVideoSink instance for rendering. This function must be called after [OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder). |
| [OH_AVErrCode OH_LowPowerVideoSink_Pause(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_pause) | Pauses an OH_LowPowerVideoSink instance. This function must be called after [OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer) or [OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume). |
| [OH_AVErrCode OH_LowPowerVideoSink_Resume(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_resume) | Resumes an OH_LowPowerVideoSink instance. This function must be called after[OH_LowPowerVideoSink_Pause](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_pause). |
| [OH_AVErrCode OH_LowPowerVideoSink_Flush(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_flush) | Clears all input and output data from the decoders and render buffers of an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_Stop(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_stop) | Stops an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_Reset(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_reset) | Resets an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_Destroy(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_destroy) | Clears internal resources of an OH_LowPowerVideoSink instance and destroys the instance. You only need to call the function once. |
| [OH_AVErrCode OH_LowPowerVideoSink_SetSyncAudioSink(OH_LowPowerVideoSink* videoSink, OH_LowPowerAudioSink* audioSink)](#oh_lowpowervideosink_setsyncaudiosink) | Sets an OH_LowPowerAudioSink instance for audio-video synchronization in an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_SetTargetStartFrame(OH_LowPowerVideoSink* sink, const int64_t framePts, OH_LowPowerVideoSink_OnTargetArrived onTargetArrived, const int64_t timeoutMs, void* userData)](#oh_lowpowervideosink_settargetstartframe) | Sets the target rendering frame for an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_SetPlaybackSpeed(OH_LowPowerVideoSink* sink, const float speed)](#oh_lowpowervideosink_setplaybackspeed) | Sets the playback speed for an OH_LowPowerVideoSink instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_ReturnSamples(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* samples)](#oh_lowpowervideosink_returnsamples) | Provides a buffer to an OH_LowPowerVideoSink instance for procesing. |
| [OH_AVErrCode OH_LowPowerVideoSink_RegisterCallback(OH_LowPowerVideoSink* sink, OH_LowPowerVideoSinkCallback* callback)](#oh_lowpowervideosink_registercallback) | Registers a callback for an OH_LowPowerVideoSink instance. |
| [OH_LowPowerVideoSinkCallback* OH_LowPowerVideoSinkCallback_Create(void)](#oh_lowpowervideosinkcallback_create) | Creates an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_Destroy(OH_LowPowerVideoSinkCallback* callback)](#oh_lowpowervideosinkcallback_destroy) | Destroys an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetDataNeededListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnDataNeeded onDataNeeded, void* userData)](#oh_lowpowervideosinkcallback_setdataneededlistener) | Sets a data needed listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetErrorListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnError onError, void* userData)](#oh_lowpowervideosinkcallback_seterrorlistener) | Sets an error listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetRenderStartListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnRenderStarted onRenderStarted, void* userData)](#oh_lowpowervideosinkcallback_setrenderstartlistener) | Sets a render start listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetStreamChangedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnStreamChanged onStreamChanged, void* userData)](#oh_lowpowervideosinkcallback_setstreamchangedlistener) | Sets a stream change listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded, void* userData)](#oh_lowpowervideosinkcallback_setfirstframedecodedlistener) | Sets a first-frame ready listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetEosListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnEos onEos, void* userData)](#oh_lowpowervideosinkcallback_seteoslistener) | Sets an end-of-stream listener for an OH_LowPowerVideoSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerVideoSink_GetLatestPts(OH_LowPowerVideoSink *sink, int64_t *pts)](#oh_lowpowervideosink_getlatestpts) | Obtains the Presentation Timestamp (PTS) of the video that is playing. |

## Function description

### OH_LowPowerVideoSink_CreateByMime()

```c
OH_LowPowerVideoSink* OH_LowPowerVideoSink_CreateByMime(const char* mime)
```

**Description**

Creates an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* mime | mime type description string, refer to {@link AVCODEC_MIME_TYPE} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_LowPowerVideoSink* | Pointer to the OH_LowPowerVideoSink instance created. If the operation fails, nullptr is returned. |

### OH_LowPowerVideoSink_Configure()

```c
OH_AVErrCode OH_LowPowerVideoSink_Configure(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)
```

**Description**

Configures an OH_LowPowerVideoSink instance. This function must be called before [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OH_AVFormat* format | A pointer to an OH_AVFormat to give the description of the video track to be decoded, key of format refer to lowpower_avsink_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): The format is not supported.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_SetParameter()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetParameter(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)
```

**Description**

Sets parameters for an OH_LowPowerVideoSink instance. The parameters can be dynamically set after [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OH_AVFormat* format | pointer to an OH_AVFormat instance, key of format refer to lowpower_avsink_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): The format is not supported.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_GetParameter()

```c
OH_AVErrCode OH_LowPowerVideoSink_GetParameter(OH_LowPowerVideoSink* sink, OH_AVFormat* format)
```

**Description**

Obtains the parameters of an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| OH_AVFormat* format | pointer to an OH_AVFormat instance, key of format refer to lowpower_avsink_base.h |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_SetVideoSurface()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetVideoSurface(OH_LowPowerVideoSink* sink, const OHNativeWindow* surface)
```

**Description**

Sets the rendering window for an OH_LowPowerVideoSink instance. This function must be called before [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OHNativeWindow* surface | A pointer to a OHNativeWindow instance, see {@link OHNativeWindow} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Prepare()

```c
OH_AVErrCode OH_LowPowerVideoSink_Prepare(OH_LowPowerVideoSink* sink)
```

**Description**

Prepares an OH_LowPowerVideoSink instance for decoding and rendering. This function must be called after [OH_LowPowerVideoSink_SetSyncAudioSink](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_setsyncaudiosink).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): The format is not supported.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_StartDecoder()

```c
OH_AVErrCode OH_LowPowerVideoSink_StartDecoder(OH_LowPowerVideoSink* sink)
```

**Description**

Starts an OH_LowPowerVideoSink instance for decoding. This function must be called after [OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare) or if no video is playing, after [OH_LowPowerVideoSink_SetTargetStartFrame](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_settargetstartframe).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): The format is not supported.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_RenderFirstFrame()

```c
OH_AVErrCode OH_LowPowerVideoSink_RenderFirstFrame(OH_LowPowerVideoSink* sink)
```

**Description**

Renders the first frame decoded by an OH_LowPowerVideoSink instance. This function must be called after [OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_StartRenderer()

```c
OH_AVErrCode OH_LowPowerVideoSink_StartRenderer(OH_LowPowerVideoSink* sink)
```

**Description**

Starts an OH_LowPowerVideoSink instance for rendering. This function must be called after [OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_UNSUPPORT](capi-native-averrors-h.md#oh_averrcode): The format is not supported.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Pause()

```c
OH_AVErrCode OH_LowPowerVideoSink_Pause(OH_LowPowerVideoSink* sink)
```

**Description**

Pauses an OH_LowPowerVideoSink instance. This function must be called after [OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer) or [OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Resume()

```c
OH_AVErrCode OH_LowPowerVideoSink_Resume(OH_LowPowerVideoSink* sink)
```

**Description**

Resumes an OH_LowPowerVideoSink instance. This function must be called after[OH_LowPowerVideoSink_Pause](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_pause).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSinkinstance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Flush()

```c
OH_AVErrCode OH_LowPowerVideoSink_Flush(OH_LowPowerVideoSink* sink)
```

**Description**

Clears all input and output data from the decoders and render buffers of an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Stop()

```c
OH_AVErrCode OH_LowPowerVideoSink_Stop(OH_LowPowerVideoSink* sink)
```

**Description**

Stops an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Reset()

```c
OH_AVErrCode OH_LowPowerVideoSink_Reset(OH_LowPowerVideoSink* sink)
```

**Description**

Resets an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_Destroy()

```c
OH_AVErrCode OH_LowPowerVideoSink_Destroy(OH_LowPowerVideoSink* sink)
```

**Description**

Clears internal resources of an OH_LowPowerVideoSink instance and destroys the instance. You only need to call the function once.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_SetSyncAudioSink()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetSyncAudioSink(OH_LowPowerVideoSink* videoSink, OH_LowPowerAudioSink* audioSink)
```

**Description**

Sets an OH_LowPowerAudioSink instance for audio-video synchronization in an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* videoSink | Pointer to an OH_LowPowerVideoSink instance |
| OH_LowPowerAudioSink* audioSink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_SetTargetStartFrame()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetTargetStartFrame(OH_LowPowerVideoSink* sink, const int64_t framePts, OH_LowPowerVideoSink_OnTargetArrived onTargetArrived, const int64_t timeoutMs, void* userData)
```

**Description**

Sets the target rendering frame for an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const int64_t framePts | target video frame pts, in microseconds |
| OH_LowPowerVideoSink_OnTargetArrived onTargetArrived | OH_LowPowerVideoSink_OnTargetArrived func, will be called once, refer to [OH_LowPowerVideoSink_OnTargetArrived](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ontargetarrived) |
| const int64_t timeoutMs | if wait first frame over timeoutMs, onTargetArrived will be called directly, in milliseconds. |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_SetPlaybackSpeed()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetPlaybackSpeed(OH_LowPowerVideoSink* sink, const float speed)
```

**Description**

Sets the playback speed for an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const float speed | Indicates the value of the playback rate. The current version is valid in the range of 0.25-4.0 |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_ReturnSamples()

```c
OH_AVErrCode OH_LowPowerVideoSink_ReturnSamples(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* samples)
```

**Description**

Provides a buffer to an OH_LowPowerVideoSink instance for procesing.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| OH_AVSamplesBuffer* samples | Pointer to an OH_AVSamplesBuffer instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_RegisterCallback()

```c
OH_AVErrCode OH_LowPowerVideoSink_RegisterCallback(OH_LowPowerVideoSink* sink, OH_LowPowerVideoSinkCallback* callback)
```

**Description**

Registers a callback for an OH_LowPowerVideoSink instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_Create()

```c
OH_LowPowerVideoSinkCallback* OH_LowPowerVideoSinkCallback_Create(void)
```

**Description**

Creates an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* | Pointer to the OH_LowPowerVideoSinkCallback instance created. If the memory is insufficient, nullptr is  returned. |

### OH_LowPowerVideoSinkCallback_Destroy()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_Destroy(OH_LowPowerVideoSinkCallback* callback)
```

**Description**

Destroys an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid. |

### OH_LowPowerVideoSinkCallback_SetDataNeededListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetDataNeededListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnDataNeeded onDataNeeded, void* userData)
```

**Description**

Sets a data needed listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnDataNeeded onDataNeeded | OH_LowPowerVideoSink_OnDataNeeded function, refer to [OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_SetErrorListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetErrorListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnError onError, void* userData)
```

**Description**

Sets an error listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnError onError | OH_LowPowerVideoSink_OnError function, refer to [OH_LowPowerVideoSink_OnError](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onerror) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_SetRenderStartListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetRenderStartListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnRenderStarted onRenderStarted, void* userData)
```

**Description**

Sets a render start listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnRenderStarted onRenderStarted | OH_LowPowerVideoSink_OnRenderStarted function, refer to [OH_LowPowerVideoSink_OnRenderStarted](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onrenderstarted) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_SetStreamChangedListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetStreamChangedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnStreamChanged onStreamChanged, void* userData)
```

**Description**

Sets a stream change listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnStreamChanged onStreamChanged | OH_LowPowerVideoSink_OnStreamChanged function, refer to [OH_LowPowerVideoSink_OnStreamChanged](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onstreamchanged) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded, void* userData)
```

**Description**

Sets a first-frame ready listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded | OH_LowPowerVideoSink_OnFirstFrameDecoded function, refer to [OH_LowPowerVideoSink_OnFirstFrameDecoded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onfirstframedecoded) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSinkCallback_SetEosListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetEosListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnEos onEos, void* userData)
```

**Description**

Sets an end-of-stream listener for an OH_LowPowerVideoSinkCallback instance.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnEos onEos | OH_LowPowerVideoSink_OnEos function, refer to [OH_LowPowerVideoSink_OnEos](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_oneos) |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |

### OH_LowPowerVideoSink_GetLatestPts()

```c
OH_AVErrCode OH_LowPowerVideoSink_GetLatestPts(OH_LowPowerVideoSink *sink, int64_t *pts)
```

**Description**

Obtains the Presentation Timestamp (PTS) of the video that is playing.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerVideoSink *sink | Pointer to an OH_LowPowerVideoSink instance. |
| int64_t *pts | Pointer to store the latest PTS value (in microseconds). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): An input parameter is nullptr or invalid.  [AV_ERR_SERVICE_DIED](capi-native-averrors-h.md#oh_averrcode): The media server is destroyed.  [AV_ERR_OPERATE_NOT_PERMIT](capi-native-averrors-h.md#oh_averrcode): The operation is not supported. |


