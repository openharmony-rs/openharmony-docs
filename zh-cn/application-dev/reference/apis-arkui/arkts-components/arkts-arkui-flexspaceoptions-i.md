# FlexSpaceOptions

设置Flex容器的子组件在主轴或交叉轴的间距。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface FlexSpaceOptions--><!--Device-unnamed-declare interface FlexSpaceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cross

```TypeScript
cross?: LengthMetrics
```

Flex容器交叉轴上相邻行之间的间距。设置后，交叉轴方向相邻行之间将按指定间距进行分隔，仅在多行布局（wrap为Wrap或WrapReverse）时生效。当space.cross为负数，或者justifyContent设置为 FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时，该参数不生效。 默认值：LengthMetrics.px(0)

**类型：** LengthMetrics

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FlexSpaceOptions-cross?: LengthMetrics--><!--Device-FlexSpaceOptions-cross?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## main

```TypeScript
main?: LengthMetrics
```

Flex容器主轴上相邻子组件之间的间距。设置后，主轴方向相邻子组件之间将按指定间距进行分隔，在单行或多行布局时均生效。当space.main为负数，或者justifyContent设置为FlexAlign.SpaceBetween 、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时，该参数不生效。 默认值：LengthMetrics.px(0)

**类型：** LengthMetrics

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FlexSpaceOptions-main?: LengthMetrics--><!--Device-FlexSpaceOptions-main?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

