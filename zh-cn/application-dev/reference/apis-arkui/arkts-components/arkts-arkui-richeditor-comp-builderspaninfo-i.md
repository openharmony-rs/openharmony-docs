# BuilderSpanInfo

```TypeScript
declare interface BuilderSpanInfo
```

定义**RichEditor**中BuilderSpan的身份与位置信息。

> **说明：** 
> 
> 当**RichEditor**组件使用[RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md)构造时，不支持此接口。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface BuilderSpanInfo--><!--Device-unnamed-declare interface BuilderSpanInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

开发者自定义的身份标识，用于标识BuilderSpan。框架不强制唯一性约束，由开发者自行保证唯一性。未传入时，值为**undefined**，表示该BuilderSpan为匿名BuilderSpan。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-BuilderSpanInfo-id?: string--><!--Device-BuilderSpanInfo-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

当作为[addRichEditorBuilderSpan](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#addricheditorbuilderspan)的参数传入时，表示BuilderSpan的插入位置。省略或当值小于0或大于所有内容长度时，添加到所有内容最后面。当通过[getRichEditorBuilderSpans](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#getricheditorbuilderspans)或回调获取时，表示BuilderSpan在文本内容中的当前偏移位置，该值由框架维护，随文本内容变化动态更新。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-BuilderSpanInfo-offset?: number--><!--Device-BuilderSpanInfo-offset?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
