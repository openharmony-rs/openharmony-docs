# NumberMarkInfo (System API)

```TypeScript
export interface NumberMarkInfo
```

Defines a number mark.

**Since:** 12

<!--Device-call-export interface NumberMarkInfo--><!--Device-call-export interface NumberMarkInfo-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## isCloud

```TypeScript
isCloud?: boolean
```

Whether the number mark is from the cloud. The default value is **false**.

- **true**: yes  
- **false**: no

**Type:** boolean

**Since:** 12

<!--Device-NumberMarkInfo-isCloud?: boolean--><!--Device-NumberMarkInfo-isCloud?: boolean-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markContent

```TypeScript
markContent?: string
```

Mark content. When **markType** is set to **MARK_TYPE_ENTERPRISE**, the returned information consists of the employee name and ID.

**Type:** string

**Since:** 12

<!--Device-NumberMarkInfo-markContent?: string--><!--Device-NumberMarkInfo-markContent?: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markCount

```TypeScript
markCount?: number
```

Mark count.

**Type:** number

**Since:** 12

<!--Device-NumberMarkInfo-markCount?: int--><!--Device-NumberMarkInfo-markCount?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markDetails

```TypeScript
markDetails?: string
```

Mark details. When **markType** is set to **MARK_TYPE_ENTERPRISE**, the value of this parameter is the department position.

**Type:** string

**Since:** 14

<!--Device-NumberMarkInfo-markDetails?: string--><!--Device-NumberMarkInfo-markDetails?: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markSource

```TypeScript
markSource?: string
```

Mark source.

**Type:** string

**Since:** 12

<!--Device-NumberMarkInfo-markSource?: string--><!--Device-NumberMarkInfo-markSource?: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markType

```TypeScript
markType: MarkType
```

Mark type.

**Type:** [MarkType](arkts-telephony-call-marktype-e-sys.md)

**Since:** 12

<!--Device-NumberMarkInfo-markType: MarkType--><!--Device-NumberMarkInfo-markType: MarkType-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
