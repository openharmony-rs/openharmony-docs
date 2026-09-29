# LeadingMarginSpan

```TypeScript
declare abstract class LeadingMarginSpan
```

Defines the custom indentation of a text paragraph, which provides only a base class, with the specific implementation defined by developers. It is suitable for scenarios that require drawing custom markers, icons, and other content at the beginning of the first line or each line of a paragraph, such as custom symbols before list items and decoration patterns at the beginning of a paragraph.

**Since:** 22

<!--Device-unnamed-declare abstract class LeadingMarginSpan--><!--Device-unnamed-declare abstract class LeadingMarginSpan-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLeadingMargin

```TypeScript
abstract getLeadingMargin(): LengthMetrics
```

Returns the indentation distance for a text paragraph.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-LeadingMarginSpan-abstract getLeadingMargin(): LengthMetrics--><!--Device-LeadingMarginSpan-abstract getLeadingMargin(): LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Indentation of the text paragraph. Percentage is not supported.<br>Default value: **0** <br> |

## onDraw

```TypeScript
abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void
```

Draws a custom pattern. This API is triggered once for each line of text in a paragraph.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-LeadingMarginSpan-abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void--><!--Device-LeadingMarginSpan-abstract onDraw(context: DrawContext, drawInfo: LeadingMarginSpanDrawInfo): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | DrawContext | Yes | Graphics drawing context.<br>The canvas method of **DrawContext** obtains the canvas of the component, and drawing does not exceed the component bounds. |
| drawInfo | [LeadingMarginSpanDrawInfo](arkts-arkui-leadingmarginspandrawinfo-i.md) | Yes | Custom drawing information. |
