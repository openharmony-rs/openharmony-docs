# native_avscreen_capture_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## Overview

Declares the structs, character constants, enums, variables, and functions used for running screen capture. Screen Recorder allows you to set the recording mode and audio/video information by configuring parameters, and obtain the recording data, status changes, and privacy protection event notifications through callback functions. It supports multiple recording modes (main screen, specified screen, and specified window), audio source types (microphone, internal recording, and specified app audio), privacy protection, and content filtering. It is applicable to scenarios where screen images and audio data need to be captured. For details about the design logic, see [AVScreenCapture](capi-avscreencapture.md).

**File to include**: <multimedia/player_framework/native_avscreen_capture_base.h>

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) | OH_AudioCaptureInfo | Describes the audio capture information.<br> When both **audioSampleRate** and **audioChannels** are **0**, the audio-related parameters are ignored and the audio data is not recorded.<br> To perform both external capture (using microphones) and internal capture, **audioSampleRate** and **audioChannels** must be the same for both audio channels.|
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) | OH_AudioEncInfo | Describes the audio encoding information.|
| [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md) | OH_AudioInfo | Describes the audio information.<br> To perform both external capture (using microphones) and internal capture, **audioSampleRate** and **audioChannels** must be the same for both audio channels. Otherwise, the recording will fail.<br> When both **audioSampleRate** and **audioChannels** for a type of audio are **0**, the audio-related parameters are ignored and the audio data is not recorded.|
| [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md) | OH_VideoCaptureInfo | Describes the video capture information. When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded.|
| [OH_VideoEncInfo](capi-avscreencapture-oh-videoencinfo.md) | OH_VideoEncInfo | Describes the video encoding information.|
| [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md) | OH_VideoInfo | Describes the video information.<br> When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded.|
| [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) | OH_RecorderInfo | Describes the recording file information.|
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) | OH_AVScreenCaptureConfig | Describes the screen capture configuration.<br> Note: If both **audioSampleRate** and **audioChannels** for a type of audio are set to **0**, parameters for this type of audio are ignored. To perform both external capture (using microphones) and internal capture, **audioSampleRate** and **audioChannels** must be the same for both audio channels. If both **videoFrameWidth** and **videoFrameHeight** are set to **0**, the video parameters are ignored.|
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md) | OH_PrivacyProtectInfo | Defines the privacy protection information.|
| [OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) | OH_AVScreenCaptureCallback | Defines all the asynchronous callback function pointers of an OH_AVScreenCapture instance. To ensure the normal running of OH_AVScreenCapture, you must register the instance of this struct with the OH_AVScreenCapture instance and process the information reported by the callback functions.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](#oh_avscreencapture_onerror) and [OH_AVScreenCapture_OnBufferAvailable](#oh_avscreencapture_onbufferavailable) instead.|
| [OH_Rect](capi-avscreencapture-oh-rect.md) | OH_Rect | Describes the width, height, and image information of the rectangle used for screen capture.|
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) | OH_AudioBuffer | Describes the configuration such as the size, type, and timestamp of audio buffer data.|
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) | OH_AVScreenCaptureHighlightConfig | Describes the style of the highlight border shown during screen capture, including its shape, thickness, and color.|
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) | OH_MultiDisplayCapability | Describes the multi-screen recording capability. It includes whether the multi-screen supports joint recording and the width and height of the screen for joint recording.|
| [OH_NativeBuffer](capi-avscreencapture-avscreencapture-oh-nativebuffer.md) | OH_NativeBuffer | Describes the native video stream class for screen capture.|
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) | OH_AVScreenCapture | Describes a screen capture instance used to obtain original video and audio streams.|
| [OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) | OH_AVScreenCapture_ContentFilter | Describes the filter used to filter audio and video content.|
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) | OH_AVScreenCapture_CaptureStrategy | Describes the screen capture strategy configured by using OH_AVScreenCapture_CaptureStrategy.|
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) | OH_AVScreenCapture_UserSelectionInfo | Describes the parameters selected by the user on the authorization UI (selection UI) by using OH_AVScreenCapture_UserSelectionInfo.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CaptureMode](#oh_capturemode) | OH_CaptureMode | Enumerates the screen capture modes.|
| [OH_AudioCaptureSourceType](#oh_audiocapturesourcetype) | OH_AudioCaptureSourceType | Enumerates the audio source types during screen capture.|
| [OH_AudioCodecFormat](#oh_audiocodecformat) | OH_AudioCodecFormat | Enumerates the audio encoding formats.|
| [OH_VideoCodecFormat](#oh_videocodecformat) | OH_VideoCodecFormat | Enumerates the video encoding formats.|
| [OH_DataType](#oh_datatype) | OH_DataType | Enumerates the data types of screen capture streams.|
| [OH_VideoSourceType](#oh_videosourcetype) | OH_VideoSourceType | Enumerates the video source formats. Currently, only the RGBA format is supported.|
| [OH_ContainerFormatType](#oh_containerformattype) | OH_ContainerFormatType | Enumerates the types of files generated during screen capture.|
| [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode) | OH_AVScreenCaptureStateCode | Enumerates the screen capture states.|
| [OH_AVScreenCaptureBufferType](#oh_avscreencapturebuffertype) | OH_AVScreenCaptureBufferType | Enumerates the buffer types.|
| [OH_AVScreenCaptureFilterableAudioContent](#oh_avscreencapturefilterableaudiocontent) | OH_AVScreenCaptureFilterableAudioContent | Enumerates the types of audio that can be added to a content filter.|
| [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent) | OH_AVScreenCaptureContentChangedEvent | Enumerates the screen capture content change events.|
| [OH_AVScreenCapture_FillMode](#oh_avscreencapture_fillmode) | OH_AVScreenCapture_FillMode | Enumerates the image fill modes.|
| [OH_ScreenCaptureHighlightMode](#oh_screencapturehighlightmode) | OH_ScreenCaptureHighlightMode | Enumerates the shapes of the highlight border shown during screen capture.|
| [OH_CapturePickerMode](#oh_capturepickermode) | OH_CapturePickerMode | Enumerates the display modes of the picker.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)](#oh_avscreencaptureonerror) | OH_AVScreenCaptureOnError | Called to notify the app when an error occurs during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](#oh_avscreencapture_onerror) instead.|
| [typedef void (\*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)](#oh_avscreencaptureonaudiobufferavailable) | OH_AVScreenCaptureOnAudioBufferAvailable | Called to notify the app when an audio buffer is available during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](#oh_avscreencapture_onbufferavailable) instead. The **OH_AVScreenCapture_OnBufferAvailable** API unifies the audio and video buffer callbacks into one API. The buffer data type is distinguished by the bufferType parameter. In addition, the **timestamp** and **userData** parameters are added. You do not need to register the audio and video callbacks separately.|
| [typedef void (\*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)](#oh_avscreencaptureonvideobufferavailable) | OH_AVScreenCaptureOnVideoBufferAvailable | Called to notify the app when a video buffer is available during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](#oh_avscreencapture_onbufferavailable) instead.|
| [typedef void (\*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)](#oh_avscreencapture_onstatechange) | OH_AVScreenCapture_OnStateChange | Called when the state changes during the running of an OH_AVScreenCapture instance.<br> This callback takes effect only after being set using the **OH_AVScreenCapture** API. If it is not set, the callback will not be invoked.<br>This callback returns the status code through the **stateCode** parameter. The state changes include starting, pausing, resuming, stopping, interrupting, and privacy scene change. For details about the status codes, see [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode).|
| [typedef void (\*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)](#oh_avscreencapture_onerror) | OH_AVScreenCapture_OnError | Called to notify the app when an error occurs during the running of an **OH_AVScreenCapture** instance. Before using this callback, register it with the **OH_AVScreenCapture** instance. Register this error callback before screen recording starts to handle errors in a timely manner.|
| [typedef void (\*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)](#oh_avscreencapture_onbufferavailable) | OH_AVScreenCapture_OnBufferAvailable | Called to notify the app when an audio or video buffer is available during the running of an **OH_AVScreenCapture** instance. Before using this callback, register it with the **OH_AVScreenCapture** instance.<br>After the callback is executed, the data buffer is no longer valid. Your app needs to process the data in a timely manner in the callback.|
| [typedef void (\*OH_AVScreenCapture_OnDisplaySelected)(OH_AVScreenCapture *capture, uint64_t displayId, void *userData)](#oh_avscreencapture_ondisplayselected) | OH_AVScreenCapture_OnDisplaySelected | Called when screen capture starts. Before using this callback, register it with the **OH_AVScreenCapture** instance. The registration must be completed before screen capture starts.|
| [typedef void (\*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)](#oh_avscreencapture_oncapturecontentchanged) | OH_AVScreenCapture_OnCaptureContentChanged | Called when the screen capture content changes during the running of an OH_AVScreenCapture instance. Before using this callback, register it with the **OH_AVScreenCapture** instance.<br>This callback returns the content change event through the **event** parameter. For details about the event values, see [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent).|
| [typedef void (\*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)](#oh_avscreencapture_onuserselected) | OH_AVScreenCapture_OnUserSelected | Called to return the parameters selected by the user on the authorization UI to the app.<br>You need to set this callback to the **OH_AVScreenCapture** instance using the registration method. You need to complete the registration before starting the authorization process to receive the user's selection result.|
| [typedef void (\*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)](#oh_avscreencapture_onprivacyprotect) | OH_AVScreenCapture_OnPrivacyProtect | Called when a privacy protection event occurs during the running of the [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance.|

### Variables

| Name| Description|
| -- | -- |
| const char * OH_SCREEN_CAPTURE_CONTENT_RECT | Obtains the key for the information about the valid content area in the screen recording image frame.<br>The return value obtained using this key is an int32_t array, in pixels (px). The array length is 4. The elements in the array are defined as [top, left, width, height], where top indicates the vertical coordinate of the upper left corner of the rectangle, left indicates the horizontal coordinate of the upper left corner of the rectangle, width indicates the width of the rectangle, and height indicates the height of the rectangle. The elements in the array can be obtained from [OH_AVFormat_GetIntBuffer](../apis-avcodec-kit/capi-native-avformat-h.md#oh_avformat_getintbuffer).<br>**Since**: 26.0.0|

## Enum Description

### OH_CaptureMode

```c
enum OH_CaptureMode
```

**Description**

Enumerates the screen capture modes.

Select a proper mode based on the recording requirements. Capturing the home screen is suitable for full-screen recording scenarios. Capturing a specified screen is suitable for scenarios where a specific screen is selected in a multi-screen environment. Capturing a specified window is suitable for scenarios where only a single app window is recorded.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_CAPTURE_HOME_SCREEN = 0 | Captures the home screen.|
| OH_CAPTURE_SPECIFIED_SCREEN = 1 | Captures a specified screen. To use this mode, you need to specify **displayId** in **OH_AVScreenCaptureConfig**.|
| OH_CAPTURE_SPECIFIED_WINDOW = 2 | Captures a specified window. To use this mode, you need to specify **windowId** in **OH_AVScreenCaptureConfig**.|
| OH_CAPTURE_INVAILD = -1 | Invalid mode.|

### OH_AudioCaptureSourceType

```c
enum OH_AudioCaptureSourceType
```

**Description**

Enumerates the audio source types during screen capture.

They are applicable to different audio recording requirements: **OH_MIC** is suitable for scenarios where external sounds (such as commentary and narration) need to be recorded; **OH_ALL_PLAYBACK** is suitable for scenarios where all internal audio streams played by the system (such as system sound effects and app audio) need to be recorded; **OH_APP_PLAYBACK** is suitable for scenarios where only the audio played by a specified app needs to be recorded.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_SOURCE_INVALID = -1 | Invalid audio source.|
| OH_SOURCE_DEFAULT = 0 | Default audio source. The default value is **OH_MIC**.|
| OH_MIC = 1 | External audio streams recorded by the microphone.|
| OH_ALL_PLAYBACK = 2 | All internal audio streams played by the system.|
| OH_APP_PLAYBACK = 3 | Internal audio streams played by a specified application.|

### OH_AudioCodecFormat

```c
enum OH_AudioCodecFormat
```

**Description**

Enumerates the audio encoding formats.

**OH_AUDIO_DEFAULT** is the default encoding format and applies to most audio and video recording scenarios. **OH_AAC_LC** is the **AAC_LC** encoding format and applies to common audio and video application scenarios that require good audio quality and small file size.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_AUDIO_DEFAULT = 0 | Default audio encoding format. The default value is **AAC_LC**.|
| OH_AAC_LC = 3 | AAC_LC audio encoding.|
| OH_AUDIO_CODEC_FORMAT_BUTT | Invalid format.|

### OH_VideoCodecFormat

```c
enum OH_VideoCodecFormat
```

**Description**

Enumerates the video encoding formats.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_VIDEO_DEFAULT = 0 | Default video encoding format. The default value is **H.264**.|
| OH_H264 = 2 | H.264. It is applicable to most recording scenarios and has the best compatibility. It is the most widely supported video encoding format.|
| OH_H265 = 4 | H.265/HEVC. Applies to scenarios that require high compression efficiency. The file size is smaller with the same image quality, but the compatibility is lower than that of H.264.|
| OH_MPEG4 = 6 | MPEG4. Applicable to scenarios that do not require high compatibility. The compression efficiency is lower than that of H.264/H.265.|
| OH_VP8 = 8 | VP8. Open-source encoding format for web scenarios. The compatibility is limited.|
| OH_VP9 = 10 | VP9. Open-source encoding format for web high-definition scenarios. It has better compression efficiency than VP8 but limited compatibility.|
| OH_VIDEO_CODEC_FORMAT_BUTT | Invalid format.|

### OH_DataType

```c
enum OH_DataType
```

**Description**

Enumerates the data types of screen capture streams.

Select a proper data format based on your requirements. The original stream format is applicable to scenarios where audio and video data needs to be processed in real time (such as real-time preview and streaming transmission). The file format is applicable to scenarios where data is directly recorded as files.

Currently, only the original stream format and file format are supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_ORIGINAL_STREAM = 0 | Original stream format, such as YUV, RGBA, and PCM.|
| OH_ENCODED_STREAM = 1 | Encoded data rate format, such as H.264 and AAC. This value is not supported yet.|
| OH_CAPTURE_FILE = 2 | Format of the recording file. The value can be **mp4**.|
| OH_INVAILD = -1 | Invalid format.|

### OH_VideoSourceType

```c
enum OH_VideoSourceType
```

**Description**

Enumerates the video source formats. Currently, only the RGBA format is supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| OH_VIDEO_SOURCE_SURFACE_YUV = 0 | YUV format. This value is not supported yet.|
| OH_VIDEO_SOURCE_SURFACE_ES | Raw format. This value is not supported yet.|
| OH_VIDEO_SOURCE_SURFACE_RGBA | RGBA format.|
| OH_VIDEO_SOURCE_BUTT | Invalid format.|

### OH_ContainerFormatType

```c
enum OH_ContainerFormatType
```

**Description**

Enumerates the types of files generated during screen capture.

The options are applicable to different file output requirements. **CFT_MPEG_4A** is the audio format M4A, which is applicable to scenarios where only audio needs to be recorded. **CFT_MPEG_4** is the video format MP4, which is applicable to scenarios where both audio and video need to be recorded.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum Item| Description|
| -- | -- |
| CFT_MPEG_4A = 0 | Audio format M4A.|
| CFT_MPEG_4 = 1 | Video format MP4.|

### OH_AVScreenCaptureStateCode

```c
enum OH_AVScreenCaptureStateCode
```

**Description**

Enumerates the screen capture states.

The state code reflects the lifecycle changes of screen capture, including the start, pause, resume, stop, interruption, and privacy scene change states. The state changes are applied through the OH_AVScreenCapture_OnStateChange callback notification.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum Item| Description|
| -- | -- |
| OH_SCREEN_CAPTURE_STATE_STARTED = 0 | Screen capture is started.|
| OH_SCREEN_CAPTURE_STATE_CANCELED = 1 | Screen capture is canceled.|
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER = 2 | Screen capture is stopped.|
| OH_SCREEN_CAPTURE_STATE_INTERRUPTED_BY_OTHER = 3 | Screen capture is interrupted by another screen capture.|
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_CALL = 4 | Screen capture is interrupted by a call.|
| OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE = 5 | The microphone is unavailable.|
| OH_SCREEN_CAPTURE_STATE_MIC_MUTED_BY_USER = 6 | The microphone is muted.|
| OH_SCREEN_CAPTURE_STATE_MIC_UNMUTED_BY_USER = 7 | The microphone is unmuted.|
| OH_SCREEN_CAPTURE_STATE_ENTER_PRIVATE_SCENE = 8 | The system enters a privacy screen.|
| OH_SCREEN_CAPTURE_STATE_EXIT_PRIVATE_SCENE = 9 | The system exits a privacy screen.|
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER_SWITCHES = 10 | Screen capture is interrupted by system user switching.|
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_USER = 11 | Screen capture is paused by the user.<br>**Since**: 26.0.0|
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_USER = 12 | Screen capture is resumed by the user.<br>**Since**: 26.0.0|
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_APP = 13 | Screen capture is paused by the application.<br>**Since**: 26.0.0|
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_APP = 14 | Screen capture is resumed by the application.<br>**Since**: 26.0.0|

### OH_AVScreenCaptureBufferType

```c
enum OH_AVScreenCaptureBufferType
```

**Description**

Enumerates the buffer types.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum Item| Description|
| -- | -- |
| OH_SCREEN_CAPTURE_BUFFERTYPE_VIDEO = 0 | Video data.|
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_INNER = 1 | Internal audio capture data.|
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_MIC = 2 | Microphone audio data.|

### OH_AVScreenCaptureFilterableAudioContent

```c
enum OH_AVScreenCaptureFilterableAudioContent
```

**Description**

Enumerates the types of audio that can be added to a content filter.

In screen recording scenarios, you can filter specific audio types to control the recorded content. Filtering notification tones is suitable for scenarios where system notification sounds may interfere with the screen recording content. Filtering the app's own audio is suitable for scenarios where only the audio within the app is recorded, excluding other sounds.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum Item| Description|
| -- | -- |
| OH_SCREEN_CAPTURE_NOTIFICATION_AUDIO = 0 | Notification tone.|
| OH_SCREEN_CAPTURE_CURRENT_APP_AUDIO = 1 | Sound of the application itself.|

### OH_AVScreenCaptureContentChangedEvent

```c
enum OH_AVScreenCaptureContentChangedEvent
```

**Description**

Enumerates the screen capture content change events.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

| Enum Item| Description|
| -- | -- |
| OH_SCREEN_CAPTURE_CONTENT_HIDE = 0 | The screen capture content is hidden.|
| OH_SCREEN_CAPTURE_CONTENT_VISIBLE = 1 | The screen capture content is visible.|
| OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE = 2 | The screen capture content becomes unavailable. For example, the screen capture window is closed.|

### OH_AVScreenCapture_FillMode

```c
enum OH_AVScreenCapture_FillMode
```

**Description**

Enumerates the image fill modes.

**OH_SCREENCAPTURE_FILLMODE_ASPECT_SCALE_FIT** is suitable for scenarios where the original aspect ratio of the image needs to be preserved to avoid distortion.<br> **OH_SCREENCAPTURE_FILLMODE_SCALE_TO_FILL** is suitable for scenarios where the target area needs to be completely filled and image distortion is acceptable.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| OH_SCREENCAPTURE_FILLMODE_ASPECT_SCALE_FIT = 0 | Keeps the original aspect ratio of the image to fit the target size. Black bars may appear if the aspect ratios differ.|
| OH_SCREENCAPTURE_FILLMODE_SCALE_TO_FILL = 1 | Stretches the image to fit the target size. The image may be distorted if the aspect ratios differ.|

### OH_ScreenCaptureHighlightMode

```c
enum OH_ScreenCaptureHighlightMode
```

**Description**

Enumerates the display modes of the highlight border shown during screen capture.

**Since**: 22

| Enum Item| Description|
| -- | -- |
| OH_HIGHLIGHT_MODE_CLOSED = 0 | Highlights the capture area with a full square border. This is the default mode.|
| OH_HIGHLIGHT_MODE_CORNER_WRAP = 1 | Highlights the capture area with a corner-wrapping border.|

### OH_CapturePickerMode

```c
enum OH_CapturePickerMode
```

**Description**

Enumerates the display modes of the picker.

Select a proper picker mode based on your app's requirements. The mode that displays only a list of windows is suitable for scenarios where users are allowed to select only windows for recording. The mode that displays only a list of screens is suitable for scenarios where users are allowed to select only the entire screen. The mode that displays both screens and windows is the default mode and is suitable for scenarios where users need to flexibly select recording targets. The mode that displays only a list of apps is suitable for scenarios where only a single app can be recorded.

**Since**: 22

| Enum Item| Description|
| -- | -- |
| OH_CAPTURE_PICKER_MODE_WINDOW_ONLY = 0 | Displays only a list of windows.|
| OH_CAPTURE_PICKER_MODE_SCREEN_ONLY = 1 | Displays only a list of screens.|
| OH_CAPTURE_PICKER_MODE_SCREEN_AND_WINDOW = 2 | Displays both screens and windows. This is the default mode.|
| OH_CAPTURE_PICKER_MODE_APP_ONLY = 3 | Displays only a list of apps.<br>**Since**: 26.0.0|
| OH_CAPTURE_PICKER_MODE_WINDOW_AND_APP = 4 | Displays both windows and apps.<br>**Since**: 26.0.0|
| OH_CAPTURE_PICKER_MODE_SCREEN_AND_APP = 5 | Displays both screens and apps.<br>**Since**: 26.0.0|
| OH_CAPTURE_PICKER_MODE_SCREEN_WINDOW_AND_APP = 6 | Displays screens, windows, and apps.<br>**Since**: 26.0.0|


## Function Description

### OH_AVScreenCaptureOnError()

```c
typedef void (*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)
```

**Description**

Called to notify the app when an error occurs during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](#oh_avscreencapture_onerror) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
|  int32_t errorCode | Error code. For details, see [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode).|

### OH_AVScreenCaptureOnAudioBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)
```

**Description**

Called to notify the app when an audio buffer is available during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](#oh_avscreencapture_onbufferavailable) instead. **OH_AVScreenCapture_OnBufferAvailable** unifies the audio and video buffer callbacks into one API. The **bufferType** parameter is used to distinguish the buffer data type. In addition, the **timestamp** and **userData** parameters are added. You do not need to register the audio and video callbacks separately.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
|  bool isReady | Whether the audio buffer is available. The value **true** indicates that the audio buffer is available, and the value **false** indicates otherwise.|
| [OH_AudioCaptureSourceType](#oh_audiocapturesourcetype) type | Audio source type, which is used to identify the source of audio data. **OH_MIC** indicates the microphone audio data. **OH_ALL_PLAYBACK** indicates the audio data recorded in the system. **OH_APP_PLAYBACK** indicates the audio data played by a specified application. You need to process the audio data based on the type, value, and pair.|

### OH_AVScreenCaptureOnVideoBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)
```

**Description**

Called to notify the app when a video buffer is available during the running of an **OH_AVScreenCapture** instance.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
|  bool isReady | Whether the video buffer is available. The value **true** indicates that the video buffer is available, and the value **false** indicates otherwise.|

### OH_AVScreenCapture_OnStateChange()

```c
typedef void (*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)
```

**Description**

Called when the state changes during the running of an OH_AVScreenCapture instance.<br> This callback takes effect only after being set using the **OH_AVScreenCapture** API. If it is not set, the callback will not be invoked.

This callback returns the status code through the **stateCode** parameter. The state changes include starting, pausing, resuming, stopping, interrupting, and privacy scene change. For details about the status codes, see [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| struct [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode) stateCode | Status code, which indicates the screen recording status change. Common statuses include **OH_SCREEN_CAPTURE_STATE_STARTED** (screen recording started), **OH_SCREEN_CAPTURE_STATE_CANCELED** (screen recording canceled by the user), and **OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER** (screen recording stopped by the user). You need to perform corresponding operations based on the status.|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnError()

```c
typedef void (*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)
```

**Description**

Called to notify the app when an error occurs during the running of an **OH_AVScreenCapture** instance. Before using this callback, register it with the **OH_AVScreenCapture** instance. Register this error callback before screen recording starts to handle errors in a timely manner.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
|  int32_t errorCode | Error code. For details about the error codes, please refer to [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode).|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnBufferAvailable()

```c
typedef void (*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)
```

**Description**

Called to notify the app when an audio or video buffer is available during the running of an **OH_AVScreenCapture** instance. Before using this callback, register it with the **OH_AVScreenCapture** instance.

After the callback is executed, the data buffer is no longer valid. Your app needs to process the data in a timely manner in the callback.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVBuffer](../apis-avcodec-kit/capi-core-oh-avbuffer.md) *buffer | Pointer to the OH_AVBuffer instance. After the callback is triggered, the buffer is no longer valid.|
| [OH_AVScreenCaptureBufferType](#oh_avscreencapturebuffertype) bufferType | Type of the available buffer.<br>**OH_SCREEN_CAPTURE_BUFFERTYPE_VIDEO**: The video buffer is available. **OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_INNER**: The internal audio buffer is available. **OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_MIC**: The microphone audio buffer is available.<br>You need to process the buffer data based on the value of **bufferType**.|
|  int64_t timestamp | Timestamp, in nanoseconds.|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnDisplaySelected()

```c
typedef void (*OH_AVScreenCapture_OnDisplaySelected)(OH_AVScreenCapture *capture, uint64_t displayId, void *userData)
```

**Description**

Called when screen capture starts. Before using this callback, register it with the **OH_AVScreenCapture** instance. The registration must be completed before screen capture starts.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
|  uint64_t displayId | ID of the screen to capture, which identifies the screen selected by the user.|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnCaptureContentChanged()

```c
typedef void (*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)
```

**Description**

Called when the screen capture content changes during the running of an OH_AVScreenCapture instance. Before using this callback, register it with the **OH_AVScreenCapture** instance.

This callback returns the content change event through the **event** parameter. For details about the event values, see [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)* capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent) event | Screen capture content change event, indicating the status change of the screen capture content.<br>**OH_SCREEN_CAPTURE_CONTENT_HIDE**: The screen recording content is hidden. For example, the privacy screen is displayed. **OH_SCREEN_CAPTURE_CONTENT_VISIBLE**: The screen recording content is visible. **OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE**: The screen recording content is unavailable. For example, the window is closed.<br>You need to adjust the screen recording status based on the event type.|
| [OH_Rect](capi-avscreencapture-oh-rect.md)* area | Pointer to the area information when the screen recording content is visible. This parameter is invalid when the screen recording content is hidden or invisible.|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnUserSelected()

```c
typedef void (*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)
```

**Description**

Called to return the parameters selected by the user on the authorization UI to the app.

You need to set this callback to the **OH_AVScreenCapture** instance using the registration method. You need to complete the registration before starting the authorization process to receive the user's selection result.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)* capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md)* selections | Pointer to capture parameters selected by the user on the authorization UI.|
|  void *userData | Pointer to the user-defined data carried in the function.|

### OH_AVScreenCapture_OnPrivacyProtect()

```c
typedef void (*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)
```
 
**Description**

Called when a privacy protection event occurs during the running of the [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance.
  
**Since**: 24

**Parameters**
  
| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)* capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md)* privacyProtect | Pointer to the privacy protection information. Pointer to the structure that contains the detailed information about the privacy protection event. This parameter is used to process the privacy protection callback event during screen recording.|
| void *userData | Pointer to the user-defined data carried in the function.|
