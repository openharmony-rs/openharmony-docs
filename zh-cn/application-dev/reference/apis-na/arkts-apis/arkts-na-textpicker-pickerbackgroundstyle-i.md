# PickerBackgroundStyle

选择器选中项的背景样式，包括选中项的背景颜色和边框圆角半径。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface PickerBackgroundStyle--><!--Device-unnamed-export declare interface PickerBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

选中项的边框圆角半径。 默认值：{ value:24, unit:LengthUnit.VP }，即四个圆角半径均为24VP。 **说明：** 1. [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md#LengthMetrics)类型的value参数同时作用于四个圆角半径大小， unit参数用于设置单位。 2. BorderRadiuses类型可以设置四个不同值的圆角半径，所有单位固定为VP。 3. LocalizedBorderRadiuses类型可以设置四个不同值的圆角半径， 并且可以单独设置每个圆角的单位。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md) \| [BorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-borderradiuses-t.md) \| [LocalizedBorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

选中项的背景颜色。 默认值： 'sys.color.comp_background_tertiary'

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PickerBackgroundStyle-color?: ResourceColor--><!--Device-PickerBackgroundStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

