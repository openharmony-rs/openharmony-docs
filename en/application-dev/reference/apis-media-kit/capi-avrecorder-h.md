# avrecorder.h

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:05:37.789Z pushedAt=2026-06-23T06:12:23.693Z -->

## Overview

The file declares the AVRecorder APIs. Applications can use the APIs to record media data.

**File to include**: <multimedia/player_framework/avrecorder.h>

**Library**: libavrecorder.so

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_AVRecorder *OH_AVRecorder_Create(void)](#oh_avrecorder_create) | Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state.|
| [OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)](#oh_avrecorder_prepare) | Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](#oh_avrecorder_create) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PREPARED state.<br>To record only audio, you do not need to set video parameters. Similarly, to record only video, you do not need to set audio parameters.|
| [OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)](#oh_avrecorder_getavrecorderconfig) | Obtains the AVRecorder configuration. This function must be called after the recording preparation is complete. **config** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.|
| [OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)](#oh_avrecorder_getinputsurface) | Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.<br>The caller obtains the **surfaceBuffer** from this surface and fills in the corresponding video data.|
| [OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)](#oh_avrecorder_updaterotation) | Updates the video rotation angle. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.|
| [OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)](#oh_avrecorder_start) | Starts recording. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.|
| [OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)](#oh_avrecorder_pause) | Pauses recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is successfully triggered and the AVRecorder is in the AVRECORDER_STARTED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PAUSED state.<br>Then, you can call [OH_AVRecorder_Resume](#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions to the AVRECORDER_STARTED state again.|
| [OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)](#oh_avrecorder_resume) | Resumes recording. This function must be called after [OH_AVRecorder_Pause](#oh_avrecorder_pause) is successfully triggered and the AVRecorder is in the AVRECORDER_PAUSED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.|
| [OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)](#oh_avrecorder_stop) | Stops recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STOPPED state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.|
| [OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)](#oh_avrecorder_reset) | Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.|
| [OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)](#oh_avrecorder_release) | Releases recording resources. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_RELEASED state.<br>The recorder memory will be released. The application layer must explicitly set the recorder to nullptr to avoid accessing to wild pointers. After the resources are released, you can no longer perform any operation on the OH_AVRecorder instance.|
| [OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info, int32_t *length)](#oh_avrecorder_getavailableencoder) | Obtains the available encoders and encoder information of the AVRecorder.<br>**info** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.|
| [OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)](#oh_avrecorder_setstatecallback) | Sets a state callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.|
| [OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)](#oh_avrecorder_seterrorcallback) | Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.|
| [OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)](#oh_avrecorder_seturicallback) | Sets a URI callback so that the application can respond to URI events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.|
| [OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)](#oh_avrecorder_setwillmutewheninterrupted) | Sets whether to enable the mute interruption mode.|
| [OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t *amplitude)](#oh_avrecorder_getaudiocapturermaxamplitude) | Obtains the maximum amplitude of the current audio capturer. The return value is the maximum amplitude between the last two calls. For example, if the maximum amplitude is obtained once at 1s and then the method is called again at 2s, the return value is the maximum amplitude between 1s and 2s.<br> This method must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop).|
| [OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)](#oh_avrecorder_setmetadata) | Sets the metadata information for recording. If the same key exists in both the metadata parameter and **config.metadata.customInfo** (refer to [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md)), the corresponding value in the former will overwrite that in the latter.<br> This method can only be called after the **OH_AVRecorder_Prepare** method call, and must be called before the [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop) method. |

## Function Description

### OH_AVRecorder_Create()

```c
OH_AVRecorder *OH_AVRecorder_Create(void)
```

**Description**

Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) | Pointer to the OH_AVRecorder instance created if the operation is successful; nullptr otherwise.|

### OH_AVRecorder_Prepare()

```c
OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)
```

**Description**

Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](#oh_avrecorder_create) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PREPARED state.<br>To record only audio, you do not need to set video parameters. Similarly, to record only video, you do not need to set audio parameters.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) *config | Pointer to the OH_AVRecorder_Config instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or the preparation fails.|

### OH_AVRecorder_GetAVRecorderConfig()

```c
OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)
```

**Description**

Obtains the AVRecorder configuration. This function must be called after the recording preparation is complete.<br>**config** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) **config | Pointer to the OH_AVRecorder_Config instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or **config** is not nullptr.<br>        **AV_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory.|

### OH_AVRecorder_GetInputSurface()

```c
OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)
```

**Description**

Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.<br>The caller obtains the **surfaceBuffer** from this surface and fills in the corresponding video data.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OHNativeWindow](../apis-arkgraphics2d/capi-nativewindow-nativewindow.md) **window | Pointer to the OHNativeWindow instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr.|

### OH_AVRecorder_UpdateRotation()

```c
OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)
```

**Description**

Updates the video rotation angle. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered and before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| int32_t rotation | Video rotation angle, in degrees (°). The value must be one of the integers 0°, 90°, 180°, and 270°. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr, **rotation** is invalid, or the update operation fails.|

### OH_AVRecorder_Start()

```c
OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)
```

**Description**

Starts recording. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to start.|

### OH_AVRecorder_Pause()

```c
OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)
```

**Description**

Pauses recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is successfully triggered and the AVRecorder is in the AVRECORDER_STARTED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_PAUSED state.<br>Then, you can call [OH_AVRecorder_Resume](#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions the AVRECORDER_STARTED state again.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to pause.|

### OH_AVRecorder_Resume()

```c
OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)
```

**Description**

Resumes recording. This function must be called after [OH_AVRecorder_Pause](#oh_avrecorder_pause) is successfully triggered and the AVRecorder is in the AVRECORDER_PAUSED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to resume.|

### OH_AVRecorder_Stop()

```c
OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)
```

**Description**

Stops recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is successfully triggered. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STOPPED state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to stop.|

### OH_AVRecorder_Reset()

```c
OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)
```

**Description**

Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to reset.|

### OH_AVRecorder_Release()

```c
OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)
```

**Description**

Releases recording resources. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_RELEASED state.<br>The recorder memory will be released. The application layer must explicitly set the recorder to nullptr to avoid access to wild pointers. After the resources are released, you can no longer perform any operation on the OH_AVRecorder instance.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to release.|

### OH_AVRecorder_GetAvailableEncoder()

```c
OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info,int32_t *length)
```

**Description**

Obtains the available encoders and encoder information of the AVRecorder.<br>**info** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_EncoderInfo](capi-avrecorder-oh-avrecorder-encoderinfo.md) **info | Pointer to the OH_AVRecorder_EncoderInfo instance.|
| int32_t *length | Pointer to the number of available encoders.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr.<br>        **AV_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory.|

### OH_AVRecorder_SetStateCallback()

```c
OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)
```

**Description**

Sets a state callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnStateChange](capi-avrecorder-base-h.md#oh_avrecorder_onstatechange) callback | Status callback function.|
| void *userData | Pointer to user-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetErrorCallback()

```c
OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)
```

**Description**

Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnError](capi-avrecorder-base-h.md#oh_avrecorder_onerror) callback | Error callback function.|
| void *userData | Pointer to user-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetUriCallback()

```c
OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)
```

**Description**

Sets a URI callback so that the application can respond to URI events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start) is called.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnUri](capi-avrecorder-base-h.md#oh_avrecorder_onuri) callback | Callback used to return the result.|
| void *userData | Pointer to user-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>        **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetWillMuteWhenInterrupted()

```c
OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)
```

**Description**

Sets whether to enable the mute interruption mode.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| bool muteWhenInterrupted | Sets whether to enable the mute interruption mode. The value **true** indicates that the application remains muted instead of being interrupted when recording is required. The value **false** indicates that the application stops recording instead of remain muted when the recording is interrupted.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.<br>         **AV_ERR_INVALID_STATE**: The function is called in an invalid state. It must be in the prepared state.|

### OH_AVRecorder_GetAudioCapturerMaxAmplitude()

```c
OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t *amplitude)
```

**Description**

Obtains the maximum amplitude of the current audio capturer. The return value is the maximum amplitude between the last two calls. For example, if the maximum amplitude is obtained once at 1s and then the method is called again at 2s, the return value is the maximum amplitude between 1s and 2s.<br> This method must be called after [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop).

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| int32_t *amplitude | Maximum amplitude of the current audio capturer.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **amplitude** is **nullptr**.<br>         **AV_ERR_INVALID_STATE**: This API cannot be called in the current state. It must be called after **OH_AVRecorder_Prepare** and before **OH_AVRecorder_Stop**.<br>         **AV_ERR_NO_MEMORY**: The memory is insufficient.<br>         **AV_ERR_UNKNOWN**: An unknown error occurs.|

### OH_AVRecorder_SetMetadata()

```c
OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)
```

**Description**

Sets the metadata information to record. If the **metadata** parameter contains the same key as that in **config.metadata.customInfo** (see [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) and [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md)), the value of the former will overwrite that of the latter.<br> This method must be called after **OH_AVRecorder_Prepare** and before [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop).

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| const [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) *metadata | Metadata information to set. The format is a string key-value pair, where the key must start with "com.openharmony." and the value length cannot exceed 256 bytes. |

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **recorder** or **metadata** is **nullptr**, or the value length in **metadata** exceeds 256 bytes.<br>         **AV_ERR_INVALID_STATE**: This API cannot be called in the current state. It must be called after **OH_AVRecorder_Prepare** and before **OH_AVRecorder_Stop**.<br>         **AV_ERR_NO_MEMORY**: The memory is insufficient.<br>         **AV_ERR_UNKNOWN**: An unknown error occurs.|