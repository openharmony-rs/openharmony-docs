# ParseOptions

XML解析选项，用于配置XmlPullParser的解析行为。开发者可通过supportDoctype和ignoreNameSpace控制解析范围，通过注册回调函数（tagValueCallbackFunction、 attributeValueCallbackFunction、tokenValueCallbackFunction等）接收不同类型的解析事件。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## attributeValueCallbackFunction

```TypeScript
attributeValueCallbackFunction?: (name: string, value: string) => boolean
```

解析属性和属性值，默认值undefined，表示不解析。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 |  |
| value | string | 是 |  |

## attributeWithTagCallbackFunction

```TypeScript
attributeWithTagCallbackFunction?: AttributeWithTagCb
```

解析tagName标签，默认值undefined，表示不解析。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## tagValueCallbackFunction

```TypeScript
tagValueCallbackFunction?: (name: string, value: string) => boolean
```

解析开始标签、标签值和结束标签，默认值undefined，表示不解析。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 |  |
| value | string | 是 |  |

## tokenValueCallbackFunction

```TypeScript
tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean
```

解析元素事件类型([EventType](arkts-arkts-xml-eventtype-e.md))和[ParseInfo](arkts-arkts-xml-parseinfo-i.md)属性，默认值undefined，表示不解析。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | EventType | 是 |  |
| value | [ParseInfo](arkts-arkts-xml-parseinfo-i.md) | 是 |  |

## ignoreNameSpace

```TypeScript
ignoreNameSpace?: boolean
```

是否忽略命名空间，忽略命名空间后，将不会对其进行解析。true表示忽略命名空间，false表示不忽略命名空间，默认值false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## supportDoctype

```TypeScript
supportDoctype?: boolean
```

是否解析文档类型，false表示不解析文档类型，true表示解析文档类型，默认值false。

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
