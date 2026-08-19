# AnimationOptions

拖拽相关的动效参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-dragController-interface AnimationOptions--><!--Device-dragController-interface AnimationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## curve

```TypeScript
curve?: Curve | ICurve
```

设置动画曲线。 默认值：Curve.EaseInOut

**类型：** Curve \| ICurve

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationOptions-curve?: Curve | ICurve--><!--Device-AnimationOptions-curve?: Curve | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

动画持续时间，单位为毫秒。 默认值：1000 **说明：** - 设置小于0的值时按0处理。 - 设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationOptions-duration?: int--><!--Device-AnimationOptions-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

