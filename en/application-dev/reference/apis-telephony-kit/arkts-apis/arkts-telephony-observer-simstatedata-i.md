# SimStateData

```TypeScript
export interface SimStateData
```

Enumerates SIM card types and states.

**Since:** 7

<!--Device-observer-export interface SimStateData--><!--Device-observer-export interface SimStateData-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## reason

```TypeScript
reason: LockReason
```

SIM card lock type.

**Type:** [LockReason](arkts-telephony-observer-lockreason-e.md)

**Since:** 8

<!--Device-SimStateData-reason: LockReason--><!--Device-SimStateData-reason: LockReason-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## state

```TypeScript
state: SimState
```

SIM card state.

**Type:** [SimState](arkts-telephony-observer-simstate-t.md)

**Since:** 7

<!--Device-SimStateData-state: SimState--><!--Device-SimStateData-state: SimState-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## type

```TypeScript
type: CardType
```

SIM card type.

**Type:** [CardType](arkts-telephony-observer-cardtype-t.md)

**Since:** 7

<!--Device-SimStateData-type: CardType--><!--Device-SimStateData-type: CardType-End-->

**System capability:** SystemCapability.Telephony.StateRegistry
