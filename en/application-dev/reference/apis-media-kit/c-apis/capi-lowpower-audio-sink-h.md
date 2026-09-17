# lowpower_audio_sink.h

## Overview

The file declares the native APIs provided by the OH_LowPowerAudioSink instance. You can use the APIs to implement low-power audio playback.

**Library**: liblowpower_avsink.so

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Related module**: [LowPowerAudioSink](capi-lowpoweraudiosink.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_LowPowerAudioSink* OH_LowPowerAudioSink_CreateByMime(const char* mime)](#oh_lowpoweraudiosink_createbymime) | Creates an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_Configure(OH_LowPowerAudioSink* sink, const OH_AVFormat* format)](#oh_lowpoweraudiosink_configure) | Configures an OH_LowPowerAudioSink instance. This function must be called before [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare). |
| [OH_AVErrCode OH_LowPowerAudioSink_SetParameter(OH_LowPowerAudioSink* sink, const OH_AVFormat* format)](#oh_lowpoweraudiosink_setparameter) | Sets parameters for an OH_LowPowerAudioSink instance. The parameters can be dynamically set after [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare). |
| [OH_AVErrCode OH_LowPowerAudioSink_GetParameter(OH_LowPowerAudioSink* sink, OH_AVFormat* format)](#oh_lowpoweraudiosink_getparameter) | Obtains the parameters of an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_Prepare(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_prepare) | Prepares an OH_LowPowerAudioSink instance for decoding and rendering. This function must be called after [OH_LowPowerAudioSink_Configure](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_configure). |
| [OH_AVErrCode OH_LowPowerAudioSink_Start(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_start) | Starts an OH_LowPowerAudioSink instance. This function must be called after a successful call to [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare). |
| [OH_AVErrCode OH_LowPowerAudioSink_Pause(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_pause) | Pauses an OH_LowPowerAudioSink instance. This function must be called after [OH_LowPowerAudioSink_Start](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_start) or [OH_LowPowerAudioSink_Resume](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_resume). |
| [OH_AVErrCode OH_LowPowerAudioSink_Resume(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_resume) | Resumes an OH_LowPowerAudioSink instance. This function must be called after [OH_LowPowerAudioSink_Pause](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_pause). |
| [OH_AVErrCode OH_LowPowerAudioSink_Flush(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_flush) | Clears all input and output data from the decoders and render buffers of an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_Stop(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_stop) | Stops an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_Reset(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_reset) | Resets an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_Destroy(OH_LowPowerAudioSink* sink)](#oh_lowpoweraudiosink_destroy) | Clears internal resources of an OH_LowPowerAudioSink instance and destroys the instance. You only need to call the function once. |
| [OH_AVErrCode OH_LowPowerAudioSink_SetVolume(OH_LowPowerAudioSink* sink, const float volume)](#oh_lowpoweraudiosink_setvolume) | Sets the rendering volume for an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_SetPlaybackSpeed(OH_LowPowerAudioSink* sink, const float speed)](#oh_lowpoweraudiosink_setplaybackspeed) | Sets the audio rendering speed for an OH_LowPowerAudioSink instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_ReturnSamples(OH_LowPowerAudioSink* sink, OH_AVSamplesBuffer* samples)](#oh_lowpoweraudiosink_returnsamples) | Provides a buffer to an OH_LowPowerAudioSink instance for procesing. |
| [OH_AVErrCode OH_LowPowerAudioSink_RegisterCallback(OH_LowPowerAudioSink* sink, OH_LowPowerAudioSinkCallback* callback)](#oh_lowpoweraudiosink_registercallback) | Registers a callback for an OH_LowPowerAudioSink instance. |
| [OH_LowPowerAudioSinkCallback* OH_LowPowerAudioSinkCallback_Create(void)](#oh_lowpoweraudiosinkcallback_create) | Creates an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_Destroy(OH_LowPowerAudioSinkCallback* callback)](#oh_lowpoweraudiosinkcallback_destroy) | Destroys an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetPositionUpdateListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnPositionUpdated onPositionUpdated, void* userData)](#oh_lowpoweraudiosinkcallback_setpositionupdatelistener) | Sets a progress update listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetDataNeededListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnDataNeeded onDataNeeded, void* userData)](#oh_lowpoweraudiosinkcallback_setdataneededlistener) | Sets a data needed listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetErrorListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnError onError, void* userData)](#oh_lowpoweraudiosinkcallback_seterrorlistener) | Sets an error listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetInterruptListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnInterrupted onInterrupted, void* userData)](#oh_lowpoweraudiosinkcallback_setinterruptlistener) | Sets an audio focus interruption listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetDeviceChangeListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnDeviceChanged onDeviceChanged, void* userData)](#oh_lowpoweraudiosinkcallback_setdevicechangelistener) | Sets an audio device change listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSinkCallback_SetEosListener(OH_LowPowerAudioSinkCallback *callback, OH_LowPowerAudioSink_OnEos onEos, void* userData)](#oh_lowpoweraudiosinkcallback_seteoslistener) | Sets an end-of-stream listener for an OH_LowPowerAudioSinkCallback instance. |
| [OH_AVErrCode OH_LowPowerAudioSink_SetLoudnessGain(OH_LowPowerAudioSink* sink, float loudnessGain)](#oh_lowpoweraudiosink_setloudnessgain) | Sets the loudness gain for an OH_LowPowerAudioSink instance. |

## Function description

### OH_LowPowerAudioSink_CreateByMime()

```c
OH_LowPowerAudioSink* OH_LowPowerAudioSink_CreateByMime(const char* mime)
```

**Description**

Creates an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* mime | mime type description string, refer to {@link AVCODEC_MIME_TYPE} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_LowPowerAudioSink* | Pointer to the OH_LowPowerAudioSink instance created. If the operation fails, nullptr is returned. |

### OH_LowPowerAudioSink_Configure()

```c
OH_AVErrCode OH_LowPowerAudioSink_Configure(OH_LowPowerAudioSink* sink, const OH_AVFormat* format)
```

**Description**

Configures an OH_LowPowerAudioSink instance. This function must be called before [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| const OH_AVFormat* format | A pointer to an OH_AVFormat to give the description of the audio track to be decoded |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_UNSUPPORT}: The format is not supported.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_SetParameter()

```c
OH_AVErrCode OH_LowPowerAudioSink_SetParameter(OH_LowPowerAudioSink* sink, const OH_AVFormat* format)
```

**Description**

Sets parameters for an OH_LowPowerAudioSink instance. The parameters can be dynamically set after [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| const OH_AVFormat* format | pointer to an OH_AVFormat instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_UNSUPPORT}: The format is not supported.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_GetParameter()

```c
OH_AVErrCode OH_LowPowerAudioSink_GetParameter(OH_LowPowerAudioSink* sink, OH_AVFormat* format)
```

**Description**

Obtains the parameters of an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| OH_AVFormat* format | pointer to an OH_AVFormat instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Prepare()

```c
OH_AVErrCode OH_LowPowerAudioSink_Prepare(OH_LowPowerAudioSink* sink)
```

**Description**

Prepares an OH_LowPowerAudioSink instance for decoding and rendering. This function must be called after [OH_LowPowerAudioSink_Configure](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_configure).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_UNSUPPORT}: The format is not supported.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Start()

```c
OH_AVErrCode OH_LowPowerAudioSink_Start(OH_LowPowerAudioSink* sink)
```

**Description**

Starts an OH_LowPowerAudioSink instance. This function must be called after a successful call to [OH_LowPowerAudioSink_Prepare](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_prepare).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_UNSUPPORT}: The format is not supported.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Pause()

```c
OH_AVErrCode OH_LowPowerAudioSink_Pause(OH_LowPowerAudioSink* sink)
```

**Description**

Pauses an OH_LowPowerAudioSink instance. This function must be called after [OH_LowPowerAudioSink_Start](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_start) or [OH_LowPowerAudioSink_Resume](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_resume).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Resume()

```c
OH_AVErrCode OH_LowPowerAudioSink_Resume(OH_LowPowerAudioSink* sink)
```

**Description**

Resumes an OH_LowPowerAudioSink instance. This function must be called after [OH_LowPowerAudioSink_Pause](capi-lowpower-audio-sink-h.md#oh_lowpoweraudiosink_pause).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Flush()

```c
OH_AVErrCode OH_LowPowerAudioSink_Flush(OH_LowPowerAudioSink* sink)
```

**Description**

Clears all input and output data from the decoders and render buffers of an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Stop()

```c
OH_AVErrCode OH_LowPowerAudioSink_Stop(OH_LowPowerAudioSink* sink)
```

**Description**

Stops an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Reset()

```c
OH_AVErrCode OH_LowPowerAudioSink_Reset(OH_LowPowerAudioSink* sink)
```

**Description**

Resets an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_Destroy()

```c
OH_AVErrCode OH_LowPowerAudioSink_Destroy(OH_LowPowerAudioSink* sink)
```

**Description**

Clears internal resources of an OH_LowPowerAudioSink instance and destroys the instance. You only need to call the function once.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_SetVolume()

```c
OH_AVErrCode OH_LowPowerAudioSink_SetVolume(OH_LowPowerAudioSink* sink, const float volume)
```

**Description**

Sets the rendering volume for an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| const float volume | Volume to set which changes from 0.0 to 1.0 |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_SetPlaybackSpeed()

```c
OH_AVErrCode OH_LowPowerAudioSink_SetPlaybackSpeed(OH_LowPowerAudioSink* sink, const float speed)
```

**Description**

Sets the audio rendering speed for an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| const float speed | The playback speed value needs to be specified, the valid value is 0.25-4.0 |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_ReturnSamples()

```c
OH_AVErrCode OH_LowPowerAudioSink_ReturnSamples(OH_LowPowerAudioSink* sink, OH_AVSamplesBuffer* samples)
```

**Description**

Provides a buffer to an OH_LowPowerAudioSink instance for procesing.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| OH_AVSamplesBuffer* samples | Pointer to an OH_AVSamplesBuffer instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_RegisterCallback()

```c
OH_AVErrCode OH_LowPowerAudioSink_RegisterCallback(OH_LowPowerAudioSink* sink, OH_LowPowerAudioSinkCallback* callback)
```

**Description**

Registers a callback for an OH_LowPowerAudioSink instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_Create()

```c
OH_LowPowerAudioSinkCallback* OH_LowPowerAudioSinkCallback_Create(void)
```

**Description**

Creates an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* | Pointer to the OH_LowPowerAudioSinkCallback instance created. If the memory is insufficient, nullptr is  returned. |

### OH_LowPowerAudioSinkCallback_Destroy()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_Destroy(OH_LowPowerAudioSinkCallback* callback)
```

**Description**

Destroys an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid. |

### OH_LowPowerAudioSinkCallback_SetPositionUpdateListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetPositionUpdateListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnPositionUpdated onPositionUpdated, void* userData)
```

**Description**

Sets a progress update listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |
| OH_LowPowerAudioSink_OnPositionUpdated onPositionUpdated | OH_LowPowerAudioSink_OnPositionUpdated function, refer to {@link OH_LowPowerAudioSink_OnPositionUpdated} |
| void* userData | Pointer to the data on which the caller depends when executing the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_SetDataNeededListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetDataNeededListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnDataNeeded onDataNeeded, void* userData)
```

**Description**

Sets a data needed listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |
| OH_LowPowerAudioSink_OnDataNeeded onDataNeeded | OH_LowPowerAudioSink_OnDataNeeded function, refer to {@link OH_LowPowerAudioSink_OnDataNeeded} |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_SetErrorListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetErrorListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnError onError, void* userData)
```

**Description**

Sets an error listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |
| OH_LowPowerAudioSink_OnError onError | OH_LowPowerAudioSink_OnError function, refer to {@link OH_LowPowerAudioSink_OnError} |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_SetInterruptListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetInterruptListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnInterrupted onInterrupted, void* userData)
```

**Description**

Sets an audio focus interruption listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSinkCallback instance |
| OH_LowPowerAudioSink_OnInterrupted onInterrupted | OH_LowPowerAudioSink_OnInterrupted function, refer to {@link OH_LowPowerAudioSink_OnInterrupted} |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_SetDeviceChangeListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetDeviceChangeListener(OH_LowPowerAudioSinkCallback* callback, OH_LowPowerAudioSink_OnDeviceChanged onDeviceChanged, void* userData)
```

**Description**

Sets an audio device change listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback* callback | Pointer to an OH_LowPowerAudioSink Callback instance |
| OH_LowPowerAudioSink_OnDeviceChanged onDeviceChanged | OH_LowPowerAudioSink_OnDeviceChanged function, refer to {@link OH_LowPowerAudioSink_OnDeviceChanged} |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSinkCallback_SetEosListener()

```c
OH_AVErrCode OH_LowPowerAudioSinkCallback_SetEosListener(OH_LowPowerAudioSinkCallback *callback, OH_LowPowerAudioSink_OnEos onEos, void* userData)
```

**Description**

Sets an end-of-stream listener for an OH_LowPowerAudioSinkCallback instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSinkCallback *callback | Pointer to an OH_LowPowerAudioSinkCallback instance |
| OH_LowPowerAudioSink_OnEos onEos | OH_LowPowerAudioSink_OnEos function, refer to {@link OH_LowPowerAudioSink_OnEos} |
| void* userData | User specific data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not supported. |

### OH_LowPowerAudioSink_SetLoudnessGain()

```c
OH_AVErrCode OH_LowPowerAudioSink_SetLoudnessGain(OH_LowPowerAudioSink* sink, float loudnessGain)
```

**Description**

Sets the loudness gain for an OH_LowPowerAudioSink instance.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_LowPowerAudioSink* sink | Pointer to an OH_LowPowerAudioSink instance. |
| float loudnessGain | Loudness gain to set which changes from -90.0 to 24.0, expressing in dB. The default loudness gain is 0.0dB. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: An input parameter is nullptr or invalid.<br>{@link AV_ERR_SERVICE_DIED}: The media server is destroyed. |


