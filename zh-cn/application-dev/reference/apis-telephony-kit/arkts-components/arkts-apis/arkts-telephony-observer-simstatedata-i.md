# SimStateData

```TypeScript
export interface SimStateData
```

SIM卡类型和状态。

**起始版本：** 7

<!--Device-observer-export interface SimStateData--><!--Device-observer-export interface SimStateData-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## reason

```TypeScript
reason: LockReason
```

SIM卡锁类型。

**类型：** [LockReason](arkts-telephony-observer-lockreason-e.md)

**起始版本：** 8

<!--Device-SimStateData-reason: LockReason--><!--Device-SimStateData-reason: LockReason-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## state

```TypeScript
state: SimState
```

SIM卡状态。

**类型：** [SimState](arkts-telephony-observer-simstate-t.md)

**起始版本：** 7

<!--Device-SimStateData-state: SimState--><!--Device-SimStateData-state: SimState-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## type

```TypeScript
type: CardType
```

SIM卡类型。

**类型：** [CardType](arkts-telephony-observer-cardtype-t.md)

**起始版本：** 7

<!--Device-SimStateData-type: CardType--><!--Device-SimStateData-type: CardType-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry
