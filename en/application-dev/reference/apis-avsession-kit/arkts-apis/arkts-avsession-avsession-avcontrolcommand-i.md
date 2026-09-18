# AVControlCommand

The definition of command to be sent to the session

@interface AVControlCommand [since 10 - 11]

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## command

```TypeScript
command: AVControlCommandType
```

The command value [AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)

**Type:** [AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## commandInfo

```TypeScript
commandInfo?: CommandInfo
```

The command value [CommandInfo](arkts-avsession-avsession-commandinfo-i.md)

**Type:** [CommandInfo](arkts-avsession-avsession-commandinfo-i.md)

**Since:** 22

**System capability:** SystemCapability.Multimedia.AVSession.Core

## parameter

```TypeScript
parameter?: LoopMode | string | number
```

parameter of the command. Whether this command requires parameters, see AVSessionCommand seek command requires a number parameter setSpeed command requires a number parameter setLoopMode command requires a [LoopMode](arkts-avsession-avsession-loopmode-e.md) parameter. toggleFavorite command requires assetId [assetId](arkts-avsession-avsession-avmetadata-i.md#assetid) parameter other commands need no parameter

**Type:** [LoopMode](arkts-avsession-avsession-loopmode-e.md) &#124; string &#124; number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
