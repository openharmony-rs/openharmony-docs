# native_audiostreambuilder.h

## Overview

Declare audio stream builder related interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)](#oh_audiostreambuilder_create) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)](#oh_audiostreambuilder_destroy) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)](#oh_audiostreambuilder_setsamplingrate) | Set the sampling rate of the stream client. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)](#oh_audiostreambuilder_setchannelcount) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)](#oh_audiostreambuilder_setsampleformat) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)](#oh_audiostreambuilder_setencodingtype) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)](#oh_audiostreambuilder_setlatencymode) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)](#oh_audiostreambuilder_setchannellayout) | Set the channel layout to the stream client |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)](#oh_audiostreambuilder_setrendererinfo) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)](#oh_audiostreambuilder_setcapturerinfo) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setrenderercallback) | (Deprecated in API20) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setrendereroutputdevicechangecallback) | Set the callback when the output device of an audio renderer changed. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)](#oh_audiostreambuilder_setrendererprivacy) | Set the privacy of audio render. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setcapturercallback) | (Deprecated in API20) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)](#oh_audiostreambuilder_generaterenderer) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)](#oh_audiostreambuilder_generatecapturer) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)](#oh_audiostreambuilder_setframesizeincallback) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)](#oh_audiostreambuilder_setwritedatawithmetadatacallback) | Set the callback of writing metadata to the renderer client |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)](#oh_audiostreambuilder_setrendererinterruptmode) | Set the interrupt mode of the stream client |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallback) | Set the callback of writing data to renderer client.<br> This function is similar with [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). Only the last callback set by OH_AudioStreamBuilder_SetRendererCallback or this function will become effective. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallbackadvanced) | Set the callback of writing data to renderer client.<br> This function is similar with [OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback). Only the last callback set by OH_AudioStreamBuilder_SetRendererWriteDataCallback or this function will become effective. Different with OH_AudioStreamBuilder_SetRendererWriteDataCallback, the callback in this function can return audio data of any length. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)](#oh_audiostreambuilder_setvolumemode) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setrendererinterruptcallback) | Sets a callback to handle interrupt events for an AudioRenderer instance. This function is similar to [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). If both OH_AudioStreamBuilder_SetRendererCallback and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setrenderererrorcallback) | Sets a callback to handle error events for an AudioRenderer instance. This function is similar to [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). If both OH_AudioStreamBuilder_SetRendererCallback and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerreaddatacallback) | Sets a callback to handle audio data read events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both {@link<br>OH_AudioStreamBuilder_SetCapturerCallback} and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerdevicechangecallback) | Sets a callback to handle device change events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerinterruptcallback) | Sets a callback to handle interrupt events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setcapturererrorcallback) | Sets a callback to handle error events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)](#oh_audiostreambuilder_setcapturerwillmutewheninterrupted) | Set audio capturer configuration, if app want its recorder only to be muted instead of interrupted. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setrendererfaststatuschangecallback) | Set the callback of fast status change event for audio renderer. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setcapturerfaststatuschangecallback) | Set the callback of fast status change event for audio capturer. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)](#oh_audiostreambuilder_setcapturerloopbackeffectenabled) | Sets if the audio capturer can capture the audio data affected by loopback effect. When the same process enables reverb effect for audio loopback in hardware mode, and the target audio capturer is in [AUDIOSTREAM_LATENCY_MODE_FAST](capi-native-audiostream-base-h.md#oh_audiostream_latencymode) mode, this function will take effect. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)](#oh_audiostreambuilder_setplaybackcapturemode) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)](#oh_audiostreambuilder_setsensitiverecordpermitcallback) | Sets the callback to receive when the sensitive warning message playback is finished for voice downlink capturer stream. This function is only needed when using [AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) to record. This callback must be successfully set, otherwise the capturer can not be created. The sensitive warning message will be automatically added to the voice data sent to the other end of the call right after the audio capturer is created. The application should wait for the callback result before starting the capturer, otherwise an error will be returned by [OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start). Make sure the audio capturer is created after the voice call started, otherwise an error will be returned by [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer). |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)](#oh_audiostreambuilder_setcellularrecordsecurityparams) | Sets phone number and token for voice downlink capturer stream. This function is only needed when using [AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) to record. The phone number and token must be successfully set, otherwise the capturer can not be created. They will be used to check whether the voice downlink capturer matches the cellular call. |

## Function description

### OH_AudioStreamBuilder_Create()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder** builder | The builder reference to the created result. |
| OH_AudioStream_Type type | The stream type to be created. [AUDIOSTREAM_TYPE_RENDERER](capi-native-audiostream-base-h.md#oh_audiostream_type) or [AUDIOSTREAM_TYPE_CAPTURER](capi-native-audiostream-base-h.md#oh_audiostream_type) |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful. |

### OH_AudioStreamBuilder_Destroy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.          [AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) Execution status exception. |

### OH_AudioStreamBuilder_SetSamplingRate()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)
```

**Description**

Set the sampling rate of the stream client.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference created by OH_AudioStreamBuilder_Create(). |
| int32_t rate | The target sampling rate. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of rate invalid. |

### OH_AudioStreamBuilder_SetChannelCount()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| int32_t channelCount | The channel count. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of channelCount invalid. |

### OH_AudioStreamBuilder_SetSampleFormat()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_SampleFormat format | Sample data format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr. |

### OH_AudioStreamBuilder_SetEncodingType()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_EncodingType encodingType | Encoding type for the stream client, {@link #AUDIOSTREAM_ENCODING_PCM} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr. |

### OH_AudioStreamBuilder_SetLatencyMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_LatencyMode latencyMode | Latency mode for the stream client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr. |

### OH_AudioStreamBuilder_SetChannelLayout()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)
```

**Description**

Set the channel layout to the stream client

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioChannelLayout channelLayout | is the layout of the speaker. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr. |

### OH_AudioStreamBuilder_SetRendererInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_Usage usage | Set the stream usage for the renderer client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of usage invalid. |

### OH_AudioStreamBuilder_SetCapturerInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_SourceType sourceType | Set the source type for the capturer client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of sourceType invalid. |

### OH_AudioStreamBuilder_SetRendererCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Deprecated**: 20

**Replaced by**: Set the callback functions separately using OH_AudioStreamBuilder_SetRendererWriteDataCallback, OH_AudioStreamBuilder_SetRendererInterruptCallback, OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback and OH_AudioStreamBuilder_SetRendererErrorCallback.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_Callbacks callbacks | Callbacks to the functions that will process renderer stream. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid. |

### OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)
```

**Description**

Set the callback when the output device of an audio renderer changed.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_OutputDeviceChangeCallback callback | Callback to the function that will process this device change event. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid. |

### OH_AudioStreamBuilder_SetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)
```

**Description**

Set the privacy of audio render.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_PrivacyType privacy | Privacy type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid. |

### OH_AudioStreamBuilder_SetCapturerCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Deprecated**: 20

**Replaced by**: Set the callback functions separately using OH_AudioStreamBuilder_SetCapturerReadDataCallback, OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback, OH_AudioStreamBuilder_SetCapturerInterruptCallback and OH_AudioStreamBuilder_SetCapturerErrorCallback.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioCapturer_Callbacks callbacks | Callbacks to the functions that will process capturer stream. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid. |

### OH_AudioStreamBuilder_GenerateRenderer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer** audioRenderer | Pointer to a viriable to receive the stream client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid;                                                  3.Create OHAudioRenderer failed. |

### OH_AudioStreamBuilder_GenerateCapturer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioCapturer** audioCapturer | Pointer to a variable to receive the stream client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid;                                                  3.Create OHAudioRenderer failed. |

### OH_AudioStreamBuilder_SetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| int32_t frameSize |  The data frame size for each callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr. |

### OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)
```

**Description**

Set the callback of writing metadata to the renderer client

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_WriteDataWithMetadataCallback callback | Callback to the functions that will write audio data with metadata to the renderer. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.StreamType invalid. |

### OH_AudioStreamBuilder_SetRendererInterruptMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)
```

**Description**

Set the interrupt mode of the stream client

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioInterrupt_Mode mode | The audio interrupt mode |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of mode invalid;                                                  3.StreamType invalid. |

### OH_AudioStreamBuilder_SetRendererWriteDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)
```

**Description**

Set the callback of writing data to renderer client.<br> This function is similar with [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). Only the last callback set by OH_AudioStreamBuilder_SetRendererCallback or this function will become effective.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_OnWriteDataCallback callback | Callback to functions that will write audio data to renderer client. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) Success.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) Parameter is invalid, e.g. builder is nullptr, e.t.c. |

### OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)
```

**Description**

Set the callback of writing data to renderer client.<br> This function is similar with [OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback). Only the last callback set by OH_AudioStreamBuilder_SetRendererWriteDataCallback or this function will become effective. Different with OH_AudioStreamBuilder_SetRendererWriteDataCallback, the callback in this function can return audio data of any length.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_OnWriteDataCallbackAdvanced callback | Callback to functions that will write audio data to renderer client. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) Success.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) Parameter is invalid, e.g. builder is nullptr, e.t.c. |

### OH_AudioStreamBuilder_SetVolumeMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| OH_AudioStream_VolumeMode volumeMode | Set the volume mode for the renderer client. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.          [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):                                                  1.The param of builder is nullptr;                                                  2.The param of volumeMode invalid. |

### OH_AudioStreamBuilder_SetRendererInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)
```

**Description**

Sets a callback to handle interrupt events for an AudioRenderer instance. This function is similar to [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). If both OH_AudioStreamBuilder_SetRendererCallback and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioRenderer_OnInterruptCallback callback | Callback used to handle the interrupt events. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetRendererErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)
```

**Description**

Sets a callback to handle error events for an AudioRenderer instance. This function is similar to [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback). If both OH_AudioStreamBuilder_SetRendererCallback and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioRenderer_OnErrorCallback callback | Callback used to handle the error events. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetCapturerReadDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)
```

**Description**

Sets a callback to handle audio data read events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both {@link<br>OH_AudioStreamBuilder_SetCapturerCallback} and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioCapturer_OnReadDataCallback callback | Callback used to handle incoming audio data. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)
```

**Description**

Sets a callback to handle device change events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioCapturer_OnDeviceChangeCallback callback | Callback used to handle the device change events. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetCapturerInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)
```

**Description**

Sets a callback to handle interrupt events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioCapturer_OnInterruptCallback callback | Callback used to handle the interrupt events. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetCapturerErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)
```

**Description**

Sets a callback to handle error events for an AudioCapturer instance. This function is similar to [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback). If both OH_AudioStreamBuilder_SetCapturerCallback and this function are called, the most recently set callback takes effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder instance, which is generated by OH_AudioStreamBuilder_Create(). |
| OH_AudioCapturer_OnErrorCallback callback | Callback used to handle the error events. |
| void* userData | Pointer to user-defined data, which will be passed back to the application in the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Result code.      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if the operation is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) is returned if a parameter is invalid, for example, if builder  is nullptr. |

### OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)
```

**Description**

Set audio capturer configuration, if app want its recorder only to be muted instead of interrupted.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | reference provided by OH_AudioStreamBuilder_Create() |
| bool muteWhenInterrupted | use {@code true} if application want to be muted instead of interrupted. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | function result code:      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) if the execution is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) the param of builder is nullptr. |

### OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)
```

**Description**

Set the callback of fast status change event for audio renderer.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| OH_AudioRenderer_OnFastStatusChange callback | Callback function that will recevie the fast status change event. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | @return      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) if the execution is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) the param of builder or callback is nullptr. |

### OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)
```

**Description**

Set the callback of fast status change event for audio capturer.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| OH_AudioCapturer_OnFastStatusChange callback | Callback function that will recevie the fast status change event. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | @return      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) if the execution is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) the param of builder or callback is nullptr. |

### OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)
```

**Description**

Sets if the audio capturer can capture the audio data affected by loopback effect. When the same process enables reverb effect for audio loopback in hardware mode, and the target audio capturer is in [AUDIOSTREAM_LATENCY_MODE_FAST](capi-native-audiostream-base-h.md#oh_audiostream_latencymode) mode, this function will take effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | reference provided by OH_AudioStreamBuilder_Create(). |
| bool enabled | Whether application want to get audio data affected by loopback effect. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | function result code:      [AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) if the execution is successful.      [AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) the param of builder is nullptr. |

### OH_AudioStreamBuilder_SetPlaybackCaptureMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)
```

**Description**

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | Reference provided by OH_AudioStreamBuilder_Create(). |
| uint32_t mode | The playback capture mode to set. This can be a combination of the available [OH_AudioStream_PlaybackCaptureMode](capi-native-audiostream-base-h.md#oh_audiostream_playbackcapturemode). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>      <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li>      <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1.The param of builder is nullptr;                         2.The param of mode is invalid.</li>      </ul> |

### OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)
```

**Description**

Sets the callback to receive when the sensitive warning message playback is finished for voice downlink capturer stream. This function is only needed when using [AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) to record. This callback must be successfully set, otherwise the capturer can not be created. The sensitive warning message will be automatically added to the voice data sent to the other end of the call right after the audio capturer is created. The application should wait for the callback result before starting the capturer, otherwise an error will be returned by [OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start). Make sure the audio capturer is created after the voice call started, otherwise an error will be returned by [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer).

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | The pointer to the [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md) object created by [OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create). |
| OH_AudioCapturer_SensitiveRecordPermitCallback callback | Callback to the functions that will process capturer stream, NULL value is not allowed. |
| void* userData | The pointer to user data, which will be passed back to the application in the callback. If application does not need to pass any data, NULL value is also allowed. But if data is not NULL, the caller should check whether the data is still valid when receive the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>          <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li>          <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder or callback is nullptr.</li>          </ul> |

### OH_AudioStreamBuilder_SetCellularRecordSecurityParams()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)
```

**Description**

Sets phone number and token for voice downlink capturer stream. This function is only needed when using [AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) to record. The phone number and token must be successfully set, otherwise the capturer can not be created. They will be used to check whether the voice downlink capturer matches the cellular call.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioStreamBuilder* builder | The pointer to the [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md) object created by [OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create). |
| const char* cellularRecordPhoneNum | The phone number for the target cellular call, which is used in makeCallWithToken(), NULL value is not allowed. |
| const char* cellularRecordToken | The token for the target cellular call, which can be obtained by makeCallWithToken() function from call management, NULL value is not allowed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>          <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li>          <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder,               cellularRecordPhoneNum or cellularRecordToken is nullptr.</li>          </ul> |


