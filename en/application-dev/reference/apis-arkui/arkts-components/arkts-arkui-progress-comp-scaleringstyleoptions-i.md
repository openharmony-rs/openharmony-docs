# ScaleRingStyleOptions

```TypeScript
declare interface ScaleRingStyleOptions extends CommonProgressStyleOptions
```

Options of the ring style with scales.

Inherits from [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** ScaleRingStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface ScaleRingStyleOptions extends CommonProgressStyleOptions--><!--Device-unnamed-declare interface ScaleRingStyleOptions extends CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: number
```

Sets the total number of scales of the ring progress bar.

Default value: 120

Value range: [2, min(width, height)*π/scaleWidth]. When the value exceeds the range, the style is displayed as a ring progress bar without scales.

When both scaleCount and scaleWidth are equal to their default values, setting the component width or height to less than 77 vp displays a ring progress bar without scales.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScaleRingStyleOptions-scaleCount?: number--><!--Device-ScaleRingStyleOptions-scaleCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

Sets the thickness of the scales of the ring progress bar (percentage setting is not supported).

Default value: 2.0vp

Value range: a value greater than 0 (unit: vp).

When the scale thickness is greater than the progress bar width, the system default thickness is used.

When both scaleCount and scaleWidth are equal to their default values, setting the component width or height to less than 77 vp displays a ring progress bar without scales.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScaleRingStyleOptions-scaleWidth?: Length--><!--Device-ScaleRingStyleOptions-scaleWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Sets the progress bar width.

Default value: 4.0vp

Value range: a value greater than 0 (unit: vp). Percentage setting is not supported.

Exceeding the value range or setting an invalid value is handled as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScaleRingStyleOptions-strokeWidth?: Length--><!--Device-ScaleRingStyleOptions-strokeWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
