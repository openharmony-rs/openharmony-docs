# RectShapeOptions

RectShape 的构造函数参数。 继承自[ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)。

**继承/实现关系：** RectShapeOptions extends [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface RectShapeOptions--><!--Device-unnamed-export interface RectShapeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## radius

```TypeScript
radius?: double | string | Array<double | string>
```

矩形形状的圆角半径。 类型为number时取值范围是0, +∞)，string时是[Length。 单位：vp 取值为异常值时按照0vp处理。

**类型：** double \| string \| Array&lt;double \| string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectShapeOptions-radius?: double | string | Array<double | string>--><!--Device-RectShapeOptions-radius?: double | string | Array<double | string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

