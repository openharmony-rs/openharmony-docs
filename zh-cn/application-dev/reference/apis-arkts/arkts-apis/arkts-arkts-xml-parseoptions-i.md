# ParseOptions

XML解析选项。

**起始版本：** 8

<!--Device-xml-interface ParseOptions--><!--Device-xml-interface ParseOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { xml } from '@kit.ArkTS';
```

## attributeValueCallbackFunction

```TypeScript
attributeValueCallbackFunction?: (name: string, value: string) => boolean
```

解析属性和属性值，默认值undefined，表示不解析。

**类型：** (name: string, value: string) => boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## attributeWithTagCallbackFunction

```TypeScript
attributeWithTagCallbackFunction?: AttributeWithTagCb
```

解析tagName标签，默认值undefined，表示不解析。

**类型：** AttributeWithTagCb

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb--><!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreNameSpace

```TypeScript
ignoreNameSpace?: boolean
```

是否忽略命名空间，忽略命名空间后，将不会对其进行解析。true表示忽略命名空间，false表示不忽略命名空间，默认值false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-ignoreNameSpace?: boolean--><!--Device-ParseOptions-ignoreNameSpace?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## supportDoctype

```TypeScript
supportDoctype?: boolean
```

是否解析文档类型，false表示不解析文档类型，true表示解析文档类型，默认值false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-supportDoctype?: boolean--><!--Device-ParseOptions-supportDoctype?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## tagValueCallbackFunction

```TypeScript
tagValueCallbackFunction?: (name: string, value: string) => boolean
```

解析开始标签、标签值和结束标签，默认值undefined，表示不解析。

**类型：** (name: string, value: string) => boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## tokenValueCallbackFunction

```TypeScript
tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean
```

解析元素事件类型([EventType](arkts-arkts-xml-eventtype-e.md))和[ParseInfo](arkts-arkts-xml-parseinfo-i.md)属性，默认值undefined，表示不解析。

**类型：** (eventType: EventType, value: ParseInfo) => boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean--><!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

