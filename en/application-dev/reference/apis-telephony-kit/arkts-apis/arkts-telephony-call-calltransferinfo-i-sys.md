# CallTransferInfo (System API)

```TypeScript
export interface CallTransferInfo
```

Defines the call transfer information.

**Since:** 8

<!--Device-call-export interface CallTransferInfo--><!--Device-call-export interface CallTransferInfo-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## endHour

```TypeScript
endHour?: number
```

Hour in the end time.

**Type:** number

**Since:** 9

<!--Device-CallTransferInfo-endHour?: int--><!--Device-CallTransferInfo-endHour?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## endMinute

```TypeScript
endMinute?: number
```

Minute in the end time.

**Type:** number

**Since:** 9

<!--Device-CallTransferInfo-endMinute?: int--><!--Device-CallTransferInfo-endMinute?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## settingType

```TypeScript
settingType: CallTransferSettingType
```

Enumerates call transfer setting types.

**Type:** [CallTransferSettingType](arkts-telephony-call-calltransfersettingtype-e-sys.md)

**Since:** 8

<!--Device-CallTransferInfo-settingType: CallTransferSettingType--><!--Device-CallTransferInfo-settingType: CallTransferSettingType-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## startHour

```TypeScript
startHour?: number
```

Hour in the start time.

**Type:** number

**Since:** 9

<!--Device-CallTransferInfo-startHour?: int--><!--Device-CallTransferInfo-startHour?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## startMinute

```TypeScript
startMinute?: number
```

Minute in the start time.

**Type:** number

**Since:** 9

<!--Device-CallTransferInfo-startMinute?: int--><!--Device-CallTransferInfo-startMinute?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## transferNum

```TypeScript
transferNum: string
```

Call transfer number.

**Type:** string

**Since:** 8

<!--Device-CallTransferInfo-transferNum: string--><!--Device-CallTransferInfo-transferNum: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## type

```TypeScript
type: CallTransferType
```

Call transfer type.

**Type:** [CallTransferType](arkts-telephony-call-calltransfertype-e.md)

**Since:** 8

<!--Device-CallTransferInfo-type: CallTransferType--><!--Device-CallTransferInfo-type: CallTransferType-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
