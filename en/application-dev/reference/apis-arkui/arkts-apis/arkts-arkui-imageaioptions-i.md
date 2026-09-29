# ImageAIOptions

```TypeScript
declare interface ImageAIOptions
```

Provides the image AI analysis options.

> **NOTE:** 
> 
> The **types** parameter of this API has a higher priority than that of
> [ImageAnalyzerConfig](arkts-arkui-imageanalyzerconfig-i.md). This means that, if both parameters are set, the value set by
> this API takes precedence.
> 
> This API depends on device capabilities and must be used together with the
> [enableAnalyzer](../arkts-components/arkts-arkui-image-comp-attribute.md#enableanalyzer) API of the corresponding component (for example, the
> [Image](../arkts-components/arkts-arkui-image-comp.md) component).

**Since:** 12

<!--Device-unnamed-declare interface ImageAIOptions--><!--Device-unnamed-declare interface ImageAIOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aiController

```TypeScript
aiController?: ImageAnalyzerController
```

Image AI analysis controller.

**Type:** [ImageAnalyzerController](arkts-arkui-imageanalyzercontroller-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAIOptions-aiController?: ImageAnalyzerController--><!--Device-ImageAIOptions-aiController?: ImageAnalyzerController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types?: ImageAnalyzerType[]
```

Image AI analysis type.

**Type:** [ImageAnalyzerType](arkts-arkui-imageanalyzertype-e.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageAIOptions-types?: ImageAnalyzerType[]--><!--Device-ImageAIOptions-types?: ImageAnalyzerType[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
