# AVCastControlCommand

The definition of cast command to be sent to the session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## command

```TypeScript
command: AVCastControlCommandType
```

The command value [AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)

**Type:** [AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## parameter

```TypeScript
parameter?: media.PlaybackSpeed | number | string | LoopMode
```

Parameter carried in the command. The seek command must carry the number parameter. The setVolume command must carry the number parameter. The toggleFavorite command must carry the [assetId](arkts-avsession-avsession-avmediadescription-i.md#assetid) parameter. The setSpeed command must carry the PlaybackSpeed parameter. The setLoopMode command must carry the [LoopMode](arkts-avsession-avsession-loopmode-e.md) parameter. Other commands do not need to carry parameters.

**Type:** [media.PlaybackSpeed](../../apis-media-kit/arkts-apis/arkts-media-media-playbackspeed-e.md) &#124; number &#124; string &#124; [LoopMode](arkts-avsession-avsession-loopmode-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast
