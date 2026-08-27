# @ohos.arkui.shape(形状)

[clipShape](../arkts-components/arkts-arkui-commonmethod-c.md#clipshape)和
 [maskShape](../arkts-components/arkts-arkui-commonmethod-c.md#maskshape)接口中传入对应的形状，实现对组件的
 裁剪和遮罩效果。适用于需要将组件裁剪为圆形、椭圆、矩形等特定形状，或通过形状遮罩实现视觉效果的场景，如头像裁剪、图标遮罩等。


## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BaseShape(形状)](arkts-arkui-arkui-shape-baseshape-c.md) | 继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。 |
| [CircleShape(形状)](arkts-arkui-arkui-shape-circleshape-c.md) | 用于clipShape和maskShape接口的圆形形状。继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。 |
| [CommonShapeMethod(形状)](arkts-arkui-arkui-shape-commonshapemethod-c.md) | 提供形状的偏移、填充和位置设置等通用方法的基类。 |
| [EllipseShape(形状)](arkts-arkui-arkui-shape-ellipseshape-c.md) | 用于clipShape和maskShape接口的椭圆形状。继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。 |
| [PathShape(形状)](arkts-arkui-arkui-shape-pathshape-c.md) | 用于clipShape和maskShape接口的路径形状。继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。 |
| [RectShape(形状)](arkts-arkui-arkui-shape-rectshape-c.md) | 用于clipShape和maskShape接口的矩形形状。继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PathShapeOptions(形状)](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | PathShape的构造函数参数。 |
| [RectShapeOptions(形状)](arkts-arkui-arkui-shape-rectshapeoptions-i.md) | RectShape 的构造函数参数。继承自[ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)。 |
| [RoundRectShapeOptions(形状)](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | RectShape 带有圆角半径的构造函数参数。继承自[ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)。 |
| [ShapeSize(形状)](arkts-arkui-arkui-shape-shapesize-i.md) | 形状的大小参数。 |
