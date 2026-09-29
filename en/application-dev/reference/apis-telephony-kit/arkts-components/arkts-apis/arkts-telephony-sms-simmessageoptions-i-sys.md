# SimMessageOptions (System API)

```TypeScript
export interface SimMessageOptions
```

Defines the SIM message options.

**Since:** 7

<!--Device-sms-export interface SimMessageOptions--><!--Device-sms-export interface SimMessageOptions-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## pdu

```TypeScript
pdu: string
```

Protocol data unit.

**Type:** string

**Since:** 7

<!--Device-SimMessageOptions-pdu: string--><!--Device-SimMessageOptions-pdu: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## slotId

```TypeScript
slotId: number
```

Card slot ID.

**Type:** number

**Since:** 7

<!--Device-SimMessageOptions-slotId: int--><!--Device-SimMessageOptions-slotId: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## smsc

```TypeScript
smsc: string
```

Short message service center.

**Type:** string

**Since:** 7

<!--Device-SimMessageOptions-smsc: string--><!--Device-SimMessageOptions-smsc: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## status

```TypeScript
status: SimMessageStatus
```

Status.

**Type:** [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md)

**Since:** 7

<!--Device-SimMessageOptions-status: SimMessageStatus--><!--Device-SimMessageOptions-status: SimMessageStatus-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
