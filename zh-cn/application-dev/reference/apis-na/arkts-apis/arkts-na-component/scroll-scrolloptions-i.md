# ScrollOptions

滚动到指定位置的参数选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ScrollOptions--><!--Device-unnamed-export declare interface ScrollOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animation

```TypeScript
animation?: ScrollAnimationOptions | boolean
```

动画配置。 匿名对象规范化。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_当前List、Scroll、Grid、WaterFlow均支持boolean类型和ICurve曲线。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** ScrollAnimationOptions \| boolean

**默认值：** ScrollAnimationOptions: { duration: 1000, curve: Curve.Ease, canOverScroll: false }

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollOptions-animation?: ScrollAnimationOptions | boolean--><!--Device-ScrollOptions-animation?: ScrollAnimationOptions | boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

滚动目标位置是否可以超出边界停留。仅当组件的edgeEffect设置为EdgeEffect.Spring时，滚动能够越界停留。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollOptions-canOverScroll?: boolean--><!--Device-ScrollOptions-canOverScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xOffset

```TypeScript
xOffset: double | string
```

水平滚动总偏移量。 匿名对象规范化。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_该参数值不支持设置百分比。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_仅滚动轴为x轴时生效。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_取值范围：当值小于0时，不带动画的滚动，按0处理。带动画的滚动，默认滚动到起始位置后停止，可通过设置animation参数，使滚动在越界时启动回弹动画。 \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_参数类型为number时单位为vp。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollOptions-xOffset: double | string--><!--Device-ScrollOptions-xOffset: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## yOffset

```TypeScript
yOffset: double | string
```

垂直滚动总偏移量。 匿名对象规范化。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_该参数值不支持设置百分比。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_仅滚动轴为y轴时生效。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_取值范围：当值小于0时，不带动画的滚动，按0处理。带动画的滚动，默认滚动到起始位置后停止，可通过设置animation参数，使滚动在越界时启动回弹动画。 \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_参数类型为number时单位为vp。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollOptions-yOffset: double | string--><!--Device-ScrollOptions-yOffset: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

