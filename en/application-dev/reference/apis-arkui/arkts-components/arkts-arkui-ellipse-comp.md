# Ellipse

The **Ellipse** component is used to draw an ellipse. It draws an ellipse shape by setting the width and height attributes, rendering the ellipse outline and fill area within a given rectangular region.

## Child Components

None

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

Constructor used to draw an ellipse. After being called, it creates an **Ellipse** object, for which the width and height attributes can be set.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipse-comp-ellipseoptions-i.md) | No | Ellipse drawing configuration options, including the width and height settings. If not passed, the default size (both width and height are 0) is used.<br>The abnormal values **undefined** and **null** are handled as invalid values, and this setting does not take effect. <br>**Note:** Since API version 18, the **EllipseOptions** parameter must be used in the stage model. |

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

Constructor used to draw an ellipse. After being called, it creates an **Ellipse** object, for which the width and height attributes can be set.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipse-comp-ellipseoptions-i.md) | No | Ellipse drawing configuration options, including the width and height settings. If not passed, the default size (both width and height are 0) is used.<br>The abnormal values **undefined** and **null** are handled as invalid values, and the setting does not take effect. <br>**Note:** Since API version 18, the EllipseOptions parameter must be used in the stage model. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EllipseOptions](arkts-arkui-ellipse-comp-ellipseoptions-i.md) | Describes the options of the ellipse. |

## Examples

### Example 1: Drawing an Ellipse

This example demonstrates how to use fillOpacity and stroke to set the opacity and stroke color of an ellipse.



```TypeScript
// xxx.ets
@Entry
@Component
struct EllipseExample {
  build() {
    Column({ space: 10 }) {
      // Draw a 150 x 80 ellipse.
      Ellipse({ width: 150, height: 80 })
      // Draw a 150 x 100 ellipse with blue strokes.
      Ellipse()
        .width(150)
        .height(100)
        .fillOpacity(0)
        .stroke(Color.Blue)
        .strokeWidth(3)
    }.width('100%')
  }
}
```

### Example 2: Drawing an Ellipse with Different Parameter Types for Width and Height

This example demonstrates how to draw an ellipse using different length types of the width and height attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct EllipseTypeExample {
  build() {
    Column({ space: 10 }) {
      // Draw a 150 x 80 ellipse.
      Ellipse({ width: '150', height: '80' }) // Use the string type.
      // Draw an ellipse of 80 × 150.
      Ellipse({ width: 80, height: 150 }) // Use the number type.
      // Use the Resource type to reference the ellipse with width and height resource strings.
      Ellipse({ width: $r('app.string.EllipseWidth'), height: $r('app.string.EllipseHeight') }) // Use the Resource type, which needs to be customized.
    }.width('100%')
  }
}
```

### Example 3: Dynamically Setting Attributes of the Ellipse Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeOpacity, strokeWidth, and antiAlias attributes of the Ellipse component.

```TypeScript
// xxx.ets
class MyEllipseModifier implements AttributeModifier<EllipseAttribute> {
  applyNormalAttribute(instance: EllipseAttribute): void {
    // Fill color: #707070; fill opacity: 0.5; stroke color: #2787D9; stroke dash array: [20]; offset to left: 15; cap style: semi-circle; stroke opacity: 0.5; stroke width: 10; anti-aliasing enabled.
    instance.fill('#707070')
    instance.fillOpacity(0.5)
    instance.stroke('#2787D9')
    instance.strokeDashArray([20])
    instance.strokeDashOffset('15')
    instance.strokeLineCap(LineCapStyle.Round)
    instance.strokeOpacity(0.5)
    instance.strokeWidth(10)
    instance.antiAlias(true)
  }
}

@Entry
@Component
struct EllipseModifierDemo {
  @State modifier: MyEllipseModifier = new MyEllipseModifier()

  build() {
    Column() {
      Ellipse({ width: 150, height: 80 })
        .attributeModifier(this.modifier)
        .offset({ x: 20, y: 20 })
    }
  }
}
```
