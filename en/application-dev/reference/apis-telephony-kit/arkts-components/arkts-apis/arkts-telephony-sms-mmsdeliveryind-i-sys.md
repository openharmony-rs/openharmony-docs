# MmsDeliveryInd (System API)

```TypeScript
export interface MmsDeliveryInd
```

Defines an MMS message delivery index.

**Since:** 8

<!--Device-sms-export interface MmsDeliveryInd--><!--Device-sms-export interface MmsDeliveryInd-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## date

```TypeScript
date: number
```

Date.

**Type:** number

**Since:** 8

<!--Device-MmsDeliveryInd-date: long--><!--Device-MmsDeliveryInd-date: long-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageId

```TypeScript
messageId: string
```

Message ID.

**Type:** string

**Since:** 8

<!--Device-MmsDeliveryInd-messageId: string--><!--Device-MmsDeliveryInd-messageId: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## status

```TypeScript
status: number
```

Status.

**Type:** number

**Since:** 8

<!--Device-MmsDeliveryInd-status: int--><!--Device-MmsDeliveryInd-status: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## to

```TypeScript
to: Array<MmsAddress>
```

Destination address.

**Type:** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**Since:** 8

<!--Device-MmsDeliveryInd-to: Array<MmsAddress>--><!--Device-MmsDeliveryInd-to: Array<MmsAddress>-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## version

```TypeScript
version: MmsVersionType
```

Version.

**Type:** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**Since:** 8

<!--Device-MmsDeliveryInd-version: MmsVersionType--><!--Device-MmsDeliveryInd-version: MmsVersionType-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
