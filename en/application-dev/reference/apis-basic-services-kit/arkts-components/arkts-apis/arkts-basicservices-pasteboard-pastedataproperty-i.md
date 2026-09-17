# PasteDataProperty

Defines the properties of PasteData in the pasteboard, including the timestamp, data types, pasteable range, and additional data. The defined properties can be applied to the pasteboard only with the [setProperty](arkts-basicservices-pasteboard-pastedata-i.md#setproperty) method.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Pasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## additions

```TypeScript
additions: Record<string, object>
```

Additional property data. It does not allow for dynamic adding of properties. Properties can be added only by re- assigning values. This parameter is left empty by default. For details, see the example of **setProperty**.

**Type:** Record&lt;string, object&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## localOnly

```TypeScript
localOnly: boolean
```

Whether the pasteboard content is for local access only. The default value is **false**. The value will be overwritten by the value of the **shareOption** attribute. You are advised to use the [ShareOption](arkts-basicservices-pasteboard-shareoption-e.md) attribute instead.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## mimeTypes

```TypeScript
readonly mimeTypes: Array<string>
```

Data types of all records in PasteData.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## shareOption

```TypeScript
shareOption: ShareOption
```

Pasteable ranges of PasteData. The default value is **CROSSDEVICE**.

**Type:** [ShareOption](arkts-basicservices-pasteboard-shareoption-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## tag

```TypeScript
tag: string
```

Custom tag. This parameter is left empty by default.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard

## timestamp

```TypeScript
readonly timestamp: number
```

Timestamp when data is written to the pasteboard (unit: nanoseconds since the device is powered on).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.MiscServices.Pasteboard
