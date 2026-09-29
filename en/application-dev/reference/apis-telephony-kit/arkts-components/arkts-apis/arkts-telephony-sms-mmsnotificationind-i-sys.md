# MmsNotificationInd (System API)

```TypeScript
export interface MmsNotificationInd
```

Defines an MMS notification index.

**Since:** 8

<!--Device-sms-export interface MmsNotificationInd--><!--Device-sms-export interface MmsNotificationInd-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## contentClass

```TypeScript
contentClass?: number
```

Content class.

**Type:** number

**Since:** 8

<!--Device-MmsNotificationInd-contentClass?: int--><!--Device-MmsNotificationInd-contentClass?: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## contentLocation

```TypeScript
contentLocation: string
```

Content location.

**Type:** string

**Since:** 8

<!--Device-MmsNotificationInd-contentLocation: string--><!--Device-MmsNotificationInd-contentLocation: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## deliveryReport

```TypeScript
deliveryReport?: number
```

Status report.

**Type:** number

**Since:** 8

<!--Device-MmsNotificationInd-deliveryReport?: int--><!--Device-MmsNotificationInd-deliveryReport?: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## expiry

```TypeScript
expiry: number
```

Expiration.

**Type:** number

**Since:** 8

<!--Device-MmsNotificationInd-expiry: int--><!--Device-MmsNotificationInd-expiry: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## from

```TypeScript
from?: MmsAddress
```

Source address.

**Type:** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**Since:** 8

<!--Device-MmsNotificationInd-from?: MmsAddress--><!--Device-MmsNotificationInd-from?: MmsAddress-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageClass

```TypeScript
messageClass: number
```

Message class.

**Type:** number

**Since:** 8

<!--Device-MmsNotificationInd-messageClass: int--><!--Device-MmsNotificationInd-messageClass: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageSize

```TypeScript
messageSize: number
```

Message size.

**Type:** number

**Since:** 8

<!--Device-MmsNotificationInd-messageSize: long--><!--Device-MmsNotificationInd-messageSize: long-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## subject

```TypeScript
subject?: string
```

Subject.

**Type:** string

**Since:** 8

<!--Device-MmsNotificationInd-subject?: string--><!--Device-MmsNotificationInd-subject?: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## transactionId

```TypeScript
transactionId: string
```

Transaction ID.

**Type:** string

**Since:** 8

<!--Device-MmsNotificationInd-transactionId: string--><!--Device-MmsNotificationInd-transactionId: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## version

```TypeScript
version: MmsVersionType
```

Version.

**Type:** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**Since:** 8

<!--Device-MmsNotificationInd-version: MmsVersionType--><!--Device-MmsNotificationInd-version: MmsVersionType-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
