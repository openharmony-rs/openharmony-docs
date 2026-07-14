# FlexOptions

设置Flex子组件的排列对齐方式。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: FlexAlign
```

当交叉轴存在额外空间时，多行内容之间的对齐方式。仅在wrap为Wrap或WrapReverse下生效。

默认值：FlexAlign.Start

异常值按默认值处理。

**类型：** FlexAlign

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: ItemAlign
```

所有子组件在Flex容器交叉轴上的对齐格式。

默认值：ItemAlign.Start

异常值按默认值处理。

**类型：** ItemAlign

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: FlexDirection
```

子组件在Flex容器上排列的方向，即主轴的方向。

默认值：FlexDirection.Row

异常值按默认值处理。

**类型：** FlexDirection

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在Flex容器主轴上的对齐格式。

默认值：FlexAlign.Start

异常值按默认值处理。

**类型：** FlexAlign

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: FlexSpaceOptions
```

所有子组件在Flex容器主轴或交叉轴的间距。

默认值：{main: LengthMetrics.px(0), cross: LengthMetrics.px(0)}

非法值：按默认值处理。

space为负数、百分比或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时不生效。

**类型：** FlexSpaceOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wrap

```TypeScript
wrap?: FlexWrap
```

Flex容器是单行/列还是多行/列排列。

默认值：FlexWrap.NoWrap

异常值按默认值处理。

**说明：**

在多行布局时，通过交叉轴方向，确认新行堆叠方向。

**类型：** FlexWrap

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

