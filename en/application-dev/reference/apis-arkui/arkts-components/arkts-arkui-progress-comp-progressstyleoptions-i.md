# ProgressStyleOptions

```TypeScript
declare interface ProgressStyleOptions extends CommonProgressStyleOptions
```

Defines the progress bar style options.

Inherits from [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** ProgressStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface ProgressStyleOptions extends CommonProgressStyleOptions--><!--Device-unnamed-declare interface ProgressStyleOptions extends CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: number
```

Sets the total number of scale marks on the ring progress bar.

Default value: 120

Value range: [2, min(width, height)*π/scaleWidth]. When the value exceeds the value range, the style is displayed as a ring progress bar without scale marks.

When both scaleCount and scaleWidth are equal to their default values, setting the component width or height to less than 77vp displays a ring progress bar without scale marks.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyleOptions-scaleCount?: number--><!--Device-ProgressStyleOptions-scaleCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

Sets the thickness of the scale marks on the ring progress bar (percentage setting not supported).

Default value: 2.0vp

Value range: a value greater than 0.

When the value exceeds the value range or an invalid value is set, the default value is used.

When the scale mark thickness is greater than the progress bar width, the system default thickness is used.

When both scaleCount and scaleWidth are equal to their default values, setting the component width or height to less than 77vp displays a ring progress bar without scale marks.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyleOptions-scaleWidth?: Length--><!--Device-ProgressStyleOptions-scaleWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Sets the progress bar width (percentage setting not supported).

Default value: 4.0vp

Value range: a value greater than 0.

When the value exceeds the value range or an invalid value is set, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressStyleOptions-strokeWidth?: Length--><!--Device-ProgressStyleOptions-strokeWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
