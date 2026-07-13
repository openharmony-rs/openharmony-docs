# native_avscreen_capture_base.h

## 概述

声明用于运行屏幕录制通用的结构体、字符常量、枚举。

**库：** libnative_avscreen_capture.so

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) | OH_AudioCaptureInfo | 音频采样信息。 |
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) | OH_AudioEncInfo | 音频编码信息。 |
| [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md) | OH_AudioInfo | 音频信息。 |
| [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md) | OH_VideoCaptureInfo | 视频录制信息。当videoFrameWidth和videoFrameHeight同时为0时，忽略视频相关参数不录制屏幕数据。 |
| [OH_VideoEncInfo](capi-avscreencapture-oh-videoencinfo.md) | OH_VideoEncInfo | 视频编码参数。 |
| [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md) | OH_VideoInfo | 视频信息。 |
| [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) | OH_RecorderInfo | 录制文件信息。 |
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) | OH_AVScreenCaptureConfig | 屏幕录制配置参数。 |
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md) | OH_PrivacyProtectInfo | 隐私保护信息结构体。 |
| [OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) | OH_AVScreenCaptureCallback | OH_AVScreenCapture中包含所有异步回调函数指针的集合。将该结构体的实例注册到OH_AVScreenCapture实例中，以便处理回调上报的信息，从而保证OH_AVScreenCapture的正常运行。 |
| [OH_Rect](capi-avscreencapture-oh-rect.md) | OH_Rect | 定义录屏界面的宽高以及画面信息。 |
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) | OH_AudioBuffer | 定义了音频数据的大小、类型、时间戳等配置信息。 |
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) | OH_AVScreenCaptureHighlightConfig | 表示高亮边框的样式，包括高亮边框的模式、边框宽度和边框颜色。 |
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) | OH_MultiDisplayCapability | 多屏幕录制能力信息。多屏场景下，用户选择的多屏幕是否支持联合录制，以及联合录制的屏幕宽度和高度。 |
| [OH_NativeBuffer](capi-avscreencapture-oh-nativebuffer.md) | OH_NativeBuffer | 提供录屏的视频原始码流类。 |
| [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) | OH_AVScreenCapture | 通过OH_AVScreenCapture可以获取视频与音频的原始码流。 |
| [OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) | OH_AVScreenCapture_ContentFilter | 通过OH_AVScreenCapture_ContentFilter过滤音视频内容。 |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) | OH_AVScreenCapture_CaptureStrategy | 通过OH_AVScreenCapture_CaptureStrategy设置录屏策略。 |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) | OH_AVScreenCapture_UserSelectionInfo | 通过OH_AVScreenCapture_UserSelectionInfo获取用户在授权界面（选择界面）选择的参数。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_CaptureMode](#oh_capturemode) | OH_CaptureMode | 枚举，表示屏幕录制的不同模式。 |
| [OH_AudioCaptureSourceType](#oh_audiocapturesourcetype) | OH_AudioCaptureSourceType | 枚举，表示屏幕录制时的音频源类型。 |
| [OH_AudioCodecFormat](#oh_audiocodecformat) | OH_AudioCodecFormat | 枚举，表示音频编码格式。 |
| [OH_VideoCodecFormat](#oh_videocodecformat) | OH_VideoCodecFormat | 枚举，表示视频编码格式。 |
| [OH_DataType](#oh_datatype) | OH_DataType | 枚举，表示屏幕录制流的数据格式。 |
| [OH_VideoSourceType](#oh_videosourcetype) | OH_VideoSourceType | 枚举，表示视频源格式。当前仅支持RGBA格式。 |
| [OH_ContainerFormatType](#oh_containerformattype) | OH_ContainerFormatType | 枚举，表示屏幕录制生成的文件类型。 |
| [OH_AVScreenCaptureStateCode](#oh_avscreencapturestatecode) | OH_AVScreenCaptureStateCode | 枚举，表示状态码。 |
| [OH_AVScreenCaptureBufferType](#oh_avscreencapturebuffertype) | OH_AVScreenCaptureBufferType | 枚举，表示buffer类型。 |
| [OH_AVScreenCaptureFilterableAudioContent](#oh_avscreencapturefilterableaudiocontent) | OH_AVScreenCaptureFilterableAudioContent | 枚举，表示buffer类型。 |
| [OH_AVScreenCaptureContentChangedEvent](#oh_avscreencapturecontentchangedevent) | OH_AVScreenCaptureContentChangedEvent | 枚举，表示录屏内容变更事件。 |
| [OH_ScreenCaptureHighlightMode](#oh_screencapturehighlightmode) | OH_ScreenCaptureHighlightMode | 枚举，表示屏幕录制高亮边框的模式。 |
| [OH_AVScreenCapture_FillMode](#oh_avscreencapture_fillmode) | OH_AVScreenCapture_FillMode | 图像填充模式。 |
| [OH_CapturePickerMode](#oh_capturepickermode) | OH_CapturePickerMode | 枚举，表示Picker显示模式。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)](#oh_avscreencaptureonerror) | OH_AVScreenCaptureOnError | 当OH_AVScreenCapture实例运行出错时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror)替代。 |
| [typedef void (\*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)](#oh_avscreencaptureonaudiobufferavailable) | OH_AVScreenCaptureOnAudioBufferAvailable | 当OH_AVScreenCapture实例操作期间音频缓存区可用时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [typedef void (\*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)](#oh_avscreencaptureonvideobufferavailable) | OH_AVScreenCaptureOnVideoBufferAvailable | 当OH_AVScreenCapture实例操作期间视频缓存区可用时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [typedef void (\*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)](#oh_avscreencapture_onstatechange) | OH_AVScreenCapture_OnStateChange | 当OH_AVScreenCapture实例操作期间发生状态变更时，将调用函数指针。 |
| [typedef void (\*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)](#oh_avscreencapture_onerror) | OH_AVScreenCapture_OnError | 当OH_AVScreenCapture实例操作期间发生错误时，将调用函数指针。 |
| [typedef void (\*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)](#oh_avscreencapture_onbufferavailable) | OH_AVScreenCapture_OnBufferAvailable | 当OH_AVScreenCapture实例操作期间音频或视频缓存区可用时，将调用该函数指针。 |
| [typedef void (\*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)](#oh_avscreencapture_oncapturecontentchanged) | OH_AVScreenCapture_OnCaptureContentChanged | 当OH_AVScreenCapture实例操作期间录屏内容变化时，将调用函数指针。 |
| [typedef void (\*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)](#oh_avscreencapture_onuserselected) | OH_AVScreenCapture_OnUserSelected | 当用户在授权界面（选择界面）选择参数时，功能接口将参数返回给应用程序。 |
| [typedef void (\*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)](#oh_avscreencapture_onprivacyprotect) | OH_AVScreenCapture_OnPrivacyProtect | 当[OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)实例在运行过程中发生隐私保护事件时，函数指针将被调用。 |

## 枚举类型说明

### OH_CaptureMode

```c
enum OH_CaptureMode
```

**描述**

枚举，表示屏幕录制的不同模式。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_CAPTURE_HOME_SCREEN = 0 | capture home screen |
| OH_CAPTURE_SPECIFIED_SCREEN = 1 | capture a specified screen |
| OH_CAPTURE_SPECIFIED_WINDOW = 2 | capture a specified window |

### OH_AudioCaptureSourceType

```c
enum OH_AudioCaptureSourceType
```

**描述**

枚举，表示屏幕录制时的音频源类型。

**起始版本：** 10

| 枚举项 | 描述 |
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

**描述**

枚举，表示音频编码格式。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_AUDIO_DEFAULT = 0 | Default format |
| OH_AAC_LC = 3 | Advanced Audio Coding Low Complexity (AAC-LC) |
| OH_AUDIO_CODEC_FORMAT_BUTT | Invalid value |

### OH_VideoCodecFormat

```c
enum OH_VideoCodecFormat
```

**描述**

枚举，表示视频编码格式。

**起始版本：** 10

| 枚举项 | 描述 |
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

**描述**

枚举，表示屏幕录制流的数据格式。

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_ORIGINAL_STREAM = 0 | YUV/RGBA/PCM, etc. original stream |
| OH_ENCODED_STREAM = 1 | h264/AAC, etc. encoded stream |
| OH_CAPTURE_FILE = 2 | mp4 file |

### OH_VideoSourceType

```c
enum OH_VideoSourceType
```

**描述**

枚举，表示视频源格式。当前仅支持RGBA格式。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_VIDEO_SOURCE_SURFACE_YUV = 0 | RGBA格式。 |
| OH_VIDEO_SOURCE_SURFACE_ES | Raw encoded data provided through graphic |
| OH_VIDEO_SOURCE_SURFACE_RGBA | RGBA video data provided through graphic |
| OH_VIDEO_SOURCE_BUTT | Invalid value |

### OH_ContainerFormatType

```c
enum OH_ContainerFormatType
```

**描述**

枚举，表示屏幕录制生成的文件类型。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| CFT_MPEG_4A = 0 | Audio format type -- m4a |
| CFT_MPEG_4 = 1 | Video format type -- mp4 |

### OH_AVScreenCaptureStateCode

```c
enum OH_AVScreenCaptureStateCode
```

**描述**

枚举，表示状态码。

**起始版本：** 12

| 枚举项 | 描述 |
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
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_USER = 11 | Screen capture paused by user<br>**起始版本：** 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_USER = 12 | Screen capture resumed by user<br>**起始版本：** 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_PAUSED_BY_APP = 13 | Screen capture paused by app<br>**起始版本：** 26.0.0 |
| OH_SCREEN_CAPTURE_STATE_RESUMED_BY_APP = 14 | Screen capture resumed by app<br>**起始版本：** 26.0.0 |

### OH_AVScreenCaptureBufferType

```c
enum OH_AVScreenCaptureBufferType
```

**描述**

枚举，表示buffer类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_SCREEN_CAPTURE_BUFFERTYPE_VIDEO = 0 | Buffer of video data from screen |
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_INNER = 1 | Buffer of audio data from inner capture |
| OH_SCREEN_CAPTURE_BUFFERTYPE_AUDIO_MIC = 2 | Buffer of audio data from microphone |

### OH_AVScreenCaptureFilterableAudioContent

```c
enum OH_AVScreenCaptureFilterableAudioContent
```

**描述**

枚举，表示buffer类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_SCREEN_CAPTURE_NOTIFICATION_AUDIO = 0 | Audio content of notification sound |
| OH_SCREEN_CAPTURE_CURRENT_APP_AUDIO = 1 | Audio content of the sound of the app itself |

### OH_AVScreenCaptureContentChangedEvent

```c
enum OH_AVScreenCaptureContentChangedEvent
```

**描述**

枚举，表示录屏内容变更事件。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| OH_SCREEN_CAPTURE_CONTENT_HIDE = 0 | 录屏内容变为隐藏。 |
| OH_SCREEN_CAPTURE_CONTENT_VISIBLE = 1 | 录屏内容变为可见。 |
| OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE = 2 | 录屏内容状态变化为不可用，如录屏窗口关闭。 |

### OH_ScreenCaptureHighlightMode

```c
enum OH_ScreenCaptureHighlightMode
```

**描述**

枚举，表示屏幕录制高亮边框的模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_HIGHLIGHT_MODE_CLOSED = 0 | 默认模式，用方形全包边框高亮显示录制区域。 |
| OH_HIGHLIGHT_MODE_CORNER_WRAP = 1 | 用四角包裹边框高亮显示录制区域。 |

### OH_AVScreenCapture_FillMode

```c
enum OH_AVScreenCapture_FillMode
```

**描述**

图像填充模式。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| OH_SCREENCAPTURE_FILLMODE_ASPECT_SCALE_FIT = 0 | 保持图像原始宽高比匹配目标图像大小，若比例不一致可能存在黑边。 |
| OH_SCREENCAPTURE_FILLMODE_SCALE_TO_FILL = 1 | 图像拉伸匹配目标图像大小，若比例不一致图像变形。 |

### OH_CapturePickerMode

```c
enum OH_CapturePickerMode
```

**描述**

枚举，表示Picker显示模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_CAPTURE_PICKER_MODE_WINDOW_ONLY = 0 | 仅显示窗口模式。 |
| OH_CAPTURE_PICKER_MODE_SCREEN_ONLY = 1 | 仅显示屏幕模式。 |
| OH_CAPTURE_PICKER_MODE_SCREEN_AND_WINDOW = 2 | 显示屏幕和窗口模式（默认模式）。 |


## 函数说明

### OH_AVScreenCaptureOnError()

```c
typedef void (*OH_AVScreenCaptureOnError)(OH_AVScreenCapture *capture, int32_t errorCode)
```

**描述**

当OH_AVScreenCapture实例运行出错时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| int32_t errorCode | 指定错误码。 |

### OH_AVScreenCaptureOnAudioBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnAudioBufferAvailable)(OH_AVScreenCapture *capture, bool isReady, OH_AudioCaptureSourceType type)
```

**描述**

当OH_AVScreenCapture实例操作期间音频缓存区可用时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| bool isReady | 音频缓存区是否可用。true表示音频缓存区可用，false表示音频缓存区不可用。 |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | 音频源类型。 |

### OH_AVScreenCaptureOnVideoBufferAvailable()

```c
typedef void (*OH_AVScreenCaptureOnVideoBufferAvailable)(OH_AVScreenCapture *capture, bool isReady)
```

**描述**

当OH_AVScreenCapture实例操作期间视频缓存区可用时，将调用函数指针。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| bool isReady | 视频缓存区是否可用。true表示视频缓存区可用，false表示视频缓存区不可用。 |

### OH_AVScreenCapture_OnStateChange()

```c
typedef void (*OH_AVScreenCapture_OnStateChange)(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData)
```

**描述**

当OH_AVScreenCapture实例操作期间发生状态变更时，将调用函数指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (struct OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode) stateCode | 指定状态码。 |
| void \*userData | 指向应用设置该回调处理方法时提供的自定义数据的指针。 |

### OH_AVScreenCapture_OnError()

```c
typedef void (*OH_AVScreenCapture_OnError)(OH_AVScreenCapture *capture, int32_t errorCode, void *userData)
```

**描述**

当OH_AVScreenCapture实例操作期间发生错误时，将调用函数指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| int32_t errorCode | 指定错误码。 |
| void \*userData | 指向应用设置该回调处理方法时提供的自定义数据的指针。 |

### OH_AVScreenCapture_OnBufferAvailable()

```c
typedef void (*OH_AVScreenCapture_OnBufferAvailable)(OH_AVScreenCapture *capture, OH_AVBuffer *buffer, OH_AVScreenCaptureBufferType bufferType, int64_t timestamp, void *userData)
```

**描述**

当OH_AVScreenCapture实例操作期间音频或视频缓存区可用时，将调用该函数指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture \*capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVBuffer](../AVCodecKit/capi-core-oh-avbuffer.md) \*buffer | 指向OH_AVBuffer缓存区实例的指针，该回调方法执行结束返回后，数据缓存区不再有效。 |
| [OH_AVScreenCaptureBufferType](capi-native-avscreen-capture-base-h.md#oh_avscreencapturebuffertype) bufferType | 可用缓存区的数据类型。 |
| int64_t timestamp | 时间戳，单位纳秒。 |
| void \*userData | 指向应用设置该回调处理方法时提供的自定义数据的指针。 |

### OH_AVScreenCapture_OnCaptureContentChanged()

```c
typedef void (*OH_AVScreenCapture_OnCaptureContentChanged)(OH_AVScreenCapture* capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect* area, void *userData)
```

**描述**

当OH_AVScreenCapture实例操作期间录屏内容变化时，将调用函数指针。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_AVScreenCaptureContentChangedEvent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturecontentchangedevent) event | enum for content change event |
| [OH_Rect](capi-avscreencapture-oh-rect.md)\* area | capture content rect position |
| void \*userData | Pointer to user specific data |

### OH_AVScreenCapture_OnUserSelected()

```c
typedef void (*OH_AVScreenCapture_OnUserSelected)(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData)
```

**描述**

当用户在授权界面（选择界面）选择参数时，功能接口将参数返回给应用程序。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md)\* selections | The recording parameter informationselected by the user on the authorization interface |
| void \*userData | Pointer to user specific data |

### OH_AVScreenCapture_OnPrivacyProtect()

```c
typedef void (*OH_AVScreenCapture_OnPrivacyProtect)(OH_AVScreenCapture* capture, OH_PrivacyProtectInfo* privacyProtect, void *userData)
```

**描述**

当[OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)实例在运行过程中发生隐私保护事件时，函数指针将被调用。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVScreenCapture\* capture | Pointer to an OH_AVScreenCapture instance |
| [OH_PrivacyProtectInfo](capi-avscreencapture-oh-privacyprotectinfo.md)\* privacyProtect | Pointer to privacy protect info |
| void \*userData | Pointer to user specific data |


