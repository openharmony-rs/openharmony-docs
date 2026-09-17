# AVCallState

Used to indicate the call state of the current call.

@interface AVCallState [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## muted

```TypeScript
muted: boolean
```

Current muted status.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## state

```TypeScript
state: CallState
```

Current call state. See [CallState](arkts-avsession-avsession-callstate-e.md)

**Type:** [CallState](arkts-avsession-avsession-callstate-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
