# BuilderSpanInfo

```TypeScript
declare interface BuilderSpanInfo
```

定义**RichEditor**中BuilderSpan的身份与位置信息。

> **说明：** 
> 
> 当**RichEditor**组件使用[RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md)构造时，不支持此接口。

**起始版本：** 26.2.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

开发者自定义的追踪标识，用于跟踪BuilderSpan。框架不强制唯一性约束，由开发者自行保证唯一性。未传入时，值为**undefined**。

**类型：** string

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

BuilderSpan在文本内容中的当前偏移位置。该值由框架维护，随文本内容变化动态更新。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
