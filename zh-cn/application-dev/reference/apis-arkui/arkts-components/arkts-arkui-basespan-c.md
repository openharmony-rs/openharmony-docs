# BaseSpan

定义BaseSpan基础类，包含Span的通用属性。

**继承/实现关系：** BaseSpan extends CommonMethod\<T>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## baselineOffset

```TypeScript
baselineOffset(value: LengthMetrics): T
```

设置Span基线的偏移量，适用于上下标排版、混合字号文本对齐微调等场景。此属性与父组件的baselineOffset是共存的。未通过该接口设置时，默认偏移量为0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | LengthMetrics | 是 | 设置Span基线的偏移量，设置该值为百分比时，按默认值显示。 正数内容向上偏移，负数向下偏移。 在ImageSpan中，设置为非0时，verticalAlign将固定为ImageSpanAlignment.BASELINE对 齐；设置为0时，要使基线对齐策略生效，需同时设置verticalAlign为ImageSpanAlignment.BASELINE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前Span的属性对象，用于链式调用。 |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle): T
```

设置文本背景样式。作为ContainerSpan的子组件时可继承该属性值，优先使用自身的设置。未通过该接口设置时，默认背景颜色为Color.Transparent（透明），圆角弧 度为0。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | 是 | 文本背景样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前Span的属性对象。 |
