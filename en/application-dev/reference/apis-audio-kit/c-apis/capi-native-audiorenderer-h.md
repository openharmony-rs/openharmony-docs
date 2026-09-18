# native_audiorenderer.h

## Overview

Declare audio stream related interfaces for output type.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)](#oh_audiorenderer_release) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)](#oh_audiorenderer_start) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)](#oh_audiorenderer_pause) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)](#oh_audiorenderer_stop) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)](#oh_audiorenderer_flush) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)](#oh_audiorenderer_getcurrentstate) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)](#oh_audiorenderer_getsamplingrate) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)](#oh_audiorenderer_getstreamid) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)](#oh_audiorenderer_getchannelcount) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)](#oh_audiorenderer_getsampleformat) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)](#oh_audiorenderer_getlatencymode) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)](#oh_audiorenderer_getrendererinfo) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)](#oh_audiorenderer_getencodingtype) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)](#oh_audiorenderer_getframeswritten) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_gettimestamp) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)](#oh_audiorenderer_getframesizeincallback) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)](#oh_audiorenderer_getspeed) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)](#oh_audiorenderer_setspeed) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)](#oh_audiorenderer_setvolume) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)](#oh_audiorenderer_setvolumewithramp) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)](#oh_audiorenderer_getvolume) | - |  |
| [OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)](#oh_audiorenderer_setmarkposition) | - | Set mark position on current renderer. Calling this function will overwrite the mark postion which has already set. |
| [OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)](#oh_audiorenderer_cancelmark) | - | Cancel mark which has set by [OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition). |
| [OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)](#oh_audiorenderer_getunderflowcount) | - | Gets the underflow count on this stream. |
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)](#oh_audiorenderer_getchannellayout) | - | Query the channel layout of the renderer client. |
| [OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)](#oh_audiorenderer_geteffectmode) | - | Query current audio effect mode. |
| [OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)](#oh_audiorenderer_seteffectmode) | - | Set current audio effect mode. |
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)](#oh_audiorenderer_getrendererprivacy) | - | Get the privacy of this stream. |
| [OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)](#oh_audiorenderer_setsilentmodeandmixwithothers) | - | Set silent and mix with other streams for this stream. |
| [OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)](#oh_audiorenderer_getsilentmodeandmixwithothers) | - | Query silent and mix with other streams status for this stream. |
| [OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)](#oh_audiorenderer_setdefaultoutputdevice) | - | Temporarily changes the current audio device This function applys on audiorenderers whose StreamUsage are STREAM_USAGE_VOICE_COMMUNICATIN/STREAM_USAGE_VIDEO_COMMUNICATION/STREAM_USAGE_VOICE_MESSAGE. Setting the device will only takes effect if no other accessory such as headphones are in use. |
| [OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_getaudiotimestampinfo) | - | Query the timestamp at which a particular frame was presented in clock monotonic timebase, the frame at the returned position was just committed to hardware. This is often used in video synchronization and recording stream alignment.<br> Position is 0 and timestamp is fixed until stream really runs and frame is committed. Position will also be reset while flush function is called. When a audio route change happens, like in device or output type change situations, the position may also be reset but timestamp remains monotonically increasing. So it is better to use the values until they becomes regularly after the change. This interface also adapts to playback speed change. For example, the increseing speed for position will be double for 2x speed playback.<br> For video synchronization usage, there is a best practice document for developer to refer **AV Synchronization**. |
| [typedef void (\*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptcallback) | OH_AudioRenderer_OnInterruptCallback | Called when an interrupt event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnInterruptEvent. |
| [typedef void (\*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)](#oh_audiorenderer_onerrorcallback) | OH_AudioRenderer_OnErrorCallback | Called when an error event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnError. |
| [OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)](#oh_audiorenderer_getfaststatus) | - | Gets audio renderer running status, check if it works in fast status. |
| [typedef void (\*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status)](#oh_audiorenderer_onfaststatuschange) | OH_AudioRenderer_OnFastStatusChange | Callback function of fast status change event for audio renderer. |
| [OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)](#oh_audiorenderer_setloudnessgain) | - | Sets the loudness gain of current renderer. The default loudness gain is 0.0dB. The stream usage of the audio renderer must be {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_MUSIC}, {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_MOVIE}<br>or {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_AUDIOBOOK}.<br>The latency mode of the audio renderer must be {@link OH_AudioStream_LatencyMode#AUDIOSTREAM_LATENCY_MODE_NORMAL}. If AudioRenderer is played through the high-resolution pipe, this operation is not supported. |
| [OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)](#oh_audiorenderer_getloudnessgain) | - | Get the loudness gain of current renderer. |
| [typedef int32_t (\*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallbackadvanced) | OH_AudioRenderer_OnWriteDataCallbackAdvanced | Callback function of write data on Render.<br> Different with OH_AudioRenderer_OnWriteDataCallback, this function allows the caller to write partial data which ranges from 0 to the callback buffer size. If 0 is returned, the callback thread will sleep for a while. Otherwise, the system may callback again immediately. |
| [OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)](#oh_audiorenderer_getlatency) | - | Gets the estimated audio latency in milliseconds for current audio route. For wireless connection audio devices cases, the latency result may not be very accurate, system just provides it for reference only. The real-time buffer status is also not taken into consideration, so it is recommended to get it only at the beginning of audio playback, and do not call th function very frequently because it may be blocked by route change. Applications should still use [OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo) to handle A/V sync after audio data has been output to hardware. |
| [OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)](#oh_audiorenderer_setindependentaudiosessionstrategy) | - | Configure audio session strategy and behavior parameters to adjust the focus preemption policy. Each time you call this interface to set parameters, you need to call the interface [OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start) again for the settings to take effect. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint) | Called when an interrupt event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnInterruptEvent.<br>**Since**: 20 |
| void (*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error) | Called when an error event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnError.<br>**Since**: 20 |
| void (*OH_AudioRenderer_OnFastStatusChange)( OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status ) | Callback function of fast status change event for audio renderer.<br>**Since**: 20 |
| int32_t (*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize) | Callback function of write data on Render.<br> Different with OH_AudioRenderer_OnWriteDataCallback, this function allows the caller to write partial data which ranges from 0 to the callback buffer size. If 0 is returned, the callback thread will sleep for a while. Otherwise, the system may callback again immediately.<br>**Since**: 20 |

## Function description

### OH_AudioRenderer_Release()

```c
OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_Start()

```c
OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | reference created by OH_AudioStreamBuilder |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_Pause()

```c
OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_Stop()

```c
OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_Flush()

```c
OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_GetCurrentState()

```c
OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_State* state | Pointer to a variable that will be set for the state value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetSamplingRate()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| int32_t* rate | Pointer to a variable that will be set for the sampling rate. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetStreamId()

```c
OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| uint32_t* streamId | Pointer to a variable that will be set for the stream id. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetChannelCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| int32_t* channelCount | Pointer to a variable that will be set for the channel count. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetSampleFormat()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_SampleFormat* sampleFormat | Pointer to a variable that will be set for the sample format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetLatencyMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_LatencyMode* latencyMode | Pointer to a variable that will be set for the latency mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetRendererInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_Usage* usage | Pointer to a variable that will be set for the stream usage. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetEncodingType()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_EncodingType* encodingType | Pointer to a variable that will be set for the encoding type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetFramesWritten()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| int64_t* frames | Pointer to a variable that will be set for the frame count number. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetTimestamp()

```c
OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| clockid_t clockId | {@link #CLOCK_MONOTONIC} |
| int64_t* framePosition | Pointer to a variable to receive the position. |
| int64_t* timestamp | Pointer to a variable to receive the timestamp, unit is nanosecond. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of renderer is nullptr;<br>                                                2.The param of clockId invalid.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioRenderer_GetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| int32_t* frameSize | Pointer to a variable that will be set for the frame size. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)
```

**Description**

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| float* speed | Pointer to a variable to receive the playback speed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_SetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)
```

**Description**

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| float speed | The playback speed, from 0.25 to 4.0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_SetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)
```

**Description**

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| float volume | Volume to set which changes from 0.0 to 1.0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of renderer is nullptr;<br>                                                2.The param of volume invalid.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception.<br>        {@link AUDIOSTREAM_ERROR_SYSTEM} An system error has occurred. |

### OH_AudioRenderer_SetVolumeWithRamp()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)
```

**Description**

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| float volume | Volume to set which changes from 0.0 to 1.0. |
| int32_t durationMs | Duration for volume ramp, in millisecond. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of renderer is nullptr;<br>                                                2.The param of volume invalid.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception.<br>        {@link AUDIOSTREAM_ERROR_SYSTEM} An system error has occurred. |

### OH_AudioRenderer_GetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)
```

**Description**

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| float* volume | Pointer to a variable to receive the volume. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:                                                  1.The param of renderer is nullptr;                                                  2.The param of volume is nullptr. |

### OH_AudioRenderer_SetMarkPosition()

```c
OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)
```

**Description**

Set mark position on current renderer. Calling this function will overwrite the mark postion which has already set.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| uint32_t samplePos | Mark position in samples. |
| OH_AudioRenderer_OnMarkReachedCallback callback | Callback used when the samplePos has reached. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of renderer is nullptr;<br>                                                2.The param of samplePos invalid.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception.<br>        {@link AUDIOSTREAM_ERROR_SYSTEM} An system error has occurred. |

### OH_AudioRenderer_CancelMark()

```c
OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)
```

**Description**

Cancel mark which has set by [OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetUnderflowCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)
```

**Description**

Gets the underflow count on this stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| uint32_t* count | Pointer to a variable to receive the underflow count number. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:                                                  1.The param of renderer is nullptr;                                                  2.The param of count is nullptr. |

### OH_AudioRenderer_GetChannelLayout()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)
```

**Description**

Query the channel layout of the renderer client.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioChannelLayout* channelLayout | Pointer to a variable to receive the channel layout |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)
```

**Description**

Query current audio effect mode.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_AudioEffectMode* effectMode | Pointer to a variable to receive current audio effect mode |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_SetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Set current audio effect mode.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_AudioEffectMode effectMode | Audio effect mode that will be set for the stream |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_GetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)
```

**Description**

Get the privacy of this stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioStream_PrivacyType* privacy | Pointer to a variable which receives the results. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of renderer is nullptr. |

### OH_AudioRenderer_SetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)
```

**Description**

Set silent and mix with other streams for this stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| bool on | The silent and mix with other streams mode. true: set the silent mode and mix with other streams. false: unset the silent mode, current stream will trigger the audio focus internally. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | result code for this function.      {@link #AUDIOSTREAM_SUCCESS} succeed in setting to the silent and mix with other streams.<br>    {@link #AUDIOSTREAM_ERROR_ILLEGAL_STATE} this stream is not allowed to set/unset the silent mode. |

### OH_AudioRenderer_GetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)
```

**Description**

Query silent and mix with other streams status for this stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| bool* on | Pointer to the silent and mix with other streams status. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | result code for this function.      {@link #AUDIOSTREAM_SUCCESS} succeed in getting silent and mix with other streams status<br>    {@link #AUDIOSTREAM_ERROR_SYSTEM} system error when calling this function. |

### OH_AudioRenderer_SetDefaultOutputDevice()

```c
OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)
```

**Description**

Temporarily changes the current audio device This function applys on audiorenderers whose StreamUsage are STREAM_USAGE_VOICE_COMMUNICATIN/STREAM_USAGE_VIDEO_COMMUNICATION/STREAM_USAGE_VOICE_MESSAGE. Setting the device will only takes effect if no other accessory such as headphones are in use.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Renderer generated by OH_AudioStreamBuilder_GenerateRenderer() |
| OH_AudioDevice_Type deviceType | The target device. The available deviceTypes are: EARPIECE: Built-in earpiece SPEAKER: Built-in speaker DEFAULT: System default output device |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | result code for this function.          {@link #AUDIOSTREAM_SUCCESS} succeed in setting the default output device<br>        {@link #AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of renderer is nullptr;<br>                                                2.The param of deviceType is not valid<br>        {@link #AUDIOSTREAM_ERROR_ILLEGAL_STATE} This audiorenderer can not reset the output device<br>        {@link #AUDIOSTREAM_ERROR_SYSTEM} system error when calling this function. |

### OH_AudioRenderer_GetAudioTimestampInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)
```

**Description**

Query the timestamp at which a particular frame was presented in clock monotonic timebase, the frame at the returned position was just committed to hardware. This is often used in video synchronization and recording stream alignment.<br> Position is 0 and timestamp is fixed until stream really runs and frame is committed. Position will also be reset while flush function is called. When a audio route change happens, like in device or output type change situations, the position may also be reset but timestamp remains monotonically increasing. So it is better to use the values until they becomes regularly after the change. This interface also adapts to playback speed change. For example, the increseing speed for position will be double for 2x speed playback.<br> For video synchronization usage, there is a best practice document for developer to refer **AV Synchronization**.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer() |
| int64_t* framePosition | Pointer to a variable to receive the position |
| int64_t* timestamp | Pointer to a variable to receive the timestamp |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                        1.The param of renderer is nullptr;<br>                                        2.The param of framePosition or timestamp is nullptr;<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE}:<br>                                        1.Only running state is legal for getting audio timestamp.<br>        {@link AUDIOSTREAM_ERROR_SYSTEM}:                                          1.Crash or blocking occurs in system process.                                          2.Other unexpected error from internal system. |

### OH_AudioRenderer_OnInterruptCallback()

```c
typedef void (*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)
```

**Description**

Called when an interrupt event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnInterruptEvent.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer\* renderer | Pointer to the AudioRenderer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetRendererInterruptCallback. |
| OH_AudioInterrupt_ForceType type | Type of force that causes the interrupt event. |
| OH_AudioInterrupt_Hint hint | Hint provided along with the interrupt event. |

**Reference**:

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnInterruptEvent


### OH_AudioRenderer_OnErrorCallback()

```c
typedef void (*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)
```

**Description**

Called when an error event occurs in an AudioRenderer instance. This function is similar to OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnError.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer\* renderer | Pointer to the AudioRenderer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetRendererErrorCallback. |
| OH_AudioStream_Result error | Specific error information. |

**Reference**:

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnError


### OH_AudioRenderer_GetFastStatus()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)
```

**Description**

Gets audio renderer running status, check if it works in fast status.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | Reference created by OH_AudioStreamBuilder_GenerateRenderer. |
| OH_AudioStream_FastStatus* status | Pointer to a variable to receive the status. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | @return      {@link AUDIOSTREAM_SUCCESS} if the execution is successful.<br>    {@link AUDIOSTREAM_ERROR_INVALID_PARAM} the param of renderer is nullptr.<br>    {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} function called in invalid state, only available before release state. |

### OH_AudioRenderer_OnFastStatusChange()

```c
typedef void (*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status)
```

**Description**

Callback function of fast status change event for audio renderer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer\* renderer | Pointer to an audio renderer instance for which this callback occurs. |
| void\* userData | Userdata which is passed by register. |
| OH_AudioStream_FastStatus status | Current fast status. |

### OH_AudioRenderer_SetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)
```

**Description**

Sets the loudness gain of current renderer. The default loudness gain is 0.0dB. The stream usage of the audio renderer must be {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_MUSIC}, {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_MOVIE}<br>or {@link OH_AudioStream_Usage#AUDIOSTREAM_USAGE_AUDIOBOOK}.<br>The latency mode of the audio renderer must be {@link OH_AudioStream_LatencyMode#AUDIOSTREAM_LATENCY_MODE_NORMAL}. If AudioRenderer is played through the high-resolution pipe, this operation is not supported.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | AudioRender created by OH_AudioStreamBuilder_GenerateRenderer() |
| float loudnessGain | Loudness gain to set which changes from -90.0 to 24.0, expressing in dB. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:                                                  1.The param of renderer is nullptr or not supported to set gain;                                                  2.The param of loudnessGain is invalid. |

### OH_AudioRenderer_GetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)
```

**Description**

Get the loudness gain of current renderer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | AudioRender created by OH_AudioStreamBuilder_GenerateRenderer() |
| float* loudnessGain | Pointer to a variable to receive the loudness gain, unit is dB. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:                                                  1.The param of renderer is nullptr;                                                  2.The param of loudnessGain is nullptr. |

### OH_AudioRenderer_OnWriteDataCallbackAdvanced()

```c
typedef int32_t (*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**Description**

Callback function of write data on Render.<br> Different with OH_AudioRenderer_OnWriteDataCallback, this function allows the caller to write partial data which ranges from 0 to the callback buffer size. If 0 is returned, the callback thread will sleep for a while. Otherwise, the system may callback again immediately.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer\* renderer | AudioRenderer where this callback occurs. |
| void\* userData | User data which is passed by user. |
| void\* audioData | Audio data pointer, where user should fill in audio data. |
| int32_t audioDataSize | Size of audio data that user should fill in, unit is byte. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the valid data that has written into audioData buffer. The return value must be in range of  [0, audioDataSize]. If the return value is less than 0, the system changes it to 0. And, if the return value is  greater than audioDataSize, the system changes it to audioDataSize. Note that the length of the returned buffer  must be an integer multiple of the length of the single sample data. For example, for 2 channels and S16 format  audio data, it must be an integer multiple of 4(216/8). Otherwise, it may cause noise during playback. |

**Reference**:

OH_AudioRenderer_OnWriteDataCallback


### OH_AudioRenderer_GetLatency()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)
```

**Description**

Gets the estimated audio latency in milliseconds for current audio route. For wireless connection audio devices cases, the latency result may not be very accurate, system just provides it for reference only. The real-time buffer status is also not taken into consideration, so it is recommended to get it only at the beginning of audio playback, and do not call th function very frequently because it may be blocked by route change. Applications should still use [OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo) to handle A/V sync after audio data has been output to hardware.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | AudioRenderer created by OH_AudioStreamBuilder_GenerateRenderer(). |
| OH_AudioStream_LatencyType type | Type of audio latency to get. |
| int32_t* latencyMs | Pointer to a variable to receive the latency in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link #AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link #AUDIOSTREAM_ERROR_INVALID_PARAM}<br>            1.The param of renderer is nullptr.<br>            2.The param of latencyMs is nullptr.<br>            3.The param of type is invalid value.<br>        {@link #AUDIOSTREAM_ERROR_SYSTEM} System internal error, like audio service error. |

### OH_AudioRenderer_SetIndependentAudioSessionStrategy()

```c
OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)
```

**Description**

Configure audio session strategy and behavior parameters to adjust the focus preemption policy. Each time you call this interface to set parameters, you need to call the interface [OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start) again for the settings to take effect.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioRenderer* renderer | AudioRenderer created by OH_AudioStreamBuilder_GenerateRenderer(). |
| const OH_AudioSession_Strategy* strategy | pointer to {@link #OH_AudioSession_Strategy} which is used to set the audio session strategy. |
| uint32_t behavior | Audio session behavior flag, which can be a single flag or a bitwise OR combination of multiple flags {@link #OH_AudioSession_BehaviorFlags}. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | {@link #AUDIOSTREAM_SUCCESS} If the execution is successful.<br>    or {@link #AUDIOSTREAM_ERROR_INVALID_PARAM} If the parameter is null or out of range.<br>    or {@link #AUDIOSTREAM_ERROR_ILLEGAL_STATE} Running and released are illegal states. |


