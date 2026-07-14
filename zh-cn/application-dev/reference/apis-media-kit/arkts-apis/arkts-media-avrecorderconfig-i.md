# AVRecorderConfig

Describes the audio and video recording parameters.

The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording,
video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**.
For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType**
and **videoSourceType**.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

Type of the audio source to record. This parameter is mandatory for audio recording.<br>**Atomic service API**:
This API can be used in atomic services since API version 12.

**类型：** AudioSourceType

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileGenerationMode

```TypeScript
fileGenerationMode?: FileGenerationMode
```

Mode for creating the file, which is used together with on('photoAssetAvailable').

**类型：** FileGenerationMode

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## location

```TypeScript
location?: Location
```

Geographical location of the recorded video. By default, the geographical location information is not recorded.
<br>This API is supported since API version 6 and deprecated since API version 12. You are advised to use
**AVMetadata.location** instead. If both parameters are set, **AVMetadata.location** is used.

**类型：** Location

**起始版本：** 9

**废弃版本：** 12

**替代接口：** location

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## maxDuration

```TypeScript
maxDuration?: number
```

Maximum recording duration, in seconds. The value range is [1, 2^31-1]. If an invalid value is provided,
it is reset to the maximum allowed duration. Once the recording reaches the specified duration,
it stops automatically and notifies via the **stateChange** callback that the recording has stopped:
AVRecorderState = 'stopped', StateChangeReason = BACKGROUND.

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## metadata

```TypeScript
metadata?: AVMetadata
```

Metadata. For details, see @AVMetadata.

**类型：** AVMetadata

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## profile

```TypeScript
profile: AVRecorderProfile
```

Recording profile. This parameter is mandatory.<br>**Atomic service API**: This API can be used in atomic
services since API version 12.

**类型：** AVRecorderProfile

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## rotation

```TypeScript
rotation?: number
```

Rotation angle of the recorded video. The value can be 0 (default), 90, 180, or 270 for MP4 videos.<br>This API
is supported since API version 6 and deprecated since API version 12. You are advised to use
**AVMetadata.videoOrientation** instead. If both parameters are set, **AVMetadata.videoOrientation** is used.

**类型：** number

**起始版本：** 9

**废弃版本：** 12

**替代接口：** videoOrientation

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## url

```TypeScript
url: string
```

Recording output URL: fd://xx (fd number).<br>This parameter is mandatory.<br>**Atomic service API**:
This API can be used in atomic services since API version 12.

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoSourceType

```TypeScript
videoSourceType?: VideoSourceType
```

Type of the video source to record. This parameter is mandatory for video recording.

**类型：** VideoSourceType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

