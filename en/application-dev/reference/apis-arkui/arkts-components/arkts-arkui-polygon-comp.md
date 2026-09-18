# Polygon

The **Polygon** component is used to draw a polygon. > **NOTE** > > This component supports dynamic constructor parameter updates using the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md) class since API version 20. > > **Child Components** > > None

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Uses new to create Polygon. Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** 
- API version 9 and later: SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygonoptions-i.md) | No | Polygon options |

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Defines the constructor of Polygon component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygonoptions-i.md) | No | Options of the polygon.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PolygonOptions](arkts-arkui-polygonoptions-i.md) | Describes the options of the polygon. |

## Examples

```TypeScript
### Example 1: Drawing a Polygon

This example draws the vertex coordinates, fill color, fill opacity, border color, and border width of the polygon through the points, fill, fillOpacity, stroke, and strokeWidth attributes, respectively.


```

```TypeScript
### Example 2: Drawing a Polygon with Different Parameter Types for Width and Height

This example demonstrates how to draw a polygon using different length types of the width and height attributes.


```

```TypeScript
### Example 3: Dynamically Setting Attributes of the Polygon Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the points, fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeLineJoin, strokeMiterLimit, strokeOpacity, strokeWidth, and antiAlias attributes of the Polygon component.
```
