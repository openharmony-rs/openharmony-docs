# Polygon

The **Polygon** component is used to draw a polygon. This component defines the shape of a polygon by setting a list of vertex coordinates, and supports attribute configuration such as fill color and border style. The component uses a two-dimensional coordinate system and connects the vertices in sequence to form a closed polygon area. It is suitable for drawing custom polygon shapes such as triangles, quadrilaterals, and pentagons, as well as for implementing visualization scenarios such as charts and icons that require polygon elements.

> **NOTE** > > Since API version 20, this component supports updating constructor parameters through the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../arkts-apis/arkts-arkui-attributeupdater-c.md) class.

## Child Components

None

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Draws a polygon.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** 
- API version 9 and later: SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygon-comp-polygonoptions-i.md) | No | Configuration options of the **Polygon** component, used to define the width and height of the drawing area. Pass this parameter when the polygon size needs to be specified. If it is not passed, the default width and height (both 0) are used. If **undefined** or **null** is passed, the parameter setting does not take effect and the component attributes remain unchanged. |

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Draws a polygon.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygon-comp-polygonoptions-i.md) | No | Configuration options of the **Polygon** component, used to define the width and height of the drawing area. Pass this parameter when the polygon size needs to be specified. If it is not passed, the default width and height (both 0) are used. If **undefined** or **null** is passed, the parameter setting does not take effect and the component attribute remains unchanged. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PolygonOptions](arkts-arkui-polygon-comp-polygonoptions-i.md) | Describes the options of the polygon. |

## Examples

### Example 1: Drawing a Polygon

This example draws the vertex coordinates, fill color, fill opacity, border color, and border width of the polygon through the points, fill, fillOpacity, stroke, and strokeWidth attributes, respectively.



```TypeScript
// xxx.ets
@Entry
@Component
struct PolygonExample {
  build() {
    Column({ space: 10 }) {
      // Draw a triangle in a 100 × 100 rectangle. The start point is (0, 0), the end point is (100, 0), and the passing point is (50, 100).
      Polygon({ width: 100, height: 100 })
        .points([[0, 0], [50, 100], [100, 0]])
        .fill(Color.Green)
      // Draw a quadrilateral in a 100 × 100 rectangle. The start point is (0, 0), the end point is (100, 0), and the passing points are (0, 100) and (100, 100).
      Polygon()
        .width(100)
        .height(100)
        .points([[0, 0], [0, 100], [100, 100], [100, 0]])
        .fillOpacity(0)
        .strokeWidth(5)
        .stroke(Color.Blue)
      // Draw a pentagon in a 100 × 100 rectangle. The start point is (50, 0), the end point is (100, 50), and the passing points are (0, 50), (20, 100), and (80, 100).
      Polygon()
        .width(100)
        .height(100)
        .points([[50, 0], [0, 50], [20, 100], [80, 100], [100, 50]])
        .fill(Color.Red)
        .fillOpacity(0.6)
    }.width('100%').margin({ top: 10 })
  }
}
```

### Example 2: Drawing a Polygon with Different Parameter Types for Width and Height

This example demonstrates how to draw a polygon using different length types of the width and height attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct PolygonTypeExample {
  build() {
    Column({ space: 10 }) {
      // Draw a triangle in a 100 × 100 rectangle. The start point is (0, 0), the end point is (100, 0), and the passing point is (50, 100).
      Polygon({ width: '100', height: '100' }) // Use the string type.
        .points([[0, 0], [50, 100], [100, 0]])
      // Draw a quadrilateral in a 100 × 100 rectangle. The start point is (0, 0), the end point is (100, 0), and the passing points are (0, 100) and (100, 100).
      Polygon({ width: 100, height: 100 })// Use the number type.
        .points([[0, 0], [0, 100], [100, 100], [100, 0]])
        .fillOpacity(0)
        .strokeWidth(5)
        .stroke(Color.Blue)
      // Draw a pentagon in a 100 × 100 rectangle. The start point is (50, 0), the end point is (100, 50), and the passing points are (0, 50), (20, 100), and (80, 100).
      Polygon({ width: $r('app.string.PolygonWidth'), height: $r('app.string.PolygonHeight') }) // Use the Resource type, which needs to be customized.
        .points([[50, 0], [0, 50], [20, 100], [80, 100], [100, 50]])
        .fillOpacity(0.6)
    }.width('100%').margin({ top: 10 })
  }
}
```

### Example 3: Dynamically Setting Attributes of the Polygon Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the points, fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeLineJoin, strokeMiterLimit, strokeOpacity, strokeWidth, and antiAlias attributes of the Polygon component.

```TypeScript
// xxx.ets
class MyPolygonModifier implements AttributeModifier<PolygonAttribute> {
  applyNormalAttribute(instance: PolygonAttribute): void {
    // Triangle starting at (0, 0), passing through (50, 100), and ending at (100, 0). Fill color: #707070; fill opacity: 0.5; stroke color: #2787D9; stroke dash array: [20]; offset to left: 15; cap style: semi-circle; join style: miter; miter limit: 5; stroke opacity: 0.5; stroke width: 10; anti-aliasing enabled.
    instance.points([[0, 0], [50, 100], [100, 0]])
    instance.fill("#707070")
    instance.fillOpacity(0.5)
    instance.stroke("#2787D9")
    instance.strokeDashArray([20])
    instance.strokeDashOffset("15")
    instance.strokeLineCap(LineCapStyle.Round)
    instance.strokeLineJoin(LineJoinStyle.Miter)
    instance.strokeMiterLimit(5)
    instance.strokeOpacity(0.5)
    instance.strokeWidth(10)
    instance.antiAlias(true)
  }
}

@Entry
@Component
struct PolygonModifierDemo {
  @State modifier: MyPolygonModifier = new MyPolygonModifier()

  build() {
    Column() {
      Polygon()
        .width(100)
        .height(100)
        .attributeModifier(this.modifier)
        .offset({ x: 20, y: 20 })
    }
  }
}
```
