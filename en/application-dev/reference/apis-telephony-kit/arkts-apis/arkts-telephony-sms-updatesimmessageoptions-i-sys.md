# UpdateSimMessageOptions (System API)

```TypeScript
export interface UpdateSimMessageOptions
```

Defines the updating SIM message options.

**Since:** 7

<!--Device-sms-export interface UpdateSimMessageOptions--><!--Device-sms-export interface UpdateSimMessageOptions-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## msgIndex

```TypeScript
msgIndex: number
```

Message index.

**Type:** number

**Since:** 7

<!--Device-UpdateSimMessageOptions-msgIndex: int--><!--Device-UpdateSimMessageOptions-msgIndex: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## newStatus

```TypeScript
newStatus: SimMessageStatus
```

New status.

**Type:** [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md)

**Since:** 7

<!--Device-UpdateSimMessageOptions-newStatus: SimMessageStatus--><!--Device-UpdateSimMessageOptions-newStatus: SimMessageStatus-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## pdu

```TypeScript
pdu: string
```

Protocol data unit.

**Type:** string

**Since:** 7

<!--Device-UpdateSimMessageOptions-pdu: string--><!--Device-UpdateSimMessageOptions-pdu: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## slotId

```TypeScript
slotId: number
```

Card slot ID.

**Type:** number

**Since:** 7

<!--Device-UpdateSimMessageOptions-slotId: int--><!--Device-UpdateSimMessageOptions-slotId: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## smsc

```TypeScript
smsc: string
```

Short message service center.

**Type:** string

**Since:** 7

<!--Device-UpdateSimMessageOptions-smsc: string--><!--Device-UpdateSimMessageOptions-smsc: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
