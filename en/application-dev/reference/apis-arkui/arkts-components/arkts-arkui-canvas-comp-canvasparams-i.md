# CanvasParams

```TypeScript
declare interface CanvasParams
```

Defines the parameters of the **Canvas** component.

**Since:** 23

<!--Device-unnamed-declare interface CanvasParams--><!--Device-unnamed-declare interface CanvasParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

AI analysis option for the component. Through this option, you can configure the analysis type or bind an analysis controller.<br> Abnormal values **null** and **undefined** are treated as not enabling the AI analysis function.<br> Default value: AI analysis function not enabled.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CanvasParams-imageAIOptions?: ImageAIOptions--><!--Device-CanvasParams-imageAIOptions?: ImageAIOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unit

```TypeScript
unit?: LengthMetricsUnit
```

Unit mode used for **Canvas** drawing. Different unit modes affect the coordinate and size calculation methods during drawing. For details, see LengthMetricsUnit.<br> This attribute can only be set when creating the **Canvas** and cannot be modified afterwards.<br> Default value: **LengthMetricsUnit.DEFAULT**

**Type:** LengthMetricsUnit

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-CanvasParams-unit?: LengthMetricsUnit--><!--Device-CanvasParams-unit?: LengthMetricsUnit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
