# CallStateInfo

```TypeScript
export interface CallStateInfo
```

Defines information about the call status.

**Since:** 11

<!--Device-observer-export interface CallStateInfo--><!--Device-observer-export interface CallStateInfo-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## number

```TypeScript
number: string
```

Phone number.

**Type:** string

**Since:** 11

<!--Device-CallStateInfo-number: string--><!--Device-CallStateInfo-number: string-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## state

```TypeScript
state: CallState
```

Call type.

**Type:** [CallState](arkts-telephony-observer-callstate-t.md)

**Since:** 11

<!--Device-CallStateInfo-state: CallState--><!--Device-CallStateInfo-state: CallState-End-->

**System capability:** SystemCapability.Telephony.StateRegistry
