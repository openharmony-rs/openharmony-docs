# AVRecorderConfig

Describes the audio and video recording parameters.

The **audioSourceType** and **videoSourceType** parameters are used to distinguish audio-only recording, video-only recording, and audio and video recording. For audio-only recording, set only **audioSourceType**. For video-only recording, set only **videoSourceType**. For audio and video recording, set both **audioSourceType** and **videoSourceType**.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## metaSourceTypes

```TypeScript
metaSourceTypes?: Array<MetaSourceType>
```

Meta source types, details see @MetaSourceType .

**Type:** Array&lt;[MetaSourceType](arkts-media-media-metasourcetype-e-sys.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**System API:** This is a system API.
