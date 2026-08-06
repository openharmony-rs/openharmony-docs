# ScrollOptions

滚动到指定位置的参数选项。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-unnamed-declare interface ScrollOptions--><!--Device-unnamed-declare interface ScrollOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animation

```TypeScript
animation?: ScrollAnimationOptions | boolean
```

动画配置。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_目前List、Scroll、Grid和WaterFlow支持Boolean类型和ICurve。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ 布尔类型启用默认弹簧动效。 [since 10 - 11] 布尔类型启用默认弹簧动效。 [since 12]

**类型：** ScrollAnimationOptions \| boolean

**默认值：** ScrollAnimationOptions: { duration: 1000, curve: Curve.Ease, canOverScroll: false } [since 18]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollOptions-animation?: ScrollAnimationOptions | boolean--><!--Device-ScrollOptions-animation?: ScrollAnimationOptions | boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

设置滚动目标位置是否可以超出边界。

**类型：** boolean

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollOptions-canOverScroll?: boolean--><!--Device-ScrollOptions-canOverScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xOffset

```TypeScript
xOffset: number | string
```

水平滚动偏移量。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_不支持设置百分比。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_无动画滚动时，设置为小于0的值按0处理。有动画滚动时，默认停在起始位置。通过设置\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_animation\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_参数，可以在滚动超出边界时启用回弹效果。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_该参数仅在滚动轴为x轴时生效。 \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_

**类型：** number \| string

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollOptions-xOffset: number | string--><!--Device-ScrollOptions-xOffset: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## yOffset

```TypeScript
yOffset: number | string
```

竖直滚动偏移量。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_不支持设置百分比。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_无动画滚动时，设置为小于0的值按0处理。有动画滚动时，默认停在起始位置。通过设置\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_animation\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_参数，可以在滚动超出边界时启用回弹效果。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_该参数仅在滚动轴为y轴时生效。 \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_

**类型：** number \| string

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollOptions-yOffset: number | string--><!--Device-ScrollOptions-yOffset: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

