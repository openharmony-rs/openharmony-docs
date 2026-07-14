# avrecorder_base.h

## 概述

定义了媒体AVRecorder的结构体和枚举。

**库：** libavrecorder.so

**起始版本：** 18

**相关模块：** [AVRecorder](capi-avrecorder.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVRecorder_Profile](capi-avrecorder-oh-avrecorder-profile.md) | OH_AVRecorder_Profile | 定义音视频录制的详细参数。 |
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) | OH_AVRecorder_Location | 提供媒体资源的地理位置信息。 |
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) | OH_AVRecorder_MetadataTemplate | 定义元数据的基本模板。 |
| [OH_AVRecorder_Metadata](capi-avrecorder-oh-avrecorder-metadata.md) | OH_AVRecorder_Metadata | 元数据信息数据结构。 |
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) | OH_AVRecorder_Config | 提供媒体AVRecorder的配置定义。 |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) | OH_AVRecorder_Range | 表示类型的范围。 |
| [OH_AVRecorder_EncoderInfo](capi-avrecorder-oh-avrecorder-encoderinfo.md) | OH_AVRecorder_EncoderInfo | 提供编码器信息。 |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) | OH_AVRecorder | 初始化AVRecorder。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVRecorder_AudioSourceType](#oh_avrecorder_audiosourcetype) | OH_AVRecorder_AudioSourceType | AVRecorder的音频源类型。 |
| [OH_AVRecorder_VideoSourceType](#oh_avrecorder_videosourcetype) | OH_AVRecorder_VideoSourceType | AVRecorder的视频源类型。 |
| [OH_AVRecorder_CodecMimeType](#oh_avrecorder_codecmimetype) | OH_AVRecorder_CodecMimeType | 编码器MIME类型。 |
| [OH_AVRecorder_ContainerFormatType](#oh_avrecorder_containerformattype) | OH_AVRecorder_ContainerFormatType | 容器格式类型（容器格式类型的缩写是 CFT）。 |
| [OH_AVRecorder_State](#oh_avrecorder_state) | OH_AVRecorder_State | AVRecorder状态。 |
| [OH_AVRecorder_StateChangeReason](#oh_avrecorder_statechangereason) | OH_AVRecorder_StateChangeReason | AVRecorder状态变化的原因。 |
| [OH_AVRecorder_FileGenerationMode](#oh_avrecorder_filegenerationmode) | OH_AVRecorder_FileGenerationMode | 创建录制文件的模式。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)](#oh_avrecorder_onstatechange) | OH_AVRecorder_OnStateChange | 当录制状态发生变化时调用。 |
| [typedef void (\*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avrecorder_onerror) | OH_AVRecorder_OnError | 当录制过程中发生错误时调用。 |
| [typedef void (\*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)](#oh_avrecorder_onuri) | OH_AVRecorder_OnUri | 当录制在[OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE模式下时调用。 |

## 枚举类型说明

### OH_AVRecorder_AudioSourceType

```c
enum OH_AVRecorder_AudioSourceType
```

**描述**

AVRecorder的音频源类型。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_DEFAULT = 0 | Default audio source type. |
| AVRECORDER_MIC = 1 | Source type mic. |
| AVRECORDER_VOICE_RECOGNITION = 2 | Source type Voice recognition. |
| AVRECORDER_VOICE_COMMUNICATION = 7 | Source type Voice communication. |
| AVRECORDER_VOICE_MESSAGE = 10 | Source type Voice message. |
| AVRECORDER_CAMCORDER = 13 | Source type Camcorder. |

### OH_AVRecorder_VideoSourceType

```c
enum OH_AVRecorder_VideoSourceType
```

**描述**

AVRecorder的视频源类型。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_SURFACE_YUV = 0 | Surface raw data. |
| AVRECORDER_SURFACE_ES = 1 | Surface ES data. |

### OH_AVRecorder_CodecMimeType

```c
enum OH_AVRecorder_CodecMimeType
```

**描述**

编码器MIME类型。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_VIDEO_AVC = 2 | H.264 codec MIME type. |
| AVRECORDER_AUDIO_AAC = 3 | AAC codec MIME type. |
| AVRECORDER_AUDIO_MP3 = 4 | mp3 codec MIME type. |
| AVRECORDER_AUDIO_G711MU = 5 | G711-mulaw codec MIME type. |
| AVRECORDER_VIDEO_MPEG4 = 6 | MPEG4 codec MIME type. |
| AVRECORDER_VIDEO_HEVC = 8 | H.265 codec MIME type. |
| AVRECORDER_AUDIO_AMR_NB = 9 | AMR-NB codec MIME type. |
| AVRECORDER_AUDIO_AMR_WB = 10 | AMR-WB codec MIME type. |

### OH_AVRecorder_ContainerFormatType

```c
enum OH_AVRecorder_ContainerFormatType
```

**描述**

容器格式类型（容器格式类型的缩写是 CFT）。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_CFT_MPEG_4 = 2 | A video container format type mp4. |
| AVRECORDER_CFT_MPEG_4A = 6 | An audio container format type m4a. |
| AVRECORDER_CFT_AMR = 8 | An audio container format type amr. |
| AVRECORDER_CFT_MP3 = 9 | An audio container format type mp3. |
| AVRECORDER_CFT_WAV = 10 | An audio container format type wav. |
| AVRECORDER_CFT_AAC = 11 | 音频容器格式类型aac（带ADTS头）。<br>**起始版本：** 20 |

### OH_AVRecorder_State

```c
enum OH_AVRecorder_State
```

**描述**

AVRecorder状态。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_IDLE = 0 | idle states |
| AVRECORDER_PREPARED = 1 | prepared states |
| AVRECORDER_STARTED = 2 | started states |
| AVRECORDER_PAUSED = 3 | paused states |
| AVRECORDER_STOPPED = 4 | stopped states |
| AVRECORDER_RELEASED = 5 | released states |
| AVRECORDER_ERROR = 6 | error states |

### OH_AVRecorder_StateChangeReason

```c
enum OH_AVRecorder_StateChangeReason
```

**描述**

AVRecorder状态变化的原因。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_USER = 0 | State changed by user operation |
| AVRECORDER_BACKGROUND = 1 | State changed by background action |

### OH_AVRecorder_FileGenerationMode

```c
enum OH_AVRecorder_FileGenerationMode
```

**描述**

创建录制文件的模式。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| AVRECORDER_APP_CREATE = 0 | Application Creation |
| AVRECORDER_AUTO_CREATE_CAMERA_SCENE = 1 | System Creation. Valid only in camera scene |


## 函数说明

### OH_AVRecorder_OnStateChange()

```c
typedef void (*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)
```

**描述**

当录制状态发生变化时调用。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVRecorder \*recorder | OH_AVRecorder实例的指针。 |
| [OH_AVRecorder_State](capi-avrecorder-base-h.md#oh_avrecorder_state) state | 表示录制器状态。 |
| [OH_AVRecorder_StateChangeReason](capi-avrecorder-base-h.md#oh_avrecorder_statechangereason) reason | 录制器状态变化的原因。 |
| void \*userData | 用户特定数据的指针。 |

### OH_AVRecorder_OnError()

```c
typedef void (*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)
```

**描述**

当录制过程中发生错误时调用。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVRecorder \*recorder | OH_AVRecorder实例的指针。 |
| int32_t errorCode | 错误码，详细说明请参见{@link OH_AVErrCode}。 |
| const char \*errorMsg | 错误信息。 |
| void \*userData | 用户特定数据的指针。 |

### OH_AVRecorder_OnUri()

```c
typedef void (*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)
```

**描述**

当录制在[OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE模式下时调用。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVRecorder \*recorder | OH_AVRecorder实例的指针。 |
| OH_MediaAsset \*asset | OH_MediaAsset实例的指针。 |
| void \*userData | 用户特定数据的指针。 |


