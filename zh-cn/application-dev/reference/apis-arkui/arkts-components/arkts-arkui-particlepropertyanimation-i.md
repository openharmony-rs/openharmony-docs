# ParticlePropertyAnimation

设置粒子属性生命周期。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

设置动画曲线。

默认值：Curve.Linear

**类型：** Curve | ICurve

**默认值：** Curve.Linear

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMillis

```TypeScript
endMillis: number
```

动画结束时间。

单位：毫秒。

取值范围：[0, +∞)。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: T
```

属性起始值。非法输入取对应属性的默认值。

**类型：** T

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMillis

```TypeScript
startMillis: number
```

动画开始时间。

单位：毫秒。

取值范围：[0, +∞)。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: T
```

属性目标值。非法输入取对应属性的默认值。

**类型：** T

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

