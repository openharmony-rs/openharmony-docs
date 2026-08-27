# CustomSpan

自定义绘制Span，仅提供基类，具体实现由开发者定义。适用于需要在文本流中嵌入自定义绘制内容的场景，例如在文本中绘制自定义图标、进度条、特殊装饰效果等。自定义绘制Span拖拽显示的缩略图为空白。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## invalidate

```TypeScript
invalidate(): void
```

主动刷新使用CustomSpan的Text组件。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDraw

```TypeScript
abstract onDraw(context: DrawContext,  drawInfo: CustomSpanDrawInfo): void
```

绘制自定义绘制Span。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | DrawContext | 是 | 图形绘制上下文。    **说明：** DrawContext的canvas方法获取的画布是Text组件的画布，绘制时不会超出Text组件的范围。 |
| drawInfo | [CustomSpanDrawInfo](arkts-arkui-customspandrawinfo-i.md) | 是 | 自定义绘制Span的绘制信息。 |

## onMeasure

```TypeScript
abstract onMeasure(measureInfo: CustomSpanMeasureInfo) : CustomSpanMetrics
```

获取自定义绘制Span的尺寸大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| measureInfo | [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md) | 是 | 自定义绘制Span的测量信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomSpanMetrics](arkts-arkui-customspanmetrics-i.md) | 自定义绘制Span的尺寸信息。 |
