# LinearStyleOptions

```TypeScript
declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

Linear style options.

Inherits from [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** LinearStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions--><!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

Sets the corner radius of the linear progress bar.

Value range: [0, strokeWidth / 2]. Default value: **strokeWidth / 2**.

If the value exceeds the value range, the default value is used.

**Type:** PX &#124; VP &#124; LPX &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** strokeWidth / 2

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource--><!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Sets the progress bar width.

Default value: **4.0vp**

Value range: a value greater than 0. Percentage setting is not supported.

If the value exceeds the value range or an invalid value is set, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LinearStyleOptions-strokeWidth?: Length--><!--Device-LinearStyleOptions-strokeWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
