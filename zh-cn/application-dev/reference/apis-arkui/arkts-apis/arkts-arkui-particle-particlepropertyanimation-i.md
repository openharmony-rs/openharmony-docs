# ParticlePropertyAnimation

设置粒子属性生命周期。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ParticlePropertyAnimation--><!--Device-unnamed-export interface ParticlePropertyAnimation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

设置动画曲线。 默认值：Curve.Linear

**类型：** [Curve](arkts-arkui-curve-e.md) \| [ICurve](../arkts-components/arkts-arkui-icurve-i.md)

**默认值：** Curve.Linear

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyAnimation-curve?: Curve | ICurve--><!--Device-ParticlePropertyAnimation-curve?: Curve | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMillis

```TypeScript
endMillis: int
```

动画结束时间。 单位：毫秒。 取值范围：[0, +∞)。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyAnimation-endMillis: int--><!--Device-ParticlePropertyAnimation-endMillis: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: T
```

属性起始值。非法输入取对应属性的默认值。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyAnimation-from: T--><!--Device-ParticlePropertyAnimation-from: T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMillis

```TypeScript
startMillis: int
```

动画开始时间。 单位：毫秒。 取值范围：[0, +∞)。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyAnimation-startMillis: int--><!--Device-ParticlePropertyAnimation-startMillis: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: T
```

属性目标值。非法输入取对应属性的默认值。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyAnimation-to: T--><!--Device-ParticlePropertyAnimation-to: T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

