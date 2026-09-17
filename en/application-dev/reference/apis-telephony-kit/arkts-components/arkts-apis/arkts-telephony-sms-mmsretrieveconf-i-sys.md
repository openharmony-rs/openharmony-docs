# MmsRetrieveConf (System API)

Defines the MMS message retrieval configuration.

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## cc

```TypeScript
cc?: Array<MmsAddress>
```

Carbon copy.

**Type:** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## contentType

```TypeScript
contentType: string
```

Content type.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## date

```TypeScript
date: number
```

Date.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## deliveryReport

```TypeScript
deliveryReport?: number
```

Status report.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## from

```TypeScript
from?: MmsAddress
```

Source address.

**Type:** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageId

```TypeScript
messageId: string
```

Message ID.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## priority

```TypeScript
priority?: MmsPriorityType
```

Priority.

**Type:** [MmsPriorityType](arkts-telephony-sms-mmsprioritytype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## readReport

```TypeScript
readReport?: number
```

Read report.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## retrieveStatus

```TypeScript
retrieveStatus?: number
```

Retrieval status.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## retrieveText

```TypeScript
retrieveText?: string
```

Retrieval text.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## subject

```TypeScript
subject?: string
```

Subject.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## to

```TypeScript
to: Array<MmsAddress>
```

Destination address.

**Type:** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## transactionId

```TypeScript
transactionId: string
```

Transaction ID.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## version

```TypeScript
version: MmsVersionType
```

Version.

**Type:** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
