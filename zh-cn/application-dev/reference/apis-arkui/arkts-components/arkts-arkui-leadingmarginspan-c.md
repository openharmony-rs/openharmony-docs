# LeadingMarginSpan

文本段落的自定义缩进，仅提供基类，具体实现由开发者定义。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getLeadingMargin

```TypeScript
abstract getLeadingMargin(): LengthMetrics
```

返回文本段落的缩进距离。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LengthMetrics | 文本段落的缩进。不支持百分比。<br/>默认值：0<br/> |

## onDraw

```TypeScript
abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void
```

绘制自定义图案。段落中的每一行文本都会触发一次onDraw。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | DrawContext | 是 | 图形绘制上下文。<br/>DrawContext的canvas方法获取的是组件的画布，绘制时不会超出组件的范围。 |
| drawInfo | LeadingMarginSpanDrawInfo | 是 | 自定义绘制信息。 |

