# native_avscreen_capture.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7938d317c00ead5ed43dc34638402f4d9dbdbe18 translatedAt=2026-11-10T10:57:09.226Z pushedAt=2026-11-10T11:13:30.994Z nl=1 -->

## Overview

Declares the APIs used to create a screen capture object.

The following two modes are supported: screen recording with stream retrieval and screen recording to file. It can capture microphone audio and internal audio data, obtain video buffer data, and provide callback mechanisms for status changes, data processing, and error handling. It supports Surface-mode screen recording, content filtering, privacy protection, capture policy configuration, capture region setting and highlighting, and multi-screen recording, making it suitable for scenarios such as implementing screen recording, screen sharing, or live streaming within an application.

**File to include:** <multimedia/player_framework/native_avscreen_capture.h>

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Related sample:** [NativeAvScreenCapture](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample)

## Summary

### Functions

<!--Table: 50%; 50% -->
| Name | Description |
| -- | -- |
| [struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)](#oh_avscreencapture_create) | Instantiates an object and creates OH_AVScreenCapture.<br> Call [OH_AVScreenCapture_Release](#oh_avscreencapture_release) to release the instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)](#oh_avscreencapture_init) | Initializes parameters related to [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md), including parameters related to microphone audio sampling (optional), internal audio recording sampling, and video resolution. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreencapture) | Starts screen capture and collects the raw stream. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreencapture) | Ends screen capture. Used together with [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture). After this interface is called, screen capture or screen sharing stops for the application that calls it, and the microphone is released. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreenrecording) | Starts screen recording. Call this interface to save the screen recording file. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreenrecording) | Stops screen recording. Used together with [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)](#oh_avscreencapture_acquireaudiobuffer) | Acquires an audio buffer. When calling this interface, the application must allocate memory of the size corresponding to the audiobuffer structure; otherwise, acquisition of the audio buffer is affected.<br> From API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)](#oh_avscreencapture_acquirevideobuffer) | Acquires a video buffer. The application obtains information such as the video buffer and timestamp through this interface.<br> After the buffer is used, call OH_AVScreenCapture_ReleaseVideoBuffer to release the video buffer.<br> From API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)](#oh_avscreencapture_releaseaudiobuffer) | Releases the buffer based on the audio type. After a frame of audio buffer is used, call this interface to release the corresponding audio buffer.<br> From API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_releasevideobuffer) | Releases the buffer based on the video type. After a frame of video buffer is used, call this interface to release the corresponding video buffer.<br> From API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)](#oh_avscreencapture_setcallback) | Sets the listener interface. By setting the listener, you can listen for error information during the call process and whether there are available video and audio buffers.<br> From API version 12, it is recommended to use [OH_AVScreenCapture_SetErrorCallback](#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](#oh_avscreencapture_setdatacallback) instead. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_release) | Releases the created OH_AVScreenCapture instance, corresponding to [OH_AVScreenCapture_Create](#oh_avscreencapture_create). |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)](#oh_avscreencapture_setmicrophoneenabled) | Sets the microphone switch.<br> When isMicrophone is true, the microphone is turned on, and raw PCM microphone data can be obtained normally by calling [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer). When isMicrophone is false, the audio data obtained is silent.<br> The microphone switch is enabled by default. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)](#oh_avscreencapture_setstatecallback) | Sets the callback method for state change handling. Call this before recording starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)](#oh_avscreencapture_setdatacallback) | Sets the callback method for data processing. Call this before recording starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)](#oh_avscreencapture_seterrorcallback) | Sets the callback method for error handling. Call this before recording starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)](#oh_avscreencapture_startscreencapturewithsurface) | Performs screen capture in Surface mode. Different from [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture), this interface outputs video data directly to the specified Surface window by passing in OHNativeWindow, which is suitable for scenarios where the captured screen data needs to be rendered to a specific window. OH_AVScreenCapture_StartScreenCapture, on the other hand, obtains raw stream data through callbacks, which is suitable for scenarios where audio and video data need to be processed by the application itself. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)](#oh_avscreencapture_setcanvasrotation) | Sets whether to enable rotation of the captured screen data. Call this before screen capture starts.<br> When canvasRotation is true, the screen data rotation feature is enabled, and the captured screen data stays upright. When canvasRotation is false, the screen data rotation feature is disabled, and the captured screen data is not automatically kept upright.<br> The default value is false. |
| [struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)](#oh_avscreencapture_createcontentfilter) | Creates a ContentFilter. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_releasecontentfilter) | Releases the ContentFilter. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)](#oh_avscreencapture_contentfilter_addaudiocontent) | Adds a filterable audio content type to the ContentFilter instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_excludecontent) | Sets the content filter ContentFilter for the OH_AVScreenCapture instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_contentfilter_addwindowcontent) | Adds a list of window IDs that can be filtered to the ContentFilter instance. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)](#oh_avscreencapture_resizecanvas) | Adjusts the screen resolution.<br> Call this method to set the resolution of the captured screen data. width is the width of the screen, and height is the height of the screen.<br> This interface currently supports only the scenario of obtaining the stream during screen capture, not the scenario of saving the recording to a file. In addition, the caller of this interface and the consumer of the video data must ensure that they can support changes in the resolution of the received video data. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_skipprivacymode) | Exempts privacy windows during screen capture. Call this before screen capture starts.<br> An application can exempt only its own privacy windows by calling this method. windowIDs is a pointer to the IDs of the privacy windows to be exempted, and windowCount is the length of the privacy window ID list. Currently, the IDs of all privacy subwindows and the main window must be passed in for exemption. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)](#oh_avscreencapture_setmaxvideoframerate) | Sets the maximum frame rate during screen capture.<br> Call this interface after screen capture starts.<br> Call this method to set the maximum frame rate during screen capture. frameRate is the desired maximum frame rate.<br> When setting the maximum frame rate with this interface, the actually set frame rate is limited by the device capability and determined by the underlying system capability.<br> Currently there is no limit on the maximum input value of this interface, but the highest supported frame rate is 60 FPS. When the input value exceeds 60 FPS, it is processed as 60 FPS. When it does not exceed the upper limit, the actual input value is used. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)](#oh_avscreencapture_showcursor) | Sets the cursor display switch. Call this before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)](#oh_avscreencapture_setdisplaycallback) | Sets the callback for obtaining the ID of the screen being captured. |
| [OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)](#oh_avscreencapture_createcapturestrategy) | Creates a capture strategy object. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)](#oh_avscreencapture_releasecapturestrategy) | Releases the capture strategy object. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)](#oh_avscreencapture_setcapturestrategy) | Sets the capture strategy for the specified OH_AVScreenCapture instance.<br> Call this interface before screen capture starts. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforcanvasfollowrotation) | Sets the configuration for the screen capture to automatically follow rotation. Setting it to true means following screen rotation and automatically swapping the virtual screen size after landscape/portrait rotation, ensuring that the output image follows the rotation in a timely manner.<br> After configuring whether to automatically follow rotation, you do not need to manually call [OH_AVScreenCapture_ResizeCanvas](#oh_avscreencapture_resizecanvas) after a screen rotation event occurs. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforkeepcaptureduringcall) | Sets whether to keep screen capture during a cellular call.<br> When value is set to true and a cellular call is answered during screen capture, for privacy reasons, the sound of the call from both parties (the local microphone and the other party's voice) is not recorded, while other system sounds are recorded normally. After the call ends, the screen capture framework resumes microphone recording. Note that if the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow background applications to start microphone recording. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)](#oh_avscreencapture_setcapturecontentchangedcallback) | Sets the callback event for changes in the captured screen content. Call this before screen capture starts. When the content in the capture area changes (for example, window content updates or window switching), the application is notified through this callback. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture \*capture, uint64_t displayId, OH_Rect\* area)](#oh_avscreencapture_setcapturearea) | Sets or updates the capture area.<br> This interface can be called before or after screen capture starts. The coordinates and width/height cannot be negative, and the capture area cannot span screens. If setting the area position fails, capture continues based on the previous area. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode(OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)](#oh_avscreencapture_strategyforprivacymaskmode) | Sets the privacy window masking mode. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)](#oh_avscreencapture_setselectioncallback) | Registers the callback for the user's selection on the recording source confirmation UI. Call this before screen capture starts. When screen capture starts, the system pops up a confirmation UI for the user to select the capture target (screen, window, or application), and the user's selection result is returned to the application through this callback. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo \*selection, int32_t\* type)](#oh_avscreencapture_getcapturetypeselected) | Obtains the type of the screen capture target selected by the user on the confirmation UI. Used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo \*selection, uint64_t\* displayId)](#oh_avscreencapture_getdisplayidselected) | Obtains the ID of the screen selected by the user on the confirmation UI for recording. Used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforbframesencoding) | Sets whether to enable B-frame encoding for the CaptureStrategy instance, to reduce the size of the recording file.<br> For the constraints and limitations related to B-frame video encoding, see [Constraints](../../media/avcodec/video-encoding-b-frame.md#constraints) for B-frame video encoding. If the current conditions do not meet the constraints and limitations of B-frame video encoding, a video without B-frames is recorded normally and no error is returned. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpickerpopup) | Sets whether to pop up the screen capture Picker. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode(OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)](#oh_avscreencapture_strategyforfillmode) | Sets the fill mode of the captured image in the target area. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_presentpicker) | After screen capture starts, call this interface to pop up the picker again to dynamically update the recording source (window or screen). The original recording process is not interrupted while updating the recording source.<br> After dynamically updating the recording source through the picker, recording can be performed based on the new recording source. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)](#oh_avscreencapture_setcaptureareahighlight) | Sets the highlight mode for the screen capture area. During screen capture, the specified capture area can be highlighted to distinguish the visual effect between the capture area and non-capture areas, helping users identify the current recording range. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)](#oh_avscreencapture_setpickermode) | Sets the Picker display mode. Defines the type of content displayed in the picker, suitable for scenarios where you need to control the content shown on the Picker UI, such as allowing users to select only screens, only windows, or both screens and windows. The mode change takes effect the next time [OH_AVScreenCapture_PresentPicker](#oh_avscreencapture_presentpicker) is called. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)](#oh_avscreencapture_excludepickerwindows) | Hides the specified windows on the Picker UI. Call this interface before the picker UI is displayed to filter and hide the specified windows. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t\*\* displayIds, size_t *count)](#oh_avscreencapture_getmultidisplayidsselected) | Obtains the list of DisplayIDs selected by the user on the picker page for recording. Used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)](#oh_avscreencapture_getmultidisplaycapturecapability) | Obtains multi-screen recording capability information to determine whether the multiple screens selected by the user support combined recording. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)](#oh_avscreencapture_setprivacyprotectcallback) | Sets the privacy protection callback function, used to respond to privacy protection events generated by screen capture. This interface must be called before screen capture starts. During screen capture, when privacy protection information is modified, the callback is triggered to report the privacy protection status to the application. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpause) | Allows pausing screen capture. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_pausescreencapture) | Pauses screen capture. |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_resumescreencapture) | Resumes screen capture. |

## Function Description

### OH_AVScreenCapture_Create()

```c
struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)
```

**Description**

Creates an OH_AVScreenCapture instance.<br> Release the instance by calling [OH_AVScreenCapture_Release](#oh_avscreencapture_release).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Return**

| Type | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) * | Pointer to an OH_AVScreenCapture instance, used for subsequent screen capture operations, parameter configuration, and callback settings. |

### OH_AVScreenCapture_Init()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)
```

**Description**

Initializes the parameters related to [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md), including the delivered audio microphone sampling parameters (optional), internal audio recording sampling parameters, and video resolution parameters.<br> In the screen capture to file scenario, the application must ensure that the video encoding parameters, video sampling parameters, audio encoding parameters, and internal audio recording sampling parameters are all valid, and that the audio microphone sampling parameters are valid (optional).<br> In the stream capture scenario, the application must ensure that at least one of the internal audio recording sampling parameters and the video sampling parameters is valid, and that the audio microphone sampling parameters are valid (optional).<br> Because the members of a struct variable are not initialized when the variable is initialized, the application must correctly set each parameter according to the usage scenario. It is recommended that the application first set all memory bytes of the OH_AVScreenCaptureConfig struct variable to 0, and then set valid parameters according to the screen capture scenario.<br> For the audio sampling parameter struct [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md), if both audioSampleRate and audioChannels are 0, the screen capture instance OH_AVScreenCapture ignores the audio parameters of this type and does not collect audio data of this type.<br> For the video sampling parameter struct [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md), if both videoFrameWidth and videoFrameHeight are 0, the screen capture instance OH_AVScreenCapture ignores the corresponding video parameters and does not collect screen data. Call OH_AVScreenCapture_Create() to create an instance first, and then call this method to initialize the parameters.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) config | Parameters related to screen capture initialization.<br> Includes audio microphone sampling parameters (optional), internal audio recording sampling parameters, video resolution parameters, video encoding parameters, audio encoding parameters, and so on.<br> Configure according to the screen capture scenario: for saving to file, ensure that the video and audio encoding and sampling parameters are valid; for stream capture, ensure that at least one of the audio or video sampling parameters is valid.<br> The application must correctly set each parameter according to the usage scenario. It is recommended to first set all memory bytes of the struct to 0 and then set valid parameters. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer. Check whether the capture parameter is a valid pointer.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: operation not permitted, initialization configuration failed. Check whether the screen capture initialization parameters are configured correctly. |

### OH_AVScreenCapture_StartScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen capture and collects raw streams.

After this API is called, you can perform the following operations:

1. Listen for whether streams are generated through the [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) callback.

2. Listen for the start status through the [OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange) callback.

3. Call [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer) to obtain the audio buffer.

4. Call [OH_AVScreenCapture_AcquireVideoBuffer](#oh_avscreencapture_acquirevideobuffer) to obtain the video buffer, thereby obtaining the raw streams of the screen capture.

Unlike [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording) and [OH_AVScreenCapture_StartScreenCaptureWithSurface](#oh_avscreencapture_startscreencapturewithsurface), this API is used to obtain real-time raw audio and video stream data, and is suitable for scenarios where the streams need to be processed secondarily. [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording) is used to save the screen capture content directly to a file, and is suitable for scenarios where only the screen capture needs to be saved. [OH_AVScreenCapture_StartScreenCaptureWithSurface](#oh_avscreencapture_startscreencapturewithsurface) outputs data in Surface mode, and is suitable for scenarios where the data needs to be rendered directly or shared with other components.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer. Check whether the capture parameter is a valid pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20) if the device does not support this operation. Check whether the device supports the screen capture function.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted, the privacy permission fails to be enabled (apply for the required privacy permission), or the screen capture fails to start. |

### OH_AVScreenCapture_StopScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen capture. This API is used together with [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture). After this API is called, screen capture or screen sharing stops for the application that calls this API, and the microphone is released.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer. Check whether the parameter is a valid pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and stopping screen capture fails. Ensure that screen capture has been started. |

### OH_AVScreenCapture_StartScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen capture. Calling this API saves the screen capture file. It is used together with OH_AVScreenCapture_StopScreenRecording.

For the screen capture to file scenario, valid video encoding parameters, audio encoding parameters, and so on must be configured during initialization. For details, see [OH_AVScreenCapture_Init](#oh_avscreencapture_init).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer. Check whether the parameter is a valid pointer.<br>         AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20): the device does not support this operation. Check whether the device supports screen capture.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. Failed to enable the privacy permission or to start screen recording. Check whether the privacy permission settings or the screen capture configuration is correct. |

### OH_AVScreenCapture_StopScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen capture. This API is used together with [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer. Check whether the parameter is a valid pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and stopping screen capture fails. Ensure that recording has been started. |

### OH_AVScreenCapture_AcquireAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)
```

**Description**

Obtains the audio buffer. When calling this API, the application must allocate memory of the size corresponding to the audiobuffer struct; otherwise, the acquisition of the audio buffer is affected.<br> Since API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

After the audio buffer is used, call [OH_AVScreenCapture_ReleaseAudioBuffer](#oh_avscreencapture_releaseaudiobuffer) to release the corresponding audio buffer.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) **audiobuffer | Struct that stores the audio buffer. Through this struct, the audio buffer and information such as the buffer timestamp are obtained. |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio buffer, which distinguishes the external stream recorded by the microphone from the internal stream of the audio played by the system. The external stream applies to scenarios where external sound needs to be recorded, and the internal stream applies to scenarios where system sound needs to be recorded. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer or the input parameter audiobuffer is a null pointer. Check whether the parameters are valid pointers.<br>         AV_SCREEN_CAPTURE_ERR_NO_MEMORY: insufficient memory, and the audiobuffer allocation failed. Release resources and retry, or check whether the system memory is sufficient.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted, and enabling the privacy permission failed or obtaining the audio buffer failed. Check the privacy permission settings or whether the screen capture state is correct. |

### OH_AVScreenCapture_AcquireVideoBuffer()

```c
OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)
```

**Description**

Obtains the video buffer. An application calls this API to obtain the video buffer, timestamp, and other information.<br> After the buffer is used, call OH_AVScreenCapture_ReleaseVideoBuffer to release the video buffer.<br> Since API version 12, it is recommended that you use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t *fence | Display-related parameter information and synchronization control of the video frame. This parameter is used to obtain the fence information for synchronizing the video frame, ensuring that the video frame is rendered before being displayed to avoid issues such as screen tearing. |
| int64_t *timestamp | Timestamp of the video frame, in nanoseconds (ns). |
| [struct OH_Rect](capi-avscreencapture-oh-rect.md) *region | Pointer to the coordinate information related to video display. It contains the display information (x and y coordinates) and display size (width and height) of the video frame, and is used to determine the display area and range of the video frame on the screen. |

**Return**

| Type | Description |
| -- | -- |
| [OH_NativeBuffer](capi-avscreencapture-avscreencapture-oh-nativebuffer.md)* | OH_NativeBuffer object returned if the operation is successful. The video buffer, resolution, and other information can be obtained through the related APIs of the OH_NativeBuffer object. |

### OH_AVScreenCapture_ReleaseAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)
```

**Description**

Releases the buffer based on the audio type. When an audio buffer of a frame is no longer used, call this API to release the corresponding audio buffer.<br> Since API version 12, it is recommended to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio buffer, which distinguishes the external stream recorded by the microphone from the internal recording stream of the audio played by the system. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. It is not allowed when a DataCallback has been set or when releasing the audio buffer fails. Handle the audio data through the OH_AVScreenCapture_OnBufferAvailable callback. |

### OH_AVScreenCapture_ReleaseVideoBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)
```

**Description**

Releases the buffer based on the video type. When a video buffer of a frame is no longer used, call this API to release the corresponding video buffer.<br> Since API version 12, it is recommended that you use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted, that is, the API is not allowed to be used when DataCallback has been set, or the video buffer fails to be released. In this case, process the video data through the OH_AVScreenCapture_OnBufferAvailable callback. |

### OH_AVScreenCapture_SetCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)
```

**Description**

Sets a listener. Through the listener, you can listen for error information during the call and check whether video buffers and audio buffers are available.<br> Since API version 12, it is recommended that you use [OH_AVScreenCapture_SetErrorCallback](#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](#oh_avscreencapture_setdatacallback) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [struct OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) callback | OH_AVScreenCaptureCallback struct that stores the related callback function pointers. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br> Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter callback is a null pointer.<br> Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and the listener fails to be set. |

### OH_AVScreenCapture_Release()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)
```

**Description**

Releases the created OH_AVScreenCapture instance, corresponding to [OH_AVScreenCapture_Create](#oh_avscreencapture_create).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer. Check whether the parameter is a valid pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and the OH_AVScreenCapture instance fails to be released. Check whether the instance state or the calling sequence is correct. |

### OH_AVScreenCapture_SetMicrophoneEnabled()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)
```

**Description**

Sets the microphone switch. This API should be called before screen capture is started.<br> When **isMicrophone** is **true**, the microphone is enabled, and the original microphone PCM data can be obtained normally by calling [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer). When **isMicrophone** is **false**, the obtained audio data is silent.<br> The microphone switch is enabled by default.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| bool isMicrophone | Microphone switch parameter.<br> **true** indicates enabling the microphone, and **false** indicates disabling the microphone.<br> The default value is **true**. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter **capture** is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and setting the microphone switch fails. Check the microphone permission and device status. |

### OH_AVScreenCapture_SetStateCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)
```

**Description**

Sets the callback method for handling state changes. Call this method before starting screen capture.<br> After this method is called successfully, user consent is requested through a privacy dialog box when screen capture is started:<br> 1. If the user consents, the screen capture process starts. After screen capture is started successfully, the state handling callback method reports the [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_STARTED state to notify the application that screen capture has been started successfully, and a screen capture notification is displayed on the screen. If screen capture fails to start, the state handling callback method reports the failure state information (for example, if the microphone is unavailable, it reports the [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE state), or the error handling callback method [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) reports the error information.<br> 2. If the user rejects, screen capture is terminated. The state handling callback method reports the [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_CANCELED state to notify the application that the user has rejected starting screen capture, and screen capture fails to start.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange) callback | Pointer to the state handling callback method instance. It is used to listen for screen capture state changes (start success/failure, user rejection, and so on) and is triggered when the state changes. It must be set before screen capture. If it is not set, state changes cannot be obtained. |
| void *userData | Pointer to the custom data provided by the application. It is passed back as an input parameter when the state handling callback method is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter callback is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_NO_MEMORY if the memory is insufficient and memory allocation fails.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and setting StateCallback fails. Check whether the callback function is valid and ensure that the callback is set at the correct time. |

### OH_AVScreenCapture_SetDataCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)
```

**Description**

Sets the data processing callback method, which is called before recording starts.<br> When an audio or video data buffer is available during the OH_AVScreenCapture operation, this data processing callback method is invoked.<br> The application needs to process microphone audio, internal audio, and video data in this data processing callback method based on the data type. After this data processing callback method returns, the data buffer is no longer valid.<br> After this method is called successfully:<br> 1. When an audio or video buffer is available during the OH_AVScreenCapture operation, the data callback methods [OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable) and [OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable) set through [OH_AVScreenCapture_SetCallback](#oh_avscreencapture_setcallback) are no longer invoked.<br> 2. The application is not allowed to call the following four methods: [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer), [OH_AVScreenCapture_ReleaseAudioBuffer](#oh_avscreencapture_releaseaudiobuffer), [OH_AVScreenCapture_AcquireVideoBuffer](#oh_avscreencapture_acquirevideobuffer), and [OH_AVScreenCapture_ReleaseVideoBuffer](#oh_avscreencapture_releasevideobuffer). Calling them directly returns a failure.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) callback | Pointer to the data processing callback method instance. It is used to obtain audio and video buffers through the callback. It is triggered when a buffer is available and must be set before recording. After it is set, data must be processed in the callback. |
| void *userData | Pointer to the custom data provided by the application, which is passed back as an input parameter when the data processing callback method is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter callback is a null pointer. Check whether the parameters are valid pointers.<br>         Returns AV_SCREEN_CAPTURE_ERR_NO_MEMORY if the memory is insufficient and memory allocation fails. Release resources and try again, or check whether the system memory is sufficient.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and setting DataCallback fails. Check whether the callback is set at the correct time. |

### OH_AVScreenCapture_SetErrorCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)
```

**Description**

Sets the error handling callback method, which is called before recording starts.<br> Call this method to set the error handling callback method. When an error occurs on the OH_AVScreenCapture instance, the error handling callback method will be invoked.<br> After this setting method is successfully called, when an error occurs on the OH_AVScreenCapture instance, the error handling callback method [OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror) set through [OH_AVScreenCapture_SetCallback](#oh_avscreencapture_setcallback) will no longer be invoked.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) callback | Pointer to the error handling callback method instance. It is used to listen for error information during screen capture and is triggered when an error occurs. It must be set before recording. If it is not set, error details cannot be obtained. |
| void *userData | Pointer to the custom data provided by the application, which is passed back as an input parameter when the error handling callback method is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer or the input parameter callback is a null pointer. Check whether the parameters are valid pointers.<br>         AV_SCREEN_CAPTURE_ERR_NO_MEMORY: insufficient memory, memory allocation failed. Release resources and try again, or check whether the system memory is sufficient.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted, and setting ErrorCallback failed. Check whether the callback setting timing is correct. |

### OH_AVScreenCapture_StartScreenCaptureWithSurface()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)
```

**Description**

Starts screen capture in Surface mode.

Before calling this API, you must call OH_AVScreenCapture_Create() to create an instance and OH_AVScreenCapture_Init() to initialize the parameters.

Unlike [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture), this API outputs video data directly to a specified Surface window by passing in an OHNativeWindow, which is suitable for scenarios where the screen capture data needs to be rendered to a specific window. In contrast, OH_AVScreenCapture_StartScreenCapture obtains raw stream data through a callback, which is suitable for scenarios where the audio and video data needs to be processed by the caller.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OHNativeWindow](../apis-arkgraphics2d/capi-nativewindow-nativewindow.md) *window | Pointer to an OHNativeWindow instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer, or the input parameter window is a null pointer, or the windowSurface pointed to by window is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20): the device does not support this operation. Check whether the device supports the screen capture function.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. Failed to enable the privacy permission or failed to start ScreenCaptureWithSurface. |

### OH_AVScreenCapture_SetCanvasRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)
```

**Description**

Sets whether to enable the screen data rotation function of the captured screen. This API must be called before screen capture is started.<br> When **canvasRotation** is **true**, the screen data rotation function of the captured screen is enabled, and the captured screen data remains upright. When **canvasRotation** is **false**, the screen data rotation function of the captured screen is disabled, and the captured screen data does not automatically remain upright.<br> The default value is **false**.

Different from [OH_AVScreenCapture_StrategyForCanvasFollowRotation](#oh_avscreencapture_strategyforcanvasfollowrotation), this API is a static rotation setting that keeps the screen capture data upright only when **canvasRotation** is **true**. In contrast, StrategyForCanvasFollowRotation is an automatic follow-rotation policy that automatically swaps the virtual screen dimensions to keep the image upright when the screen rotates. It is recommended to use this API only when a fixed upright output is required, and to use StrategyForCanvasFollowRotation when dynamic rotation following is required.

> **NOTE**
>
> Since API version 20, foldable PCs and 2-in-1 devices are supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| bool canvasRotation | Whether to enable the screen data rotation function of the captured screen.<br> **true** means to enable the screen data rotation function of the captured screen, and the captured screen data remains upright; **false** means to disable the screen data rotation function of the captured screen, and the captured screen data follows the screen rotation.<br> The default value is **false**. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter **capture** is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20) if the device does not support this operation. Check whether the device supports screen capture.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and setting the screen data rotation of the captured screen fails. |

### OH_AVScreenCapture_CreateContentFilter()

```c
struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)
```

**Description**

Creates a ContentFilter.

After creation, add the content to be filtered through [OH_AVScreenCapture_ContentFilter_AddAudioContent](#oh_avscreencapture_contentfilter_addaudiocontent) or [OH_AVScreenCapture_ContentFilter_AddWindowContent](#oh_avscreencapture_contentfilter_addwindowcontent), set the filter through [OH_AVScreenCapture_ExcludeContent](#oh_avscreencapture_excludecontent), and call [OH_AVScreenCapture_ReleaseContentFilter](#oh_avscreencapture_releasecontentfilter) to release it after use. This applies to scenarios where specific content (such as sensitive windows or specific audio types) needs to be filtered during screen capture to protect privacy or meet business requirements.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Return**

| Type | Description |
| -- | -- |
| struct [OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) * | Pointer to the OH_AVScreenCapture_ContentFilter instance returned if the operation is successful, which is used to configure the sound types and window content to be filtered. A null pointer is returned otherwise. |

### OH_AVScreenCapture_ReleaseContentFilter()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Releases the ContentFilter.

Used together with [OH_AVScreenCapture_CreateContentFilter](#oh_avscreencapture_createcontentfilter) to release the created ContentFilter instance. The ContentFilter can be released after it is set to the OH_AVScreenCapture instance through [OH_AVScreenCapture_ExcludeContent](#oh_avscreencapture_excludecontent).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter filter is a null pointer. |

### OH_AVScreenCapture_ContentFilter_AddAudioContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)
```

**Description**

Adds a filterable sound type to a ContentFilter instance.

You must first call OH_AVScreenCapture_CreateContentFilter() to create a ContentFilter instance. After the addition is complete, call OH_AVScreenCapture_ExcludeContent() to apply the ContentFilter to the OH_AVScreenCapture instance. This is suitable for scenarios where specific sounds need to be excluded from the screen capture audio, such as filtering out system notification sounds when recording a tutorial or excluding audio from other applications when recording a meeting. The calling sequence is CreateContentFilter → AddAudioContent/AddWindowContent → ExcludeContent → ReleaseContentFilter.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to an OH_AVScreenCapture_ContentFilter instance. |
| [OH_AVScreenCaptureFilterableAudioContent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturefilterableaudiocontent) content | Filterable sound type. Specifies the type of audio content to be excluded from the screen capture. Select the corresponding enum value based on the type of audio content to be filtered. Multiple audio types can be combined to filter multiple types. For details about the enum values and their applicable scenarios, see [OH_AVScreenCaptureFilterableAudioContent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturefilterableaudiocontent). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter filter is a null pointer or the input parameter content is invalid. |

### OH_AVScreenCapture_ExcludeContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Sets the content filter ContentFilter of the OH_AVScreenCapture instance.

Applies to scenarios where specific audio or window content needs to be excluded from screen capture, such as excluding sensitive windows for privacy protection and avoiding recording irrelevant system notification sounds.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter filter is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_UNSUPPORT if the operation is not supported. For streams, call the AudioCapturer API at startup.<br>         For capture files, call the Recorder API at startup. |

### OH_AVScreenCapture_ContentFilter_AddWindowContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)
```

**Description**

Adds a list of window IDs that can be filtered to a ContentFilter instance.

This API is applicable to scenarios where specific windows need to be excluded from the screen capture, for example, excluding a chat window when recording a tutorial, or excluding the notification panel when recording a presentation.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to an OH_AVScreenCapture_ContentFilter instance. |
| int32_t *windowIDs | Pointer to the array of window IDs to be filtered. The window IDs can be obtained through the window management APIs. |
| int32_t windowCount | Length of the window ID list. It must be a positive integer and consistent with the actual length of the windowIDs array. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code. Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful; returns a specific error code otherwise. |

### OH_AVScreenCapture_ResizeCanvas()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)
```

**Description**

Adjusts the resolution of the captured screen data.<br> Call this method to set the resolution of the captured screen data, where width is the width of the screen and height is the height of the screen.<br> This API currently supports only the screen capture encoding scenario, and does not support the screen capture to file scenario. The application must ensure that it can support changes in the resolution of the received video data.

Constraints:

- This API can be called only during the screen capture running phase.
- When the automatic follow rotation configuration [OH_AVScreenCapture_StrategyForCanvasFollowRotation](#oh_avscreencapture_strategyforcanvasfollowrotation) is set, calling this API to adjust the screen capture resolution is not supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t width | Width of the captured screen. The unit is pixel (px). The value must be a positive integer, and it is recommended not to exceed the width of the device screen resolution. It must be used together with height and set based on actual recording requirements. Only the screen capture encoding scenario is supported, and the screen capture to file scenario is not supported. Calling this API when the automatic follow rotation configuration is set is not supported. |
| int32_t height | Height of the captured screen. The unit is pixel (px). The value must be a positive integer, and it is recommended not to exceed the height of the device screen resolution. It must be used together with width and set based on actual recording requirements. Only the screen capture encoding scenario is supported, and the screen capture to file scenario is not supported. Calling this API when the automatic follow rotation configuration is set is not supported. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20): the device does not support this operation. Check whether the device supports the screen capture function.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. |

### OH_AVScreenCapture_SkipPrivacyMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)
```

**Description**

Exempts privacy windows during screen capture. This API must be called before screen capture starts.<br> An application can exempt only its own privacy windows by calling this API. windowIDs is a pointer to the IDs of the privacy windows to be exempted, and windowCount is the length of the privacy window ID list. Currently, the IDs of all privacy subwindows and the main window must be passed in for exemption.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t *windowIDs | Pointer to the privacy window IDs. |
| int32_t windowCount | Length of the privacy window ID list. It must be a positive integer and match the actual length of the windowIDs array. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br> Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer.<br> Returns AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20) if the device does not support this operation. Check whether the device supports screen capture.<br> Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted. |

### OH_AVScreenCapture_SetMaxVideoFrameRate()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)
```

**Description**

Sets the maximum frame rate for screen capture.<br> This API should be called after screen capture starts.<br> Calling this API sets the maximum frame rate for screen capture, where frameRate is the desired maximum frame rate.<br> When this API sets the maximum frame rate, the actually applied frame rate is limited by the device capability and determined by the underlying system capability.<br> Currently, no upper limit is imposed on the input parameter, but the highest supported frame rate is 60 FPS. If the input value exceeds 60 FPS, it is processed as 60 FPS. If it does not exceed the upper limit, it is processed according to the actual input value.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 14

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t frameRate | Maximum frame rate for screen capture, in frames per second (FPS). The highest supported frame rate is 60 FPS. A low frame rate (1-15) is suitable for static content, a medium frame rate (16-30) for common scenarios, and a high frame rate (31-60) for scenarios requiring high smoothness. The actual frame rate is limited by the device capability. If the input value exceeds 60 FPS, it is processed as 60 FPS. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter frameRate is not supported.<br>         Returns AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20) if the device does not support this operation. Check whether the device supports screen capture.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted. |

### OH_AVScreenCapture_ShowCursor()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)
```

**Description**

Sets whether to show the cursor. This API must be called before screen capture starts.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| bool showCursor | Cursor display parameter.<br> The value **true** means to show the cursor, and **false** means to hide the cursor.<br> The default value is **true**. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_UNSUPPORT (added in API version 20): the device does not support this operation. Check whether the device supports screen capture.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. Failed to set the cursor. |

### OH_AVScreenCapture_SetDisplayCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)
```

**Description**

Sets the callback for obtaining the screen ID of the captured screen. Call this API before starting the recording.

When multiple screens exist in the system, this callback notifies the application of the screen ID selected by the user during screen capture startup, so that the application can determine the target screen for screen capture.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnDisplaySelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_ondisplayselected) callback | Pointer to the callback method instance for the screen ID of the captured screen. It is used to obtain the screen ID selected by the user for recording, and is triggered after the user selects a screen. It must be set before recording. If it is not set, the screen ID selected by the user cannot be obtained. |
| void *userData | Pointer to the custom data provided by the application. It is passed back as an input parameter when the callback method for the screen ID of the captured screen is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the input parameter callback is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_NO_MEMORY if the memory is insufficient and memory allocation fails.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_STATE if the callback is not called before the start method. |

### OH_AVScreenCapture_CreateCaptureStrategy()

```c
OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)
```

**Description**

Creates a screen capture policy object.

Used to configure various policy parameters for screen capture. You can use the StrategyFor* series APIs to configure policies such as rotation following, keeping screen capture during calls, B-frame encoding, and Picker pop-up.

After use, call [OH_AVScreenCapture_ReleaseCaptureStrategy](#oh_avscreencapture_releasecapturestrategy) to release it.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Return**

| Type | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md)* | Pointer to the OH_AVScreenCapture_CaptureStrategy instance returned on success, which is used to configure the screen capture policy (such as automatic rotation following, keeping screen capture during calls, and B-frame encoding). A null pointer is returned otherwise. |

### OH_AVScreenCapture_ReleaseCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)
```

**Description**

Releases the screen capture policy object.

Used in pair with [OH_AVScreenCapture_CreateCaptureStrategy](#oh_avscreencapture_createcapturestrategy) to release the created CaptureStrategy instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md)* strategy | Pointer to the screen capture policy object. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter strategy is a null pointer. |

### OH_AVScreenCapture_SetCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)
```

**Description**

Sets the capture policy for an OH_AVScreenCapture instance.<br> This API should be called before screen capture starts.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the capture policy object. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture or strategy is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_STATE if this API is called after screen capture starts. |

### OH_AVScreenCapture_StrategyForCanvasFollowRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets the configuration for automatically following screen rotation during screen capture. When set to true, the virtual screen follows the screen rotation, and after a landscape-portrait rotation, the virtual screen size is automatically swapped to ensure that the output image follows the rotation in a timely manner.<br> After the configuration for automatically following rotation is set, you do not need to manually call [OH_AVScreenCapture_ResizeCanvas](#oh_avscreencapture_resizecanvas) after a screen rotation event occurs.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance. |
| bool value | Whether the width and height of the virtual screen rotate with the screen rotation.<br> true indicates that the width and height of the virtual screen rotate with the screen rotation, and false indicates that the width and height of the virtual screen remain as initially set.<br> The default value is false. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter strategy is a null pointer. |

### OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to keep screen capture during a cellular call.<br> If value is set to true, when a cellular call is answered during screen capture, the voices of both parties (the local microphone and the remote party) are not recorded for privacy reasons, while other system sounds are recorded normally. After the call ends, the screen capture framework resumes microphone recording. Note that if the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow a background application to start microphone recording.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy object. |
| bool value | Whether screen capture is allowed during a cellular call.<br> The value true means that screen capture is allowed during a cellular call, and false means that screen capture is not allowed during a cellular call.<br> The default value is false. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter strategy is a null pointer. |

### OH_AVScreenCapture_SetCaptureContentChangedCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)
```

**Description**

Sets the callback event for screen capture content changes. This API must be called before screen capture starts.

When the content within the screen capture area changes (for example, window content updates or window switching), the application is notified through this callback.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnCaptureContentChanged](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_oncapturecontentchanged) callback | Pointer to the callback method instance for screen capture content changes. It is used to listen for screen capture content change events and is triggered when the content changes. It must be set before screen capture starts. If it is not set, content change information cannot be obtained. |
| void *userData | Pointer to the custom data provided by the application. It is passed back as an input parameter when the screen capture content change callback method is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: the operation is successful.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: invalid parameter. The input parameter capture or callback is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. Failed to set the screen capture content callback. |

### OH_AVScreenCapture_SetCaptureArea()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)
```

**Description**

Sets or updates the capture area.<br> This API can be called before or after screen capture starts. The coordinates, width, and height set cannot be negative, and the capture area cannot span multiple screens. If the area setting fails, the previous area is still used for capture.

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| uint64_t displayId | ID of the screen on which screen capture is to be performed. The list of screen IDs supported by the device can be obtained through the OH_AVScreenCapture_OnDisplaySelected callback or system APIs. In a multi-screen scenario, specify the ID of the screen to be captured. In a single-screen scenario, the default screen ID can be used. |
| [OH_Rect](capi-avscreencapture-oh-rect.md)* area | Pointer to the capture area struct, which specifies the area range for screen capture. It contains the position coordinates (x and y) and dimensions (width and height) of the area. The coordinates, width, and height set cannot be negative, and the capture area cannot span multiple screens. If the setting fails, the previous area is still used for capture. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer, the input displayId does not exist, or the input capture area is invalid. |

### OH_AVScreenCapture_StrategyForPrivacyMaskMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode(OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)
```

**Description**

Sets the privacy window masking mode.

The full-screen masking mode (value=0) applies to scenarios with strict privacy protection requirements. For example, when a privacy window appears during recording of a financial application, the entire screen is masked. The privacy window masking mode (value=1) applies to scenarios where only the privacy window area needs to be masked while the rest of the content can still be recorded normally.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance. |
| int32_t value | Set this parameter to 0 to use the full-screen masking mode when a privacy window exists.<br> Set this parameter to 1 to use the privacy window masking mode when a privacy window exists. Setting this parameter to any other value returns an error.<br> The default value is 0 (full-screen masking mode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br> Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter strategy is a null pointer or the input value is invalid. |

### OH_AVScreenCapture_SetSelectionCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)
```

**Description**

Registers the callback for the confirmation UI where the user selects the recording source. This API must be called before screen capture starts.

When screen capture starts, the system displays a confirmation UI for the user to select the capture target (screen, window, or application). The user's selection is returned to the application through this callback.

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the screen capture instance for which the callback is to be registered. |
| [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback | Callback invoked to notify the application for logical processing after the user confirms the selection in the UI. It is used to obtain the information about the capture target (screen or window) selected by the user in the Picker UI. It must be set before screen capture starts. If it is not set, the user's selection result cannot be obtained. |
| void *userData | Pointer to the control block provided by the application, which is passed back as an input parameter when the callback method is invoked. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer. |

### OH_AVScreenCapture_GetCaptureTypeSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)
```

**Description**

Obtains the type of the screen capture object selected by the user on the confirmation screen. This API is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends.

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance. |
| int32_t* type | Type of the capture object selected by the user. The value 0 indicates the screen, 1 indicates a window, and 2 indicates an application. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter selection is a null pointer. |

### OH_AVScreenCapture_GetDisplayIdSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)
```

**Description**

Obtains the ID of the screen selected by the user on the confirmation UI. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends.

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance. |
| uint64_t* displayId | Returns the ID of the screen selected by the user. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter selection is a null pointer. |

### OH_AVScreenCapture_StrategyForBFramesEncoding()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to enable B-frame encoding for a CaptureStrategy instance to reduce the size of the recorded file.<br> For the constraints and limitations of B-frame video encoding, see [Constraints](../../media/avcodec/video-encoding-b-frame.md#constraints) for B-frame video encoding. If the current conditions do not meet the constraints and limitations of B-frame video encoding, a video without B-frames is recorded normally, and no error is returned.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy object. |
| bool value | Whether to enable B-frame encoding for the screen capture file.<br> The value **true** means to enable B-frame encoding for the screen capture file, and **false** means to disable it.<br> The default value is **false**. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br> AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter **strategy** is a null pointer. |

### OH_AVScreenCapture_StrategyForPickerPopUp()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to display the screen capture Picker UI. Picker is the screen capture source selection UI, where users can select the screen or window to capture.

Applicable scenarios: display Picker when user interaction is required to select the capture source (for example, selecting a screen in a multi-screen environment); disable Picker for automatic capture when the application has explicitly specified the capture source or no user intervention is required.

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy object. |
| bool value | If this parameter is set to **false**, the application has specified the screen capture content, and Picker is not displayed after screen capture starts. If this parameter is set to **true**, Picker is displayed after screen capture starts. If not set, whether to display Picker is automatically determined based on the current capture configuration when screen capture starts. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter strategy is a null pointer or the input value is invalid. |

### OH_AVScreenCapture_StrategyForFillMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode(OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)
```

**Description**

Sets the fill mode of the captured image in the target area.

When the size of the captured image differs from that of the target output area, the fill mode determines how the image is displayed in the target area. This applies to scenarios where the screen capture frame does not match the output size and a specific adaptation mode must be specified, such as maintaining the aspect ratio without stretching in video conferences, or stretching to fill the full screen in game recording. For details, see [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode).

**Since**: 20

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy object. |
| [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode) mode | Fill mode of the captured image on the output image. Select an appropriate fill mode based on the size difference between the capture area and the output area. For details about the enum values and their applicable scenarios, see [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode).<br>Different modes determine how the captured image is scaled, cropped, or stretched in the output area. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter strategy is a null pointer. |

### OH_AVScreenCapture_PresentPicker()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)
```

**Description**

After screen capture starts, calling this API presents the picker again to dynamically update the recording source (window or screen). During the update of the recording source, the ongoing recording process is not interrupted.<br> After the recording source is dynamically updated through the picker, recording can proceed with the new recording source.

**Since**: 22

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted. |

### OH_AVScreenCapture_SetCaptureAreaHighlight()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)
```

**Description**

Sets the highlight mode of the screen capture area.

During screen capture, the specified capture area can be highlighted to distinguish the visual effect between the capture area and the non-capture area, helping users identify the current screen capture range. This is applicable to scenarios where the boundary of the capture area needs to be highlighted during screen capture, such as helping users identify the current recording range in multi-area recording, or marking key operation areas in teaching demonstrations.

> **NOTE**
>
> This function takes effect only when [OH_CaptureMode](capi-native-avscreen-capture-base-h.md#oh_capturemode) is set to OH_CAPTURE_SPECIFIED_WINDOW for recording a specified window, or when a window is selected through Picker for recording.

**Since**: 22

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) config | Highlight parameters for this screen capture. Set this parameter when the capture area needs to be visually highlighted during recording. If it is not set or an empty configuration is passed in, the highlight mode is not used by default. You can configure properties such as the border style and color of the highlight area as needed. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the value of config is invalid. |

### OH_AVScreenCapture_SetPickerMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)
```

**Description**

Sets the Picker display mode. Defines the type of content displayed in the Picker, applicable to scenarios where the content displayed in the Picker interface needs to be controlled, such as allowing the user to select only a screen, only a window, or both a screen and a window for selection. The mode change takes effect the next time the [OH_AVScreenCapture_PresentPicker](#oh_avscreencapture_presentpicker) function is called.

**Since**: 22

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_CapturePickerMode](capi-native-avscreen-capture-base-h.md#oh_capturepickermode) pickerMode | Picker display mode, which defines the type of content displayed in the Picker.<br>For the effect of each mode enum value, see [OH_CapturePickerMode](capi-native-avscreen-capture-base-h.md#oh_capturepickermode). Different modes determine the type of screen capture object available for the user to select in the Picker. Select the content type to display based on application requirements (for example, display only screens, only windows, or both). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input parameter capture is a null pointer or the pickerMode parameter value is invalid.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. |

### OH_AVScreenCapture_ExcludePickerWindows()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)
```

**Description**

Hides the specified windows in the Picker UI. Call this API before the Picker UI is displayed to filter and hide the specified windows.

**Since**: 22

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| const int32_t *excludedWindowIDs | Array of IDs of the windows to hide (existing windows). |
| uint32_t windowCount | Length of the array of window IDs to hide. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input parameter capture is a null pointer or the window ID parameter value is invalid.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted. |

### OH_AVScreenCapture_GetMultiDisplayIdsSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t** displayIds, size_t *count)
```

**Description**

Obtains the list of display IDs selected by the user on the picker page for screen capture. This API is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The selection pointer is destroyed after the callback ends.

**Since**: 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance. |
| uint64_t** displayIds | Array of display IDs selected by the user. The memory of the displayIds parameter is managed by OH_AVScreenCapture_UserSelectionInfo and does not need to be released manually. |
| size_t *count | Number of display IDs selected by the user. The value must be greater than or equal to 1 and consistent with the actual length of the displayIds array. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: the operation is successful.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the selection parameter that contains the user selection information is a null pointer. |

### OH_AVScreenCapture_GetMultiDisplayCaptureCapability()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)
```

**Description**

Obtains the multi-display capture capability information to determine whether the multiple screens selected by the user support joint capture.

**Since**: 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| uint64_t *displayIds | Array of the display IDs selected by the user. |
| size_t count | Number of the display IDs selected by the user. |
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) *capability | Pointer to an OH_MultiDisplayCapability instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input screen capture instance parameter capture is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted and data acquisition fails. |

### OH_AVScreenCapture_SetPrivacyProtectCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)
```

**Description**

Sets a privacy protection callback to respond to privacy protection events generated during screen capture. This API must be called before screen capture starts.

During screen capture, when privacy protection information is modified, the callback is triggered to report the privacy protection status to the application.

**Since**: 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCapture_OnPrivacyProtect](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onprivacyprotect) callback | Privacy protection callback. If it is not set, privacy protection events cannot be obtained. |
| void *userData | Pointer to the custom data provided by the application, which is passed back as an input parameter when the privacy protection callback is invoked. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input screen capture instance is a null pointer or the input callback is a null pointer. |

### OH_AVScreenCapture_StrategyForPause()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Allows pausing screen capture.

Applies to scenarios where screen capture may need to be temporarily paused, for example, when the user switches applications or answers a call and needs to interrupt recording without ending the screen capture session. When set to true, pausing is allowed; when set to false, the screen capture process cannot be paused. After value is set to true, OH_AVScreenCapture_PauseScreenCapture can be called to pause screen capture and OH_AVScreenCapture_ResumeScreenCapture can be called to resume screen capture during the running phase of screen capture. This policy must be configured through OH_AVScreenCapture_SetCaptureStrategy before screen capture starts.

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance. |
| bool value | Whether to allow pausing screen capture. The value true means allowed, and false means not allowed. The default value is false. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if strategy is a null pointer. |

### OH_AVScreenCapture_PauseScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Pauses screen capture. This API should be called after screen capture is started.

Used together with [OH_AVScreenCapture_ResumeScreenCapture](#oh_avscreencapture_resumescreencapture). After this API is called, screen data capture is paused, and the data already captured remains valid. Before calling this API, you need to enable the pause policy through [OH_AVScreenCapture_StrategyForPause](#oh_avscreencapture_strategyforpause) (set value to true), and complete the policy configuration through OH_AVScreenCapture_SetCaptureStrategy before screen capture is started.

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the initialized screen capture instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         AV_SCREEN_CAPTURE_ERR_OK: success.<br>         AV_SCREEN_CAPTURE_ERR_INVALID_VAL: the input screen capture instance is a null pointer.<br>         AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. |

### OH_AVScreenCapture_ResumeScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Resumes screen capture. It should be called after screen capture is started.

Used together with [OH_AVScreenCapture_PauseScreenCapture](#oh_avscreencapture_pausescreencapture), it resumes screen data capture after being called. Before calling this API, you need to enable the pause policy through OH_AVScreenCapture_StrategyForPause (set value to true), and complete the policy configuration through OH_AVScreenCapture_SetCaptureStrategy before screen capture is started.

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the initialized screen capture instance. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Result code.<br>         Returns AV_SCREEN_CAPTURE_ERR_OK if the operation is successful.<br>         Returns AV_SCREEN_CAPTURE_ERR_INVALID_VAL if the input screen capture instance is a null pointer.<br>         Returns AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT if the operation is not permitted. |
