# BaseSpan

定义BaseSpan基础类，包含Span的通用属性。

**继承/实现关系：** BaseSpan extends [CommonMethod<T>](CommonMethod<T>)

**起始版本：** 11

<!--Device-unnamed-declare class BaseSpan<T> extends CommonMethod<T>--><!--Device-unnamed-declare class BaseSpan<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="baselineoffset"></a>
## baselineOffset

```TypeScript
baselineOffset(value: LengthMetrics): T
```

设置Span基线的偏移量。此属性与父组件的baselineOffset是共存的。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSpan-baselineOffset(value: LengthMetrics): T--><!--Device-BaseSpan-baselineOffset(value: LengthMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 设置Span基线的偏移量，设置该值为百分比时，按默认值显示。<br/>正数内容向上偏移，负数向下偏移。<br/>默认值：0<br/>在ImageSpan中，设置为非0时，[verticalAlign](ImageSpanAttribute#verticalAlign)将固定为ImageSpanAlignment.BASELINE对齐；设置为0时，要使基线对齐策略生效，需同时设置[verticalAlign](ImageSpanAttribute#verticalAlign)为ImageSpanAlignment.BASELINE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前Span的属性。 |

<a id="textbackgroundstyle"></a>
## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle): T
```

设置背景样式。作为[ContainerSpan](arkts-arkui-containerspan.md)的子组件时可以继承它的此属性值，优先使用其自身的此属性。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseSpan-textBackgroundStyle(style: TextBackgroundStyle): T--><!--Device-BaseSpan-textBackgroundStyle(style: TextBackgroundStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | 是 | 背景样式。<br />默认值:<br />{<br /> color: Color.Transparent,<br /> radius: 0<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前Span的属性。 |

