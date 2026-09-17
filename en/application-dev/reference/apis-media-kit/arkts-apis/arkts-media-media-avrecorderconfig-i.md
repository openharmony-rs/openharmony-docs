# AVRecorderConfig

Describes the audio and video recording parameters.

The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording, video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**. For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType** and **videoSourceType**.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

Type of the audio source to record. This parameter is mandatory for audio recording.<br>**Atomic service API**: This API can be used in atomic services since API version 12.

**Type:** [AudioSourceType](arkts-media-media-audiosourcetype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## fileGenerationMode

```TypeScript
fileGenerationMode?: FileGenerationMode
```

Mode for creating the file, which is used together with on('photoAssetAvailable').

**Type:** [FileGenerationMode](arkts-media-media-filegenerationmode-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## location

```TypeScript
location?: Location
```

Geographical location of the recorded video. By default, the geographical location information is not recorded. <br>This API is supported since API version 6 and deprecated since API version 12. You are advised to use **AVMetadata.location** instead. If both parameters are set, **AVMetadata.location** is used.

**Type:** [Location](arkts-media-media-location-i.md)

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [location](arkts-media-media-avmetadata-i.md#location)

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## maxDuration

```TypeScript
maxDuration?: number
```

Maximum recording duration, in seconds. The value range is [1, 2^31-1]. If an invalid value is provided, it is reset to the maximum allowed duration. Once the recording reaches the specified duration, it stops automatically and notifies via the **stateChange** callback that the recording has stopped: AVRecorderState = 'stopped', StateChangeReason = BACKGROUND.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## metadata

```TypeScript
metadata?: AVMetadata
```

Metadata. For details, see @AVMetadata.

**Type:** [AVMetadata](arkts-media-media-avmetadata-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## profile

```TypeScript
profile: AVRecorderProfile
```

Recording profile. This parameter is mandatory.<br>**Atomic service API**: This API can be used in atomic services since API version 12.

**Type:** [AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## rotation

```TypeScript
rotation?: number
```

Rotation angle of the recorded video, in degrees. The value can be 0 (default), 90, 180, or 270 for MP4 videos. <br>This API is supported since API version 6 and deprecated since API version 12. You are advised to use. **AVMetadata.videoOrientation** instead. If both parameters are set, **AVMetadata.videoOrientation** is used.

**Type:** number

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [videoOrientation](arkts-media-media-avmetadata-i.md#videoorientation)

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## url

```TypeScript
url: string
```

Recording output URL: fd://xx (fd number).<br>This parameter is mandatory.<br>**Atomic service API**: This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## videoSourceType

```TypeScript
videoSourceType?: VideoSourceType
```

Type of the video source to record. This parameter is mandatory for video recording.

**Type:** [VideoSourceType](arkts-media-media-videosourcetype-e.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder
