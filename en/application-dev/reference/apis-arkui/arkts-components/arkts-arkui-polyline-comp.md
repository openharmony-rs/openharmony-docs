# Polyline

The **Polyline** component is used to draw a polyline. > **NOTE** > > This component supports dynamic constructor parameter updates using the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md) class since API version 20. > > **Child Components** > > None

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

Uses new to create Polyline. Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | No | Poly line options |

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

Defines the constructor of Polyline component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | No | Options of the polyline.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PolylineOptions](arkts-arkui-polylineoptions-i.md) | Describes the options of the polyline. |

## Examples

```TypeScript
### Example 1: Drawing a Polyline

This example draws the passing coordinates, opacity, stroke color, stroke width, join style, and endpoint style of the polyline through the points, fillOpacity, stroke, strokeWidth, strokeLineJoin, and strokeLineCap attributes, respectively.


```

```TypeScript
### Example 2: Drawing a Polyline with Different Parameter Types for Width and Height

This example demonstrates how to draw a polyline using different length types of the width and height attributes.


```

```TypeScript
### Example 3: Dynamically Setting Attributes of the Polyline Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the points, fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeLineJoin, strokeMiterLimit, strokeOpacity, strokeWidth, and antiAlias attributes of the Polyline component.
```
