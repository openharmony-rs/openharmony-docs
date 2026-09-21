# Line

The **Line** component is used to draw a straight line in the app UI. It supports customizing the start point, end point, color, width, opacity, dash style, and cap style of the line. It is suitable for drawing separators, decorative lines, coordinate axes or connecting lines in charts, and custom graphic borders.

> **NOTE** > > Since API version 20, this component supports updating constructor parameters through the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../arkts-apis/arkts-arkui-attributeupdater-c.md) class. > > - The **Line** component cannot form a closed area, so the **fill** and **fillOpacity** attributes do not take > effect. > > - The **Line** component does not support corners, so the **strokeLineJoin** and **strokeMiterLimit** attributes do > not take effect.

## Child Components

None

## Line

```TypeScript
Line(options?: LineOptions)
```

Draws a straight line. The **Line** component draws the line within the rectangular area defined by **width** and **height**. The upper left corner of the drawing area is the coordinate origin (0,0), with the x-axis extending to the right and the y-axis extending downward.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LineOptions](arkts-arkui-line-comp-lineoptions-i.md) | No | Drawing area of the **Line** component, which contains the **width** and **height** attributes used to set the width and height of the **Line** component. If this parameter is not passed, the **width** and **height** attributes of the **Line** component are processed according to the default logic of their respective attributes (see the **LineOptions** object description).<br>The abnormal values **undefined** and **null** are processed as invalid values, and this setting does not take effect. |

## Line

```TypeScript
Line(options?: LineOptions)
```

Draws a straight line. The **Line** component draws the line within the rectangular area defined by **width** and **height**. The upper left corner of the drawing area is the coordinate origin (0,0), with the x-axis extending to the right and the y-axis extending downward.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LineOptions](arkts-arkui-line-comp-lineoptions-i.md) | No | Drawing area of the **Line** component, which contains the **width** and **height** attributes used to set the width and height of the **Line** component. If this parameter is not passed, the **width** and **height** attributes of the Line component are processed based on their respective default logic (see **LineOptions** object description).<br>The abnormal values **undefined** and **null** are processed as invalid values, and this setting does not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [LineOptions](arkts-arkui-line-comp-lineoptions-i.md) | Describes the options of the line. |

## Examples

### Example 1: Drawing a Line

This example draws the start point, end point, opacity, line color, line width, stroke gap, and drawing start point of the line through the startPoint, endPoint, strokeOpacity, stroke, strokeWidth, strokeDashArray, and strokeDashOffset attributes, respectively.



```TypeScript
// xxx.ets
@Entry
@Component
struct LineExample {
  build() {
    Column({ space: 10 }) {
      // The coordinates of the start and end points of the line are determined relative to the coordinates of the drawing area of the <Line> component.
      Line()
        .width(200)
        .height(150)
        .startPoint([0, 0])
        .endPoint([50, 100])
        .stroke(Color.Black)
        .backgroundColor('#F5F5F5')
      // Set the start point to (50, 50), the end point to (150, 150), the line width to 5, the line color to orange, and the line opacity to 0.5.
      Line()
        .width(200)
        .height(150)
        .startPoint([50, 50])
        .endPoint([150, 150])
        .strokeWidth(5)
        .stroke(Color.Orange)
        .strokeOpacity(0.5)
        .backgroundColor('#F5F5F5')
      // strokeDashOffset is used to define the offset when the associated strokeDashArray array is rendered.
      Line()
        .width(200)
        .height(150)
        .startPoint([0, 0])
        .endPoint([100, 100])
        .stroke(Color.Black)
        .strokeWidth(3)
        .strokeDashArray([10, 3])
        .strokeDashOffset(5)
        .backgroundColor('#F5F5F5')
      // When the coordinate values exceed the width and height range of the Line component, the line is drawn outside the component drawing area. Set the dashed line mode: dash length 10, gap length 3.
      Line()
        .width(50)
        .height(50)
        .startPoint([0, 0])
        .endPoint([100, 100])
        .stroke(Color.Black)
        .strokeWidth(3)
        .strokeDashArray([10, 3])
        .backgroundColor('#F5F5F5')
    }
  }
}
```

### Example 2: Drawing Line Caps

This example draws the cap style of the line through the strokeLineCap attribute.



```TypeScript
// xxx.ets
@Entry
@Component
struct LineExample1 {
  build() {
    Row({ space: 10 }) {
      // Set LineCapStyle to Butt.
      Line()
        .width(100)
        .height(200)
        .startPoint([50, 50])
        .endPoint([50, 200])
        .stroke(Color.Black)
        .strokeWidth(20)
        .strokeLineCap(LineCapStyle.Butt)
        .backgroundColor('#F5F5F5')
        .margin(10)
      // Set LineCapStyle to Round.
      Line()
        .width(100)
        .height(200)
        .startPoint([50, 50])
        .endPoint([50, 200])
        .stroke(Color.Black)
        .strokeWidth(20)
        .strokeLineCap(LineCapStyle.Round)
        .backgroundColor('#F5F5F5')
      // Set LineCapStyle to Square.
      Line()
        .width(100)
        .height(200)
        .startPoint([50, 50])
        .endPoint([50, 200])
        .stroke(Color.Black)
        .strokeWidth(20)
        .strokeLineCap(LineCapStyle.Square)
        .backgroundColor('#F5F5F5')
    }
  }
}
```

### Example 3: Drawing Stroke Gaps

This example draws the stroke gaps through the strokeDashArray attribute.

```TypeScript
// xxx.ets
@Entry
@Component
struct LineExample {
  build() {
    Column() {
      Line()
        .width(300)
        .height(30)
        .startPoint([50, 30])
        .endPoint([300, 30])
        .stroke(Color.Black)
        .strokeWidth(10)
      // Set the interval for strokeDashArray to 50.
      Line()
        .width(300)
        .height(30)
        .startPoint([50, 20])
        .endPoint([300, 20])
        .stroke(Color.Black)
        .strokeWidth(10)
        .strokeDashArray([50])
      // Set the interval for strokeDashArray to 50, 10.
      Line()
        .width(300)
        .height(30)
        .startPoint([50, 20])
        .endPoint([300, 20])
        .stroke(Color.Black)
        .strokeWidth(10)
        .strokeDashArray([50, 10])
      // Set the interval for strokeDashArray to 50, 10, 20.
      Line()
        .width(300)
        .height(30)
        .startPoint([50, 20])
        .endPoint([300, 20])
        .stroke(Color.Black)
        .strokeWidth(10)
        .strokeDashArray([50, 10, 20])
      // Set the interval for strokeDashArray to 50, 10, 20, 30.
      Line()
        .width(300)
        .height(30)
        .startPoint([50, 20])
        .endPoint([300, 20])
        .stroke(Color.Black)
        .strokeWidth(10)
        .strokeDashArray([50, 10, 20, 30])
    }
  }
}
```

### Example 4: Drawing a Line with Different Parameter Types for Width and Height

This example demonstrates how to draw a line using different length types of the width and height attributes.



```TypeScript
// xxx.ets
@Entry
@Component
struct LineTypeExample {
  build() {
    Column({ space: 10 }) {
      // Draw a line with a width of 10 in a 200 × 200 area, with the start point at (0,0) and the end point at (150,150).
      Line({ width: '200', height: '200' })// Use the string type.
        .startPoint([0, 0])
        .endPoint([150, 150])
        .stroke(Color.Black)
        .strokeWidth(10)
        .backgroundColor('#F5F5F5')
        .margin(10)
      // Draw a line with a width of 10 in a 200 × 200 area, with the start point at (0,50) and the end point at (150,150).
      Line({ width: 200, height: 200 })// Use the number type.
        .startPoint([0, 50])
        .endPoint([150, 150])
        .stroke(Color.Black)
        .strokeWidth(10)
        .backgroundColor('#F5F5F5')
        .margin(10)
      // Draw a line with a width of 10 in a 200 × 200 area, with the start point at (0,100) and the end point at (150,150).
      Line({ width: $r('app.string.LineWidth'), height: $r('app.string.LineHeight') })// Use the Resource type, which needs to be customized.
        .startPoint([0, 100])
        .endPoint([150, 150])
        .stroke(Color.Black)
        .strokeWidth(10)
        .backgroundColor('#F5F5F5')
        .margin(10)
    }.width('100%')
  }
}
```

### Example 5: Dynamically Setting Attributes of the Line Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the startPoint, endPoint, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeOpacity, strokeWidth, and antiAlias attributes of the Line component.

```TypeScript
// xxx.ets
class MyLineModifier implements AttributeModifier<LineAttribute> {
  applyNormalAttribute(instance: LineAttribute): void {
    // A line from the start point (10, 10) to the end point (120, 10), with line color #2787D9, stroke gap [20], dash offset 15, round line cap style, line opacity 0.5, line width 10, and anti-aliasing enabled.
    instance.startPoint([10, 10])
    instance.endPoint([120, 10])
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
struct LineModifierDemo {
  @State modifier: MyLineModifier = new MyLineModifier()

  build() {
    Column() {
      Line()
        .attributeModifier(this.modifier)
        .offset({ x: 20, y: 20 })
    }
  }
}
```
