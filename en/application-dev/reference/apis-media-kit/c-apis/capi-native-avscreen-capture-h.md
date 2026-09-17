# native_avscreen_capture.h

## Overview

The file declares the APIs used to create an OH_AVScreenCapture instance.

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)](#oh_avscreencapture_create) | Creates an OH_AVScreenCapture instance. You can release the instance by calling [OH_AVScreenCapture_Release](capi-native-avscreen-capture-h.md#oh_avscreencapture_release). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)](#oh_avscreencapture_init) | Initializes parameters related to an {@link OH_AVScreenCapture} instance, including audio sampling parameters<br>for external capture using microphones (optional), audio sampling parameters for internal capture, and video<br>resolution parameters.<br>In the scenario where screen recording files are stored, the application must ensure that the video encoding<br>parameters, video sampling parameters, audio encoding parameters, audio sampling parameters for internal capture,<br>and audio sampling parameters for external capture using microphones (optional) are valid.<br>In the scenario where screen capture streams are generated, the application must ensure that either audio sampling<br>parameters for internal capture or video sampling parameters are valid, or both are valid, and audio sampling<br>parameters for external capture using microphones are valid (optional).<br>The members of the struct variables are not initialized during initialization. Therefore, the application must<br>correctly set the parameters based on the use scenario. You are advised to set all memory bytes of the<br>OH_AVScreenCaptureConfig struct variables to **0**, and then set valid parameters based on the screen capture<br>scenario.<br>If both **audioSampleRate** and **audioChannels** in the {@link OH_AudioCaptureInfo} struct are **0**, the<br>OH_AVScreenCapture instance ignores the corresponding audio parameters and does not collect the audio data.<br>If both **videoFrameWidth** and **videoFrameHeight** in the {@link OH_VideoCaptureInfo} struct are **0**, the OH_AVScreenCapture instance ignores the corresponding video parameters and does not collect the screen data. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreencapture) | Starts screen capture and collects original streams. After this function is called, the callback {@link OH_AVScreenCapture_OnBufferAvailable} can be used to check whether streams are generated, and the callback {@link OH_AVScreenCapture_OnStateChange} can be used to check the startup status. The application can obtain the original streams of screen capture by calling [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)<br>and [OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreencapture) | Stops screen capture. This function is used in pair with [OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture). After calling this function, the application stops screen capture or screen share and releases the microphone. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreenrecording) | Starts screen recording, with recordings saved in files. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreenrecording) | Stops screen recording. This function is used in pair with [OH_AVScreenCapture_StartScreenRecording](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)](#oh_avscreencapture_acquireaudiobuffer) | Obtains an audio buffer. When calling this function, the application must allocate the memory of the corresponding struct size to the audio buffer. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead. |
| [OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)](#oh_avscreencapture_acquirevideobuffer) | Obtains a video buffer. The application can call this function to obtain information such as the video buffer and timestamp. When a video buffer is no longer needed, call **OH_AVScreenCapture_ReleaseVideoBuffer** to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)](#oh_avscreencapture_releaseaudiobuffer) | Releases an audio buffer. When an audio buffer is no longer needed, call this function to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_releasevideobuffer) | Releases a video buffer. When a video buffer is no longer needed, call this function to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)](#oh_avscreencapture_setcallback) | Sets a callback to listen for available video buffers and audio buffers and errors that occur during the function calling. Starting from API version 12, you are advised to use [OH_AVScreenCapture_SetErrorCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setdatacallback) instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_release) | Releases an OH_AVScreenCapture instance. This function is used in pair with [OH_AVScreenCapture_Create](capi-native-avscreen-capture-h.md#oh_avscreencapture_create). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)](#oh_avscreencapture_setmicrophoneenabled) | Enables or disables the microphone. When **isMicrophone** is set to **true**, the microphone is enabled, and the original PCM data of the microphone can be obtained by calling [OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer). When **isMicrophone** is set to **false**, the obtained audio data is silent data. By default, the microphone is enabled. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)](#oh_avscreencapture_setstatecallback) | Sets a state change callback. This function must be called before screen capture starts. The callback is triggered when the state changes during the running of an OH_AVScreenCapture instance. A privacy dialog box is displayed to ask for user consent before screen capture starts. After a successful call to this function, the following scenarios are possible: 1. If the user agrees, the screen capture startup process starts. If screen capture starts successfully, the state change callback is triggered to report the {@link OH_AVScreenCaptureStateCode}.OH_SCREEN_CAPTURE_STATE_STARTED status to notify the application of the startup success, with a screen capture notification displayed. If screen capture fails to start, the state change callback is triggered to report the failure information (for example, {@link OH_AVScreenCaptureStateCode}.<br>OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE if the microphone is unavailable), or the error processing callback {@link OH_AVScreenCapture_OnError}<br>is triggered to report the error information.<br>2. If the user disagrees, the screen capture startup process stops. The state change callback is triggered to report<br>the {@link OH_AVScreenCaptureStateCode}.OH_SCREEN_CAPTURE_STATE_CANCELED status to notify the application of the startup failure due to user rejection. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)](#oh_avscreencapture_setdatacallback) | Sets a data processing callback. This function must be called before screen capture starts. The callback is triggered when an audio buffer or a video buffer becomes available during the running of an OH_AVScreenCapture instance. The application needs to process microphone audio, internal audio, and video data based on the data type in the callback. After the callback is triggered, the buffer is no longer valid. A successful call to this function leads to the following scenarios: 1. The callbacks {@link OH_AVScreenCaptureOnAudioBufferAvailable} and {@link OH_AVScreenCaptureOnVideoBufferAvailable} set by calling [OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback) will no longer be triggered, even when an audio buffer or a<br>video buffer becomes available.<br>2. A failure message is returned for a call to any of the following functions: [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer),<br>[OH_AVScreenCapture_ReleaseAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releaseaudiobuffer), [OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer), and [OH_AVScreenCapture_ReleaseVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releasevideobuffer). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)](#oh_avscreencapture_seterrorcallback) | Sets an error processing callback. This function must be called before screen capture starts. The callback is triggered when an error occurs during the running of an OH_AVScreenCapture instance. After a successful call to this function, the callback {@link OH_AVScreenCaptureOnError} set by calling [OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback) will no longer be triggered, even when an error occurs in the OH_AVScreenCapture instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)](#oh_avscreencapture_setcapturecontentchangedcallback) | Sets the callback for screen capture content changes. This function must be called before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)](#oh_avscreencapture_startscreencapturewithsurface) | Starts screen capture in surface mode. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)](#oh_avscreencapture_setcanvasrotation) | Sets whether the captured screen data should rotate. When **canvasRotation** is set to **true**, rotation is enabled and the captured screen data remains upright. The default value is **false**. |
| [struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)](#oh_avscreencapture_createcontentfilter) | Creates a content filter. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_releasecontentfilter) | Releases a content filter. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)](#oh_avscreencapture_contentfilter_addaudiocontent) | Adds audio content to a content filter. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_excludecontent) | Sets a content filter for an OH_AVScreenCapture instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_contentfilter_addwindowcontent) | Adds a list of window IDs to a ContentFilter instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)](#oh_avscreencapture_resizecanvas) | Adjusts the screen resolution. This function is used to set the resolution of screen capture data. **width** indicates the screen width and **<br>height** indicates the screen height. Currently, this function supports only the scenario of capturing streams, but not the scenario of storing captured files. In addition, the caller of this function and the video data consumer must ensure that they support resolution changes of the received video data. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_skipprivacymode) | Exempts privacy windows during screen capture. Currently, all the IDs of the subwindows and main windows to skip must be passed in. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)](#oh_avscreencapture_setmaxvideoframerate) | Sets the maximum frame rate for screen capture. This function must be called after screen capture starts. The maximum frame rate that can be configured is subject to the device's limitations and is ultimately governed by the capabilities of the underlying system. Although there is no limit on the maximum value of the input parameter, the maximum frame rate supported is 60 FPS. If the input parameter value exceeds 60 FPS, 60 FPS is used. If the value does not exceed the upper limit, the passed value is used. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)](#oh_avscreencapture_showcursor) | Sets whether to show the cursor. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)](#oh_avscreencapture_setcapturearea) | Sets or updates the capture area. This function can be called before or after screen capture starts. The coordinates and dimensions provided must be non-negative, and the capture area must not span multiple screens. If setting the area fails, the previously set area is used for capturing. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)](#oh_avscreencapture_setcaptureareahighlight) | Sets the highlight style for the screen capture area. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)](#oh_avscreencapture_setselectioncallback) | Registers a callback to handle user selection results on the manual confirmation UI. This callback must be invoked before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)](#oh_avscreencapture_getcapturetypeselected) | Obtains the screen capture object type selected by the user on the confirmation UI. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)](#oh_avscreencapture_getdisplayidselected) | Obtains the display ID of the screen selected by the user for capture. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete. |
| [OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)](#oh_avscreencapture_createcapturestrategy) | Creates a screen capture strategy. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)](#oh_avscreencapture_releasecapturestrategy) | Releases a screen capture strategy. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy( 
 struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)](#oh_avscreencapture_setcapturestrategy) | Sets a screen capture strategy for an OH_AVScreenCapture instance. This function must be called before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforkeepcaptureduringcall) | Sets whether to keep screen capture during a cellular call. When **value** is set to **true** and screen capture is active during a cellular call, for privacy reasons, the voices of both parties (local microphone and remote speaker) are not captured. Other system sounds are captured normally. After the call ends, the screen capture framework resumes microphone recording. If the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow background applications to activate microphone recording. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode( OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)](#oh_avscreencapture_strategyforprivacymaskmode) | Set the fill mode for screen capture when a privacy window exists |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforbframesencoding) | Sets whether to enable B-frame encoding for a CaptureStrategy instance to reduce the size of the recorded file. For details about the restrictions on B-frame video encoding, see {@link Constraints in B-Frame Video Encoding}. If the current environment does not meet the restrictions, B-frames will be skipped during screen capture, and no error will be returned. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforcanvasfollowrotation) | Sets the automatic rotation following configuration for screen capture. If the value is set to **true**, the screen capture follows the rotation, and the virtual screen size is automatically adjusted after a rotation to ensure the output image matches the new orientation. After this setting, there is no need to manually call [OH_AVScreenCapture_ResizeCanvas](capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas) after rotation notifications. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpickerpopup) | Sets whether to display the screen capture picker. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode( OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)](#oh_avscreencapture_strategyforfillmode) | Sets the fill mode of the captured image in the target region. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)](#oh_avscreencapture_setdisplaycallback) | Sets a callback function for obtaining the display ID. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)](#oh_avscreencapture_excludepickerwindows) | Hides the specified window in the picker. This function is called before the picker is displayed. It is to filter and hide a window. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)](#oh_avscreencapture_setpickermode) | Sets the display mode of the picker. You can define the content type displayed in the picker. The mode change takes effect when [OH_AVScreenCapture_PresentPicker](capi-native-avscreen-capture-h.md#oh_avscreencapture_presentpicker) is called next time. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_presentpicker) | Displays the picker once more after the screen capture starts, allowing for dynamic updates to the recording source, such as changing the window or screen being captured. The ongoing capture process remains uninterrupted while updating the recording source. Following the dynamic update of the recording source through the picker, the capture can proceed with the newly selected source. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)](#oh_avscreencapture_getmultidisplaycapturecapability) | Obtains the multi-screen recording capability information and determines whether the selected screens support joint recording. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t **displayIds, size_t *count)](#oh_avscreencapture_getmultidisplayidsselected) | Obtains the list of display IDs selected by the user for recording on the picker page. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)](#oh_avscreencapture_setprivacyprotectcallback) | Sets a privacy protection callback so that the application can respond to privacy protection events generated during screen capture. This API must be called before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpause) | Allow to pause screen capture |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_pausescreencapture) | Pause screen capture |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_resumescreencapture) | Resume screen capture |

## Function description

### OH_AVScreenCapture_Create()

```c
struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)
```

**Description**

Creates an OH_AVScreenCapture instance. You can release the instance by calling [OH_AVScreenCapture_Release](capi-native-avscreen-capture-h.md#oh_avscreencapture_release).

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| struct OH_AVScreenCapture * | Pointer to the OH_AVScreenCapture instance. |

### OH_AVScreenCapture_Init()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)
```

**Description**

Initializes parameters related to an {@link OH_AVScreenCapture} instance, including audio sampling parameters<br>for external capture using microphones (optional), audio sampling parameters for internal capture, and video<br>resolution parameters.<br>In the scenario where screen recording files are stored, the application must ensure that the video encoding<br>parameters, video sampling parameters, audio encoding parameters, audio sampling parameters for internal capture,<br>and audio sampling parameters for external capture using microphones (optional) are valid.<br>In the scenario where screen capture streams are generated, the application must ensure that either audio sampling<br>parameters for internal capture or video sampling parameters are valid, or both are valid, and audio sampling<br>parameters for external capture using microphones are valid (optional).<br>The members of the struct variables are not initialized during initialization. Therefore, the application must<br>correctly set the parameters based on the use scenario. You are advised to set all memory bytes of the<br>OH_AVScreenCaptureConfig struct variables to **0**, and then set valid parameters based on the screen capture<br>scenario.<br>If both **audioSampleRate** and **audioChannels** in the {@link OH_AudioCaptureInfo} struct are **0**, the<br>OH_AVScreenCapture instance ignores the corresponding audio parameters and does not collect the audio data.<br>If both **videoFrameWidth** and **videoFrameHeight** in the {@link OH_VideoCaptureInfo} struct are **0**, the OH_AVScreenCapture instance ignores the corresponding video parameters and does not collect the screen data.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCaptureConfig config | Parameters related to screen capture initialization. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The configuration fails to be  initialized. |

### OH_AVScreenCapture_StartScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen capture and collects original streams. After this function is called, the callback {@link OH_AVScreenCapture_OnBufferAvailable} can be used to check whether streams are generated, and the callback {@link OH_AVScreenCapture_OnStateChange} can be used to check the startup status. The application can obtain the original streams of screen capture by calling [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)<br>and [OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_UNSUPPORT} (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The privacy permission fails to be  enabled or screen capture fails to start. |

### OH_AVScreenCapture_StopScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen capture. This function is used in pair with [OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture). After calling this function, the application stops screen capture or screen share and releases the microphone.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. Screen capture fails to stop. |

### OH_AVScreenCapture_StartScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen recording, with recordings saved in files.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_UNSUPPORT} (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The privacy permission fails to be  enabled or screen capture fails to start. |

### OH_AVScreenCapture_StopScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen recording. This function is used in pair with [OH_AVScreenCapture_StartScreenRecording](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. Screen capture fails to stop. |

### OH_AVScreenCapture_AcquireAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)
```

**Description**

Obtains an audio buffer. When calling this function, the application must allocate the memory of the corresponding struct size to the audio buffer. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AudioBuffer **audiobuffer | Pointer to the struct for storing the audio buffer. This struct is used to obtain the information about the audio buffer and the timestamp of the buffer. |
| OH_AudioCaptureSourceType type | Type of the audio buffer, which is used to distinguish external streams recorded by the microphone from internal streams played by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or audiobuffer is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_NO_MEMORY}: The audio buffer fails to be allocated due to insufficient memory.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The privacy permission fails to be  enabled or the audio buffer fails to be obtained. |

### OH_AVScreenCapture_AcquireVideoBuffer()

```c
OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)
```

**Description**

Obtains a video buffer. The application can call this function to obtain information such as the video buffer and timestamp. When a video buffer is no longer needed, call **OH_AVScreenCapture_ReleaseVideoBuffer** to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t *fence | Pointer to parameters for synchronization display. |
| int64_t *timestamp | Pointer to the timestamp of the video frame, in nanosecond. |
| struct OH_Rect *region | Pointer to the coordinates related to video display. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeBuffer* | OH_NativeBuffer object if the operation is successful. The application can call the APIs provided by the  OH_NativeBuffer object to obtain information such as the video buffer and resolution. |

### OH_AVScreenCapture_ReleaseAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)
```

**Description**

Releases an audio buffer. When an audio buffer is no longer needed, call this function to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AudioCaptureSourceType type | Type of the audio buffer, which is used to distinguish external streams recorded by the microphone from internal streams played by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The data callback has been set or the  audio buffer fails to be released. |

### OH_AVScreenCapture_ReleaseVideoBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)
```

**Description**

Releases a video buffer. When a video buffer is no longer needed, call this function to release it. Starting from API version 12, you are advised to use {@link OH_AVScreenCapture_OnBufferAvailable} instead.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The data callback has been set or the  vedio buffer fails to be released. |

### OH_AVScreenCapture_SetCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)
```

**Description**

Sets a callback to listen for available video buffers and audio buffers and errors that occur during the function calling. Starting from API version 12, you are advised to use [OH_AVScreenCapture_SetErrorCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setdatacallback) instead.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| struct OH_AVScreenCaptureCallback callback | OH_AVScreenCaptureCallback struct, which stores related callback function pointers. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The callback fails to be set. |

### OH_AVScreenCapture_Release()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)
```

**Description**

Releases an OH_AVScreenCapture instance. This function is used in pair with [OH_AVScreenCapture_Create](capi-native-avscreen-capture-h.md#oh_avscreencapture_create).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The OH_AVScreenCapture instance fails to  be released. |

### OH_AVScreenCapture_SetMicrophoneEnabled()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)
```

**Description**

Enables or disables the microphone. When **isMicrophone** is set to **true**, the microphone is enabled, and the original PCM data of the microphone can be obtained by calling [OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer). When **isMicrophone** is set to **false**, the obtained audio data is silent data. By default, the microphone is enabled.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| bool isMicrophone | Whether to enable the microphone. **true** to enable, **false** to disable. The default value is **true**. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The microphone fails to be enabled or  disabled. |

### OH_AVScreenCapture_SetStateCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)
```

**Description**

Sets a state change callback. This function must be called before screen capture starts. The callback is triggered when the state changes during the running of an OH_AVScreenCapture instance. A privacy dialog box is displayed to ask for user consent before screen capture starts. After a successful call to this function, the following scenarios are possible: 1. If the user agrees, the screen capture startup process starts. If screen capture starts successfully, the state change callback is triggered to report the {@link OH_AVScreenCaptureStateCode}.OH_SCREEN_CAPTURE_STATE_STARTED status to notify the application of the startup success, with a screen capture notification displayed. If screen capture fails to start, the state change callback is triggered to report the failure information (for example, {@link OH_AVScreenCaptureStateCode}.<br>OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE if the microphone is unavailable), or the error processing callback {@link OH_AVScreenCapture_OnError}<br>is triggered to report the error information.<br>2. If the user disagrees, the screen capture startup process stops. The state change callback is triggered to report<br>the {@link OH_AVScreenCaptureStateCode}.OH_SCREEN_CAPTURE_STATE_CANCELED status to notify the application of the startup failure due to user rejection.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnStateChange callback | State change callback. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the state change callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The state callback fails to be set. |

### OH_AVScreenCapture_SetDataCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)
```

**Description**

Sets a data processing callback. This function must be called before screen capture starts. The callback is triggered when an audio buffer or a video buffer becomes available during the running of an OH_AVScreenCapture instance. The application needs to process microphone audio, internal audio, and video data based on the data type in the callback. After the callback is triggered, the buffer is no longer valid. A successful call to this function leads to the following scenarios: 1. The callbacks {@link OH_AVScreenCaptureOnAudioBufferAvailable} and {@link OH_AVScreenCaptureOnVideoBufferAvailable} set by calling [OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback) will no longer be triggered, even when an audio buffer or a<br>video buffer becomes available.<br>2. A failure message is returned for a call to any of the following functions: [OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer),<br>[OH_AVScreenCapture_ReleaseAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releaseaudiobuffer), [OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer), and [OH_AVScreenCapture_ReleaseVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releasevideobuffer).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnBufferAvailable callback | Data processing callback. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the data processing callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The data callback fails to be set. |

### OH_AVScreenCapture_SetErrorCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)
```

**Description**

Sets an error processing callback. This function must be called before screen capture starts. The callback is triggered when an error occurs during the running of an OH_AVScreenCapture instance. After a successful call to this function, the callback {@link OH_AVScreenCaptureOnError} set by calling [OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback) will no longer be triggered, even when an error occurs in the OH_AVScreenCapture instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnError callback | Error processing callback. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the error processing callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The error callback fails to be set. |

### OH_AVScreenCapture_SetCaptureContentChangedCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)
```

**Description**

Sets the callback for screen capture content changes. This function must be called before screen capture starts.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnCaptureContentChanged callback | Pointer to the callback method instance for the screen capture content change event. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the error processing callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The screen capture callback fails to be  set. |

### OH_AVScreenCapture_StartScreenCaptureWithSurface()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)
```

**Description**

Starts screen capture in surface mode.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance. |
| OHNativeWindow *window | Pointer to an OHNativeWindow instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture, input parameter window, or <br>windowSurface pointed to by window is nullptr.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The privacy permission fails to be  enabled or screen capture with a surface fails to start. |

### OH_AVScreenCapture_SetCanvasRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)
```

**Description**

Sets whether the captured screen data should rotate. When **canvasRotation** is set to **true**, rotation is enabled and the captured screen data remains upright. The default value is **false**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |
| bool canvasRotation | whether to rotate the canvas |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. Canvas rotation fails to be set for  screen capture. |

### OH_AVScreenCapture_CreateContentFilter()

```c
struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)
```

**Description**

Creates a content filter.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| struct OH_AVScreenCapture_ContentFilter * | OH_AVScreenCapture_ContentFilter instance if the operation is successful; nullptr otherwise. |

### OH_AVScreenCapture_ReleaseContentFilter()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Releases a content filter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture_ContentFilter *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter filter is nullptr. |

### OH_AVScreenCapture_ContentFilter_AddAudioContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)
```

**Description**

Adds audio content to a content filter.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture_ContentFilter *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |
| OH_AVScreenCaptureFilterableAudioContent content | Pointer to the OH_AVScreenCaptureFilterableAudioContent instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter filter is nullptr or the input parameter content  is invalid. |

### OH_AVScreenCapture_ExcludeContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Sets a content filter for an OH_AVScreenCapture instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| struct OH_AVScreenCapture_ContentFilter *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or filter is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_UNSUPPORT}: The operation is not supported. For streams, the AudioCapturer API must be  called for the operation to take effect during the start.  For captured files, the Recorder API must be called for the operation to take effect during the start. |

### OH_AVScreenCapture_ContentFilter_AddWindowContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)
```

**Description**

Adds a list of window IDs to a ContentFilter instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture_ContentFilter *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |
| int32_t *windowIDs | Pointer to the window IDs. |
| int32_t windowCount | Length of the window ID list. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK if the operation is successful; a specific error code if the operation fails. |

### OH_AVScreenCapture_ResizeCanvas()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)
```

**Description**

Adjusts the screen resolution. This function is used to set the resolution of screen capture data. **width** indicates the screen width and **<br>height** indicates the screen height. Currently, this function supports only the scenario of capturing streams, but not the scenario of storing captured files. In addition, the caller of this function and the video data consumer must ensure that they support resolution changes of the received video data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t width | Video frame width of avscreeencapture, in px. |
| int32_t height | Video frame height of avscreeencapture, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_SkipPrivacyMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)
```

**Description**

Exempts privacy windows during screen capture. Currently, all the IDs of the subwindows and main windows to skip must be passed in.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t *windowIDs | Pointer of windowID list |
| int32_t windowCount | length of windowID list |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_SetMaxVideoFrameRate()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)
```

**Description**

Sets the maximum frame rate for screen capture. This function must be called after screen capture starts. The maximum frame rate that can be configured is subject to the device's limitations and is ultimately governed by the capabilities of the underlying system. Although there is no limit on the maximum value of the input parameter, the maximum frame rate supported is 60 FPS. If the input parameter value exceeds 60 FPS, 60 FPS is used. If the value does not exceed the upper limit, the passed value is used.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t frameRate | max frame rate of video, in fps. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr, or the input parameter <br>frameRate is not supported.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_ShowCursor()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)
```

**Description**

Sets whether to show the cursor.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture instance |
| bool showCursor | The switch of the cursor |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>AV_SCREEN_CAPTURE_ERR_UNSUPPORT (available since API version 20): The device does not support the operation.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The cursor setting fails. |

### OH_AVScreenCapture_SetCaptureArea()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)
```

**Description**

Sets or updates the capture area. This function can be called before or after screen capture starts. The coordinates and dimensions provided must be non-negative, and the capture area must not span multiple screens. If setting the area fails, the previously set area is used for capturing.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | capture Pointer to an OH_AVScreenCapture instance |
| uint64_t displayId | Indicates the screen index for setting area recording |
| OH_Rect* area | Pointer to an object describing the location and size of the region |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is a nullptr, the input displayId does  not exist, or the input area is abnormal. |

### OH_AVScreenCapture_SetCaptureAreaHighlight()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)
```

**Description**

Sets the highlight style for the screen capture area.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to OH_AVScreenCapture which want to set highlight style. |
| OH_AVScreenCaptureHighlightConfig config | the highlight parameters are to be set for this screen capture. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr or config is invalid. |

### OH_AVScreenCapture_SetSelectionCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)
```

**Description**

Registers a callback to handle user selection results on the manual confirmation UI. This callback must be invoked before screen capture starts.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to OH_AVScreenCapture which want to handle user selection info |
| OH_AVScreenCapture_OnUserSelected callback | user selection callback function, see {@link OH_AVScreenCapture_OnUserSelected} |
| void *userData | The control block pointer passed by the application is carried to the application when it is returned |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr. |

### OH_AVScreenCapture_GetCaptureTypeSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)
```

**Description**

Obtains the screen capture object type selected by the user on the confirmation UI. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_UserSelectionInfo *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance |
| int32_t* type | The capture object type selected by the user, 0: represents the screen, 1: represents the window, 2: represents the app. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter selection is nullptr. |

### OH_AVScreenCapture_GetDisplayIdSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)
```

**Description**

Obtains the display ID of the screen selected by the user for capture. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_UserSelectionInfo *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance |
| uint64_t* displayId | Returns the screen ID value selected by the user |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter selection is nullptr. |

### OH_AVScreenCapture_CreateCaptureStrategy()

```c
OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)
```

**Description**

Creates a screen capture strategy.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy* | OH_AVScreenCapture_CaptureStrategy instance if the operation is successful; nullptr otherwise. |

### OH_AVScreenCapture_ReleaseCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)
```

**Description**

Releases a screen capture strategy.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy* strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr. |

### OH_AVScreenCapture_SetCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy( 
 struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)
```

**Description**

Sets a screen capture strategy for an OH_AVScreenCapture instance. This function must be called before screen capture starts.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to an OH_AVScreenCapture which need to be setted. |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy which want to set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or strategy is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_STATE}: This function is called after screen capture starts. |

### OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to keep screen capture during a cellular call. When **value** is set to **true** and screen capture is active during a cellular call, for privacy reasons, the voices of both parties (local microphone and remote speaker) are not captured. Other system sounds are captured normally. After the call ends, the screen capture framework resumes microphone recording. If the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow background applications to activate microphone recording.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | The default value is false, which means that screen recording is not allowed during cellular calls. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr. |

### OH_AVScreenCapture_StrategyForPrivacyMaskMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode( OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)
```

**Description**

Set the fill mode for screen capture when a privacy window exists

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| int32_t value |  If set to 0, it means that when there is a privacy window interface, the output screen image is completely black.  If set to 1, it means that when there is a privacy window interface, only the privacy window area of the output screen becomes black,  and other values returns an error. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.          {@link AV_SCREEN_CAPTURE_ERR_OK} if the execution is successful.<br>        {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL} strategy is nullptr or  value is invalid. |

### OH_AVScreenCapture_StrategyForBFramesEncoding()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to enable B-frame encoding for a CaptureStrategy instance to reduce the size of the recorded file. For details about the restrictions on B-frame video encoding, see {@link Constraints in B-Frame Video Encoding}. If the current environment does not meet the restrictions, B-frames will be skipped during screen capture, and no error will be returned.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | The default value is false, which means B frames  encoding are disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr. |

### OH_AVScreenCapture_StrategyForCanvasFollowRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets the automatic rotation following configuration for screen capture. If the value is set to **true**, the screen capture follows the rotation, and the virtual screen size is automatically adjusted after a rotation to ensure the output image matches the new orientation. After this setting, there is no need to manually call [OH_AVScreenCapture_ResizeCanvas](capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas) after rotation notifications.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | The default value is False, which means that the width and height of the VirtualDisplay remain the initial settings. If set to True, it means that the width and height of the VirtualDisplay rotates with the rotation of the screen.. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr. |

### OH_AVScreenCapture_StrategyForPickerPopUp()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to display the screen capture picker.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | If set to false, it means that the APP don't need to pop up the Picker after screen capture starts; If set to True, the Picker will pop up uniformly after screen capture starts; If not set, it means using the system recommended behavior. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr or value is invalid. |

### OH_AVScreenCapture_StrategyForFillMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode( OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)
```

**Description**

Sets the fill mode of the captured image in the target region.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| OH_AVScreenCapture_FillMode mode | Value of the captured image fill mode |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter strategy is nullptr. |

### OH_AVScreenCapture_SetDisplayCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)
```

**Description**

Sets a callback function for obtaining the display ID.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnDisplaySelected callback | Callback function for returning the display ID. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the state change callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture or callback is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_NO_MEMORY}: The memory fails to be allocated due to insufficient memory.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_STATE}: The callback must be called before the start function. |

### OH_AVScreenCapture_ExcludePickerWindows()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)
```

**Description**

Hides the specified window in the picker. This function is called before the picker is displayed. It is to filter and hide a window.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| const int32_t *excludedWindowIDs | Array of IDs of the windows to be hidden (existing windows). |
| uint32_t windowCount | Size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr or excludedWindowIDs is<br>invalid.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_SetPickerMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)
```

**Description**

Sets the display mode of the picker. You can define the content type displayed in the picker. The mode change takes effect when [OH_AVScreenCapture_PresentPicker](capi-native-avscreen-capture-h.md#oh_avscreencapture_presentpicker) is called next time.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_CapturePickerMode pickerMode | Display mode of the picker. For details, see **OH_CapturePickerMode**. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr or pickerMode is invalid.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_PresentPicker()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)
```

**Description**

Displays the picker once more after the screen capture starts, allowing for dynamic updates to the recording source, such as changing the window or screen being captured. The ongoing capture process remains uninterrupted while updating the recording source. Following the dynamic update of the recording source through the picker, the capture can proceed with the newly selected source.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is nullptr.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. |

### OH_AVScreenCapture_GetMultiDisplayCaptureCapability()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)
```

**Description**

Obtains the multi-screen recording capability information and determines whether the selected screens support joint recording.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| uint64_t *displayIds | Pointer to the array of display IDs selected by the user. |
| size_t count | Number of display IDs selected by the user. |
| OH_MultiDisplayCapability *capability | Pointer to the **OH_MultiDisplayCapability** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter capture is a null pointer.<br>{@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed, and data fails to be obtained. |

### OH_AVScreenCapture_GetMultiDisplayIdsSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t **displayIds, size_t *count)
```

**Description**

Obtains the list of display IDs selected by the user for recording on the picker page. This function is used in the {@link OH_AVScreenCapture_OnUserSelected} callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_UserSelectionInfo *selection | Pointer to the OH_AVScreenCapture_UserSelectionInfo instance. |
| uint64_t **displayIds | Double pointer to the array of display IDs selected by the user. The memory of the **displayIds**<br>parameter is managed by **OH_AVScreenCapture_UserSelectionInfo** and does not need to be manually released. |
| size_t *count | Pointer to the number of display IDs selected by the user. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input parameter selection is a null pointer. |

### OH_AVScreenCapture_SetPrivacyProtectCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)
```

**Description**

Sets a privacy protection callback so that the application can respond to privacy protection events generated during screen capture. This API must be called before screen capture starts.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVScreenCapture_OnPrivacyProtect callback | Privacy protection callback function. |
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the state change callback is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | {@link AV_SCREEN_CAPTURE_ERR_OK}: The operation is successful.<br>{@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: The input screen capture instance or callback is a null pointer. |

### OH_AVScreenCapture_StrategyForPause()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Allow to pause screen capture

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVScreenCapture_CaptureStrategy *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance. |
| bool value | The default value is false, which means that screen recording is not allowed to pause |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.          {@link AV_SCREEN_CAPTURE_ERR_OK}: the execution is successful.<br>        {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: strategy value is nullptr. |

### OH_AVScreenCapture_PauseScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Pause screen capture

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Initialized screen capture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.          {@link AV_SCREEN_CAPTURE_ERR_OK}: the execution is successful.<br>        {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: capture value is nullptr.<br>        {@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: operation not permitted. |

### OH_AVScreenCapture_ResumeScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Resume screen capture

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct OH_AVScreenCapture *capture | Initialized screen capture instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.          {@link AV_SCREEN_CAPTURE_ERR_OK}: the execution is successful.<br>        {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL}: capture value is nullptr.<br>        {@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT}: operation not permitted. |


