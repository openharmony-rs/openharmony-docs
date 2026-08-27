# CircleShape

用于clipShape和maskShape接口的圆形形状。继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。

**继承/实现关系：** CircleShape extends BaseShape<CircleShape>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ShapeSize)
```

创建CircleShape对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md) | 否 | 形状的大小，包含width（宽度）和height（高度）属性，用于设置形状的尺寸。不传入时使用默认尺寸，默认宽度0vp，默认高度0vp。 |
