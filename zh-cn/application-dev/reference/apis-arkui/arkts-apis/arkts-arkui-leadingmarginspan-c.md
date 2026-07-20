# LeadingMarginSpan

文本段落的自定义缩进，仅提供基类，具体实现由开发者定义。

**起始版本：** 22

<!--Device-unnamed-declare abstract class LeadingMarginSpan--><!--Device-unnamed-declare abstract class LeadingMarginSpan-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getleadingmargin"></a>
## getLeadingMargin

```TypeScript
abstract getLeadingMargin(): LengthMetrics
```

返回文本段落的缩进距离。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LeadingMarginSpan-abstract getLeadingMargin(): LengthMetrics--><!--Device-LeadingMarginSpan-abstract getLeadingMargin(): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 文本段落的缩进。不支持百分比。<br/>默认值：0<br/> |

<a id="ondraw"></a>
## onDraw

```TypeScript
abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void
```

绘制自定义图案。段落中的每一行文本都会触发一次onDraw。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LeadingMarginSpan-abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void--><!--Device-LeadingMarginSpan-abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | 是 | 图形绘制上下文。<br/>DrawContext的canvas方法获取的是组件的画布，绘制时不会超出组件的范围。 |
| drawInfo | [LeadingMarginSpanDrawInfo](arkts-arkui-leadingmarginspandrawinfo-i.md) | 是 | 自定义绘制信息。 |

