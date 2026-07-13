# ParseOptions

XML解析选项。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## attributeValueCallbackFunction

```TypeScript
attributeValueCallbackFunction?: (name: string, value: string) => boolean
```

解析属性和属性值，默认值undefined，表示不解析。

**类型：** (name: string, value: string) => boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## attributeWithTagCallbackFunction

```TypeScript
attributeWithTagCallbackFunction?: AttributeWithTagCb
```

解析tagName标签，默认值undefined，表示不解析。

**类型：** AttributeWithTagCb

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ignoreNameSpace

```TypeScript
ignoreNameSpace?: boolean
```

是否忽略命名空间，忽略命名空间后，将不会对其进行解析。true表示忽略命名空间，false表示不忽略命名空间，默认值false。

**类型：** boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## supportDoctype

```TypeScript
supportDoctype?: boolean
```

是否解析文档类型，false表示不解析文档类型，true表示解析文档类型，默认值false。

**类型：** boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## tagValueCallbackFunction

```TypeScript
tagValueCallbackFunction?: (name: string, value: string) => boolean
```

解析开始标签、标签值和结束标签，默认值undefined，表示不解析。

**类型：** (name: string, value: string) => boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## tokenValueCallbackFunction

```TypeScript
tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean
```

解析元素事件类型([EventType](arkts-arkts-eventtype-e.md))和[ParseInfo](arkts-arkts-parseinfo-i.md)属性，默认值undefined，表示不解析。

**类型：** (eventType: EventType, value: ParseInfo) => boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

