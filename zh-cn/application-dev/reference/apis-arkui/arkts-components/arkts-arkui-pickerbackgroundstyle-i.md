# PickerBackgroundStyle

选择器选中项的背景样式，包括选中项的背景颜色和边框圆角半径。

**起始版本：** 20

<!--Device-unnamed-declare interface PickerBackgroundStyle--><!--Device-unnamed-declare interface PickerBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

选中项的边框圆角半径。 > 默认值：{ value:24, unit:LengthUnit.VP }，即四个圆角半径均为24vp。 > 单位：默认为vp，可通过LengthMetrics或LocalizedBorderRadiuses类型指定单位。 > **说明：** > > 1. [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md)类型的value参数同时作用于四个圆角半径大小， > unit参数用于设置单位。 > 2. BorderRadiuses类型可以设置四个不同值的圆角半径，所有单位固定为vp。 > 3. LocalizedBorderRadiuses类型可以设置四个不同值的圆角半径，并且可以单独设置每个圆角的单位。

**类型：** LengthMetrics \| BorderRadiuses \| LocalizedBorderRadiuses

**默认值：** { value:24, unit:LengthUnit.VP }

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

选中项的背景颜色。 > 默认值： > > 'sys.color.comp_background_tertiary' > **说明：**未设置该属性时，使用默认值。

**类型：** ResourceColor

**默认值：** 'sys.color.comp_background_tertiary'

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PickerBackgroundStyle-color?: ResourceColor--><!--Device-PickerBackgroundStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

