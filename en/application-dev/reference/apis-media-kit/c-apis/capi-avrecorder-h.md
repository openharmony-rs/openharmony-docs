# avrecorder.h

## Overview

The file declares the AVRecorder APIs. Applications can use the APIs to record media data.

**Library**: libavrecorder.so

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_AVRecorder *OH_AVRecorder_Create(void)](#oh_avrecorder_create) | Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. |
| [OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)](#oh_avrecorder_prepare) | Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](capi-avrecorder-h.md#oh_avrecorder_create) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PREPARED state. To record only audio, you do not need to set video parameters. Similarly, to record only video, you do not need to set audio parameters. |
| [OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)](#oh_avrecorder_getavrecorderconfig) | Obtains the AVRecorder configuration. This function must be called after the recording preparation is complete. **config** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing. |
| [OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)](#oh_avrecorder_getinputsurface) | Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. The caller obtains the **surfaceBuffer** from this surface and fills in the corresponding video data. |
| [OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)](#oh_avrecorder_updaterotation) | Updates the video rotation angle. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. |
| [OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)](#oh_avrecorder_start) | Starts recording. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state. |
| [OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)](#oh_avrecorder_pause) | Pauses recording. This function must be called after [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is successfully triggered and the AVRecorder is in the AVRECORDER_STARTED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PAUSED state. Then, you can call [OH_AVRecorder_Resume](capi-avrecorder-h.md#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions the AVRECORDER_STARTED state again. |
| [OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)](#oh_avrecorder_resume) | Resumes recording. This function must be called after [OH_AVRecorder_Pause](capi-avrecorder-h.md#oh_avrecorder_pause) is successfully triggered and the AVRecorder is in the AVRECORDER_PAUSED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state. |
| [OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)](#oh_avrecorder_stop) | Stops recording. This function must be called after [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STOPPED state. For audio-only recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) again for re-recording. For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](capi-avrecorder-h.md#oh_avrecorder_getinputsurface) again for re-recording. |
| [OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)](#oh_avrecorder_reset) | Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. For audio-only recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) again for re-recording. For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](capi-avrecorder-h.md#oh_avrecorder_getinputsurface) again for re-recording. |
| [OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)](#oh_avrecorder_release) | Releases recording resources. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_RELEASED state. The recorder memory will be released. The application layer must explicitly set the recorder to nullptr to avoid access to wild pointers. After the resources are released, you can no longer perform any operation on the OH_AVRecorder instance. |
| [OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info, int32_t *length)](#oh_avrecorder_getavailableencoder) | Obtains the available encoders and encoder information of the AVRecorder. **info** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing. |
| [OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)](#oh_avrecorder_setstatecallback) | Sets a state callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. |
| [OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)](#oh_avrecorder_seterrorcallback) | Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. |
| [OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)](#oh_avrecorder_seturicallback) | Sets a URI callback so that the application can respond to URI events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. |
| [OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)](#oh_avrecorder_setwillmutewheninterrupted) | Sets whether to enable the mute interruption mode. |
| [OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t* amplitude)](#oh_avrecorder_getaudiocapturermaxamplitude) | Obtains the maximum amplitude of the current audio capturer. The amplitude value is the max value from the last call to the current call. For example, if you have obtained the maximum amplitude at 1s, and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.<br> This API can be called only after the **prepare()** API is called. If this API is called after **stop()** is successfully called, an error is reported. |
| [OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)](#oh_avrecorder_setmetadata) | Set metadata (key-value pairs) for the recording file of the recorder. This metadata overwrites the value in config.metadata.customInfo (see {prepare()} and {OH_AVRecorder_Config}) if they have same key. This API can be called only after the **prepare()** API is called, before stop recorder. |

## Function description

### OH_AVRecorder_Create()

```c
OH_AVRecorder *OH_AVRecorder_Create(void)
```

**Description**

Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state.

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVRecorder * | Pointer to the OH_AVRecorder instance created if the operation is successful; nullptr otherwise. |

### OH_AVRecorder_Prepare()

```c
OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)
```

**Description**

Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](capi-avrecorder-h.md#oh_avrecorder_create) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PREPARED state. To record only audio, you do not need to set video parameters. Similarly, to record only video, you do not need to set audio parameters.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_Config *config | Pointer to the OH_AVRecorder_Config instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or the preparation fails. |

### OH_AVRecorder_GetAVRecorderConfig()

```c
OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)
```

**Description**

Obtains the AVRecorder configuration. This function must be called after the recording preparation is complete. **config** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_Config **config | Pointer to the OH_AVRecorder_Config instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or config is not nullptr.<br>{@link AV_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory. |

### OH_AVRecorder_GetInputSurface()

```c
OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)
```

**Description**

Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called. The caller obtains the **surfaceBuffer** from this surface and fills in the corresponding video data.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OHNativeWindow **window | Pointer to the OHNativeWindow instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr. |

### OH_AVRecorder_UpdateRotation()

```c
OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)
```

**Description**

Updates the video rotation angle. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| int32_t rotation | Video rotation angle, in degrees. The value must be an integer in the range [0, 90, 180, 270]. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr, rotation is invalid, or the update  operation fails. |

### OH_AVRecorder_Start()

```c
OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)
```

**Description**

Starts recording. This function must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to start. |

### OH_AVRecorder_Pause()

```c
OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)
```

**Description**

Pauses recording. This function must be called after [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is successfully triggered and the AVRecorder is in the AVRECORDER_STARTED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PAUSED state. Then, you can call [OH_AVRecorder_Resume](capi-avrecorder-h.md#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions the AVRECORDER_STARTED state again.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to pause. |

### OH_AVRecorder_Resume()

```c
OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)
```

**Description**

Resumes recording. This function must be called after [OH_AVRecorder_Pause](capi-avrecorder-h.md#oh_avrecorder_pause) is successfully triggered and the AVRecorder is in the AVRECORDER_PAUSED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to resume. |

### OH_AVRecorder_Stop()

```c
OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)
```

**Description**

Stops recording. This function must be called after [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STOPPED state. For audio-only recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) again for re-recording. For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](capi-avrecorder-h.md#oh_avrecorder_getinputsurface) again for re-recording.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to stop. |

### OH_AVRecorder_Reset()

```c
OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)
```

**Description**

Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. For audio-only recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) again for re-recording. For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](capi-avrecorder-h.md#oh_avrecorder_getinputsurface) again for re-recording.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to reset. |

### OH_AVRecorder_Release()

```c
OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)
```

**Description**

Releases recording resources. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_RELEASED state. The recorder memory will be released. The application layer must explicitly set the recorder to nullptr to avoid access to wild pointers. After the resources are released, you can no longer perform any operation on the OH_AVRecorder instance.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr or recording fails to release. |

### OH_AVRecorder_GetAvailableEncoder()

```c
OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info, int32_t *length)
```

**Description**

Obtains the available encoders and encoder information of the AVRecorder. **info** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_EncoderInfo **info | Pointer to the OH_AVRecorder_EncoderInfo instance. |
| int32_t *length | Pointer to the number of available encoders. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder is nullptr.<br>{@link AV_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory. |

### OH_AVRecorder_SetStateCallback()

```c
OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)
```

**Description**

Sets a state callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_OnStateChange callback | Status callback function. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder or callback is nullptr. |

### OH_AVRecorder_SetErrorCallback()

```c
OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)
```

**Description**

Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_OnError callback | Error callback function. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder or callback is nullptr. |

### OH_AVRecorder_SetUriCallback()

```c
OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)
```

**Description**

Sets a URI callback so that the application can respond to URI events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) is called.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| OH_AVRecorder_OnUri callback | Callback used to return the result. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder or callback is nullptr. |

### OH_AVRecorder_SetWillMuteWhenInterrupted()

```c
OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)
```

**Description**

Sets whether to enable the mute interruption mode.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to the OH_AVRecorder instance. |
| bool muteWhenInterrupted | Sets whether to enable the mute interruption mode. The value **true** indicates that the application remains muted instead of being interrupted when recording is required. The value **false** indicates that the application stops recording instead of remain muted when the recording is interrupted. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>{@link AV_ERR_INVALID_VAL}: The input parameter recorder or callback is nullptr.<br>{@link AV_ERR_INVALID_STATE}: The function is called in an invalid state. It must be in the prepared state. |

### OH_AVRecorder_GetAudioCapturerMaxAmplitude()

```c
OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t* amplitude)
```

**Description**

Obtains the maximum amplitude of the current audio capturer. The amplitude value is the max value from the last call to the current call. For example, if you have obtained the maximum amplitude at 1s, and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.<br> This API can be called only after the **prepare()** API is called. If this API is called after **stop()** is successfully called, an error is reported.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to an OH_AVRecorder instance |
| int32_t* amplitude | The max amplitude value of audio capturer |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.          {@link AV_ERR_OK}: the execution is successful.<br>        {@link AV_ERR_INVALID_VAL}: input recorder is nullptr or amplitude is nullptr.<br>        {@link AV_ERR_INVALID_STATE}: function called in invalid state.<br>        {@link AV_ERR_NO_MEMORY}: failed to malloc memory.<br>        {@link AV_ERR_UNKNOWN}: unknown error. |

### OH_AVRecorder_SetMetadata()

```c
OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)
```

**Description**

Set metadata (key-value pairs) for the recording file of the recorder. This metadata overwrites the value in config.metadata.customInfo (see {prepare()} and {OH_AVRecorder_Config}) if they have same key. This API can be called only after the **prepare()** API is called, before stop recorder.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVRecorder *recorder | Pointer to an OH_AVRecorder instance |
| const OH_AVFormat *metadata | The key-value pairs added to the the recording file. The key string should start with "com.openharmony.", the length of value can't be more than 256 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.          {@link AV_ERR_OK}: the execution is successful.<br>        {@link AV_ERR_INVALID_VAL}: input recorder is nullptr or metadata is nullptr<br>                                    or the length of value exceed max length.<br>        {@link AV_ERR_INVALID_STATE}: function called in invalid state.<br>        {@link AV_ERR_NO_MEMORY}: failed to malloc memory.<br>        {@link AV_ERR_UNKNOWN}: unknown error. |


