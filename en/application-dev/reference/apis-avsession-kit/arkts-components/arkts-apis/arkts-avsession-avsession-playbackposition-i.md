# PlaybackPosition

```TypeScript
interface PlaybackPosition
```

Playback position definition

**Since:** 10

<!--Device-avSession-interface PlaybackPosition--><!--Device-avSession-interface PlaybackPosition-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## elapsedTime

```TypeScript
elapsedTime: number
```

Elapsed time(position) of this media set by the app, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackPosition-elapsedTime: long--><!--Device-PlaybackPosition-elapsedTime: long-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core

## updateTime

```TypeScript
updateTime: number
```

Record the system time when elapsedTime is set, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackPosition-updateTime: long--><!--Device-PlaybackPosition-updateTime: long-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core
