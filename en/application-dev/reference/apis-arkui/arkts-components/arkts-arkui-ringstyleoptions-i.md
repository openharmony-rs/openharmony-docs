# RingStyleOptions

Options of the ring style without scales.

Inherits from [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** RingStyleOptions extends [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: boolean
```

Whether to enable the shadow effect.

**true**: The shadow effect is enabled. **false**: The shadow effect is disabled.

Default value: **false**

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ProgressStatus
```

Progress state. When this parameter is set to **ProgressStatus.LOADING**, the update check animation is enabled, and the progress value setting does not take effect. When the value changes from **ProgressStatus.LOADING** to **ProgressStatus.PROGRESSING**, the update check animation runs to completion and then stops.

Default value: **ProgressStatus.PROGRESSING**

**Type:** [ProgressStatus](arkts-arkui-progressstatus-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Stroke width of the progress indicator. Percentage values are not supported.

Default value: **4.0vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
