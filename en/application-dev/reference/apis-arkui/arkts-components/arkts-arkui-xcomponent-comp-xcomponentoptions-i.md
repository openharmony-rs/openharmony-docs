# XComponentOptions

```TypeScript
declare interface XComponentOptions
```

Defines the options of the **XComponent**.

**Since:** 12

<!--Device-unnamed-declare interface XComponentOptions--><!--Device-unnamed-declare interface XComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: XComponentController
```

Controller bound to the component, which can be used to invoke methods of the component. This parameter is effective only when **type** is **SURFACE** or **TEXTURE**.

**Type:** [XComponentController](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentOptions-controller: XComponentController--><!--Device-XComponentOptions-controller: XComponentController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

Sets an AI analysis option for the component. Through this option, you can configure the analysis type or bind an analysis controller. It takes effect only when the type is SURFACE or TEXTURE. If this option is not set, no AI analysis option is configured, and AI analysis can be enabled separately through the enableAnalyzer attribute.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions--><!--Device-XComponentOptions-imageAIOptions?: ImageAIOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

Type of the component.

**Type:** [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentOptions-type: XComponentType--><!--Device-XComponentOptions-type: XComponentType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
