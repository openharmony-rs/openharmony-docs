# ParseOptions

XML解析选项，用于配置XmlPullParser的解析行为。开发者可通过supportDoctype和ignoreNameSpace控制解析范围，通过注册回调函数（tagValueCallbackFunction、 attributeValueCallbackFunction、tokenValueCallbackFunction等）接收不同类型的解析事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-xml-interface ParseOptions--><!--Device-xml-interface ParseOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## attributeValueCallbackFunction

```TypeScript
attributeValueCallbackFunction?: (name: string, value: string) => boolean
```

解析属性和属性值，默认值undefined，表示不解析。

**类型：** (name: string, value: string) =&gt; boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-attributeValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## attributeWithTagCallbackFunction

```TypeScript
attributeWithTagCallbackFunction?: AttributeWithTagCb
```

解析tagName标签，默认值undefined，表示不解析。

**类型：** [AttributeWithTagCb](arkts-arkts-xml-attributewithtagcb-t.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb--><!--Device-ParseOptions-attributeWithTagCallbackFunction?: AttributeWithTagCb-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreNameSpace

```TypeScript
ignoreNameSpace?: boolean
```

是否忽略命名空间，忽略命名空间后，将不会对其进行解析。true表示忽略命名空间，false表示不忽略命名空间，默认值false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-ignoreNameSpace?: boolean--><!--Device-ParseOptions-ignoreNameSpace?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## supportDoctype

```TypeScript
supportDoctype?: boolean
```

是否解析文档类型，false表示不解析文档类型，true表示解析文档类型，默认值false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-supportDoctype?: boolean--><!--Device-ParseOptions-supportDoctype?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## tagValueCallbackFunction

```TypeScript
tagValueCallbackFunction?: (name: string, value: string) => boolean
```

解析开始标签、标签值和结束标签，默认值undefined，表示不解析。

**类型：** (name: string, value: string) =&gt; boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean--><!--Device-ParseOptions-tagValueCallbackFunction?: (name: string, value: string) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## tokenValueCallbackFunction

```TypeScript
tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean
```

解析元素事件类型([EventType](arkts-arkts-xml-eventtype-e.md#EventType))和[ParseInfo](arkts-arkts-xml-parseinfo-i.md#ParseInfo)属性，默认值undefined，表示不解析。

**类型：** (eventType: EventType, value: ParseInfo) =&gt; boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean--><!--Device-ParseOptions-tokenValueCallbackFunction?: (eventType: EventType, value: ParseInfo) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

