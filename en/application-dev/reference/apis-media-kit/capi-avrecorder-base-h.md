# avrecorder_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## Overview

Defines the struct, enums, and callbacks used by AVRecorder.

**File to include**: &lt;multimedia/player_framework/avrecorder_base.h&gt;

**Library**: libavrecorder.so

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVRecorder_Profile](capi-avrecorder-oh-avrecorder-profile.md) | OH_AVRecorder_Profile | Describes the parameters used for audio and video recording. By configuring parameters such as the audio/video encoding format, bitrate, sampling rate, frame rate, resolution, container format, HDR recording, and whether to enable temporally scalable video encoding, you can flexibly control the recording quality and file size. This is applicable to scenarios where you need to customize the recording quality, select the recording content type (audio-only, video-only, or both), and enable HDR recording or temporally scalable video encoding.<br>You can choose to record only audio, only video, or both by setting the parameters.<br>1. When **audioBitrate** or **audioChannels** is set to **0**, audio recording is disabled.<br>2. When **videoFrameWidth** or **videoFrameHeight** is set to **0**, video recording is disabled.<br>For details about the value range of each parameter, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9).|
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) | OH_AVRecorder | Defines a struct for audio and video recording, which is used to represent an AVRecorder instance. It supports audio and video data collection and recording, and provides capabilities such as recording process control and callbacks for event listeners. It is applicable to scenarios where audio and video need to be recorded and saved as files, such as video conference recording, screen recording apps, and security surveillance recording.|
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) | OH_AVRecorder_Location | Describes the geographical location information about a media asset and supports the annotation of latitude and longitude during audio and video recording. This struct uses the [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) API of AVRecorder to write the latitude and longitude information into the metadata of the recording file. You need to set the latitude and longitude parameters of this structure before recording. During recording, the geographical location information is automatically embedded into the generated media file. This struct is applicable to scenarios where geographical locations need to be embedded in the recording result, such as marking the shooting location during video shooting, marking the track location in activity record apps, and recording the itinerary coordinates in travel diary apps. This facilitates subsequent retrieval and classification management of media resources by location.|
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) | OH_AVRecorder_MetadataTemplate | Defines the basic template of metadata during audio and video recording. Metadata is organized in key-value pair format. This struct is applicable to scenarios where custom metadata (such as title, author, and description) needs to be added to the recording output, facilitating the classification, retrieval, and management of recorded files. You can use the [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) API of AVRecorder to set the metadata in this struct to the recording output file.|
| [OH_AVRecorder_Metadata](capi-avrecorder-oh-avrecorder-metadata.md) | OH_AVRecorder_Metadata | Defines the metadata structure for recording, which is used to describe the genre, video rotation angle, geographical location, and custom parameters of media resources. This struct is applicable to scenarios where media metadata needs to be carried or read during recording.|
| [OH_AVRecorder_Config](capi-avrecorder-oh-avrecorder-config.md) | OH_AVRecorder_Config | Describes the AVRecorder configuration, which is used to set the audio source type, video source type, encoding configuration, output file URL, file generation mode, metadata, and maximum recording duration during audio and video recording. This struct is applicable to scenarios where custom recording configurations are required.|
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) | OH_AVRecorder_Range | Defines the value range of AVRecorder parameters (such as the bit rate and frame rate) to limit the configurable range of recording parameters. You can use the [OH_AVRecorder_GetAvailableEncoder](capi-avrecorder-h.md#oh_avrecorder_getavailableencoder) API to obtain the value range of encoder parameters and set the parameter values within the range from **min** to **max** to ensure that the configuration is valid.|
| [OH_AVRecorder_EncoderInfo](capi-avrecorder-oh-avrecorder-encoderinfo.md) | OH_AVRecorder_EncoderInfo | Provides AVRecorder encoder capability information, including the MIME type, bit rate range, and frame rate range of the encoder. This struct is applicable to scenarios where you need to query and select a proper audio or video encoder configuration before recording, helping you select the optimal encoding configuration based on the encoder capability parameters. You can obtain this struct object by calling [OH_AVRecorder_GetAvailableEncoder](capi-avrecorder-h.md#oh_avrecorder_getavailableencoder).|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVRecorder_AudioSourceType](#oh_avrecorder_audiosourcetype) | OH_AVRecorder_AudioSourceType | Enumerates the audio source types of the AVRecorder.|
| [OH_AVRecorder_VideoSourceType](#oh_avrecorder_videosourcetype) | OH_AVRecorder_VideoSourceType | Enumerates the video source types of the AVRecorder.|
| [OH_AVRecorder_CodecMimeType](#oh_avrecorder_codecmimetype) | OH_AVRecorder_CodecMimeType | Enumerates the MIME types of the encoder, which are used to specify the encoding format of audio and video data during recording. The encoder type must match the container format. If they do not match, the recording will fail. For details about the mapping, see the description of the corresponding encoder type.|
| [OH_AVRecorder_ContainerFormatType](#oh_avrecorder_containerformattype) | OH_AVRecorder_ContainerFormatType | Enumerates the Container Format Types (CFTs), which are used to specify the encapsulation format of recording files. The container format must be compatible with the MIME type of the encoder. If they are incompatible, the recording will fail. For details about the encoder types supported by each container format, see the description of the corresponding container format.|
| [OH_AVRecorder_State](#oh_avrecorder_state) | OH_AVRecorder_State | Enumerates the AVRecorder states, which indicate the different phases of the recorder in its lifecycle. The operations that can be performed vary depending on the state.|
| [OH_AVRecorder_StateChangeReason](#oh_avrecorder_statechangereason) | OH_AVRecorder_StateChangeReason | Enumerates the reasons for AVRecorder state changes, which are used to determine whether the state change is triggered by a user operation or a background event. This helps the app execute the corresponding processing logic based on the reason.|
| [OH_AVRecorder_FileGenerationMode](#oh_avrecorder_filegenerationmode) | OH_AVRecorder_FileGenerationMode | Defines the mode for generating a recording file. This mode specifies how media files are created. It is applicable to recording scenarios where you need to choose whether the app or the system automatically manages the files.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)](#oh_avrecorder_onstatechange) | OH_AVRecorder_OnStateChange | Called when the AVRecorder state changes.|
| [typedef void (*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avrecorder_onerror) | OH_AVRecorder_OnError | Called when an error occurs during recording.|
| [typedef void (*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)](#oh_avrecorder_onuri) | OH_AVRecorder_OnUri | Called when the recording file is generated in [OH_AVRecorder_FileGenerationMode](#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE mode to notify the app to obtain the media resources generated during recording.|

## Enum Description

### OH_AVRecorder_AudioSourceType

```c
enum OH_AVRecorder_AudioSourceType
```

**Description**

Enumerates the audio source types of the AVRecorder.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_DEFAULT = 0 | Default audio source. This parameter is applicable to common recording scenarios where no specific audio source type needs to be specified.|
| AVRECORDER_MIC = 1 | Microphone audio source.|
| AVRECORDER_VOICE_RECOGNITION = 2 | Audio source in speech recognition scenarios.|
| AVRECORDER_VOICE_COMMUNICATION = 7 | Voice communication source.|
| AVRECORDER_VOICE_MESSAGE = 10 | Voice message source.|
| AVRECORDER_CAMCORDER = 13 | Audio source in camera recording scenarios.|

### OH_AVRecorder_VideoSourceType

```c
enum OH_AVRecorder_VideoSourceType
```

**Description**

Enumerates the video source types of the AVRecorder.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_SURFACE_YUV = 0 | Raw data surface. This parameter is applicable to scenarios where the original video frame data needs to be encoded.|
| AVRECORDER_SURFACE_ES = 1 | ES data surface. This parameter is applicable to scenarios where the existing encoded data (such as the hard coding output) does not need to be encoded again.|

### OH_AVRecorder_CodecMimeType

```c
enum OH_AVRecorder_CodecMimeType
```

**Description**

Enumerates the MIME types of the encoder, which are used to specify the encoding format of audio and video data during recording. The encoder type must match the container format. If they do not match, the recording will fail. For details about the mapping, see the description of the corresponding encoder type.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_VIDEO_AVC = 2 | MIME type of the H.264 video encoder. It must be used together with the MP4 container format.|
| AVRECORDER_AUDIO_AAC = 3 | MIME type of the AAC audio encoder. It must be used together with the AAC, MP4, or M4A container format.|
| AVRECORDER_AUDIO_MP3 = 4 | MIME type of the MP3 audio encoder. It must be used together with the MP3 container format.|
| AVRECORDER_AUDIO_G711MU = 5 | MIME type of the G711-mulaw audio encoder. It must be used together with the WAV container format.|
| AVRECORDER_VIDEO_MPEG4 = 6 | MIME type of the MPEG4 video encoder. It must be used together with the MP4 container format.|
| AVRECORDER_VIDEO_HEVC = 8 | MIME type of the H.265 video encoder. It must be used together with the MP4 container format.|
| AVRECORDER_AUDIO_AMR_NB = 9 | MIME type of the AMR_NB audio encoder. It must be used together with the AMR container format.|
| AVRECORDER_AUDIO_AMR_WB = 10 | MIME type of the AMR_WB audio encoder. It must be used together with the AMR container format.|

### OH_AVRecorder_ContainerFormatType

```c
enum OH_AVRecorder_ContainerFormatType
```

**Description**

Enumerates the Container Format Types (CFTs), which are used to specify the encapsulation format of recording files. The container format must be compatible with the MIME type of the encoder. If they are incompatible, the recording will fail. For details about the encoder types supported by each container format, see the description of the corresponding container format.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_CFT_MPEG_4 = 2 | Video container format mp4. AAC audio encoder and MPEG4, H.264, or H.265 video encoder are supported.|
| AVRECORDER_CFT_MPEG_4A = 6 | Audio container format m4a. AAC audio encoder is supported.|
| AVRECORDER_CFT_AMR = 8 | Audio container format amr. AMR_NB and AMR_WB audio encoders are supported.|
| AVRECORDER_CFT_MP3 = 9 | Audio container format mp3. MP3 audio encoder is supported.|
| AVRECORDER_CFT_WAV = 10 | Audio container format wav. G711-mulaw audio encoder is supported.|
| AVRECORDER_CFT_AAC = 11 | Audio container format aac (with ADTS header). AAC audio encoder is supported.<br>**Since**: 20|

### OH_AVRecorder_State

```c
enum OH_AVRecorder_State
```

**Description**

Enumerates the AVRecorder states, which indicate the different phases of the recorder in its lifecycle. The operations that can be performed vary depending on the state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_IDLE = 0 | Idle. This is the default initial state after an AVRecorder instance is created. In this state, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) to set recording parameters, and the AVRecorder transitions to the **AVRECORDER_PREPARED** state.|
| AVRECORDER_PREPARED = 1 | Prepared. After the parameters are set, you can call [OH_AVRecorder_Start](capi-avrecorder-h.md#oh_avrecorder_start) to start recording, and the AVRecorder transitions to the **AVRECORDER_STARTED** state.|
| AVRECORDER_STARTED = 2 | Started. Recording is in progress. In this case, you can call [OH_AVRecorder_Pause](capi-avrecorder-h.md#oh_avrecorder_pause) to pause recording, and the AVRecorder transitions to the **AVRECORDER_PAUSED** state.<br>You can also call [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop) to stop recording, and the AVRecorder transitions to the **AVRECORDER_STOPPED** state.|
| AVRECORDER_PAUSED = 3 | Paused. In this state, you can call [OH_AVRecorder_Resume](capi-avrecorder-h.md#oh_avrecorder_resume) to resume recording, and the AVRecorder transitions to the **AVRECORDER_STARTED** state.<br>You can also call [OH_AVRecorder_Stop](capi-avrecorder-h.md#oh_avrecorder_stop) to stop recording, and the AVRecorder transitions to the **AVRECORDER_STOPPED** state.|
| AVRECORDER_STOPPED = 4 | Stopped. In this state, you can call [OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) to set recording parameters, and the AVRecorder reenters the **AVRECORDER_PREPARED** state.|
| AVRECORDER_RELEASED = 5 | Released. The recording resources are released. No operation can be performed at this time. In any other state, you can call [OH_AVRecorder_Release](capi-avrecorder-h.md#oh_avrecorder_release) to transition to the **AVRECORDER_RELEASED** state.|
| AVRECORDER_ERROR = 6 | Error state. AVRecorder transitions to this state when an irreversible error occurs in the AVRecorder instance.<br>You should call [OH_AVRecorder_Reset](capi-avrecorder-h.md#oh_avrecorder_reset) to reset the AVRecorder instance or call [OH_AVRecorder_Release](capi-avrecorder-h.md#oh_avrecorder_release) to release resources in the **AVRECORDER_ERROR** state. The recording cannot continue.|

### OH_AVRecorder_StateChangeReason

```c
enum OH_AVRecorder_StateChangeReason
```

**Description**

Enumerates the reasons for AVRecorder state changes, which are used to determine whether the state change is triggered by a user operation or a background event. This helps the app execute the corresponding processing logic based on the reason.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_USER = 0 | The state change is caused by user operations. For example, when the user proactively calls the **Start**, **Pause**, **Resume**, or **Stop** API.|
| AVRECORDER_BACKGROUND = 1 | The state change is caused by background operations. For example, when the recording state is automatically changed due to audio interruption or recording timeout.|

### OH_AVRecorder_FileGenerationMode

```c
enum OH_AVRecorder_FileGenerationMode
```

**Description**

Defines the mode for generating a recording file. This mode specifies how media files are created. It is applicable to recording scenarios where you need to choose whether the app or the system automatically manages the files.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18

| Enum Item| Description|
| -- | -- |
| AVRECORDER_APP_CREATE = 0 | The app creates a media file in the sandbox. In this mode, the [OH_AVRecorder_OnUri](#oh_avrecorder_onuri) callback will not be triggered.|
| AVRECORDER_AUTO_CREATE_CAMERA_SCENE = 1 | The system creates a media file. In this mode, the [OH_AVRecorder_OnUri](#oh_avrecorder_onuri) callback will be triggered. The app can obtain the media resource object generated during recording through the callback.|


## Function Description

### OH_AVRecorder_OnStateChange()

```c
typedef void (*OH_AVRecorder_OnStateChange)(OH_AVRecorder *recorder, OH_AVRecorder_State state, OH_AVRecorder_StateChangeReason reason, void *userData)
```

**Description**

Called when the AVRecorder state changes.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_AVRecorder_State](#oh_avrecorder_state) state | AVRecorder state.|
| [OH_AVRecorder_StateChangeReason](#oh_avrecorder_statechangereason) reason | Reason for the AVRecorder state change.|
|  void *userData | Pointer to the custom data passed during callback registration. When the callback is triggered, the system returns the custom data to the caller.|

### OH_AVRecorder_OnError()

```c
typedef void (*OH_AVRecorder_OnError)(OH_AVRecorder *recorder, int32_t errorCode, const char *errorMsg, void *userData)
```

**Description**

Called when an error occurs during recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
|  int32_t errorCode | Error code. For details, see [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode).|
|  const char *errorMsg | A character string that describes the error message.|
| void *userData | Pointer to the custom data passed during callback registration. When the callback is triggered, the system returns the custom data to the caller.|

### OH_AVRecorder_OnUri()

```c
typedef void (*OH_AVRecorder_OnUri)(OH_AVRecorder *recorder, OH_MediaAsset *asset, void *userData)
```

**Description**

Called when the recording file is generated in [OH_AVRecorder_FileGenerationMode](#oh_avrecorder_filegenerationmode).AVRECORDER_AUTO_CREATE_CAMERA_SCENE mode to notify the app to obtain the media resources generated during recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Since**: 18


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVRecorder](capi-avrecorder-oh-avrecorder.md) *recorder | Pointer to the OH_AVRecorder instance.|
| [OH_MediaAsset](../apis-media-library-kit/capi-mediaassetmanager-oh-mediaasset.md) *asset | Pointer to the **OH_MediaAsset** instance, which is used to return the media resource object automatically created by the system. Your app can use this object to access the media file generated after recording.|
|  void *userData | Pointer to the custom data passed during callback registration. When the callback is triggered, the system returns the custom data to the caller.|
