# LinearStyleOptions

```TypeScript
declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

Linear style options.

Inherits from [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** LinearStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

Border radius of the linear progress indicator.

Value range: [0, strokeWidth/2] Default value: **strokeWidth/2**

**Type:** PX &#124; VP &#124; LPX &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** strokeWidth / 2

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
