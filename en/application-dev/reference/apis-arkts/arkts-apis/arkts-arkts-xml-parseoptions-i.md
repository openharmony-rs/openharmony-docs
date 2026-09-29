# ParseOptions

```TypeScript
interface ParseOptions
```

Parse options for XmlPullParser.

**Since:** 8

<!--Device-xml-interface ParseOptions--><!--Device-xml-interface ParseOptions-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { xml } from '@kit.ArkTS';
```

## attributeValueCallbackFunction

```TypeScript
attributeValueCallbackFunction?: (name: string, value: string) => boolean
```

Attribute value callback function.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes |  |
| value | string | Yes |  |

## attributeWithTagCallbackFunction

```TypeScript
attributeWithTagCallbackFunction?: AttributeWithTagCb
```

Attribute value and tag callback function.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb--><!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb-End-->

**System capability:** SystemCapability.Utils.Lang

## tagValueCallbackFunction

```TypeScript
tagValueCallbackFunction?: (name: string, value: string) => boolean
```

Tag value callback function.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes |  |
| value | string | Yes |  |

## tokenValueCallbackFunction

```TypeScript
tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean
```

Token value callback function.

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean--><!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventType | [EventType](arkts-arkts-xml-eventtype-e.md) | Yes |  |
| value | [ParseInfo](arkts-arkts-xml-parseinfo-i.md) | Yes |  |

## ignoreNameSpace

```TypeScript
ignoreNameSpace?: boolean
```

Whether to ignore parsing texts of the elements.

**Type:** boolean

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ParseOptions-ignoreNameSpace?: boolean--><!--Device-ParseOptions-ignoreNameSpace?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang

## supportDoctype

```TypeScript
supportDoctype?: boolean
```

Whether to parsing Doctype of the elements.

**Type:** boolean

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ParseOptions-supportDoctype?: boolean--><!--Device-ParseOptions-supportDoctype?: boolean-End-->

**System capability:** SystemCapability.Utils.Lang
