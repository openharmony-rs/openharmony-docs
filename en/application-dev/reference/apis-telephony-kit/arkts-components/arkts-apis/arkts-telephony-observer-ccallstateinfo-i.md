# CCallStateInfo

```TypeScript
export interface CCallStateInfo
```

Defines information about the call status.

**Since:** 23

<!--Device-observer-export interface CCallStateInfo--><!--Device-observer-export interface CCallStateInfo-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## state

```TypeScript
state: CCallState
```

Call type.

**Type:** [CCallState](arkts-telephony-observer-ccallstate-t.md)

**Since:** 23

<!--Device-CCallStateInfo-state: CCallState--><!--Device-CCallStateInfo-state: CCallState-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## teleNumber

```TypeScript
teleNumber: string
```

Phone number.

**Type:** string

**Since:** 23

<!--Device-CCallStateInfo-teleNumber: string--><!--Device-CCallStateInfo-teleNumber: string-End-->

**System capability:** SystemCapability.Telephony.StateRegistry
