# DividerOptions

分割线的信息。

**起始版本：** 12

<!--Device-unnamed-declare interface DividerOptions--><!--Device-unnamed-declare interface DividerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

分割线的颜色。

默认值：'#33000000'

**类型：** ResourceColor

**默认值：** '#33000000'

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DividerOptions-color?: ResourceColor--><!--Device-DividerOptions-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Dimension
```

分割线与TextPicker侧边结束端的距离。

默认值：0

单位：默认为vp，也可指定单位为px。

取值范围：endMargin小于0时无效，最大值不得超过TextPicker列宽。不支持“百分比”类型。

**类型：** Dimension

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DividerOptions-endMargin?: Dimension--><!--Device-DividerOptions-endMargin?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Dimension
```

分割线与TextPicker侧边起始端的距离。

默认值：0

单位：默认为vp，也可指定单位为px。

取值范围：startMargin小于0时无效，最大值不得超过TextPicker列宽。不支持“百分比”类型。

**类型：** Dimension

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DividerOptions-startMargin?: Dimension--><!--Device-DividerOptions-startMargin?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Dimension
```

分割线的线宽。

默认值：2.0px

单位：默认为vp，也可指定单位为px。

取值范围：strokeWidth小于0取默认值，最大不得超过列高的一半。不支持“百分比”类型。

**类型：** Dimension

**默认值：** 2.0px

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DividerOptions-strokeWidth?: Dimension--><!--Device-DividerOptions-strokeWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

