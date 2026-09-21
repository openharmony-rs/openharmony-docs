# ImageAIOptions

```TypeScript
declare interface ImageAIOptions
```

Provides the AI image analysis options.

> **NOTE:** 
> 
> The **types** parameter of this API has a higher priority than that of
> [ImageAnalyzerConfig](arkts-arkui-imageanalyzerconfig-i.md). This means that, if both parameters are set, the value set by
> this API takes precedence.
> 
> This API depends on device capabilities and must be used together with the
> [enableAnalyzer](../arkts-components/arkts-arkui-image-comp-attribute.md#enableanalyzer) API of the corresponding component (for example, the
> [Image](../arkts-components/arkts-arkui-image-comp.md#image) component).

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aiController

```TypeScript
aiController?: ImageAnalyzerController
```

AI image analysis controller.

**Type:** [ImageAnalyzerController](arkts-arkui-imageanalyzercontroller-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types?: ImageAnalyzerType[]
```

AI image analysis types.

**Type:** [ImageAnalyzerType](arkts-arkui-imageanalyzertype-e.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
