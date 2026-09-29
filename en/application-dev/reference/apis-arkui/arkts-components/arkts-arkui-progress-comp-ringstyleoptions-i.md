# RingStyleOptions

```TypeScript
declare interface RingStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

Options of the ring style without scales.

Inherits from [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** RingStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface RingStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions--><!--Device-unnamed-declare interface RingStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: boolean
```

Whether to enable the shadow of the progress bar.

true: enables the shadow of the progress bar; false: disables the shadow of the progress bar.

Default value: **false**

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RingStyleOptions-shadow?: boolean--><!--Device-RingStyleOptions-shadow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ProgressStatus
```

Sets the status of the progress bar. When the value is set to **ProgressStatus.LOADING**, the check-and-update animation is enabled. When the value changes from **ProgressStatus.LOADING** to **ProgressStatus.PROGRESSING**, the check-and-update animation runs to the end point before stopping.

Default value: **ProgressStatus.PROGRESSING**

**Note:** When the value is set to **ProgressStatus.LOADING**, the progress value setting does not take effect. For details, see the description of [value](arkts-arkui-progress-comp-attribute.md#value).

**Type:** [ProgressStatus](arkts-arkui-progress-comp-progressstatus-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RingStyleOptions-status?: ProgressStatus--><!--Device-RingStyleOptions-status?: ProgressStatus-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Sets the width of the progress bar.

Default value: **4.0vp**

Value range: a value greater than 0. Percentage setting is not supported.

If the value exceeds the value range or an invalid value is set, the default value is used.

When the width is greater than or equal to the radius, the width is changed to half of the radius by default.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RingStyleOptions-strokeWidth?: Length--><!--Device-RingStyleOptions-strokeWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
