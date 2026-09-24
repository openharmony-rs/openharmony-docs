# CustomSpan

```TypeScript
declare abstract class CustomSpan
```

Describes the custom span. Only the base class is provided. You need to define the specific implementation.

The drag preview of a custom span is blank.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## invalidate

```TypeScript
invalidate(): void
```

Manually triggers a refresh of the **Text** component that uses this **CustomSpan**.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDraw

```TypeScript
abstract onDraw(context: DrawContext,  drawInfo: CustomSpanDrawInfo): void
```

Called to draw a custom span.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | DrawContext | Yes | Drawing context.<br>**NOTE:** <br>The **canvas** method of **DrawContext** obtains the canvas of the **Text** component. As such, the custom span does not extend beyond the area of the **Text** component. |
| drawInfo | [CustomSpanDrawInfo](arkts-arkui-customspandrawinfo-i.md) | Yes | Drawing information of the custom span. |

## onMeasure

```TypeScript
abstract onMeasure(measureInfo: CustomSpanMeasureInfo) : CustomSpanMetrics
```

Called to obtain the size of a custom span.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| measureInfo | [CustomSpanMeasureInfo](arkts-arkui-customspanmeasureinfo-i.md) | Yes | Font size of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| [CustomSpanMetrics](arkts-arkui-customspanmetrics-i.md) | Size of the custom span.<br>**NOTE:** <br>The final height of the custom span is subject to the line height of the **Text** component. If no value is specified for **height**, the custom span takes the **fontSize** value of the **Text** component as its height. If the value specified is greater than the height of other child components on the same line, the custom span takes the line height of the **Text** component as its height. |
