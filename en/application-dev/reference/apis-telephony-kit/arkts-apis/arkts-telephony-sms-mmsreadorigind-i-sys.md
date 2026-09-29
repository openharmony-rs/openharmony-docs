# MmsReadOrigInd (System API)

```TypeScript
export interface MmsReadOrigInd
```

Defines the original MMS message reading index.

**Since:** 8

<!--Device-sms-export interface MmsReadOrigInd--><!--Device-sms-export interface MmsReadOrigInd-End-->

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

<!--Device-MmsReadOrigInd-date: long--><!--Device-MmsReadOrigInd-date: long-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## from

```TypeScript
from: MmsAddress
```

Source address.

**Type:** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**Since:** 8

<!--Device-MmsReadOrigInd-from: MmsAddress--><!--Device-MmsReadOrigInd-from: MmsAddress-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageId

```TypeScript
messageId: string
```

Message ID.

**Type:** string

**Since:** 8

<!--Device-MmsReadOrigInd-messageId: string--><!--Device-MmsReadOrigInd-messageId: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## readStatus

```TypeScript
readStatus: number
```

Read status.

**Type:** number

**Since:** 8

<!--Device-MmsReadOrigInd-readStatus: int--><!--Device-MmsReadOrigInd-readStatus: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## to

```TypeScript
to: Array<MmsAddress>
```

Destination address.

**Type:** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**Since:** 8

<!--Device-MmsReadOrigInd-to: Array<MmsAddress>--><!--Device-MmsReadOrigInd-to: Array<MmsAddress>-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## version

```TypeScript
version: MmsVersionType
```

Version.

**Type:** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**Since:** 8

<!--Device-MmsReadOrigInd-version: MmsVersionType--><!--Device-MmsReadOrigInd-version: MmsVersionType-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
