# native_audiorenderer.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=5e96177c24aa23aee8ea58c394f1a2c3298d3e1c translatedAt=2026-11-10T03:07:19.618Z pushedAt=2026-11-10T04:46:11.386Z nl=1 -->

## Overview

The file declares the functions related to an audio renderer.

**File to include**: <ohaudio/native_audiorenderer.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)](#oh_audiorenderer_release) | - | Releases an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)](#oh_audiorenderer_start) | - | Starts an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)](#oh_audiorenderer_pause) | - | Pauses an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)](#oh_audiorenderer_stop) | - | Stops an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)](#oh_audiorenderer_flush) | - | Clears audio data in the buffer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)](#oh_audiorenderer_getcurrentstate) | - | Obtains the state of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)](#oh_audiorenderer_getsamplingrate) | - | Obtains the sampling rate of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)](#oh_audiorenderer_getstreamid) | - | Obtains the stream ID of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)](#oh_audiorenderer_getchannelcount) | - | Obtains the number of channels for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)](#oh_audiorenderer_getsampleformat) | - | Obtains the sampling format of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)](#oh_audiorenderer_getlatencymode) | - | Obtains the latency mode of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)](#oh_audiorenderer_getrendererinfo) | - | Obtains the usage type of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)](#oh_audiorenderer_getencodingtype) | - | Obtains the encoding type of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)](#oh_audiorenderer_getframeswritten) | - | Obtains the number of frames that have been written since the stream was created.|
| [OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_gettimestamp) | - | Obtains the timestamp and position information of the output audio stream.<br>This API can obtain the actual playback position (framePosition) of the audio channel and the timestamp when the audio is played to that position.<br>The playback position is in samples, and the timestamp is in nanoseconds (ns).<br> When a device switch or pause recovery occurs, because the playback path itself needs some time to recover, the playback position and timestamp obtained by calling this API remain briefly in the state before the switch or pause.<br> This API is usually used to implement audio-video synchronization. The call frequency is recommended to be higher than once every 200 ms, and the recommended frequency is once per minute. When the audio-video synchronization effect can be guaranteed, there is no need to query the timestamp frequently to avoid power consumption issues. |
| [OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_getaudiotimestampinfo) | - | Obtains the timestamp and position information of the output audio stream, adapted to the speed change API.<br> Obtains the timestamp and position information of the output audio stream, which is usually used for audio-video synchronization alignment. The playback position is in samples, and the timestamp is in nanoseconds (ns).<br> When a device switch or pause recovery occurs, because the playback path itself needs some time to recover, the playback position and timestamp obtained by calling this API remain briefly in the state before the switch or pause.<br> This API is usually used to implement audio-video synchronization. The call frequency is recommended to be higher than once every 200 ms, and the recommended frequency is once per minute. When the audio-video synchronization effect can be guaranteed, there is no need to query the timestamp frequently to avoid power consumption issues.|
| [OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)](#oh_audiorenderer_getframesizeincallback) | - | Obtains the frame size in the callback. The frame size is the fixed length of the buffer returned by each callback.|
| [OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)](#oh_audiorenderer_getspeed) | - | Obtains the rate of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)](#oh_audiorenderer_setspeed) | - | Sets the rate for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)](#oh_audiorenderer_setmarkposition) | - | Sets the mark position for an audio renderer. When this function is called, the mark position that has been set will be overwritten.|
| [OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)](#oh_audiorenderer_cancelmark) | - | Cancels the mark set by [OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition).|
| [OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)](#oh_audiorenderer_setvolume) | - | Sets the volume for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)](#oh_audiorenderer_setvolumewithramp) | - | Sets the volume with a ramp within the specified duration for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)](#oh_audiorenderer_getvolume) | - | Obtains the volume of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)](#oh_audiorenderer_getunderflowcount) | - | Obtains the number of underloaded audio streams of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)](#oh_audiorenderer_getchannellayout) | - | Obtains the channel layout of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)](#oh_audiorenderer_geteffectmode) | - | Obtains the effect mode of an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)](#oh_audiorenderer_seteffectmode) | - | Sets the effect mode for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)](#oh_audiorenderer_getrendererprivacy) | - | Checks whether the audio stream being played can be recorded by other applications.|
| [OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)](#oh_audiorenderer_setsilentmodeandmixwithothers) | - | Sets the silent mode in concurrent playback for an audio renderer.<br> If the silent mode in concurrent playback is enabled, the system mutes the audio stream and does not interrupt other audio streams. If the silent mode in concurrent playback is disabled, the audio stream can gain focus based on the system focus strategy.|
| [OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)](#oh_audiorenderer_getsilentmodeandmixwithothers) | - | Checks whether the silent mode in concurrent playback is enabled for an audio renderer.|
| [OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)](#oh_audiorenderer_setdefaultoutputdevice) | - | Sets the default built-in audio output device.<br> This function applies only to the scenario where [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) is set to voice messages, VoIP voice calls, and VoIP video calls and the available device types are the receiver, speaker, and system default device.<br> This function can be called at any time after an AudioRenderer instance is created. The system records the default built-in audio output device set by the application. When the application is started, if an external device such as a Bluetooth or wired headset is connected, the system preferentially uses the external device to play sound. Otherwise, the system uses this default device to play sound.<br>|
| [typedef void (\*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptcallback) | OH_AudioRenderer_OnInterruptCallback | Defines the callback for interruption events of an audio renderer.|
| [typedef void (\*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)](#oh_audiorenderer_onerrorcallback) | OH_AudioRenderer_OnErrorCallback | Defines a pointer to the callback invoked when an error occurs in the audio stream. It is triggered when an internal system fault occurs, such as an abnormal exit of the audio service, and is not caused by application calls. |
| [OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)](#oh_audiorenderer_getfaststatus) | - | Obtains the running status of an audio renderer to determine whether it is running in low-latency mode.|
| [typedef void (\*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status)](#oh_audiorenderer_onfaststatuschange) | OH_AudioRenderer_OnFastStatusChange | Defines a callback function for low-latency status changes during audio playback.|
| [OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)](#oh_audiorenderer_setloudnessgain) | - | Sets the loudness of audio playback. The default loudness value is 0.0 dB. The audio stream playback type must be one of the following: Music: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC;<br> movies or videos: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE;<br> audiobooks (including books, crosstalk, and storytelling), audio news, podcasts, and others: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio stream must be [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> Loudness settings are not supported for high-definition audio channels.<br> Due to the buffer between the audio framework and hardware, there may be a delay in the actual effect of loudness adjustment. The delay duration depends on the buffer length.<br> You are advised to set the loudness before starting playback of different audio streams to achieve the optimal balance effect.|
| [OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)](#oh_audiorenderer_getloudnessgain) | - | Obtains the loudness of audio playback.|
| [typedef int32_t (\*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallbackadvanced) | OH_AudioRenderer_OnWriteDataCallbackAdvanced | Defines a function pointer to the callback used to write audio data. Unlike **OH_AudioRenderer_OnWriteDataCallback**, this function allows the application to fill data of the length ranging [0, audioDataSize].<br> Here, **audioDataSize** refers to the length of the callback buffer. The caller notifies the system of the length of the data written through the return value.<br> If the return value is 0, the callback thread sleeps for a period of time.<br> Otherwise, the system may immediately initiate the next callback.|
| [OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)](#oh_audiorenderer_getlatency) | - | Obtains the estimated latency of the current audio route, in milliseconds. For audio devices connected in wireless mode, the latency estimation may be inaccurate. The result is for reference only.<br> Since the latency is not counted in the real-time buffer, you are advised to obtain the latency only when audio playback starts. Frequent calls may block this API due to route switching.<br> After audio data is output to the hardware, you are advised to use [OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo) for audio-video synchronization.|
| [OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)](#oh_audiorenderer_setindependentaudiosessionstrategy) | - | Sets the independent audio session strategy and behavior parameters. If this API is called while an audio renderer is running, you must call the [OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start) API again for the settings to take effect.|

## Function Description

### OH_AudioRenderer_Release()

```c
OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)
```

**Description**

Releases an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_Start()

```c
OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)
```

**Description**

Starts an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_Pause()

```c
OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)
```

**Description**

Pauses an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_Stop()

```c
OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)
```

**Description**

Stops an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_Flush()

```c
OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)
```

**Description**

Clears audio data in the buffer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_GetCurrentState()

```c
OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)
```

**Description**

Obtains the state of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_State](capi-native-audiostream-base-h.md#oh_audiostream_state)* state | Pointer to a variable used to receive the state.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetSamplingRate()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)
```

**Description**

Obtains the sampling rate of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| int32_t* rate | Pointer to a variable used to receive the sampling rate.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetStreamId()

```c
OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)
```

**Description**

Obtains the stream ID of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| uint32_t* streamId | Pointer to a variable used to receive the stream ID.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetChannelCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)
```

**Description**

Obtains the number of channels for an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| int32_t* channelCount | Pointer to a variable used to receive the channel count.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetSampleFormat()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)
```

**Description**

Obtains the sampling format of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat)* sampleFormat | Pointer to a variable used to receive the sampling format.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetLatencyMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)
```

**Description**

Obtains the latency mode of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode)* latencyMode | Pointer to a variable used to receive the latency mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetRendererInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)
```

**Description**

Obtains the usage type of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)* usage | Pointer to a variable used to receive the usage type.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetEncodingType()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)
```

**Description**

Obtains the encoding type of an audio renderer.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype)* encodingType | Pointer to a variable used to receive the encoding type.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetFramesWritten()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)
```

**Description**

Obtains the number of frames that have been written since the stream was created.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| int64_t* frames | Pointer to the variable used to receive the number of frames written. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetTimestamp()

```c
OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)
```

**Description**

Obtains the timestamp and position information of the output audio stream.<br>This API can obtain the actual playback position (framePosition) of the audio channel and the timestamp at which the audio reaches that position.<br>The playback position is in samples, and the timestamp is in nanoseconds (ns).<br> When a device switch or a pause-resume occurs, because the playback path itself takes some time to recover, the playback position and timestamp obtained by calling this API will briefly remain in the state before the switch or pause.<br> This API is usually used to implement audio-video synchronization. It is recommended that the call frequency be lower than once every 200 ms, with a recommended frequency of once per minute. When the audio-video synchronization effect can be guaranteed, there is no need to query the timestamp frequently to avoid power consumption issues.

> **NOTE**
>
> - When the actual playback position (framePosition) is 0, the timestamp is a fixed value and is updated only when the stream actually starts running.
> - The playback position (framePosition) is in samples. The number of samples is calculated as the sampling rate multiplied by time. For example, when the sampling rate is 48000 Hz, the number of samples corresponding to 20 ms of audio data is 48000*0.02, that is, 960 sample points.
> - The actual playback position is also reset when the Flush API is called.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| clockid_t clockId | Clock identifier. Use **CLOCK_MONOTONIC**.|
| int64_t* framePosition | Pointer to a variable used to receive the position information.|
| int64_t* timestamp | Pointer to a variable used to receive the timestamp, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **clockId** parameter is set to an invalid value.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|

### OH_AudioRenderer_GetAudioTimestampInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)
```

**Description**

Obtains the timestamp and position information of the output audio stream, adapted to the speed change API.<br> Obtains the timestamp and position information of the output audio stream, which is usually used for audio-video synchronization alignment. The playback position is in samples, and the timestamp is in nanoseconds (ns).<br> When a device switch or a pause-resume occurs, because the playback path itself takes some time to recover, the playback position and timestamp obtained by calling this API will briefly remain in the state before the switch or pause.<br> This API is usually used to implement audio-video synchronization. It is recommended that the call frequency be lower than once every 200 ms, with a recommended frequency of once per minute. When the audio-video synchronization effect can be guaranteed, there is no need to query the timestamp frequently to avoid power consumption issues.

> **NOTE**
>
> - When the actual playback position (framePosition) is 0, the timestamp is a fixed value and is updated only when the stream actually starts running.
> - The playback position (framePosition) is in samples. The number of samples is calculated as the sampling rate multiplied by time. For example, when the sampling rate is 48000 Hz, the number of samples corresponding to 20 ms of audio data is 48000*0.02, that is, 960 sample points.
> - The actual playback position is also reset when the Flush API is called.
> - Before calling this function, ensure that the audio stream is in the running state and that at least one frame of data has been played successfully.
> - When the audio stream route changes, for example, when the device or the output type changes, the playback position may also be reset, but the timestamp continues to increase. It is recommended to use the values obtained by this API only after the changes of the actual playback position and timestamp become stable.
> - This API is adapted to the speed change API. For example, when the playback speed is set to 2x, the growth rate of the playback position is also returned as 2x the normal rate.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| int64_t* framePosition | Pointer to a variable used to receive the position information.|
| int64_t* timestamp | Pointer to a variable used to receive the timestamp, in nanoseconds.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **framePosition** or **timestamp** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The current stream status is invalid.<br>         **AUDIOSTREAM_ERROR_SYSTEM**:<br>                                          1. The system process breaks down or is blocked.<br>                                          2. An internal system error occurs.|

### OH_AudioRenderer_GetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)
```

**Description**

Obtains the frame size in the callback. The frame size is the fixed length of the buffer returned by each callback.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| int32_t* frameSize | Pointer to the variable used to receive the frame size. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)
```

**Description**

Obtains the rate of an audio renderer.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float* speed | Pointer to the variable that receives the playback rate.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)
```

**Description**

Sets the rate for an audio renderer.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float speed | Playback rate, which ranges from 0.25 to 4.0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetMarkPosition()

```c
OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)
```

**Description**

Sets the mark position for an audio renderer. When this function is called, the mark position that has been set will be overwritten.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| uint32_t samplePos | Mark position.|
| [OH_AudioRenderer_OnMarkReachedCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onmarkreachedcallback) callback | Callback invoked when the target mark position is reached.|
| void* userData | Pointer to the application data passed through the callbacks.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **samplePos** parameter is set to an invalid value.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.<br>         **AUDIOSTREAM_ERROR_SYSTEM**: A system error occurs.|

### OH_AudioRenderer_CancelMark()

```c
OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)
```

**Description**

Cancels the mark set by [OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)
```

**Description**

Sets the volume for an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float volume | Target volume, in the range of [0.0, 1.0].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **volume** parameter is set to an invalid value.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.<br>         **AUDIOSTREAM_ERROR_SYSTEM**: A system error occurs.|

### OH_AudioRenderer_SetVolumeWithRamp()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)
```

**Description**

Sets the volume with a ramp within the specified duration for an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float volume | Target volume, in the range of [0.0, 1.0].|
| int32_t durationMs | Duration, in milliseconds.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **volume** parameter is set to an invalid value.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.<br>         **AUDIOSTREAM_ERROR_SYSTEM**: A system error occurs.|

### OH_AudioRenderer_GetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)
```

**Description**

Obtains the volume of an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float* volume | Pointer to the variable used to receive the current audio stream volume. The value ranges from 0.0 to 1.0. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **volume** parameter is nullptr.|

### OH_AudioRenderer_GetUnderflowCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)
```

**Description**

Obtains the number of underloaded audio streams of an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| uint32_t* count | Pointer to a variable used to receive the number of underloaded audio streams.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **count** parameter is nullptr.|

### OH_AudioRenderer_GetChannelLayout()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)
```

**Description**

Obtains the channel layout of an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioChannelLayout](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)* channelLayout | Pointer to a variable used to receive the channel layout.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)
```

**Description**

Obtains the effect mode of an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_AudioEffectMode](capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode)* effectMode | Pointer to a variable used to receive the effect mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Sets the effect mode for an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_AudioEffectMode](capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode) effectMode | Effect mode to set.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)
```

**Description**

Checks whether the audio stream being played can be recorded by other applications.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_PrivacyType](capi-native-audiostream-base-h.md#oh_audiostream_privacytype)* privacy | Pointer to the privacy type, which specifies whether the audio stream being played can be recorded by other applications.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)
```

**Description**

Sets the silent mode in concurrent playback for an audio renderer.<br> If the silent mode in concurrent playback is enabled, the system mutes the audio stream and does not interrupt other audio streams. If the silent mode in concurrent playback is disabled, the audio stream can gain focus based on the system focus strategy.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| bool on | Status of the silent mode in concurrent playback.<br>     The value **true** means that the audio stream being played is muted and the playback of other audio streams is not interrupted.<br>     The value **false** means that the audio stream being played is unmuted and can gain focus based on the system focus strategy.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_GetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)
```

**Description**

Checks whether the silent mode in concurrent playback is enabled for an audio renderer.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| bool* on | Whether the silent mode in concurrent playback is enabled. **true** if enabled, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.|

### OH_AudioRenderer_SetDefaultOutputDevice()

```c
OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)
```

**Description**

Sets the default built-in audio output device.<br> This function applies only to the scenario where [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) is set to voice messages, VoIP voice calls, and VoIP video calls and the available device types are the receiver, speaker, and system default device.<br> This function can be called at any time after an AudioRenderer instance is created. The system records the default built-in audio output device set by the application. When the application is started, if an external device such as a Bluetooth or wired headset is connected, the system preferentially uses the external device to play sound. Otherwise, the system uses this default device to play sound.<br>

**Device behavior difference**: If the default audio output device is set to earpiece on a device without a earpiece, the speaker will still be used for audio output.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) deviceType | Device type. For details about the available options, see [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type). The device types that can be set are as follows:<br>                                             **AUDIO_DEVICE_TYPE_EARPIECE**: receiver.<br>                                             **AUDIO_DEVICE_TYPE_SPEAKER**: speaker.<br>                                             **AUDIO_DEVICE_TYPE_DEFAULT**: system default device.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | Result code.<br>         Returns AUDIOSTREAM_SUCCESS if the function is executed successfully.<br>         Returns AUDIOSTREAM_ERROR_INVALID_PARAM if:<br>                                                  1. The renderer parameter is nullptr.<br>                                                  2. The deviceType parameter is invalid.<br>         Returns AUDIOSTREAM_ERROR_ILLEGAL_STATE if the execution state is abnormal.<br>         Returns AUDIOSTREAM_ERROR_SYSTEM if a system error occurs. |

### OH_AudioRenderer_OnInterruptCallback()

```c
typedef void (*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)
```

**Description**

Defines the callback for interruption events of an audio renderer.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  void* userData | Pointer to the data storage area customized by the application.|
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | Type of force that causes audio interruption.|
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | Hint provided along with audio interruption.|

### OH_AudioRenderer_OnErrorCallback()

```c
typedef void (*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)
```

**Description**

Callback for the audio stream error event. It is triggered when an internal system fault occurs, such as an abnormal exit of the audio service, and is not caused by an application call.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  void* userData | Pointer to the data storage area customized by the application.|
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | Audio renderer error.|

### OH_AudioRenderer_GetFastStatus()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)
```

**Description**

Obtains the running status of an audio renderer to determine whether it is running in low-latency mode.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus)* status | Pointer to the running status.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The **renderer** parameter is nullptr.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The function is called in an incorrect state.|

### OH_AudioRenderer_OnFastStatusChange()

```c
typedef void (*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status
)
```

**Description**

Defines a callback function for low-latency status changes during audio playback.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| void* userData | Pointer to the data storage area customized by the application.|
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus) status | Current low-latency status. |

### OH_AudioRenderer_SetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)
```

**Description**

Sets the loudness of audio playback. The default loudness value is 0.0 dB. The audio stream playback type must be one of the following: Music: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC;<br> movies or videos: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE;<br> audiobooks (including books, crosstalk, and storytelling), audio news, podcasts, and others: [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio stream must be [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> Loudness settings are not supported for high-definition audio channels.<br> Due to the buffer between the audio framework and hardware, there may be a delay in the actual effect of loudness adjustment. The delay duration depends on the buffer length.<br> You are advised to set the loudness before starting playback of different audio streams to achieve the optimal balance effect.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float loudnessGain | Loudness, in the range [-90.0, 24.0], in dB.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr, or audio streams do not support setting the loudness.<br>                                                 2. The **loudnessGain** parameter is not within the allowed range.|

### OH_AudioRenderer_GetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)
```

**Description**

Obtains the loudness of audio playback.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| float* loudnessGain | Pointer to a variable that receives the playback loudness, in decibels.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **loudnessGain** parameter is nullptr.|

### OH_AudioRenderer_OnWriteDataCallbackAdvanced()

```c
typedef int32_t (*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**Description**

Defines a function pointer to the callback used to write audio data. Unlike **OH_AudioRenderer_OnWriteDataCallback**, this function allows the application to fill data of the length ranging [0, audioDataSize].<br> Here, **audioDataSize** refers to the length of the callback buffer. The caller notifies the system of the length of the data written through the return value.<br> If the return value is 0, the callback thread sleeps for a period of time.<br> Otherwise, the system may immediately initiate the next callback.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to the instance for which the callback occurs.|
|  void* userData | Pointer to the application data passed through the callbacks.|
|  void* audioData | Pointer to the audio data to be filled by the application.|
|  int32_t audioDataSize | Length of the audio data, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Length of the valid audio data actually filled by the application. The return value must be within the range [0, audioDataSize].<br> If the return value is less than 0, the system adjusts it to 0. If the return value is greater than audioDataSize, the system adjusts it to audioDataSize.<br> Note that the return value must be an integer multiple of the size of a single sample point.<br> For example, for dual-channel S16-format audio data, it must be an integer multiple of 4 (2 * 16 / 8).<br> Otherwise, playback noise may occur. |

### OH_AudioRenderer_GetLatency()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)
```

**Description**

Obtains the estimated latency of the current audio route, in milliseconds. For audio devices connected in wireless mode, the latency estimation may be inaccurate. The result is for reference only.<br> Since the latency is not counted in the real-time buffer, you are advised to obtain the latency only when audio playback starts. Frequent calls may block this API due to route switching.<br> After audio data is output to the hardware, you are advised to use [OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo) for audio-video synchronization.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [OH_AudioStream_LatencyType](capi-native-audiostream-base-h.md#oh_audiostream_latencytype) type | Latency type to be obtained.|
| int32_t* latencyMs | Pointer to the variable used to receive the latency, in milliseconds.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**:<br>                                                 1. The **renderer** parameter is nullptr.<br>                                                 2. The **latencyMs** parameter is nullptr.<br>                                                 3. The **type** parameter is invalid.<br>         **AUDIOSTREAM_ERROR_SYSTEM**: Internal system error, for example, abnormal audio service.|

### OH_AudioRenderer_SetIndependentAudioSessionStrategy()

```c
OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)
```

**Description**

Sets the independent audio session strategy and behavior parameters. If this API is called while an audio renderer is running, you must call the [OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start) API again for the settings to take effect.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
| [const OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md)* strategy | Pointer to the independent audio session policy.|
| uint32_t behavior | Audio session behavior flag. This can be a single flag or a bitwise OR combination of multiple flags. For details about the supported audio session behaviors, see [OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | **AUDIOSTREAM_SUCCESS**: The function is executed successfully.<br>         **AUDIOSTREAM_ERROR_INVALID_PARAM**: The parameter value is a null pointer or out of range.<br>         **AUDIOSTREAM_ERROR_ILLEGAL_STATE**: The execution status is abnormal.|


