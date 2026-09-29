# @ohos.arkui.shape(形状)

[clipShape](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#clipshape)和
 [maskShape](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#maskshape)接口中传入对应的形状，实现对组件的
 裁剪和遮罩效果。适用于需要将组件裁剪为圆形、椭圆、矩形等特定形状，或通过形状遮罩实现视觉效果的场景，如头像裁剪、图标遮罩等。



## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md) | 继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。 |
| [CircleShape](arkts-arkui-arkui-shape-circleshape-c.md) | 用于clipShape和maskShape接口的圆形形状。 |
| [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md) | 提供形状的偏移、填充和位置设置等通用方法的基类。 |
| [EllipseShape](arkts-arkui-arkui-shape-ellipseshape-c.md) | 用于clipShape和maskShape接口的椭圆形状。 |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | 用于clipShape和maskShape接口的路径形状，继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。 |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | 用于clipShape和maskShape接口的矩形形状。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | PathShape的构造函数参数。 |
| [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) | RectShape 的构造函数参数。 |
| [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | RectShape 带有圆角半径的构造函数参数。 |
| [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md) | 形状的大小参数。 |

## 示例

该示例主要演示通过[clipShape](../arkui-ts/ts-universal-attributes-sharp-clipping.md#clipshape12)和[maskShape](../arkui-ts/ts-universal-attributes-sharp-clipping.md#maskshape12)将图片裁剪和遮罩成不同形状。

```TypeScript
import { CircleShape, EllipseShape, PathShape, RectShape } from '@kit.ArkUI';

@Entry
@Component
struct ShapeExample {
  build() {
    Column({ space: 15 }) {
      Text('CircleShape, position').fontSize(20).width('75%').fontColor('#DCDCDC')
      // $r('app.media.startIcon')需替换为开发者所需的资源文件
      Image($r('app.media.startIcon'))
        .clipShape(new CircleShape({ width: '280px', height: '280px' }).position({ x: '20px', y: '20px' }))
        .width('500px').height('280px')

      Text('EllipseShape, offset').fontSize(20).width('75%').fontColor('#DCDCDC')
      // $r('app.media.startIcon')需替换为开发者所需的资源文件
      Image($r('app.media.startIcon'))
        .clipShape(new EllipseShape({ width: '350px', height: '280px' }).offset({ x: '10px', y: '10px' }))
        .width('500px').height('280px')

      Text('PathShape, fill').fontSize(20).width('75%').fontColor('#DCDCDC')
      // $r('app.media.startIcon')需替换为开发者所需的资源文件
      Image($r('app.media.startIcon'))
        // 使用SVG路径指令绘制三角形作为遮罩形状
        .maskShape(new PathShape().commands('M100 0 L200 240 L0 240 Z').fill(Color.Red))
        .width('500px').height('280px')
    
      Text('RectShape, width, height, fill').fontSize(20).width('75%').fontColor('#DCDCDC')
      // $r('app.media.startIcon')需替换为开发者所需的资源文件
      Image($r('app.media.startIcon'))
        .maskShape(new RectShape().width('350px').height('280px').fill(Color.Red))
        .width('500px').height('280px')
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```
