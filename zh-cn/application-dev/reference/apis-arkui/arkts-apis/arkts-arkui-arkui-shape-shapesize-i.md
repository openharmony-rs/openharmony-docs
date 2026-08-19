# ShapeSize

形状的尺寸参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ShapeSize--><!--Device-unnamed-export interface ShapeSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height?: double | string
```

形状的高度。 类型为number时取值范围是0, +∞)，string时是[Length。 单位：vp 取值为异常值时按照0vp处理。

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeSize-height?: double | string--><!--Device-ShapeSize-height?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: double | string
```

形状的宽度。 类型为number时取值范围是0, +∞)，string时是[Length。 单位：vp 取值为异常值时按照0vp处理。

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeSize-width?: double | string--><!--Device-ShapeSize-width?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

