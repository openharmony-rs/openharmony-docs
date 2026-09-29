# PickerBackgroundStyle

```TypeScript
declare interface PickerBackgroundStyle
```

Defines the background style configuration for selected picker items.

**Since:** 20

<!--Device-unnamed-declare interface PickerBackgroundStyle--><!--Device-unnamed-declare interface PickerBackgroundStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

Corner radius of the border of the selected item.

Default value: { value:24, unit:LengthUnit.VP }, that is, the radius of all four corners is 24vp.

Unit: vp by default. The unit can be specified through the LengthMetrics or LocalizedBorderRadiuses type.

**NOTE:** 

1. The value parameter of the [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md) type applies to the
radius of all four corners, and the unit parameter is used to set the unit.
2. The [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) type can set four different corner radii, with all units fixed to vp.
3. The [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md) type can set four different corner radii, and the
unit of each corner can be set separately.

**Type:** LengthMetrics &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**Default:** { value:24, unit:LengthUnit.VP }

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-PickerBackgroundStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Background color of the selected item.

Default value:

'sys.color.comp_background_tertiary'

**Note:** If this attribute is not set, the default value is used.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** 'sys.color.comp_background_tertiary'

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-PickerBackgroundStyle-color?: ResourceColor--><!--Device-PickerBackgroundStyle-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
