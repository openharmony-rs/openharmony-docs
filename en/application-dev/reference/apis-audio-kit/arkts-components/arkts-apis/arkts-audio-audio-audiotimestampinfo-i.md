# AudioTimestampInfo

Describes the information about the audio stream timestamp and the current data frame position.

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## framePos

```TypeScript
readonly framePos: number
```

Position of the current data frame for playback or recording.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Core

## timestamp

```TypeScript
readonly timestamp: number
```

Timestamp corresponding to the current data frame position during playback or recording, in nanoseconds.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Core
