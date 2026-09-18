# native_audiocapturer.h

## Overview

Declare audio stream related interfaces for input type.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer)](#oh_audiocapturer_release) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer)](#oh_audiocapturer_start) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer)](#oh_audiocapturer_pause) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer)](#oh_audiocapturer_stop) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer)](#oh_audiocapturer_flush) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetCurrentState(OH_AudioCapturer* capturer, OH_AudioStream_State* state)](#oh_audiocapturer_getcurrentstate) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetLatencyMode(OH_AudioCapturer* capturer, OH_AudioStream_LatencyMode* latencyMode)](#oh_audiocapturer_getlatencymode) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetStreamId(OH_AudioCapturer* capturer, uint32_t* streamId)](#oh_audiocapturer_getstreamid) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetSamplingRate(OH_AudioCapturer* capturer, int32_t* rate)](#oh_audiocapturer_getsamplingrate) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetChannelCount(OH_AudioCapturer* capturer, int32_t* channelCount)](#oh_audiocapturer_getchannelcount) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetSampleFormat(OH_AudioCapturer* capturer, OH_AudioStream_SampleFormat* sampleFormat)](#oh_audiocapturer_getsampleformat) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetEncodingType(OH_AudioCapturer* capturer, OH_AudioStream_EncodingType* encodingType)](#oh_audiocapturer_getencodingtype) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetCapturerInfo(OH_AudioCapturer* capturer, OH_AudioStream_SourceType* sourceType)](#oh_audiocapturer_getcapturerinfo) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetFrameSizeInCallback(OH_AudioCapturer* capturer, int32_t* frameSize)](#oh_audiocapturer_getframesizeincallback) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetTimestamp(OH_AudioCapturer* capturer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)](#oh_audiocapturer_gettimestamp) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetFramesRead(OH_AudioCapturer* capturer, int64_t* frames)](#oh_audiocapturer_getframesread) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_GetOverflowCount(OH_AudioCapturer* capturer, uint32_t* count)](#oh_audiocapturer_getoverflowcount) | - | Gets the overflow count on this stream. |
| [typedef void (\*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiocapturer_onreaddatacallback) | OH_AudioCapturer_OnReadDataCallback | Called when audio data is available to read. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnReadData. |
| [typedef void (\*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray)](#oh_audiocapturer_ondevicechangecallback) | OH_AudioCapturer_OnDeviceChangeCallback | Called when the input device of an AudioCapturer instance changes. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnStreamEvent. |
| [typedef void (\*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptcallback) | OH_AudioCapturer_OnInterruptCallback | Called when an interrupt event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnInterruptEvent. |
| [typedef void (\*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)](#oh_audiocapturer_onerrorcallback) | OH_AudioCapturer_OnErrorCallback | Called when an error event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnError. |
| [OH_AudioStream_Result OH_AudioCapturer_GetFastStatus(OH_AudioCapturer* capturer, OH_AudioStream_FastStatus* status)](#oh_audiocapturer_getfaststatus) | - | Gets audio capturer running status, check if it works in fast status. |
| [typedef void (\*OH_AudioCapturer_OnFastStatusChange)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status)](#oh_audiocapturer_onfaststatuschange) | OH_AudioCapturer_OnFastStatusChange | Callback function of fast status change event for audio capturer. |
| [typedef void (\*OH_AudioCapturer_OnPlaybackCaptureStartCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state)](#oh_audiocapturer_onplaybackcapturestartcallback) | OH_AudioCapturer_OnPlaybackCaptureStartCallback | Callback function to get playback capture start result. |
| [OH_AudioStream_Result OH_AudioCapturer_RequestPlaybackCaptureStart(OH_AudioCapturer* capturer, OH_AudioCapturer_OnPlaybackCaptureStartCallback callback, void* userData)](#oh_audiocapturer_requestplaybackcapturestart) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_SetMuteHint(OH_AudioCapturer* capturer, bool mute)](#oh_audiocapturer_setmutehint) | - | Sets recording mute state to audio system. This method is used as a hint for power optimization, it does not mute the recording stream, only affects internal processing strategy. Audio system may disable some recording effects when application notifies its muted state to system. Mute hint state can only be set when current stream is in running state. |
| [OH_AudioStream_Result OH_AudioCapturer_SetIndependentAudioSessionStrategy(OH_AudioCapturer* capturer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)](#oh_audiocapturer_setindependentaudiosessionstrategy) | - | Configure audio session strategy and behavior parameters to adjust the focus preemption policy. Each time you call this interface to set parameters, you need to call the interface [OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start) again for the settings to take effect. |
| [typedef void (\*OH_AudioCapturer_SensitiveRecordPermitCallback)(OH_AudioCapturer* capturer, void* userData, bool isPermitted)](#oh_audiocapturer_sensitiverecordpermitcallback) | OH_AudioCapturer_SensitiveRecordPermitCallback | Callback used to receive when the sensitive warning message playback for cellular call recording is finished. The application must wait for the permitted result before starting cellular call recording. |
| [OH_AudioStream_Result OH_AudioCapturer_SetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode noiseReductionMode)](#oh_audiocapturer_setnoisereductionmode) | - | Sets noise reduction mode for current audio capturer. The supported mode should be obtained by {@link #getSupportedNoiseReductionModes}. The actual effect may vary from different audio devices, and will be invalid when there are multiple direct streams running simultaneously. The mode can only be changed in created and stopped state. |
| [OH_AudioStream_Result OH_AudioCapturer_GetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionMode)](#oh_audiocapturer_getnoisereductionmode) | - | Gets the noise reduction mode for current audio capturer. The mode will only consider the default and setted status, audio input device and stream concurrency will not be considered. |
| [OH_AudioStream_Result OH_AudioCapturer_GetSupportedNoiseReductionModes(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionModeArray, uint32_t inModeArraySize, uint32_t *outModeArraySize)](#oh_audiocapturer_getsupportednoisereductionmodes) | - | Gets all the supported noise reduction modes for current device platform. Currently the noise reduction effect is only supported when using {@link AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE}, other supported usage may be extened later. The supported modes will only consider the audio format and device platform, audio input device and stream concurrency will not be considered. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize) | Called when audio data is available to read. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnReadData.<br>**Since**: 20 |
| void (*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray) | Called when the input device of an AudioCapturer instance changes. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnStreamEvent.<br>**Since**: 20 |
| void (*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint) | Called when an interrupt event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnInterruptEvent.<br>**Since**: 20 |
| void (*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error) | Called when an error event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnError.<br>**Since**: 20 |
| void (*OH_AudioCapturer_OnFastStatusChange)( OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status ) | Callback function of fast status change event for audio capturer.<br>**Since**: 20 |
| void (*OH_AudioCapturer_OnPlaybackCaptureStartCallback)( OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state) | Callback function to get playback capture start result.<br>**Since**: 23 |
| void (*OH_AudioCapturer_SensitiveRecordPermitCallback)( OH_AudioCapturer* capturer, void* userData, bool isPermitted) | Callback used to receive when the sensitive warning message playback for cellular call recording is finished. The application must wait for the permitted result before starting cellular call recording.<br>**Since**: 26.0.0 |

## Function description

### OH_AudioCapturer_Release()

```c
OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer)
```

**Description**

**Required permission**: ohos.permission.MICROPHONE

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by OH_AudioStreamBuilder_GenerateCapturer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_Start()

```c
OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer)
```

**Description**

**Required permission**: ohos.permission.MICROPHONE

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by OH_AudioStreamBuilder_GenerateCapturer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_Pause()

```c
OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer)
```

**Description**

**Required permission**: ohos.permission.MICROPHONE

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by OH_AudioStreamBuilder_GenerateCapturer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_Stop()

```c
OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer)
```

**Description**

**Required permission**: ohos.permission.MICROPHONE

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by OH_AudioStreamBuilder_GenerateCapturer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_Flush()

```c
OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by OH_AudioStreamBuilder_GenerateCapturer() |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_GetCurrentState()

```c
OH_AudioStream_Result OH_AudioCapturer_GetCurrentState(OH_AudioCapturer* capturer, OH_AudioStream_State* state)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| OH_AudioStream_State* state | Pointer to a variable that will be set for the state value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetLatencyMode()

```c
OH_AudioStream_Result OH_AudioCapturer_GetLatencyMode(OH_AudioCapturer* capturer, OH_AudioStream_LatencyMode* latencyMode)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| OH_AudioStream_LatencyMode* latencyMode | Pointer to a variable that will be set for the latency mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetStreamId()

```c
OH_AudioStream_Result OH_AudioCapturer_GetStreamId(OH_AudioCapturer* capturer, uint32_t* streamId)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| uint32_t* streamId | Pointer to a variable that will be set for the stream id. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetSamplingRate()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSamplingRate(OH_AudioCapturer* capturer, int32_t* rate)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| int32_t* rate | Pointer to a variable that will be set for the sampling rate. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetChannelCount()

```c
OH_AudioStream_Result OH_AudioCapturer_GetChannelCount(OH_AudioCapturer* capturer, int32_t* channelCount)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| int32_t* channelCount | Pointer to a variable that will be set for the channel count. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetSampleFormat()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSampleFormat(OH_AudioCapturer* capturer, OH_AudioStream_SampleFormat* sampleFormat)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| OH_AudioStream_SampleFormat* sampleFormat | Pointer to a variable that will be set for the sample format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetEncodingType()

```c
OH_AudioStream_Result OH_AudioCapturer_GetEncodingType(OH_AudioCapturer* capturer, OH_AudioStream_EncodingType* encodingType)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| OH_AudioStream_EncodingType* encodingType | Pointer to a variable that will be set for the encoding type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetCapturerInfo()

```c
OH_AudioStream_Result OH_AudioCapturer_GetCapturerInfo(OH_AudioCapturer* capturer, OH_AudioStream_SourceType* sourceType)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| OH_AudioStream_SourceType* sourceType | Pointer to a variable that will be set for the stream sourceType. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFrameSizeInCallback(OH_AudioCapturer* capturer, int32_t* frameSize)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| int32_t* frameSize | Pointer to a variable that will be set for the frame size. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_GetTimestamp()

```c
OH_AudioStream_Result OH_AudioCapturer_GetTimestamp(OH_AudioCapturer* capturer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| clockid_t clockId | {@link #CLOCK_MONOTONIC} |
| int64_t* framePosition | Pointer to a variable to receive the position. |
| int64_t* timestamp | Pointer to a variable to receive the timestamp, unit is nanosecond. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM}:<br>                                                1.The param of capturer is nullptr;<br>                                                2.The param of clockId invalid.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Execution status exception. |

### OH_AudioCapturer_GetFramesRead()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFramesRead(OH_AudioCapturer* capturer, int64_t* frames)
```

**Description**

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer() |
| int64_t* frames | Pointer to a variable that will be set for the frame count number. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_GetOverflowCount()

```c
OH_AudioStream_Result OH_AudioCapturer_GetOverflowCount(OH_AudioCapturer* capturer, uint32_t* count)
```

**Description**

Gets the overflow count on this stream.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Capturer generated by OH_AudioStreamBuilder_GenerateCapturer() |
| uint32_t* count | Pointer to a variable that will be set for the overflow count number. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr. |

### OH_AudioCapturer_OnReadDataCallback()

```c
typedef void (*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize)
```

**Description**

Called when audio data is available to read. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnReadData.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to the AudioCapturer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetCapturerReadDataCallback. |
| void\* audioData | Pointer to the available audio data. |
| int32_t audioDataSize | Size of the available audio data, unit is byte. |

**Reference**:

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnReadData


### OH_AudioCapturer_OnDeviceChangeCallback()

```c
typedef void (*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray)
```

**Description**

Called when the input device of an AudioCapturer instance changes. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnStreamEvent.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to the AudioCapturer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback. |
| OH_AudioDeviceDescriptorArray\* deviceArray | Pointer to an array of the new input devices. |

**Reference**:

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnStreamEvent


### OH_AudioCapturer_OnInterruptCallback()

```c
typedef void (*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)
```

**Description**

Called when an interrupt event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnInterruptEvent.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to the AudioCapturer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetCapturerInterruptCallback. |
| OH_AudioInterrupt_ForceType type | Type of force that causes the interrupt event. |
| OH_AudioInterrupt_Hint hint | Hint provided along with the interrupt event. |

**Reference**:

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnInterruptEvent


### OH_AudioCapturer_OnErrorCallback()

```c
typedef void (*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)
```

**Description**

Called when an error event occurs in an AudioCapturer instance. This function is similar to OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnError.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to the AudioCapturer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via OH_AudioStreamBuilder_SetCapturerErrorCallback. |
| OH_AudioStream_Result error | Specific error information. |

**Reference**:

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnError


### OH_AudioCapturer_GetFastStatus()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFastStatus(OH_AudioCapturer* capturer, OH_AudioStream_FastStatus* status)
```

**Description**

Gets audio capturer running status, check if it works in fast status.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer. |
| OH_AudioStream_FastStatus* status | Pointer to a variable to receive the status. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | @return      {@link AUDIOSTREAM_SUCCESS} if the execution is successful.<br>    {@link AUDIOSTREAM_ERROR_INVALID_PARAM} the param of capturer is nullptr.<br>    {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} function called in invalid state, only available before release state. |

### OH_AudioCapturer_OnFastStatusChange()

```c
typedef void (*OH_AudioCapturer_OnFastStatusChange)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status)
```

**Description**

Callback function of fast status change event for audio capturer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to an audio capturer instance for which this callback occurs. |
| void\* userData | Userdata which is passed by register. |
| OH_AudioStream_FastStatus status | Current fast status. |

### OH_AudioCapturer_OnPlaybackCaptureStartCallback()

```c
typedef void (*OH_AudioCapturer_OnPlaybackCaptureStartCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state)
```

**Description**

Callback function to get playback capture start result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | Pointer to the AudioCapturer instance that triggers the callback. |
| void\* userData | Pointer to the user data passed when setting the callback via [OH_AudioCapturer_RequestPlaybackCaptureStart](capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart). |
| OH_AudioStream_PlaybackCaptureStartState state | The final state to describe whether start request is successful. |

### OH_AudioCapturer_RequestPlaybackCaptureStart()

```c
OH_AudioStream_Result OH_AudioCapturer_RequestPlaybackCaptureStart(OH_AudioCapturer* capturer, OH_AudioCapturer_OnPlaybackCaptureStartCallback callback, void* userData)
```

**Description**

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | reference created by {@link #OH_AudioStreamBuilder_GenerateCapturer} |
| [OH_AudioCapturer_OnPlaybackCaptureStartCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onplaybackcapturestartcallback) callback | Callback function used to receive the final result of start request. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:      {@link #AUDIOSTREAM_SUCCESS} If the execution is successful.<br>    {@link #AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr or callback is invalid.<br>    {@link #AUDIOSTREAM_ERROR_ILLEGAL_STATE} Running and released are illegal states.<br>    {@link #AUDIOSTREAM_ERROR_SYSTEM} System internal error, like audio service error. |

### OH_AudioCapturer_SetMuteHint()

```c
OH_AudioStream_Result OH_AudioCapturer_SetMuteHint(OH_AudioCapturer* capturer, bool mute)
```

**Description**

Sets recording mute state to audio system. This method is used as a hint for power optimization, it does not mute the recording stream, only affects internal processing strategy. Audio system may disable some recording effects when application notifies its muted state to system. Mute hint state can only be set when current stream is in running state.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Reference created by OH_AudioStreamBuilder_GenerateCapturer(). |
| bool mute | use true if application recording stream muted by application itself. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | Function result code:          {@link AUDIOSTREAM_SUCCESS} If the execution is successful.<br>        {@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>        {@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Operation not permitted at current state, stream is not running. |

### OH_AudioCapturer_SetIndependentAudioSessionStrategy()

```c
OH_AudioStream_Result OH_AudioCapturer_SetIndependentAudioSessionStrategy(OH_AudioCapturer* capturer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)
```

**Description**

Configure audio session strategy and behavior parameters to adjust the focus preemption policy. Each time you call this interface to set parameters, you need to call the interface [OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start) again for the settings to take effect.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | Capturer generated by OH_AudioStreamBuilder_GenerateCapturer() |
| const OH_AudioSession_Strategy* strategy | pointer to {@link #OH_AudioSession_Strategy} which is used to set the audio session strategy. |
| uint32_t behavior | Audio session behavior flag, which can be a single flag or a bitwise OR combination of multiple flags {@link #OH_AudioSession_BehaviorFlags}. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | {@link #AUDIOSTREAM_SUCCESS} If the execution is successful.<br>    or {@link #AUDIOSTREAM_ERROR_INVALID_PARAM} If the parameter is null or out of range.<br>    or {@link #AUDIOSTREAM_ERROR_ILLEGAL_STATE} Running and released are illegal states. |

### OH_AudioCapturer_SensitiveRecordPermitCallback()

```c
typedef void (*OH_AudioCapturer_SensitiveRecordPermitCallback)(OH_AudioCapturer* capturer, void* userData, bool isPermitted)
```

**Description**

Callback used to receive when the sensitive warning message playback for cellular call recording is finished. The application must wait for the permitted result before starting cellular call recording.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer\* capturer | The pointer to the {@link OH_AudioCapturer} object created<br>    by {@link OH_AudioStreamBuilder_GenerateCapturer}. |
| void\* userData | The pointer to user data which is set in {@link OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback}. |
| bool isPermitted | Indicates whether the sensitive warning message playback is finished. If the result is true, the recording can start, otherwise the recording is not permitted. |

### OH_AudioCapturer_SetNoiseReductionMode()

```c
OH_AudioStream_Result OH_AudioCapturer_SetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode noiseReductionMode)
```

**Description**

Sets noise reduction mode for current audio capturer. The supported mode should be obtained by {@link #getSupportedNoiseReductionModes}. The actual effect may vary from different audio devices, and will be invalid when there are multiple direct streams running simultaneously. The mode can only be changed in created and stopped state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | [in] Pointer to the audio capturer created by {@link OH_AudioStreamBuilder_GenerateCapturer}. |
| OH_AudioNoiseReductionMode noiseReductionMode | [in] The noise reduction mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>          <li>{@link AUDIOSTREAM_SUCCESS} If the execution is successful.</li><br>        <li>{@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>                                                    The param of noiseReductionMode is invalid.</li><br>        <li>{@link AUDIOSTREAM_ERROR_ILLEGAL_STATE} Illegal state, audio capturer is in running state.</li><br>        <li>{@link AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY} The setted mode is not supported.</li><br>        <li>{@link AUDIOSTREAM_ERROR_SERVICE_DIED} Audio server process died.</li>          </ul> |

### OH_AudioCapturer_GetNoiseReductionMode()

```c
OH_AudioStream_Result OH_AudioCapturer_GetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionMode)
```

**Description**

Gets the noise reduction mode for current audio capturer. The mode will only consider the default and setted status, audio input device and stream concurrency will not be considered.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | [in] Pointer to the audio capturer created by {@link OH_AudioStreamBuilder_GenerateCapturer}. |
| OH_AudioNoiseReductionMode* noiseReductionMode | [out] Pointer to get the input noise reduction mode, the default value is {@link AUDIO_NOISE_REDUCTION_MODE_FIDELITY}. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>          <li>{@link AUDIOSTREAM_SUCCESS} If the execution is successful.</li><br>        <li>{@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.                                                      The param of noiseReductionMode is nullptr.</li>          </ul> |

### OH_AudioCapturer_GetSupportedNoiseReductionModes()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSupportedNoiseReductionModes(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionModeArray, uint32_t inModeArraySize, uint32_t *outModeArraySize)
```

**Description**

Gets all the supported noise reduction modes for current device platform. Currently the noise reduction effect is only supported when using {@link AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE}, other supported usage may be extened later. The supported modes will only consider the audio format and device platform, audio input device and stream concurrency will not be considered.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioCapturer* capturer | [in] Pointer to the audio capturer created by {@link OH_AudioStreamBuilder_GenerateCapturer}. |
| OH_AudioNoiseReductionMode* noiseReductionModeArray | [out] Pointer to a user-allocated array to get the supported noise reduction modes, at least {@link AUDIO_NOISE_REDUCTION_MODE_FIDELITY} is supported. |
| uint32_t inModeArraySize | [in] The allocated size of the 'noiseReductionModeArray' input parameter, it is recommanded to allocate a larger size, such as 20, to adapt the new modes in the future. |
| uint32_t *outModeArraySize | [out] Pointer to get the actual modes size. When the supported modes size is larger than 'inModeArraySize', only part of the modes will be filled into 'noiseReductionModeArray', and the 'outModeArraySize' will be equal to 'inModeArraySize'. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioStream_Result | <ul>          <li>{@link AUDIOSTREAM_SUCCESS} If the execution is successful.</li><br>        <li>{@link AUDIOSTREAM_ERROR_INVALID_PARAM} The param of capturer is nullptr.<br>                                                    The param of noiseReductionModeArray is nullptr.<br>                                                    The param of outModeArraySize is nullptr.</li><br>        <li>{@link AUDIOSTREAM_ERROR_SERVICE_DIED} Audio server process died.</li>          </ul> |


