# MmsRespInd (System API)

```TypeScript
export interface MmsRespInd
```

Defines an MMS response index.

**Since:** 8

<!--Device-sms-export interface MmsRespInd--><!--Device-sms-export interface MmsRespInd-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## reportAllowed

```TypeScript
reportAllowed?: ReportType
```

Report allowed.

**Type:** [ReportType](arkts-telephony-sms-reporttype-e-sys.md)

**Since:** 8

<!--Device-MmsRespInd-reportAllowed?: ReportType--><!--Device-MmsRespInd-reportAllowed?: ReportType-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## status

```TypeScript
status: number
```

Status.

**Type:** number

**Since:** 8

<!--Device-MmsRespInd-status: int--><!--Device-MmsRespInd-status: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## transactionId

```TypeScript
transactionId: string
```

Event ID.

**Type:** string

**Since:** 8

<!--Device-MmsRespInd-transactionId: string--><!--Device-MmsRespInd-transactionId: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## version

```TypeScript
version: MmsVersionType
```

Version.

**Type:** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**Since:** 8

<!--Device-MmsRespInd-version: MmsVersionType--><!--Device-MmsRespInd-version: MmsVersionType-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
