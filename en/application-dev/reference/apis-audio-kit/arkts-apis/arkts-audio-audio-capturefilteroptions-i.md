# CaptureFilterOptions

```TypeScript
interface CaptureFilterOptions
```

Defines the options for filtering the played audio streams to be recorded.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** OH_AVScreenCapture in native interface.

<!--Device-audio-interface CaptureFilterOptions--><!--Device-audio-interface CaptureFilterOptions-End-->

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## usages

```TypeScript
usages: Array<StreamUsage>
```

Filter by stream usages. But not allow to capture voice streams.

**Type:** Array&lt;[StreamUsage](arkts-audio-audio-streamusage-e.md)&gt;

**Since:** 10

**Deprecated since:** 12

**Substitutes:** OH_AVScreenCapture in native interface.

**Required permissions:** 
- API version 11 and later: N/A
- API version 10: ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO

<!--Device-CaptureFilterOptions-usages: Array<StreamUsage>--><!--Device-CaptureFilterOptions-usages: Array<StreamUsage>-End-->

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture
