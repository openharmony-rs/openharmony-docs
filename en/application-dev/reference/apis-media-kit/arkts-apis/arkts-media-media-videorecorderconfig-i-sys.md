# VideoRecorderConfig (System API)

```TypeScript
interface VideoRecorderConfig
```

Provides the video recorder configuration definitions.

**Since:** 9

<!--Device-media-interface VideoRecorderConfig--><!--Device-media-interface VideoRecorderConfig-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

audio source type, details see @AudioSourceType .

**Type:** [AudioSourceType](arkts-media-media-audiosourcetype-e.md)

**Since:** 9

<!--Device-VideoRecorderConfig-audioSourceType?: AudioSourceType--><!--Device-VideoRecorderConfig-audioSourceType?: AudioSourceType-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## location

```TypeScript
location?: Location
```

geographical location information.

**Type:** [Location](arkts-media-media-location-i.md)

**Since:** 9

<!--Device-VideoRecorderConfig-location?: Location--><!--Device-VideoRecorderConfig-location?: Location-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## profile

```TypeScript
profile: VideoRecorderProfile
```

video recorder profile, can get by "getVideoRecorderProfile", details see @VideoRecorderProfile .=

**Type:** [VideoRecorderProfile](arkts-media-media-videorecorderprofile-i-sys.md)

**Since:** 9

<!--Device-VideoRecorderConfig-profile: VideoRecorderProfile--><!--Device-VideoRecorderConfig-profile: VideoRecorderProfile-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## rotation

```TypeScript
rotation?: number
```

Sets the video rotation angle in output file, and for the file to playback, in degrees. mp4 support. the range of rotation angle should be {0, 90, 180, 270}, default is 0.

**Type:** number

**Since:** 9

<!--Device-VideoRecorderConfig-rotation?: int--><!--Device-VideoRecorderConfig-rotation?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## url

```TypeScript
url: string
```

video output uri.support two kind of uri now. format like: scheme + "://" + "context". fd: fd://fd

**Type:** string

**Since:** 9

<!--Device-VideoRecorderConfig-url: string--><!--Device-VideoRecorderConfig-url: string-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.

## videoSourceType

```TypeScript
videoSourceType: VideoSourceType
```

video source type, details see @VideoSourceType .

**Type:** [VideoSourceType](arkts-media-media-videosourcetype-e.md)

**Since:** 9

<!--Device-VideoRecorderConfig-videoSourceType: VideoSourceType--><!--Device-VideoRecorderConfig-videoSourceType: VideoSourceType-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoRecorder

**System API:** This is a system API.
