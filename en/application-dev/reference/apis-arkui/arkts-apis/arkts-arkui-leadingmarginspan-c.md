# LeadingMarginSpan

```TypeScript
declare abstract class LeadingMarginSpan
```

Defines custom indentation for text paragraphs. Only a base class is provided; the specific implementation is left to developers.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLeadingMargin

```TypeScript
abstract getLeadingMargin(): LengthMetrics
```

Returns the indentation distance for a text paragraph.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Paragraph indentation distance. The value cannot be in percentage.<br>Default value: **0**. <br> |

## onDraw

```TypeScript
abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void
```

Draws a custom pattern. This API is triggered once for each line of text in a paragraph.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | DrawContext | Yes | Drawing context.<br>The **canvas** method of **DrawContext** obtains the canvas of the component. As such, the custom span does not extend beyond the area of the component. |
| drawInfo | [LeadingMarginSpanDrawInfo](arkts-arkui-leadingmarginspandrawinfo-i.md) | Yes | Custom drawing information. |
