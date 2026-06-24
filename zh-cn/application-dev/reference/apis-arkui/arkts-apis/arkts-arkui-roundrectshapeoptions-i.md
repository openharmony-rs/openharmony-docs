# RoundRectShapeOptions

RectShape 带有半径的构造函数参数。

继承自[ShapeSize](arkts-arkui-shapesize-i.md#ShapeSize)。

**继承/实现关系：** RoundRectShapeOptions extends [ShapeSize](arkts-arkui-shapesize-i.md#ShapeSize)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radiusHeight

```TypeScript
radiusHeight?: number | string
```

矩形形状圆角半径的高度。

类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-units-length-t.md#Length)。

单位：vp

取值为异常值时按照0vp处理。

**类型：** number | string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radiusWidth

```TypeScript
radiusWidth?: number | string
```

矩形形状圆角半径的宽度。

类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-units-length-t.md#Length)。

单位：vp

取值为异常值时按照0vp处理。

**类型：** number | string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

