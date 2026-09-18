# native_audio_accessory_input_stream_manager.h

## Overview

Declare audio accessory input stream manager related interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)](#oh_audioaccessory_openinputstreamcallback) | OH_AudioAccessory_OpenInputStreamCallback | Callback for opening an input stream on an audio accessory.<br> <b>When Called:</b> The audio framework calls this callback when an application requests audio capture from this audio accessory. The framework passes the audio stream information of the stream being opened, so the accessory can prepare the corresponding data path.<br> <b>Usage Requirements:</b> In this callback, you MUST call [OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback), [OH_AudioAccessoryInputStreamManager_RegisterStopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstopcallback), [OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerreleasecallback), [OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerlatencycallback), and [OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerframepositioncallback) to register required stream callbacks. This is the ONLY time when callback registration is allowed. |
| [typedef bool (\*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_startcallback) | OH_AudioAccessoryInputStream_StartCallback | Callback for stream started event.<br> <b>When Called:</b> After the stream is successfully started and ready to receive audio data. After this callback returns, you may call Write() to send audio data. |
| [typedef bool (\*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_stopcallback) | OH_AudioAccessoryInputStream_StopCallback | Callback for stream stopped event.<br> <b>When Called:</b> After the stream is stopped. After this callback returns, you must stop calling Write(). The stream handle remains valid and may be started again. |
| [typedef bool (\*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_releasecallback) | OH_AudioAccessoryInputStream_ReleaseCallback | Callback for stream released event.<br> <b>When Called:</b> When the stream is being released. This is always the last callback for a stream. After this callback returns, the stream handle is no longer valid and must not be used. |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)](#oh_audioaccessoryinputstream_getlatencycallback) | OH_AudioAccessoryInputStream_GetLatencyCallback | Callback for querying the current latency of the stream.<br> <b>When Called:</b> When the framework needs the current latency value reported by the accessory stream. |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)](#oh_audioaccessoryinputstream_getframepositioncallback) | OH_AudioAccessoryInputStream_GetFramePositionCallback | Callback for querying the current frame position of the stream.<br> <b>When Called:</b> When the framework needs the current capture position reported by the accessory stream. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)](#oh_audioaccessoryinputstreammanager_registerstartcallback) | - | Registers the callback for stream started event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)](#oh_audioaccessoryinputstreammanager_registerstopcallback) | - | Registers the callback for stream stopped event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)](#oh_audioaccessoryinputstreammanager_registerreleasecallback) | - | Registers the callback for stream released event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)](#oh_audioaccessoryinputstreammanager_registerlatencycallback) | - | Registers the callback for stream latency query.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)](#oh_audioaccessoryinputstreammanager_registerframepositioncallback) | - | Registers the callback for stream frame position query.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)](#oh_audioaccessoryinputstreammanager_write) | - | Writes audio data to the audio accessory input stream.<br> This is a blocking interface. After being called, the function blocks until the whole frame is written successfully or an error occurs. Each call must write exactly 20 ms of audio data. The caller must ensure that dataSize matches the byte count corresponding to 20 ms under the current stream configuration. If dataSize does not match 20 ms of audio data, this function returns {@link AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH}.<br>The caller must invoke this function at a 20 ms cadence. That is, each call<br>must submit 20 ms of audio data, and the interval between two consecutive<br>calls must also be 20 ms.<br>If the stream buffer does not currently have enough writable space for the<br>whole frame, this function blocks until enough space becomes available or an<br>error occurs. Partial-frame writes are not supported by this interface. If<br>the last frame has less than 20 ms of audio data, the caller may discard<br>this frame or pad it with zeros to 20 ms before calling this function.<br><b>Calling Context and Concurrency:</b><br>This function is not reentrant for the same stream. The caller is advised<br>to use only one thread to write audio data serially to the same stream.<br>If this function is called concurrently with the stop or release callback<br>for the same stream, it returns<br>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if the stop or release operation completes before this function acquires the lock. |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)](#oh_audioaccessoryinputstreammanager_getwritablesize) | - | Obtains the writable size of the audio accessory input stream buffer.<br> This function can be used by the caller to probe current buffer availability before calling [OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write). The returned writable size reflects the current state only, and may change immediately after the function returns. |

### Variable

| Name | Description |
| -- | -- |
| bool (*OH_AudioAccessory_OpenInputStreamCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo) | Callback for opening an input stream on an audio accessory.<br> <b>When Called:</b> The audio framework calls this callback when an application requests audio capture from this audio accessory. The framework passes the audio stream information of the stream being opened, so the accessory can prepare the corresponding data path.<br> <b>Usage Requirements:</b> In this callback, you MUST call [OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback), [OH_AudioAccessoryInputStreamManager_RegisterStopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstopcallback), [OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerreleasecallback), [OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerlatencycallback), and [OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerframepositioncallback) to register required stream callbacks. This is the ONLY time when callback registration is allowed.<br>**Since**: 26.0.0 |
| bool (*OH_AudioAccessoryInputStream_StartCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream) | Callback for stream started event.<br> <b>When Called:</b> After the stream is successfully started and ready to receive audio data. After this callback returns, you may call Write() to send audio data.<br>**Since**: 26.0.0 |
| bool (*OH_AudioAccessoryInputStream_StopCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream) | Callback for stream stopped event.<br> <b>When Called:</b> After the stream is stopped. After this callback returns, you must stop calling Write(). The stream handle remains valid and may be started again.<br>**Since**: 26.0.0 |
| bool (*OH_AudioAccessoryInputStream_ReleaseCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream) | Callback for stream released event.<br> <b>When Called:</b> When the stream is being released. This is always the last callback for a stream. After this callback returns, the stream handle is no longer valid and must not be used.<br>**Since**: 26.0.0 |
| bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency) | Callback for querying the current latency of the stream.<br> <b>When Called:</b> When the framework needs the current latency value reported by the accessory stream.<br>**Since**: 26.0.0 |
| bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)( OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp) | Callback for querying the current frame position of the stream.<br> <b>When Called:</b> When the framework needs the current capture position reported by the accessory stream.<br>**Since**: 26.0.0 |

## Function description

### OH_AudioAccessory_OpenInputStreamCallback()

```c
typedef bool (*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)
```

**Description**

Callback for opening an input stream on an audio accessory.<br> <b>When Called:</b> The audio framework calls this callback when an application requests audio capture from this audio accessory. The framework passes the audio stream information of the stream being opened, so the accessory can prepare the corresponding data path.<br> <b>Usage Requirements:</b> In this callback, you MUST call [OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback), [OH_AudioAccessoryInputStreamManager_RegisterStopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstopcallback), [OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerreleasecallback), [OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerlatencycallback), and [OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerframepositioncallback) to register required stream callbacks. This is the ONLY time when callback registration is allowed.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory on which the stream is opened. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the newly created input stream. Use this handle to register callbacks via Register...Callback. |
| OH_AudioStreamInfo \*streamInfo | [in] Pointer to the audio stream information of the stream being opened. This parameter describes the requested stream format and can be used by the accessory to configure its data path. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the stream is accepted.</li>          <li>`false` otherwise.</li>          </ul> |

**Reference**:

[OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback)


### OH_AudioAccessoryInputStream_StartCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback for stream started event.<br> <b>When Called:</b> After the stream is successfully started and ready to receive audio data. After this callback returns, you may call Write() to send audio data.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory that owns this stream. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the input stream that is started. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the start event is handled successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioAccessoryInputStream_StopCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback for stream stopped event.<br> <b>When Called:</b> After the stream is stopped. After this callback returns, you must stop calling Write(). The stream handle remains valid and may be started again.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory that owns this stream. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the input stream that is stopped. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the stop event is handled successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioAccessoryInputStream_ReleaseCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**Description**

Callback for stream released event.<br> <b>When Called:</b> When the stream is being released. This is always the last callback for a stream. After this callback returns, the stream handle is no longer valid and must not be used.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory that owns this stream. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the input stream that is released. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the release event is handled successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioAccessoryInputStream_GetLatencyCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)
```

**Description**

Callback for querying the current latency of the stream.<br> <b>When Called:</b> When the framework needs the current latency value reported by the accessory stream.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory that owns this stream. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the input stream. |
| int32_t \*latency | [out] Output parameter. Returns the latency, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the latency is obtained successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioAccessoryInputStream_GetFramePositionCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)
```

**Description**

Callback for querying the current frame position of the stream.<br> <b>When Called:</b> When the framework needs the current capture position reported by the accessory stream.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessory \*accessory | [in] The audio accessory that owns this stream. |
| OH_AudioAccessoryInputStream \*stream | [in] Reference to the input stream. |
| int64_t \*framePosition | [out] Output parameter. Returns the cumulative number of audio frames captured since the most recent successful start of this input stream. |
| int64_t \*timestamp | [out] Returns the capture timestamp corresponding to the frame position reported through {@p framePosition}. The timestamp must use the<br>    {@link CLOCK_MONOTONIC} time base and is expressed in nanoseconds. It represents<br>    the monotonic clock time at which the frame identified by {@p framePosition} was captured. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul>          <li>`true` if the frame position is obtained successfully.</li>          <li>`false` otherwise.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStartCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)
```

**Description**

Registers the callback for stream started event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| [OH_AudioAccessoryInputStream_StartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_startcallback) callback | [in] Pointer to the callback function. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if called outside                   [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) or stream is released.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStopCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)
```

**Description**

Registers the callback for stream stopped event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| [OH_AudioAccessoryInputStream_StopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_stopcallback) callback | [in] Pointer to the callback function. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if called outside                   [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) or stream is released.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)
```

**Description**

Registers the callback for stream released event.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| [OH_AudioAccessoryInputStream_ReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_releasecallback) callback | [in] Pointer to the callback function. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if called outside                   [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) or stream is released.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)
```

**Description**

Registers the callback for stream latency query.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| [OH_AudioAccessoryInputStream_GetLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getlatencycallback) callback | [in] Pointer to the callback function. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if called outside                   [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) or stream is released.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)
```

**Description**

Registers the callback for stream frame position query.<br> <b>CRITICAL: Registration Timing Constraint</b><br> This function MUST be called ONLY during the execution of [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback). Calling this function at any other time will result in {@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE}.<br> <b>Requirement:</b> This callback is MANDATORY. If not registered, the framework will reject the stream creation and trigger cleanup.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| [OH_AudioAccessoryInputStream_GetFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getframepositioncallback) callback | [in] Pointer to the callback function. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if called outside                   [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) or stream is released.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_Write()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)
```

**Description**

Writes audio data to the audio accessory input stream.<br> This is a blocking interface. After being called, the function blocks until the whole frame is written successfully or an error occurs. Each call must write exactly 20 ms of audio data. The caller must ensure that dataSize matches the byte count corresponding to 20 ms under the current stream configuration. If dataSize does not match 20 ms of audio data, this function returns {@link AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH}.<br>The caller must invoke this function at a 20 ms cadence. That is, each call<br>must submit 20 ms of audio data, and the interval between two consecutive<br>calls must also be 20 ms.<br>If the stream buffer does not currently have enough writable space for the<br>whole frame, this function blocks until enough space becomes available or an<br>error occurs. Partial-frame writes are not supported by this interface. If<br>the last frame has less than 20 ms of audio data, the caller may discard<br>this frame or pad it with zeros to 20 ms before calling this function.<br><b>Calling Context and Concurrency:</b><br>This function is not reentrant for the same stream. The caller is advised<br>to use only one thread to write audio data serially to the same stream.<br>If this function is called concurrently with the stop or release callback<br>for the same stream, it returns<br>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if the stop or release operation completes before this function acquires the lock.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| const uint8_t *data | [in] Pointer to the audio data buffer. Must not be null. |
| uint32_t dataSize | [in] Size of the audio data in bytes. Must be > 0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH} if dataSize does not correspond<br>                 to 20 ms of audio data under the current stream configuration.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if stream is not started or the required<br>                 stream callbacks are not fully registered.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} if audio server process die.</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_GetWritableSize()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)
```

**Description**

Obtains the writable size of the audio accessory input stream buffer.<br> This function can be used by the caller to probe current buffer availability before calling [OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write). The returned writable size reflects the current state only, and may change immediately after the function returns.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioAccessoryInputStream *stream | [in] Pointer to the input stream handle. |
| uint32_t *writableSize | [out] Output parameter. Returns the number of bytes that can be written. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameters are null.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} if the stream is released.</li>          </ul> |


