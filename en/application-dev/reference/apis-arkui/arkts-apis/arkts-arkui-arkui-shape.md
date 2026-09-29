# @ohos.arkui.shape(Shape)

The **Shape** module provides multiple shape definitions such as **CircleShape**, **EllipseShape**, **PathShape**,
 and **RectShape**, which can be passed to the
 [clipShape](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#clipshape) and
 [maskShape](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#maskshape) APIs to clip and
 mask components. It is suitable for scenarios where components need to be clipped into specific shapes such as
 circles, ellipses, and rectangles, or where visual effects are achieved through shape masking, such as avatar
 clipping and icon masking.



## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md) | This API inherits from [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md). |
| [CircleShape](arkts-arkui-arkui-shape-circleshape-c.md) | Represents a circle shape used in the **clipShape** and **maskShape** APIs. |
| [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md) | A base class that provides common methods such as offset, fill, and position settings for shapes. |
| [EllipseShape](arkts-arkui-arkui-shape-ellipseshape-c.md) | Represents an ellipse shape used in the **clipShape** and **maskShape** APIs. |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | Represents a path shape used for the **clipShape** and **maskShape** APIs. It inherits from [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md). |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | Represents a rectangle shape used in the **clipShape** and **maskShape** APIs. |

### Interfaces

| Name | Description |
| --- | --- |
| [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | Represents the parameter of the constructor used to create a **PathShape** object. |
| [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) | Represents the parameter of the constructor used to create a **RectShape** object. |
| [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | Represents the parameters of the constructor used to create a **RectShape** object with rounded corners. |
| [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md) | Provides the size parameters of a shape. |

## Examples

This example demonstrates how to use [clipShape](../arkui-ts/ts-universal-attributes-sharp-clipping.md#clipshape12) and [maskShape](../arkui-ts/ts-universal-attributes-sharp-clipping.md#maskshape12) to clip and mask images into different shapes.

```TypeScript
import { CircleShape, EllipseShape, PathShape, RectShape } from '@kit.ArkUI';

@Entry
@Component
struct ShapeExample {
  build() {
    Column({ space: 15 }) {
      Text('CircleShape, position').fontSize(20).width('75%').fontColor('#DCDCDC')
      // Replace $r('app.media.startIcon') with the resource file you use.
      Image($r('app.media.startIcon'))
        .clipShape(new CircleShape({ width: '280px', height: '280px' }).position({ x: '20px', y: '20px' }))
        .width('500px').height('280px')

      Text('EllipseShape, offset').fontSize(20).width('75%').fontColor('#DCDCDC')
      // Replace $r('app.media.startIcon') with the resource file you use.
      Image($r('app.media.startIcon'))
        .clipShape(new EllipseShape({ width: '350px', height: '280px' }).offset({ x: '10px', y: '10px' }))
        .width('500px').height('280px')

      Text('PathShape, fill').fontSize(20).width('75%').fontColor('#DCDCDC')
      // Replace $r('app.media.startIcon') with the resource file you use.
      Image($r('app.media.startIcon'))
        // Use SVG path commands to draw a triangle as the mask shape.
        .maskShape(new PathShape().commands('M100 0 L200 240 L0 240 Z').fill(Color.Red))
        .width('500px').height('280px')
    
      Text('RectShape, width, height, fill').fontSize(20).width('75%').fontColor('#DCDCDC')
      // Replace $r('app.media.startIcon') with the resource file you use.
      Image($r('app.media.startIcon'))
        .maskShape(new RectShape().width('350px').height('280px').fill(Color.Red))
        .width('500px').height('280px')
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```
