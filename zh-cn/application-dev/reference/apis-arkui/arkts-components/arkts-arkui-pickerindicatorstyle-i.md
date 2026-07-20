# PickerIndicatorStyle

选中项指示器样式的参数说明。

**起始版本：** 22

<!--Device-unnamed-declare interface PickerIndicatorStyle--><!--Device-unnamed-declare interface PickerIndicatorStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

选中项背景的颜色。

默认值：'sys.color.comp_background_tertiary'

说明：

当type为PickerIndicatorType.BACKGROUND时生效。

**类型：** ResourceColor

**默认值：** 'sys.color.comp_background_tertiary'

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-backgroundColor?: ResourceColor--><!--Device-PickerIndicatorStyle-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

选中项背景的边框圆角半径。

默认值：{ value:12, unit:LengthUnit.vp }，即四个圆角半径均为12vp。

取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，使用默认值；当取值大于最大值时，使用最大值。

说明：

1. 当type为PickerIndicatorType.BACKGROUND时生效。2. [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md)：统一设置四个圆角半径的大小和单位。3. [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md)：单独设置四个圆角半径的大小（单位为vp）。4. [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)：单独设置四个圆角半径的大小和单位。

**类型：** LengthMetrics \| BorderRadiuses \| LocalizedBorderRadiuses

**默认值：** { value:12, unit:LengthUnit.vp }

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-PickerIndicatorStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dividerColor

```TypeScript
dividerColor?: ResourceColor
```

分割线的颜色。

默认值：'sys.color.comp_divider'

说明：

当type为PickerIndicatorType.DIVIDER时生效。

**类型：** ResourceColor

**默认值：** $r('sys.color.comp_divider')

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-dividerColor?: ResourceColor--><!--Device-PickerIndicatorStyle-dividerColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: LengthMetrics
```

分割线与UIPickerComponent容器侧边结束端的距离。

默认值：0

单位：与LengthMetrics一致。

取值范围：startMargin与endMargin之和不得超过UIPickerComponent容器的宽度。设置小于0或startMargin与endMargin之和超过UIPickerComponent容器的宽度时，使用默认值。不支持“百分比”类型。

说明：

当type为PickerIndicatorType.DIVIDER时生效。

**类型：** LengthMetrics

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-endMargin?: LengthMetrics--><!--Device-PickerIndicatorStyle-endMargin?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: LengthMetrics
```

分割线与UIPickerComponent容器侧边起始端的距离。

默认值：0

单位：与LengthMetrics一致。

取值范围：startMargin与endMargin之和不得超过UIPickerComponent容器的宽度。设置小于0或startMargin与endMargin之和超过UIPickerComponent容器的宽度时，使用默认值。不支持“百分比”类型。

说明：

当type为PickerIndicatorType.DIVIDER时生效。

**类型：** LengthMetrics

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-startMargin?: LengthMetrics--><!--Device-PickerIndicatorStyle-startMargin?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

分割线的线宽。

默认值：2.0px

单位：与LengthMetrics一致。

取值范围：[0, 选中项高度的一半（即20vp）]。strokeWidth小于0或大于选中项高度的一半时使用默认值。不支持“百分比”类型。

说明：

1. 当type为PickerIndicatorType.DIVIDER时生效。2. 通过LengthMetrics.resource方式设置时，使用非长度属性的值会按照0vp处理。

**类型：** LengthMetrics

**默认值：** 2.0px

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-strokeWidth?: LengthMetrics--><!--Device-PickerIndicatorStyle-strokeWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: PickerIndicatorType
```

选中项指示器的类型。

默认值：PickerIndicatorType.BACKGROUND

当type的值为小数时，使用向下取整后的整数；当type的值不在PickerIndicatorType枚举范围内时，使用默认值。

**类型：** PickerIndicatorType

**默认值：** PickerIndicatorType.BACKGROUND

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-PickerIndicatorStyle-type: PickerIndicatorType--><!--Device-PickerIndicatorStyle-type: PickerIndicatorType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

