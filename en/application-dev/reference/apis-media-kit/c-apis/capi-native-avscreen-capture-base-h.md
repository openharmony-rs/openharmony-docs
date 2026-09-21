# native_avscreen_capture_base.h

## Overview

The file declares the common structs, character constants, and enums used for running screen capture.

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) | OH_AudioCaptureInfo | The struct describes the audio capture information. |
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) | OH_AudioEncInfo | The struct describes the audio encoding information. |
| [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md) | OH_AudioInfo | The struct describes the audio information. |
| [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md) | OH_VideoCaptureInfo | The struct describes the video capture information. When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded. |
| [OH_VideoEncInfo](capi-avscreencapture-oh-videoencinfo.md) | OH_VideoEncInfo | The struct describes the video encoding information. |
| [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md) | OH_VideoInfo | The struct describes the video information. |
| [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) | OH_RecorderInfo | The struct describes the recording file information. |
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) | OH_AVScreenCaptureConfig | The struct describes the screen capture configuration. |
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md) | OH_PrivacyProtectInfo | Defines the privacy protection information. |
| [OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) | OH_AVScreenCaptureCallback | Defines all the asynchronous callback function pointers of an **OH_AVScreenCapture** instance. To ensure the normal running of **OH_AVScreenCapture**, you must register the instance of this struct with the **<br>OH_AVScreenCapture** instance to process the information reported by the callback functions. |
| [OH_Rect](capi-avscreencapture-oh-rect.md) | OH_Rect | The struct describes the width, height, and image information of the rectangle used for screen capture. |
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) | OH_AudioBuffer | The struct describes the configuration such as the size, type, and timestamp of audio data. |
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) | OH_AVScreenCaptureHighlightConfig | The struct describes the style of the highlight border shown during screen capture, including its shape, thickness, and color. |
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) | OH_MultiDisplayCapability | Defines a struct for the multi-screen recording capability. It includes whether the multi-screen supports joint recording and the width and height of the screen for joint recording. |
| [OH_NativeBuffer](capi-avscreencapture-oh-nativebuffer.md) | OH_NativeBuffer | The struct describes the native video stream class for screen capture. |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) | OH_AVScreenCapture | Defines all the asynchronous callback function pointers of an **OH_AVScreenCapture** instance. To ensure the normal running of **OH_AVScreenCapture**, you must register the instance of this struct with the **<br>OH_AVScreenCapture** instance to process the information reported by the callback functions. |
| [OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) | OH_AVScreenCapture_ContentFilter | The OH_AVScreenCapture_ContentFilter struct describes the filter used to filter audio and video content. |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) | OH_AVScreenCapture_CaptureStrategy | The OH_AVScreenCapture_CaptureStrategy struct describes the screen capture strategy. |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) | OH_AVScreenCapture_UserSelectionInfo | The OH_AVScreenCapture_UserSelectionInfo struct describes the parameters selected by the user on the authorization UI (selection UI). |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CaptureMode](#oh_capturemode) | OH_CaptureMode | Enumerates the screen capture modes. |
| [OH_AudioCaptureSourceType](#oh_audiocapturesourcetype) | OH_AudioCaptureSourceType | Enumerates the audio source types during screen capture. |
| [OH_AudioCodecFormat](#oh_audiocodecformat) | OH_AudioCodecFormat | Enumerates the audio encoding formats. |
| [OH_VideoCodecFormat](#oh_videocodecformat) | OH_VideoCodecFormat | Enumerates the video encoding formats. |
| [OH_DataType](#oh_datatype) | OH_DataType | Enumerates the data types of screen capture streams. |
| [OH_VideoSourceType](#oh_videosourcetype) | OH_VideoSourceType | Enumerates the video source formats. Currently, only the RGBA format is supported. |
| [OH_ContainerFormatType](#oh_containerformattype) | OH_ContainerFormatType | Enumerates the types of files generated during screen capture. |
| [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode) | OH_AVScreenCaptureStateCode | Enumerates the screen capture states. |
| [OH_AVScreenCaptureBufferType](#oh_avscreencapturebuffertype) | OH_AVScreenCaptureBufferType | Enumerates the buffer types. |
| [OH_AVScreenCaptureFilterableAudioContent](#oh_avscreencapturefilterableaudiocontent) | OH_AVScreenCaptureFilterableAudioContent | Enumerates the buffer types. |
| [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent) | OH_AVScreenCaptureContentChangedEvent | Enumerates the screen capture content change events. |
| [OH_ScreenCaptureHighlightMode](#oh_screencapturehighlightmode) | OH_ScreenCaptureHighlightMode | Enumerates the display modes of the highlight border shown during screen capture. |
| [OH_AVScreenCapture_FillMode](#oh_avscreencapture_fillmode) | OH_AVScreenCapture_FillMode | Enumerates the image fill modes. |
| [OH_CapturePickerMode](#oh_capturepickermode) | OH_CapturePickerMode | Enumerates the display modes of the picker. |

### Macro

| Name | Description |
| -- | -- |
| NATIVE_AVSCREEN_CAPTURE_BASE_H | The file declares the common structs, character constants, and enums used for running screen capture.<br>**Since**: 10<br>**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)](#oh_avscreencaptureonerror) | OH_AVScreenCaptureOnError | Called when an error occurs during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) instead. |
| [typedef void (\*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)](#oh_avscreencaptureonaudiobufferavailable) | OH_AVScreenCaptureOnAudioBufferAvailable | Called when an audio buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [typedef void (\*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)](#oh_avscreencaptureonvideobufferavailable) | OH_AVScreenCaptureOnVideoBufferAvailable | Called when a video buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [typedef void (\*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)](#oh_avscreencapture_onstatechange) | OH_AVScreenCapture_OnStateChange | Called when the state changes during the running of an OH_AVScreenCapture instance. |
| [typedef void (\*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)](#oh_avscreencapture_onerror) | OH_AVScreenCapture_OnError | Called when an error occurs during the running of an OH_AVScreenCapture instance. |
| [typedef void (\*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)](#oh_avscreencapture_onbufferavailable) | OH_AVScreenCapture_OnBufferAvailable | Called when an audio buffer or a video buffer is available during the running of an OH_AVScreenCapture instance. |
| [typedef void (\*OH_AVScreenCapture_OnDisplaySelected)(OH_AVScreenCapture *capture, uint64_t displayId, void *userData)](#oh_avscreencapture_ondisplayselected) | OH_AVScreenCapture_OnDisplaySelected | When one of the display devices start being captured, the function pointer will be called |
| [typedef void (\*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)](#oh_avscreencapture_oncapturecontentchanged) | OH_AVScreenCapture_OnCaptureContentChanged | Called when the screen capture content changes during the running of an OH_AVScreenCapture instance. |
| [typedef void (\*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)](#oh_avscreencapture_onuserselected) | OH_AVScreenCapture_OnUserSelected | Called to return the parameters selected by the user on the authorization UI to the application. |
| [typedef void (\*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)](#oh_avscreencapture_onprivacyprotect) | OH_AVScreenCapture_OnPrivacyProtect | Called when a privacy protection event occurs during the running of the [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance. |

### Variable

| Name | Description |
| -- | -- |
| const char *OH_SCREEN_CAPTURE_CONTENT_RECT | Key for obtaining the valid content area information in the screen recording image frame. The returned value is an int32_t array. The array length is 4. The array elements are defined as [top,left,width,height]. The value can be obtained from [OH_AVFormat_GetIntBuffer](capi-native-avformat-h.md#oh_avformat_getintbuffer).<br>**Since**: 26.0.0 |
| void (*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode) | Called when an error occurs during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) instead.<br>**Since**: 10 |
| void (*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type) | Called when an audio buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.<br>**Since**: 10 |
| void (*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady) | Called when a video buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.<br>**Since**: 10 |
| void (*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData) | Called when the state changes during the running of an OH_AVScreenCapture instance.<br>**Since**: 12 |
| void (*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData) | Called when an error occurs during the running of an OH_AVScreenCapture instance.<br>**Since**: 12 |
| void (*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData) | Called when an audio buffer or a video buffer is available during the running of an OH_AVScreenCapture instance.<br>**Since**: 12 |
| void (*OH_AVScreenCapture_OnDisplaySelected)(OH_AVScreenCapture *capture, uint64_t displayId, void *userData) | When one of the display devices start being captured, the function pointer will be called<br>**Since**: 15 |
| void (*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData) | Called when the screen capture content changes during the running of an OH_AVScreenCapture instance.<br>**Since**: 20 |
| void (*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData) | Called to return the parameters selected by the user on the authorization UI to the application.<br>**Since**: 20 |
| void (*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData) | Called when a privacy protection event occurs during the running of the [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance.<br>**Since**: 24 |

## Enum type description

### OH_CaptureMode

```c
enum OH_CaptureMode
```

**Description**

Enumerates the screen capture modes.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_CAPTURE_HOME_SCREEN = 0 | capture home screen |
| OH_CAPTURE_SPECIFIED_SCREEN = 1 | capture a specified screen |
| OH_CAPTURE_SPECIFIED_WINDOW = 2 | capture a specified window |
| OH_CAPTURE_VIRTUAL_EXTENDED_SCREEN = 3 | Create a virtual extended screen and capture the contents of that screen<br>**Since**: 26.0.1 |

### OH_AudioCaptureSourceType

```c
enum OH_AudioCaptureSourceType
```

**Description**

Enumerates the audio source types during screen capture.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_SOURCE_INVALID = -1 | Invalid audio source |
| OH_SOURCE_DEFAULT = 0 | Default audio source |
| OH_MIC = 1 | Microphone |
| OH_ALL_PLAYBACK = 2 | inner all PlayBack |
| OH_APP_PLAYBACK = 3 | inner app PlayBack |

### OH_AudioCodecFormat

```c
enum OH_AudioCodecFormat
```

**Description**

Enumerates the audio encoding formats.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_AUDIO_DEFAULT = 0 | Default format |
| OH_AAC_LC = 3 | Advanced Audio Coding Low Complexity (AAC-LC) |
| OH_AUDIO_CODEC_FORMAT_BUTT | Invalid value |

### OH_VideoCodecFormat

```c
enum OH_VideoCodecFormat
```

**Description**

Enumerates the video encoding formats.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_VIDEO_DEFAULT = 0 | Default format |
| OH_H264 = 2 | H.264 |
| OH_H265 = 4 | H.265/HEVC |
| OH_MPEG4 = 6 | MPEG4 |
| OH_VP8 = 8 | VP8 |
| OH_VP9 = 10 | VP9 |
| OH_VIDEO_CODEC_FORMAT_BUTT | Invalid format |

### OH_DataType

```c
enum OH_DataType
```

**Description**

Enumerates the data types of screen capture streams.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_ORIGINAL_STREAM = 0 | YUV/RGBA/PCM, etc. original stream |
| OH_ENCODED_STREAM = 1 | h264/AAC, etc. encoded stream |
| OH_CAPTURE_FILE = 2 | mp4 file |

### OH_VideoSourceType

```c
enum OH_VideoSourceType
```

**Description**

Enumerates the video source formats. Currently, only the RGBA format is supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_VIDEO_SOURCE_SURFACE_YUV = 0 | RGBA format. |
| OH_VIDEO_SOURCE_SURFACE_ES | Raw encoded data provided through graphic |
| OH_VIDEO_SOURCE_SURFACE_RGBA | RGBA video data provided through graphic |
| OH_VIDEO_SOURCE_BUTT | Invalid value |

### OH_ContainerFormatType

```c
enum OH_ContainerFormatType
```

**Description**

Enumerates the types of files generated during screen capture.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum item | Description |
| -- | -- |
| CFT_MPEG_4A = 0 | Audio format type -- m4a |
| CFT_MPEG_4 = 1 | Video format type -- mp4 |

### OH_AVScreenCaptureStateCode

```c
enum OH_AVScreenCaptureStateCode
```

**Description**

Enumerates the screen capture states.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_SCREEN_CAPTURE_STATE_STARTED = 0 | Screen capture started by user |
| OH_SCREEN_CAPTURE_STATE_CANCELED = 1 | Screen capture canceled by user |
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER = 2 | ScreenCapture stopped by user |
| OH_SCREEN_CAPTURE_STATE_INTERRUPTED_BY_OTHER = 3 | ScreenCapture interrupted by other screen capture |
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_CALL = 4 | ScreenCapture stopped by SIM call |
| OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE = 5 | Microphone is temporarily unavailable |
| OH_SCREEN_CAPTURE_STATE_MIC_MUTED_BY_USER = 6 | Microphone is muted by user |
| OH_SCREEN_CAPTURE_STATE_MIC_UNMUTED_BY_USER = 7 | Microphone is unmuted by user |
| OH_SCREEN_CAPTURE_STATE_ENTER_PRIVATE_SCENE = 8 | Current captured screen has private window |
| OH_SCREEN_CAPTURE_STATE_EXIT_PRIVATE_SCENE = 9 | Private window disappeared on current captured screen |
| OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER_SWITCHES = 10 | ScreenCapture stopped by user switches |
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_USER = 11 | Screen capture paused by user<br>**Since**: 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_USER = 12 | Screen capture resumed by user<br>**Since**: 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_APP = 13 | Screen capture paused by app<br>**Since**: 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_APP = 14 | Screen capture resumed by app<br>**Since**: 26.0.0 |

### OH_AVScreenCaptureBufferType

```c
enum OH_AVScreenCaptureBufferType
```

**Description**

Enumerates the buffer types.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_SCREEN_CAPTURE_BUFFERTYPE_VIDEO = 0 | Buffer of video data from screen |
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_INNER = 1 | Buffer of audio data from inner capture |
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_MIC = 2 | Buffer of audio data from microphone |

### OH_AVScreenCaptureFilterableAudioContent

```c
enum OH_AVScreenCaptureFilterableAudioContent
```

**Description**

Enumerates the buffer types.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_SCREEN_CAPTURE_NOTIFICATION_AUDIO = 0 | Audio content of notification sound |
| OH_SCREEN_CAPTURE_CURRENT_APP_AUDIO = 1 | Audio content of the sound of the app itself |

### OH_AVScreenCaptureContentChangedEvent

```c
enum OH_AVScreenCaptureContentChangedEvent
```

**Description**

Enumerates the screen capture content change events.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_SCREEN_CAPTURE_CONTENT_HIDE = 0 | The screen capture content is hidden. |
| OH_SCREEN_CAPTURE_CONTENT_VISIBLE = 1 | The screen capture content is visible. |
| OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE = 2 | The screen capture content becomes unavailable. For example, the screen capture window is closed. |

### OH_ScreenCaptureHighlightMode

```c
enum OH_ScreenCaptureHighlightMode
```

**Description**

Enumerates the display modes of the highlight border shown during screen capture.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 22

| Enum item | Description |
| -- | -- |
| OH_HIGHLIGHT_MODE_CLOSED = 0 | Highlights the capture area with a full square border. This is the default mode. |
| OH_HIGHLIGHT_MODE_CORNER_WRAP = 1 | Highlights the capture area with a corner-wrapping border. |

### OH_AVScreenCapture_FillMode

```c
enum OH_AVScreenCapture_FillMode
```

**Description**

Enumerates the image fill modes.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_SCREENCAPTURE_FILLMODE_ASPECT_SCALE_FIT = 0 | Keeps the original aspect ratio of the image to fit the target size. Black bars may appear if the aspect ratios differ. |
| OH_SCREENCAPTURE_FILLMODE_SCALE_TO_FILL = 1 | Stretches the image to fill the target size. The image may stretch and distort if the aspect ratios differ. |

### OH_CapturePickerMode

```c
enum OH_CapturePickerMode
```

**Description**

Enumerates the display modes of the picker.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 22

| Enum item | Description |
| -- | -- |
| OH_CAPTURE_PICKER_MODE_WINDOW_ONLY = 0 | Displays only a list of windows. |
| OH_CAPTURE_PICKER_MODE_SCREEN_ONLY = 1 | Displays only a list of screens. |
| OH_CAPTURE_PICKER_MODE_SCREEN_AND_WINDOW = 2 | Displays both screens and windows. This is the default mode. |
| OH_CAPTURE_PICKER_MODE_APP_ONLY = 3 | Show application options only.<br>**Since**: 26.0.0 |
| OH_CAPTURE_PICKER_MODE_WINDOW_AND_APP = 4 | Show both window and application options.<br>**Since**: 26.0.0 |
| OH_CAPTURE_PICKER_MODE_SCREEN_AND_APP = 5 | Show both screen and application options.<br>**Since**: 26.0.0 |
| OH_CAPTURE_PICKER_MODE_SCREEN_WINDOW_AND_APP = 6 | Show screen, window, and application options.<br>**Since**: 26.0.0 |


## Function description

### OH_AVScreenCaptureOnError()

```c
typedef void (*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)
```

**Description**

Called when an error occurs during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t errorCode | Error code. |

### OH_AVScreenCaptureOnAudioBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)
```

**Description**

Called when an audio buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| bool isReady | Whether the audio buffer is available. The values include **true** (yes) and **false** (no). |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Audio source type. |

### OH_AVScreenCaptureOnVideoBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)
```

**Description**

Called when a video buffer is available during the running of an OH_AVScreenCapture instance. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| bool isReady | Whether the video buffer is available. The values include **true** (yes) and **false** (no). |

### OH_AVScreenCapture_OnStateChange()

```c
typedef void (*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)
```

**Description**

Called when the state changes during the running of an OH_AVScreenCapture instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode) stateCode | Status code. |
| void \*userData | Pointer to the user-defined data carried in the function. |

### OH_AVScreenCapture_OnError()

```c
typedef void (*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)
```

**Description**

Called when an error occurs during the running of an OH_AVScreenCapture instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| int32_t errorCode | Error code. |
| void \*userData | Pointer to the user-defined data carried in the function. |

### OH_AVScreenCapture_OnBufferAvailable()

```c
typedef void (*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)
```

**Description**

Called when an audio buffer or a video buffer is available during the running of an OH_AVScreenCapture instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to the OH_AVScreenCapture instance. |
| OH_AVBuffer \*buffer | Pointer to the OH_AVBuffer instance. After the callback is triggered, the buffer is no longer valid. |
| [OH_AVScreenCaptureBufferType](capi-native-avscreen-capture-base-h.md#oh_avscreencapturebuffertype) bufferType | Type of the buffer. |
| int64_t timestamp | Timestamp, in nanoseconds. |
| void \*userData | Pointer to the user-defined data carried in the function. |

### OH_AVScreenCapture_OnDisplaySelected()

```c
typedef void (*OH_AVScreenCapture_OnDisplaySelected)(OH_AVScreenCapture *capture, uint64_t displayId, void *userData)
```

**Description**

When one of the display devices start being captured, the function pointer will be called

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) \*capture | Pointer to an OH_AVScreenCapture instance |
| uint64_t displayId | Id of the display device that being captured |
| void \*userData | Pointer to user specific data |

### OH_AVScreenCapture_OnCaptureContentChanged()

```c
typedef void (*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)
```

**Description**

Called when the screen capture content changes during the running of an OH_AVScreenCapture instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_AVScreenCaptureContentChangedEvent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturecontentchangedevent) event | enum for content change event |
| [OH_Rect](capi-avscreencapture-oh-rect.md)\* area | capture content rect position |
| void \*userData | Pointer to user specific data |

### OH_AVScreenCapture_OnUserSelected()

```c
typedef void (*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)
```

**Description**

Called to return the parameters selected by the user on the authorization UI to the application.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md)\* selections | The recording parameter information selected by the user on the authorization interface |
| void \*userData | Pointer to user specific data |

### OH_AVScreenCapture_OnPrivacyProtect()

```c
typedef void (*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)
```

**Description**

Called when a privacy protection event occurs during the running of the [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md)\* privacyProtect | Pointer to privacy protect info |
| void \*userData | Pointer to user specific data |


