# SimShortMessage (System API)

```TypeScript
export interface SimShortMessage
```

Defines a SIM message.

**Since:** 7

<!--Device-sms-export interface SimShortMessage--><!--Device-sms-export interface SimShortMessage-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## indexOnSim

```TypeScript
indexOnSim: number
```

SIM card index.

**Type:** number

**Since:** 7

<!--Device-SimShortMessage-indexOnSim: int--><!--Device-SimShortMessage-indexOnSim: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## shortMessage

```TypeScript
shortMessage: ShortMessage
```

SMS message.

**Type:** [ShortMessage](arkts-telephony-sms-shortmessage-i.md)

**Since:** 7

<!--Device-SimShortMessage-shortMessage: ShortMessage--><!--Device-SimShortMessage-shortMessage: ShortMessage-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## simMessageStatus

```TypeScript
simMessageStatus: SimMessageStatus
```

SIM message status.

**Type:** [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md)

**Since:** 7

<!--Device-SimShortMessage-simMessageStatus: SimMessageStatus--><!--Device-SimShortMessage-simMessageStatus: SimMessageStatus-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
