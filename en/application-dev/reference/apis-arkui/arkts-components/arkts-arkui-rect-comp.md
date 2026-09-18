# Rect

The **Rect** component is used to draw a rectangle. > **NOTE** > > This component supports dynamic constructor parameter updates using the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md) class since API version 20. > > **Child Components** > > None

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

Use new function to create Rect. Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) &#124; [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | No | Rect options |

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

Defines the constructor of Rect component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) &#124; [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | No | Options of the rectangle.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RectOptions](arkts-arkui-rectoptions-i.md) | Describes the options of the rectangle. |
| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | Describes the options of the rounded rectangle. |

## Examples

```TypeScript
### Example 1: Drawing a Rectangle

This example demonstrates how to use fill, fillOpacity, stroke, and radius to draw rectangles with specific fill colors, opacity, stroke colors, and rounded corners.


```

```TypeScript
### Example 2: Drawing a Gradient Rectangle

This example uses the universal attributes [linearGradient](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-gradient-color.md#lineargradient18) and [clipShape](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clipshape18) to draw a rectangle with a gradient color.

The universal attributes linearGradient and clipShape are supported since API version 18.


```

```TypeScript
### Example 3: Drawing a Rectangle with Different Parameter Types

This example demonstrates how to draw a rectangle using different parameter types for the width, height, radius, radiusWidth, and radiusHeight attributes.


```

```TypeScript
### Example 4: Dynamically Setting Attributes of the Rect Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeLineJoin, strokeMiterLimit, strokeOpacity, strokeWidth, and antiAlias attributes of the Rect component.
```
