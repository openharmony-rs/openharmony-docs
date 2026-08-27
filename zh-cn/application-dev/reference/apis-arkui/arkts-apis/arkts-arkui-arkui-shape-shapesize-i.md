# ShapeSize

形状的大小参数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height?: number | string
```

形状的高度。类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。单位：vp默认值：0vp取值为异常值时按照0vp处理。不设置时默认值为0vp。

**类型：** number \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number | string
```

形状的宽度。类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。单位：vp默认值：0vp取值为异常值时按照0vp处理。不设置时默认值为0vp。

**类型：** number \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
