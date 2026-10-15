# avrecorder.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## Overview

The file declares the AVRecorder APIs. AVRecorder enables media recording and supports audio and video data collection and recording, complete status management and callback listening, flexible encoder selection, and parameter configuration. It is suitable for scenarios where audio and video need to be recorded and saved as files.

**File to include**: <multimedia/player_framework/avrecorder.h>

**Library**: libavrecorder.so

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_AVRecorder *OH_AVRecorder_Create(void)](#oh_avrecorder_create) | Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. After using the AVRecorder instance, you must call [OH_AVRecorder_Release](#oh_avrecorder_release) to release resources to prevent resource leaks.|
| [OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)](#oh_avrecorder_prepare) | Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](#oh_avrecorder_create) and before [OH_AVRecorder_Start](#oh_avrecorder_start). After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_PREPARED** state.<br>If video-related parameters are not set, only audio is recorded. Similarly, if audio-related parameters are not set, only video is recorded.|
| [OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)](#oh_avrecorder_getavrecorderconfig) | Obtains the AVRecorder configuration. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare). Typical use scenarios include checking whether the configuration parameters are correct before recording starts and displaying the current recording settings on the UI.<br>**config** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing.|
| [OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)](#oh_avrecorder_getinputsurface) | Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>**window** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.<br>The caller obtains the **surfaceBuffer** from this surface and fills in data of the video to be recorded.|
| [OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)](#oh_avrecorder_updaterotation) | Updates the video rotation angle. Typical use scenarios include adjusting the video orientation when the device is switched between landscape and portrait modes, and setting the video rotation angle based on the camera image capture direction. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Start](#oh_avrecorder_start).|
| [OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)](#oh_avrecorder_start) | Starts recording. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is called. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_STARTED state.|
| [OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)](#oh_avrecorder_pause) | Pauses recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_PAUSED** state.<br>Then, you can call [OH_AVRecorder_Resume](#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions the AVRECORDER_STARTED state again.|
| [OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)](#oh_avrecorder_resume) | Resumes recording. This function must be called after [OH_AVRecorder_Pause](#oh_avrecorder_pause) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_STARTED** state.|
| [OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)](#oh_avrecorder_stop) | Stops recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_STOPPED** state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.<br>When [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) is used during media file creation, the [OH_MediaAsset](../apis-media-library-kit/capi-mediaassetmanager-oh-mediaasset.md) object is called back to the app through [OH_AVRecorder_SetUriCallback](#oh_avrecorder_seturicallback) after the **stop** operation is complete.|
| [OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)](#oh_avrecorder_reset) | Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. Typical use scenarios include reconfiguring parameters for a new round of recording after the previous recording is complete, and resetting the AVRecorder to the initial state and starting recording again after an error occurs during recording.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.|
| [OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)](#oh_avrecorder_release) | Releases recording resources. This function must be called when the AVRecorder is not in the **AVRECORDER_RELEASED** state. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_RELEASED** state.<br>After this function is called, the recorder memory is released. The app layer must explicitly set the recorder pointer to **nullptr** to avoid access to wild pointers. After the resources are released, you can no longer perform any operation on the OH_AVRecorder instance.|
| [OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info, int32_t *length)](#oh_avrecorder_getavailableencoder) | Obtains information about the available encoders of the AVRecorder. This API must be called when the AVRecorder is not in the **AVRECORDER_RELEASED** or **AVRECORDER_ERROR** state. Typical use scenarios include querying the encoders supported by the device when the app is started, selecting a proper encoding format based on the available encoders, and displaying the list of available encoders on the encoder selection screen.<br>**info** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing.|
| [OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)](#oh_avrecorder_setstatecallback) | Sets a state change callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one state change callback. If the app set multiple callbacks, the last one set will take effect.|
| [OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)](#oh_avrecorder_seterrorcallback) | Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one error callback. If the app set multiple callbacks, the last one set will take effect.|
| [OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)](#oh_avrecorder_seturicallback) | Sets a URI callback. When [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) is used during media file creation, this callback is triggered after the [OH_AVRecorder_Stop](#oh_avrecorder_stop) operation is complete, and the [OH_MediaAsset](../apis-media-library-kit/capi-mediaassetmanager-oh-mediaasset.md) object is called back to the app. Typical use scenarios include obtaining the URI of the output file for file sharing or display after the recording is complete, and updating the file list in the app based on the URI. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one URI callback. If the app set multiple callbacks, the last one set will take effect.|
| [OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)](#oh_avrecorder_setwillmutewheninterrupted) | Sets whether to enable the mute interruption mode. This mode controls the behavior when the audio stream is interrupted. The value **true** indicates that the recording is muted when the audio stream is interrupted. The value **false** indicates that the recording stops when the audio stream is interrupted. The default value is **false**. Typical use scenarios: In scenarios where continuous recording is required, such as conference recording, enable the mute interruption mode to ensure that the recording remains muted when an incoming call interrupts the recording, preventing loss of subsequent content. In normal recording scenarios, disable the mute interruption mode so that the recording stops directly when interrupted, saving storage space. This function must be called before [OH_AVRecorder_Prepare](#oh_avrecorder_prepare).|
| [OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t *amplitude)](#oh_avrecorder_getaudiocapturermaxamplitude) | Obtains the maximum amplitude of the current audio capturer. Typical use scenarios include real-time display of the volume level during audio recording, audio waveform display, and checking whether the recording is muted. The return value is the maximum amplitude between the last two calls. For example, if the maximum amplitude is obtained once at 1s and then the API is called again at 2s, the return value is the maximum amplitude between 1s and 2s. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).|
| [OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)](#oh_avrecorder_setmetadata) | Sets the metadata information to record. Typical use scenarios include adding custom metadata such as author information, copyright information, geographical location, and recording time to recorded video or audio files. If the **metadata** parameter contains the same key as that in **config.metadata.customInfo** (see [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md)), the value of the former will overwrite that of the latter. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).|

## Function Description

### OH_AVRecorder_Create()

```c
OH_AVRecorder *OH_AVRecorder_Create(void)
```

**Description**

Creates an AVRecorder instance. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. After using the AVRecorder instance, you must call [OH_AVRecorder_Release](#oh_avrecorder_release) to release resources to prevent resource leaks.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) * | Pointer to the **OH_AVRecorder** instance created if the operation is successful; **nullptr** otherwise. If the operation is successful, this parameter is used in the subsequent recording operations such as **Prepare**, **Start**, and **Pause**.|

### OH_AVRecorder_Prepare()

```c
OH_AVErrCode OH_AVRecorder_Prepare(OH_AVRecorder *recorder, OH_AVRecorder_Config *config)
```

**Description**

Sets AVRecorder parameters to prepare for recording. This function must be called after [OH_AVRecorder_Create](#oh_avrecorder_create) and before [OH_AVRecorder_Start](#oh_avrecorder_start). After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_PREPARED** state.<br>If video-related parameters are not set, only audio is recorded. Similarly, if audio-related parameters are not set, only video is recorded.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) *config | Pointer to the **OH_AVRecorder_Config** instance, which is used to configure parameters of the audio and video to be recorded, including the encoding format, sampling rate, and resolution. If video-related parameters are not set, only audio is recorded. If audio-related parameters are not set, only video is recorded. The value cannot be **nullptr**. Otherwise, **AV_ERR_INVALID_VAL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **config** is **nullptr** or the preparation fails.|

### OH_AVRecorder_GetAVRecorderConfig()

```c
OH_AVErrCode OH_AVRecorder_GetAVRecorderConfig(OH_AVRecorder *recorder, OH_AVRecorder_Config **config)
```

**Description**

Obtains the AVRecorder configuration. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare). Typical use scenarios include checking whether the configuration parameters are correct before recording starts and displaying the current recording settings on the UI.<br>**config** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) **config | Pointer to the pointer to the **OH_AVRecorder_Config** instance, which is used to obtain the current recording parameter configuration. **config** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing. After the call is successful, **config** points to the configuration instance allocated by the framework layer.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or **config** is not nullptr.<br>**AV_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory. Release resources and try again.|

### OH_AVRecorder_GetInputSurface()

```c
OH_AVErrCode OH_AVRecorder_GetInputSurface(OH_AVRecorder *recorder, OHNativeWindow **window)
```

**Description**

Obtains an input surface. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>**window** must be set to nullptr. The framework layer allocates and releases the memory in a unified manner to avoid issues with memory management, such as leaks or double freeing.<br>The caller obtains the **surfaceBuffer** from this surface and fills in data of the video to be recorded.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OHNativeWindow](../apis-arkgraphics2d/capi-nativewindow-nativewindow.md) **window | Pointer to the pointer to the **OHNativeWindow** instance, which is used to obtain the input surface. **window** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing. After the call is successful, **window** points to the **OHNativeWindow** instance allocated by the framework layer. The caller can obtain the surface from this instance and fill in video data. If **window** is not **nullptr**, the error **AV_ERR_INVALID_VAL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or **window** is not nullptr.|

### OH_AVRecorder_UpdateRotation()

```c
OH_AVErrCode OH_AVRecorder_UpdateRotation(OH_AVRecorder *recorder, int32_t rotation)
```

**Description**

Updates the video rotation angle. Typical use scenarios include adjusting the video orientation when the device is switched between landscape and portrait modes, and setting the video rotation angle based on the camera image capture direction. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Start](#oh_avrecorder_start).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| int32_t rotation | Video rotation angle, in degrees (°). The options are as follows: **0°**: no rotation, applicable to recording in the normal orientation; **90°**: rotation by 90°, applicable to adjusting the video orientation when the device is switched to the landscape mode clockwise; **180°**: rotation by 180°, applicable to recording in the inverted direction; **270°**: rotation by 270°, applicable to adjusting the video direction when the device is switched to the landscape mode counterclockwise. The value must be one of the preceding values. If another angle is passed, **AV_ERR_INVALID_VAL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr, **rotation** is invalid, or the video rotation angle update fails.|

### OH_AVRecorder_Start()

```c
OH_AVErrCode OH_AVRecorder_Start(OH_AVRecorder *recorder)
```

**Description**

Starts recording. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_STARTED** state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to start.|

### OH_AVRecorder_Pause()

```c
OH_AVErrCode OH_AVRecorder_Pause(OH_AVRecorder *recorder)
```

**Description**

Pauses recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_PAUSED** state.<br>Then, you can call [OH_AVRecorder_Resume](#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions the AVRECORDER_STARTED state again.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to pause.|

### OH_AVRecorder_Resume()

```c
OH_AVErrCode OH_AVRecorder_Resume(OH_AVRecorder *recorder)
```

**Description**

Resumes recording. This function must be called after [OH_AVRecorder_Pause](#oh_avrecorder_pause) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_STARTED** state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to resume.|

### OH_AVRecorder_Stop()

```c
OH_AVErrCode OH_AVRecorder_Stop(OH_AVRecorder *recorder)
```

**Description**

Stops recording. This function must be called after [OH_AVRecorder_Start](#oh_avrecorder_start) is called. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_STOPPED** state.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.<br>When [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) is used during media file creation, the [OH_MediaAsset](../apis-media-library-kit/capi-mediaassetmanager-oh-mediaasset.md) object is called back to the app through [OH_AVRecorder_SetUriCallback](#oh_avrecorder_seturicallback) after the **stop** operation is complete.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to stop.|

### OH_AVRecorder_Reset()

```c
OH_AVErrCode OH_AVRecorder_Reset(OH_AVRecorder *recorder)
```

**Description**

Resets the recording state. This function must be called when the AVRecorder is not in the AVRECORDER_RELEASED state. After this function is successfully called, the AVRecorder transitions to the AVRECORDER_IDLE state. Typical use scenarios include reconfiguring parameters for a new round of recording after the previous recording is complete, and resetting the AVRecorder to the initial state and starting recording again after an error occurs during recording.<br>For audio-only recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) again for re-recording.<br>For video-only recording or audio and video recording, you can call [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_GetInputSurface](#oh_avrecorder_getinputsurface) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to reset.|

### OH_AVRecorder_Release()

```c
OH_AVErrCode OH_AVRecorder_Release(OH_AVRecorder *recorder)
```

**Description**

Releases recording resources. This function must be called when the AVRecorder is not in the **AVRECORDER_RELEASED** state. After this function is successfully called, the AVRecorder transitions to the **AVRECORDER_RELEASED** state.<br>After this function is called, the recorder memory is released. The app layer must explicitly set the recorder pointer to **nullptr** to avoid access to wild pointers. After the resources are released, you can no longer perform any operation on the **OH_AVRecorder** instance.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or recording fails to release.|

### OH_AVRecorder_GetAvailableEncoder()

```c
OH_AVErrCode OH_AVRecorder_GetAvailableEncoder(OH_AVRecorder *recorder, OH_AVRecorder_EncoderInfo **info, int32_t *length)
```

**Description**

Obtains information about the available encoders of the AVRecorder. This API must be called when the AVRecorder is not in the **AVRECORDER_RELEASED** or **AVRECORDER_ERROR** state. Typical use scenarios include querying the encoders supported by the device when the app is started, selecting a proper encoding format based on the available encoders, and displaying the list of available encoders on the encoder selection screen.<br>**info** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_EncoderInfo](capi-avrecorder-oh-avrecorder-encoderinfo.md) **info | Pointer to the **OH_AVRecorder_EncoderInfo** instance, which is used to obtain the array of available encoder information. **info** must be set to **nullptr**. The framework layer allocates and releases the memory in a unified manner to avoid leaks or double freeing. After the call is successful, **info** points to the encoder information array allocated by the framework layer.|
| int32_t *length | Number of elements in the array of available encoders. This is an output parameter. The value cannot be **nullptr**. After the call is successful, the value of **length** indicates the number of encoder information elements in the **info** array. This parameter is used together with the **info** parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr or **info** is not nullptr.<br>**AV_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory. Release resources and try again.|

### OH_AVRecorder_SetStateCallback()

```c
OH_AVErrCode OH_AVRecorder_SetStateCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnStateChange callback, void *userData)
```

**Description**

Sets a state change callback so that the application can respond to state change events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one state change callback. If the app set multiple callbacks, the last one set will take effect.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnStateChange](capi-avrecorder-base-h.md#oh_avrecorder_onstatechange) callback | State callback function, which is used to receive AVRecorder state change events. This callback is triggered when the AVRecorder state changes, for example, when recording starts, pauses, or stops. The value must be a valid function pointer and cannot be **nullptr**.|
| void *userData | Pointer to the custom data, which is passed to the callback function when the state change callback function is triggered and can be used by the app layer. If custom data does not need to be passed, pass **nullptr**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetErrorCallback()

```c
OH_AVErrCode OH_AVRecorder_SetErrorCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnError callback, void *userData)
```

**Description**

Sets an error callback so that the application can respond to error events generated by the AVRecorder. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one error callback. If the app set multiple callbacks, the last one set will take effect.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnError](capi-avrecorder-base-h.md#oh_avrecorder_onerror) callback | Error callback, which is used to receive AVRecorder error events. This callback is triggered when an error occurs during recording, for example, when the encoder is abnormal or the file fails to be written. The value must be a valid function pointer and cannot be **nullptr**.|
| void *userData | Pointer to the custom data, which is passed to the callback function when the error callback function is triggered and can be used by the app layer. If custom data does not need to be passed, pass **nullptr**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetUriCallback()

```c
OH_AVErrCode OH_AVRecorder_SetUriCallback(OH_AVRecorder *recorder, OH_AVRecorder_OnUri callback, void *userData)
```

**Description**

Sets a URI callback. When [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) is used during media file creation, this callback is triggered after the [OH_AVRecorder_Stop](#oh_avrecorder_stop) operation is complete, and the [OH_MediaAsset](../apis-media-library-kit/capi-mediaassetmanager-oh-mediaasset.md) object is called back to the app. Typical use scenarios include obtaining the URI of the output file for file sharing or display after the recording is complete, and updating the file list in the app based on the URI. This function must be called before [OH_AVRecorder_Start](#oh_avrecorder_start).<br>An app can set only one URI callback. If the app set multiple callbacks, the last one set will take effect.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_OnUri](capi-avrecorder-base-h.md#oh_avrecorder_onuri) callback | URI callback used to receive the resource file created by the system. This callback is triggered only after the recording is complete. You need to set **FileGenerationMode** to the mode where the system creates media files in the recording configuration. The value must be a valid function pointer and cannot be **nullptr**.|
| void *userData | Pointer to the custom data, which is passed to the callback function when the URI callback function is triggered and can be used by the app layer. If custom data does not need to be passed, pass **nullptr**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **callback** is nullptr.|

### OH_AVRecorder_SetWillMuteWhenInterrupted()

```c
OH_AVErrCode OH_AVRecorder_SetWillMuteWhenInterrupted(OH_AVRecorder *recorder, bool muteWhenInterrupted)
```

**Description**

Sets whether to enable the mute interruption mode. This mode controls the behavior when the audio stream is interrupted. The value **true** indicates that the recording is muted when the audio stream is interrupted. The value **false** indicates that the recording stops when the audio stream is interrupted. The default value is **false**. Typical use scenarios: In scenarios where continuous recording is required, such as conference recording, enable the mute interruption mode to ensure that the recording remains muted when an incoming call interrupts the recording, preventing loss of subsequent content. In normal recording scenarios, disable the mute interruption mode so that the recording stops directly when interrupted, saving storage space. This function must be called before [OH_AVRecorder_Prepare](#oh_avrecorder_prepare).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 20


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| bool muteWhenInterrupted | Whether to enable the mute interruption mode. The value **true** indicates that the mute interruption mode is enabled. When the audio stream is interrupted, the recording is muted. The value **false** indicates that the mute interruption mode is disabled. When the audio stream is interrupted, the recording stops. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** is nullptr.<br>**AV_ERR_INVALID_STATE**: This function cannot be called in the current state. It must be called before [OH_AVRecorder_Prepare](#oh_avrecorder_prepare).|

### OH_AVRecorder_GetAudioCapturerMaxAmplitude()

```c
OH_AVErrCode OH_AVRecorder_GetAudioCapturerMaxAmplitude(OH_AVRecorder *recorder, int32_t* amplitude)
```

**Description**

Obtains the maximum amplitude of the current audio capturer. Typical use scenarios include real-time display of the volume level during audio recording, audio waveform display, and checking whether the recording is muted. The return value is the maximum amplitude between the last two calls. For example, if the maximum amplitude is obtained once at 1s and then the API is called again at 2s, the return value is the maximum amplitude between 1s and 2s. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| int32_t* amplitude | Maximum audio amplitude obtained, indicating the maximum amplitude of the audio signal between the last two calls. This is an output parameter. The value cannot be **nullptr**. Otherwise, **AV_ERR_INVALID_VAL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **amplitude** is **nullptr**.<br>**AV_ERR_INVALID_STATE**: This function cannot be called in the current state. It must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).<br>**AV_ERR_NO_MEMORY**: Insufficient memory. Release resources and try again.<br>**AV_ERR_UNKNOWN**: This is an unknown error. Check the log for details.|

### OH_AVRecorder_SetMetadata()

```c
OH_AVErrCode OH_AVRecorder_SetMetadata(OH_AVRecorder *recorder, const OH_AVFormat *metadata)
```

**Description**

Sets the metadata information to record. Typical use scenarios include adding custom metadata such as author information, copyright information, geographical location, and recording time to recorded video or audio files. If the **metadata** parameter contains the same key as that in **config.metadata.customInfo** (see [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md)), the value of the former will overwrite that of the latter. This function must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| const [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) *metadata | Metadata embedded into the recorded media file. The value cannot be **nullptr**. Otherwise, **AV_ERR_INVALID_VAL** is returned. The value is a string key-value pair. The key must start with **com.openharmony**. If not, the key-value pair will be ignored. The value contains a maximum of 256 bytes. If the value is out of range, **AV_ERR_INVALID_VAL** is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input parameter **recorder** or **metadata** is **nullptr**, or the value length in **metadata** exceeds 256 bytes.<br>**AV_ERR_INVALID_STATE**: This function cannot be called in the current state. It must be called after [OH_AVRecorder_Prepare](#oh_avrecorder_prepare) and before [OH_AVRecorder_Stop](#oh_avrecorder_stop).<br>**AV_ERR_NO_MEMORY**: Insufficient memory. Release resources and try again.<br>**AV_ERR_UNKNOWN**: This is an unknown error. Check the log for details.|
