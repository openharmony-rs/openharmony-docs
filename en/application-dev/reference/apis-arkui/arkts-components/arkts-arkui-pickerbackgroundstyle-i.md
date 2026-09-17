# PickerBackgroundStyle

Defines the background style configuration for selected picker items.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

Border radius of the selected item.

Default value: **{ value:24, unit:LengthUnit.VP }**, meaning 24 vp for all corners.

**NOTE:** 

1. [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md): uniform radius with a customizable unit
2. [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md): per-corner radius values (vp units only)
3. [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md): per-corner radius values with individual units

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**Default:** { value:24, unit:LengthUnit.VP }

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Background color of the selected item.

Default value: 'sys.color.comp_background_tertiary'

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** 'sys.color.comp_background_tertiary'

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
