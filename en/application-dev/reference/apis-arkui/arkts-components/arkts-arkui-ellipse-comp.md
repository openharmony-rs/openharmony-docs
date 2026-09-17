# Ellipse

The **Ellipse** component is used to draw an ellipse. > **Child Components** > > None

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

use new function to set the value. Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipseoptions-i.md) | No | ellipse options |

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

Set the value.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipseoptions-i.md) | No | Options of the ellipse.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EllipseOptions](arkts-arkui-ellipseoptions-i.md) | Describes the options of the ellipse. |

## Examples

```TypeScript
### Example 1: Drawing an Ellipse

This example demonstrates how to use fillOpacity and stroke to set the opacity and stroke color of an ellipse.


```

```TypeScript
### Example 2: Drawing an Ellipse with Different Parameter Types for Width and Height

This example demonstrates how to draw an ellipse using different length types of the width and height attributes.


```

```TypeScript
### Example 3: Dynamically Setting Attributes of the Ellipse Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeOpacity, strokeWidth, and antiAlias attributes of the Ellipse component.
```
