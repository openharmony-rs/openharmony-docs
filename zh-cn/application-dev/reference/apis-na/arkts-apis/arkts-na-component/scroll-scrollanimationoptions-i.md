# ScrollAnimationOptions

自定义滚动动效的参数选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ScrollAnimationOptions--><!--Device-unnamed-export declare interface ScrollAnimationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

设置滚动动画滚动到边界后，是否转换成越界回弹动画。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_仅在设置为true，且组件的edgeEffect设置为EdgeEffect.Spring时，使用动画滚动到边界会转换为越界回弹动画， 设置为false时，滚动到边界会直接停止动画，不会转换为越界回弹动画。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollAnimationOptions-canOverScroll?: boolean--><!--Device-ScrollAnimationOptions-canOverScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

设置滚动曲线。

**类型：** Curve \| ICurve

**默认值：** Curve.Ease

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollAnimationOptions-curve?: Curve | ICurve--><!--Device-ScrollAnimationOptions-curve?: Curve | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

设置滚动时长。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 取值限定为整数。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_设置为小于0的值时，按默认值显示。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** int

**默认值：** 1000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollAnimationOptions-duration?: int--><!--Device-ScrollAnimationOptions-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

