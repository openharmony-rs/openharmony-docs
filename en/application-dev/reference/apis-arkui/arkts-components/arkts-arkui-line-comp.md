# Line

The **Line** component is used to draw a straight line. > **NOTE** > > This component supports dynamic constructor parameter updates using the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md) class since API version 20. > > **Child Components** > > None

## Line

```TypeScript
Line(options?: LineOptions)
```

Uses new to create the line. Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LineOptions](arkts-arkui-lineoptions-i.md) | No | Line options |

## Line

```TypeScript
Line(options?: LineOptions)
```

Defines the constructor of Line component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LineOptions](arkts-arkui-lineoptions-i.md) | No | Options of the line.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [LineOptions](arkts-arkui-lineoptions-i.md) | Describes the options of the line. |

## Examples

```TypeScript
### Example 1: Drawing a Line

This example draws the start point, end point, opacity, line color, line width, stroke gap, and drawing start point of the line through the startPoint, endPoint, strokeOpacity, stroke, strokeWidth, strokeDashArray, and strokeDashOffset attributes, respectively.


```

```TypeScript
### Example 2: Drawing Line Caps

This example draws the cap style of the line through the strokeLineCap attribute.


```

```TypeScript
### Example 3: Drawing Stroke Gaps

This example draws the stroke gaps through the strokeDashArray attribute.
```

```TypeScript
### Example 4: Drawing a Line with Different Parameter Types for Width and Height

This example demonstrates how to draw a line using different length types of the width and height attributes.


```

```TypeScript
### Example 5: Dynamically Setting Attributes of the Line Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the startPoint, endPoint, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeOpacity, strokeWidth, and antiAlias attributes of the Line component.
```
