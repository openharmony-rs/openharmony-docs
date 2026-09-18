# NumberMarkInfo (System API)

Defines a number mark.

**Since:** 12

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

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markContent

```TypeScript
markContent?: string
```

Mark content. When **markType** is set to **MARK_TYPE_ENTERPRISE**, the returned information consists of the employee name and ID.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markCount

```TypeScript
markCount?: number
```

Mark count.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markDetails

```TypeScript
markDetails?: string
```

Mark details. When **markType** is set to **MARK_TYPE_ENTERPRISE**, the value of this parameter is the department position.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markSource

```TypeScript
markSource?: string
```

Mark source.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## markType

```TypeScript
markType: MarkType
```

Mark type.

**Type:** [MarkType](arkts-telephony-call-marktype-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
