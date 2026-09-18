# CanvasParams

Defines the parameters of the **Canvas** component.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

AI image analysis options. You can configure the analysis type or bind an analyzer controller through this parameter.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unit

```TypeScript
unit?: LengthMetricsUnit
```

Indicates the unit mode employed by Canvas during drawing. <br>It can only be set when creating the **Canvas** component and cannot be modified afterwards. <br>Default value: **LengthMetricsUnit.DEFAULT**

**Type:** [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
