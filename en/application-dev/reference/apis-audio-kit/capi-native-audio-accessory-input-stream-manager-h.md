# native_audio_accessory_input_stream_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=2682872f0f2f8e756a94a4840ecbd41e2087deeb translatedAt=2026-11-03T03:46:50.338Z pushedAt=2026-11-04T03:11:46.943Z nl=1 -->

## Overview

Declares the APIs related to the audio accessory input stream manager.

The APIs provided in this file are used to manage the input audio streams of audio accessories, including callback registration, audio data writing, and buffer query.

**File to include:** <ohaudio/native_audio_accessory_input_stream_manager.h>

**Library:** libohaudio.so

**System capability:** SystemCapability.Multimedia.Audio.Core

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

## Summary

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)](#oh_audioaccessory_openinputstreamcallback) | OH_AudioAccessory_OpenInputStreamCallback | Callback for opening the input stream of an audio accessory. |
| [typedef bool (\*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_startcallback) | OH_AudioAccessoryInputStream_StartCallback | Callback for the input stream start event. |
| [typedef bool (\*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_stopcallback) | OH_AudioAccessoryInputStream_StopCallback | Callback for the input stream stop event. |
| [typedef bool (\*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_releasecallback) | OH_AudioAccessoryInputStream_ReleaseCallback | Callback for the input stream release event. |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)](#oh_audioaccessoryinputstream_getlatencycallback) | OH_AudioAccessoryInputStream_GetLatencyCallback | Callback for querying the current latency of the input stream. |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)](#oh_audioaccessoryinputstream_getframepositioncallback) | OH_AudioAccessoryInputStream_GetFramePositionCallback | Callback for querying the current capture position of the input stream. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)](#oh_audioaccessoryinputstreammanager_registerstartcallback) | - | Registers the callback for the input stream start event. When an application needs to capture audio through the audio accessory input stream, it must register this callback. If it is not registered, the audio system will refuse to create the input stream and clean up related resources. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)](#oh_audioaccessoryinputstreammanager_registerstopcallback) | - | Registers the callback for the input stream stop event. When an application needs to capture audio through the audio accessory input stream, it must register this callback. If it is not registered, the audio system will refuse to create the input stream and clean up related resources. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)](#oh_audioaccessoryinputstreammanager_registerreleasecallback) | - | Registers the callback for the input stream release event. When an application needs to capture audio through the audio accessory input stream, it must register this callback. If it is not registered, the audio system will refuse to create the input stream and clean up related resources. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)](#oh_audioaccessoryinputstreammanager_registerlatencycallback) | - | Registers the callback for querying the input stream latency. When an application needs to capture audio through the audio accessory input stream, it must register this callback. If it is not registered, the audio system will refuse to create the input stream and clean up related resources. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)](#oh_audioaccessoryinputstreammanager_registerframepositioncallback) | - | Registers the callback for querying the input stream frame position, which is used to query the current capture position of the input stream. When an application needs to capture audio through the audio accessory input stream, it must register this callback. If it is not registered, the audio system will refuse to create the input stream and clean up related resources. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)](#oh_audioaccessoryinputstreammanager_write) | - | Writes audio data to the audio accessory input stream. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)](#oh_audioaccessoryinputstreammanager_getwritablesize) | - | Obtains the writable size of the audio accessory input stream buffer. |

## Function Description

### OH_AudioAccessory_OpenInputStreamCallback()

```c
typedef bool (*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)
```

**Description**

Callback function for opening an input stream of an audio accessory.

Trigger timing: When an application requests to capture audio from this audio accessory, the audio system invokes this callback. The system passes the information of the input stream being opened so that the accessory can prepare the corresponding audio data transmission channel.

Usage requirements: In this callback, you need to register the callbacks for starting, stopping, releasing, querying the latency, and querying the frame position of the input stream. These input stream callbacks can be registered only during the execution of this callback.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory whose input stream is being opened. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Handle of the newly created input stream. Use this handle to register the callbacks related to the input stream. |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Pointer to the audio stream information of the input stream being opened. This parameter describes the requested stream format,<br>and the accessory can use this information to configure the audio data transmission channel. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if the stream is opened successfully.<br>false if the stream fails to be opened. |

### OH_AudioAccessoryInputStream_StartCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback function for the input stream start event.

Trigger timing: triggered after the input stream is successfully started and ready to receive audio data. After this callback returns, you can call OH_AudioAccessoryInputStreamManager_Write to send audio data.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory to which this input stream belongs. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Handle of the started input stream. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if the start event is processed successfully; false otherwise. |

### OH_AudioAccessoryInputStream_StopCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback function for the input stream stop event.

Trigger timing: triggered after the input stream stops. After this callback returns, calling OH_AudioAccessoryInputStreamManager_Write should be stopped. The input stream handle remains valid and can be started again.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory to which this input stream belongs. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Handle of the stopped input stream. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if the stop event is processed successfully; false otherwise. |

### OH_AudioAccessoryInputStream_ReleaseCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback function for the input stream release event.

Trigger timing: triggered when the input stream is releasing resources. This is the last callback of this input stream. After this callback returns, the input stream handle is no longer valid and must not be used further.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory to which this input stream belongs. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Handle of the input stream (recording/capture stream) to be released. |

**Return**

| Type | Description |
| -- | -- |
| bool | true: the release event is processed successfully.<br>false: the release event fails to be processed. |

### OH_AudioAccessoryInputStream_GetLatencyCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)
```

**Description**

Callback function for querying the current latency of the input stream.

Trigger timing: triggered when the system needs to obtain the current latency value of the audio accessory input stream.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory to which this input stream belongs. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Input stream handle. |
| int32_t *latency | Output parameter, which returns the latency value in milliseconds (ms). |

**Return**

| Type | Description |
| -- | -- |
| bool | true if the latency is obtained successfully; false otherwise. |

### OH_AudioAccessoryInputStream_GetFramePositionCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)
```

**Description**

Callback function for querying the current capture position of the input stream.

Trigger timing: triggered when the system needs to obtain the current capture position of the input stream on the audio accessory (external audio device).

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | Audio accessory (external audio device) to which this input stream belongs. |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Input stream handle. |
| int64_t *framePosition | Output parameter, which returns the total number of audio frames captured since the last successful start of this input stream. |
| int64_t *timestamp | Output parameter, which returns the capture timestamp corresponding to framePosition.<br>The timestamp must use the CLOCK_MONOTONIC time base, in nanoseconds (ns),<br>indicating the point in time when the audio frame was captured. |

**Return**

| Type | Description |
| -- | -- |
| bool | true: the frame position is obtained successfully.<br>false: the frame position fails to be obtained. |

### OH_AudioAccessoryInputStreamManager_RegisterStartCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)
```

**Description**

Registers the callback function for the input stream start event. When an application needs to capture audio through the audio accessory input stream, it needs to register this callback. If not registered, the audio system will refuse to create the input stream and clean up related resources.

> **NOTE**
>
> - This function needs to be called during the execution of OH_AudioAccessory_OpenInputStreamCallback.
> - Calling this function at other times will return AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| OH_AudioAccessoryInputStream_StartCallback callback | Pointer to the callback function, which must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: function execution succeeded.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter is null.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: not called during the execution of OH_AudioAccessory_OpenInputStreamCallback, or the input stream has already been released. |

### OH_AudioAccessoryInputStreamManager_RegisterStopCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)
```

**Description**

Registers the callback function for the input stream stop event. When an application needs to capture audio data through the audio accessory input stream, it needs to register this callback. If not registered, the audio system will refuse to create the input stream and clean up related resources.

> **NOTE**
>
> - This function needs to be called during execution of OH_AudioAccessory_OpenInputStreamCallback.
> - Calling this function at other times will return AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| OH_AudioAccessoryInputStream_StopCallback callback | Callback for the input stream stop event. It must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution succeeds.<br>Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if a parameter is null.<br>Returns AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE if the function is not called during execution of OH_AudioAccessory_OpenInputStreamCallback, or the input stream is already released. |

### OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)
```

**Description**

Registers the input stream release event callback function. When an application needs to capture audio data through an audio accessory input stream, it needs to register this callback. If not registered, the audio system will refuse to create the input stream and clean up related resources.

> **NOTE**
>
> - This function needs to be called during the execution of OH_AudioAccessory_OpenInputStreamCallback.
> - Calling this function at other times will return AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| OH_AudioAccessoryInputStream_ReleaseCallback callback | Pointer to the callback function, which must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution succeeds.<br>Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if a parameter is null.<br>Returns AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE if the function is not called during the execution of OH_AudioAccessory_OpenInputStreamCallback, or if the input stream has already been released. |

### OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)
```

**Description**

Registers the callback function for querying the input stream latency. When an application needs to capture audio through an audio accessory input stream, it needs to register this callback. If not registered, the audio system will refuse to create the input stream and clean up related resources.

> **NOTE**
>
> - This function needs to be called during the execution of OH_AudioAccessory_OpenInputStreamCallback.
> - Calling this function at other times will return AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| OH_AudioAccessoryInputStream_GetLatencyCallback callback | Pointer to the callback function, which must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: function execution success.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter is null.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: not called during the execution of OH_AudioAccessory_OpenInputStreamCallback, or the input stream has already been released. |

### OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)
```

**Description**

Registers the input stream frame position query callback function, which is used to query the current sampling position of the input stream. When an application needs to capture audio data through an audio accessory input stream, it needs to register this callback. If not registered, the audio system will refuse to create the input stream and clean up related resources.

> **NOTE**
>
> - This function needs to be called during the execution of OH_AudioAccessory_OpenInputStreamCallback.
> - Calling this function at other times will return AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| OH_AudioAccessoryInputStream_GetFramePositionCallback callback | Callback function pointer, which must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: function execution succeeds.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter is null.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: not called during the execution of OH_AudioAccessory_OpenInputStreamCallback, or the input stream has already been released. |

### OH_AudioAccessoryInputStreamManager_Write()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)
```

**Description**

Writes audio data to the audio accessory input stream.

> **NOTE**
>
> - After this function is called, it returns after a frame of audio data is written successfully or an error occurs.
> - Each call must write complete 20 ms audio data. The caller must ensure that dataSize is consistent with the number of bytes corresponding to 20 ms audio data under the current input stream configuration. If the audio data frame length does not match the current input stream configuration, this function returns AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH.
> - The caller must call this function at 20 ms intervals, that is, submit 20 ms audio data each time, and the interval between two consecutive calls must also be 20 ms.
> - If the input stream buffer currently does not have enough writable space to accommodate one frame of data, this function waits until the writable space meets the requirement or returns an error.
> - This function does not support partial frame writing.
> - If the last frame has less than 20 ms audio data, the caller can discard the frame or pad it with zeros to 20 ms before calling this function.

Concurrency limit

Concurrent calls to this function on the same input stream are not supported. It is recommended that the caller use only one thread to write audio data to the same input stream serially. If this function is called concurrently with the stop or release callback of the same input stream, and the stop or release operation completes first, this function returns AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| const uint8_t *data | Pointer to the audio data buffer, which must not be null. |
| uint32_t dataSize | Size of the audio data, in bytes, which must be greater than 0. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>AUDIOCOMMON_RESULT_SUCCESS: function execution succeeds.<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter is null.<br>AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH: audio data frame length does not match the current input stream configuration.<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: input stream is not started or the required stream callbacks are not all registered.<br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: audio service process is dead. |

### OH_AudioAccessoryInputStreamManager_GetWritableSize()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)
```

**Description**

Obtains the writable size of the audio accessory input stream buffer.

> **NOTE**
>
> - The caller can use this function to query the available space in the current buffer before calling OH_AudioAccessoryInputStreamManager_Write.
> - The returned writable size only reflects the state at the time of the query and may change immediately after the function returns.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | Pointer to the input stream handle. |
| uint32_t *writableSize | Output parameter, which returns the writable size, in bytes. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution succeeds.<br>Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if a parameter is null.<br>Returns AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE if the input stream has already been released. |
