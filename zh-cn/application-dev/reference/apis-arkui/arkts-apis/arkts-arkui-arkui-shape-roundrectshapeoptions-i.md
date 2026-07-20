# RoundRectShapeOptions

RectShape 带有半径的构造函数参数。

继承自[ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)。

**继承/实现关系：** RoundRectShapeOptions extends [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)

**起始版本：** 12

<!--Device-unnamed-interface RoundRectShapeOptions extends ShapeSize--><!--Device-unnamed-interface RoundRectShapeOptions extends ShapeSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## radiusHeight

```TypeScript
radiusHeight?: number | string
```

矩形形状圆角半径的高度。

类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。

单位：vp

取值为异常值时按照0vp处理。

**类型：** number \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-RoundRectShapeOptions-radiusHeight?: number | string--><!--Device-RoundRectShapeOptions-radiusHeight?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radiusWidth

```TypeScript
radiusWidth?: number | string
```

矩形形状圆角半径的宽度。

类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。

单位：vp

取值为异常值时按照0vp处理。

**类型：** number \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-RoundRectShapeOptions-radiusWidth?: number | string--><!--Device-RoundRectShapeOptions-radiusWidth?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

