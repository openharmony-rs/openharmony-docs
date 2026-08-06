# ScrollAnimationOptions

自定义滚动动效的参数选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface ScrollAnimationOptions--><!--Device-unnamed-declare interface ScrollAnimationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

是否启用过滚动。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ 设置为\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_true\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_时可以滚动超出边界并触发回弹动画，同时组件的\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_edgeEffect\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_属性需设置为EdgeEffect.Spring。 \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_

**类型：** boolean

**默认值：** false

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-canOverScroll?: boolean--><!--Device-ScrollAnimationOptions-canOverScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

滚动曲线。

**类型：** Curve \| ICurve

**默认值：** Curve.Ease

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-curve?: Curve | ICurve--><!--Device-ScrollAnimationOptions-curve?: Curve | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

滚动时长。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_设置为小于0的值时，按默认值处理。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** number

**默认值：** 1000

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-duration?: number--><!--Device-ScrollAnimationOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

