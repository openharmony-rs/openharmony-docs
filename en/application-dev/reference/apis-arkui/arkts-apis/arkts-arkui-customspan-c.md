# CustomSpan

```TypeScript
declare abstract class CustomSpan
```

Defines a custom drawing span that provides only a base class, with the specific implementation defined by developers. It is suitable for scenarios that require embedding custom drawing content in the text flow, such as drawing custom icons, progress bars, and special decoration effects in text.

The drag preview of a custom span is blank.

**Since:** 12

<!--Device-unnamed-declare abstract class CustomSpan--><!--Device-unnamed-declare abstract class CustomSpan-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## invalidate

```TypeScript
invalidate(): void
```

Manually triggers a refresh of the **Text** component that uses this **CustomSpan**.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-CustomSpan-invalidate(): void--><!--Device-CustomSpan-invalidate(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDraw

```TypeScript
abstract onDraw(context: DrawContext,  drawInfo: CustomSpanDrawInfo): void
```

Called to draw a custom span.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomSpan-abstract onDraw(context: DrawContext,  drawInfo: CustomSpanDrawInfo): void--><!--Device-CustomSpan-abstract onDraw(context: DrawContext,  drawInfo: CustomSpanDrawInfo): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | DrawContext | Yes | Graphics drawing context.<br>**NOTE:** <br>The canvas obtained through the canvas method of **DrawContext** is the canvas of the **Text** component, and the drawing will not exceed the range of the **Text** component. |
| drawInfo | [CustomSpanDrawInfo](arkts-arkui-customspandrawinfo-i.md) | Yes | Drawing information of the custom span. |

## onMeasure

```TypeScript
abstract onMeasure(measureInfo: CustomSpanMeasureInfo) : CustomSpanMetrics
```

Called to obtain the size of a custom span.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomSpan-abstract onMeasure(measureInfo: CustomSpanMeasureInfo) : CustomSpanMetrics--><!--Device-CustomSpan-abstract onMeasure(measureInfo: CustomSpanMeasureInfo) : CustomSpanMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| measureInfo | [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md) | Yes | Measurement information of the custom-drawn span. |

**Return value:**

| Type | Description |
| --- | --- |
| [CustomSpanMetrics](arkts-arkui-customspanmetrics-i.md) | Size information of the custom drawing span.<br>**Note:** <br>The final height of **CustomSpan** is determined by the line height of the current **Text** component. If **height** is not set, the **fontSize** value of the **Text** component is used as the height of **CustomSpan** by default. If **height** is greater than the height of other child components in the current line, **height** is used as the line height of the **Text** component. |
