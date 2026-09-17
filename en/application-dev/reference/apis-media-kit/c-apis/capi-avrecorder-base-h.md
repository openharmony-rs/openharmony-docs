# avrecorder_base.h

## Overview

The file declares the struct and enums used by the AVRecorder.

**Library**: libavrecorder.so

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVRecorder_Profile](capi-avrecorder-oh-avrecorder-profile.md) | OH_AVRecorder_Profile | The struct describes the parameters used for audio and video recording. |
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) | OH_AVRecorder_Location | The struct describes the geographical location information about a media asset. |
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) | OH_AVRecorder_MetadataTemplate | The struct describes the basic template of metadata. |
| [OH_AVRecorder_Metadata](capi-avrecorder-oh-avrecorder-metadata.md) | OH_AVRecorder_Metadata | The struct describes the metadata. |
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) | OH_AVRecorder_Config | The struct describes the AVRecorder configuration. |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) | OH_AVRecorder_Range | The struct describes the range. |
| [OH_AVRecorder_EncoderInfo](capi-avrecorder-oh-avrecorder-encoderinfo.md) | OH_AVRecorder_EncoderInfo | The struct describes the encoder information. |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) | OH_AVRecorder | The struct initializes an AVRecorder. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVRecorder_AudioSourceType](#oh_avrecorder_audiosourcetype) | OH_AVRecorder_AudioSourceType | Enumerates the audio source types of the AVRecorder. |
| [OH_AVRecorder_VideoSourceType](#oh_avrecorder_videosourcetype) | OH_AVRecorder_VideoSourceType | Enumerates the video source types of the AVRecorder. |
| [OH_AVRecorder_CodecMimeType](#oh_avrecorder_codecmimetype) | OH_AVRecorder_CodecMimeType | Enumerates the MIME types of the encoder. |
| [OH_AVRecorder_ContainerFormatType](#oh_avrecorder_containerformattype) | OH_AVRecorder_ContainerFormatType | Enumerates the Container Format Types (CFTs). |
| [OH_AVRecorder_State](#oh_avrecorder_state) | OH_AVRecorder_State | Enumerates the AVRecorder states. |
| [OH_AVRecorder_StateChangeReason](#oh_avrecorder_statechangereason) | OH_AVRecorder_StateChangeReason | Enumerates the reasons for AVRecorder state changes. |
| [OH_AVRecorder_FileGenerationMode](#oh_avrecorder_filegenerationmode) | OH_AVRecorder_FileGenerationMode | Enumerates the modes available for creating a recording file. |

### Macro

| Name | Description |
| -- | -- |
| MULTIMEDIA_PLAYER_FRAMEWORK_NATIVE_AVRECORDER_BASE_H | The file declares the struct and enums used by the AVRecorder.<br>**Since**: 18 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)](#oh_avrecorder_onstatechange) | OH_AVRecorder_OnStateChange | Called when the AVRecorder state changes. |
| [typedef void (\*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avrecorder_onerror) | OH_AVRecorder_OnError | Called when an error occurs during recording. |
| [typedef void (\*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)](#oh_avrecorder_onuri) | OH_AVRecorder_OnUri | Called when the recording is in [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE mode. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData) | Called when the AVRecorder state changes.<br>**Since**: 18 |
| void (*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData) | Called when an error occurs during recording.<br>**Since**: 18 |
| void (*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData) | Called when the recording is in [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE mode.<br>**Since**: 18 |

## Enum type description

### OH_AVRecorder_AudioSourceType

```c
enum OH_AVRecorder_AudioSourceType
```

**Description**

Enumerates the audio source types of the AVRecorder.

**Since**: 18

| Enum item | Description |
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

**Description**

Enumerates the video source types of the AVRecorder.

**Since**: 18

| Enum item | Description |
| -- | -- |
| AVRECORDER_SURFACE_YUV = 0 | Surface raw data. |
| AVRECORDER_SURFACE_ES = 1 | Surface ES data. |

### OH_AVRecorder_CodecMimeType

```c
enum OH_AVRecorder_CodecMimeType
```

**Description**

Enumerates the MIME types of the encoder.

**Since**: 18

| Enum item | Description |
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

**Description**

Enumerates the Container Format Types (CFTs).

**Since**: 18

| Enum item | Description |
| -- | -- |
| AVRECORDER_CFT_MPEG_4 = 2 | A video container format type mp4. |
| AVRECORDER_CFT_MPEG_4A = 6 | An audio container format type m4a. |
| AVRECORDER_CFT_AMR = 8 | An audio container format type amr. |
| AVRECORDER_CFT_MP3 = 9 | An audio container format type mp3. |
| AVRECORDER_CFT_WAV = 10 | An audio container format type wav. |
| AVRECORDER_CFT_AAC = 11 | Audio container format aac (with ADTS header).<br>**Since**: 20 |

### OH_AVRecorder_State

```c
enum OH_AVRecorder_State
```

**Description**

Enumerates the AVRecorder states.

**Since**: 18

| Enum item | Description |
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

**Description**

Enumerates the reasons for AVRecorder state changes.

**Since**: 18

| Enum item | Description |
| -- | -- |
| AVRECORDER_USER = 0 | State changed by user operation |
| AVRECORDER_BACKGROUND = 1 | State changed by background action |

### OH_AVRecorder_FileGenerationMode

```c
enum OH_AVRecorder_FileGenerationMode
```

**Description**

Enumerates the modes available for creating a recording file.

**Since**: 18

| Enum item | Description |
| -- | -- |
| AVRECORDER_APP_CREATE = 0 | Application Creation |
| AVRECORDER_AUTO_CREATE_CAMERA_SCENE = 1 | System Creation. Valid only in camera scene |


## Function description

### OH_AVRecorder_OnStateChange()

```c
typedef void (*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)
```

**Description**

Called when the AVRecorder state changes.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) \*recorder | Pointer to the OH_AVRecorder instance. |
| [OH_AVRecorder_State](capi-avrecorder-base-h.md#oh_avrecorder_state) state | AVRecorder state. |
| [OH_AVRecorder_StateChangeReason](capi-avrecorder-base-h.md#oh_avrecorder_statechangereason) reason | Reason for the AVRecorder state change. |
| void \*userData | Pointer to user-defined data. |

### OH_AVRecorder_OnError()

```c
typedef void (*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)
```

**Description**

Called when an error occurs during recording.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) \*recorder | Pointer to the OH_AVRecorder instance. |
| int32_t errorCode | Error code. For details, see {@link OH_AVErrCode}. |
| const char \*errorMsg | Pointer to the error message. |
| void \*userData | Pointer to user-defined data. |

### OH_AVRecorder_OnUri()

```c
typedef void (*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)
```

**Description**

Called when the recording is in [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE mode.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) \*recorder | Pointer to the OH_AVRecorder instance. |
| OH_MediaAsset \*asset | Pointer to the OH_MediaAsset instance. |
| void \*userData | Pointer to user-defined data. |


