# NativeXComponentParameters

```TypeScript
declare interface NativeXComponentParameters
```

Defines the specific configuration parameters used by XComponent on the native side. An XComponent created with this constructor can pass its corresponding [FrameNode](../arkts-apis/arkts-arkui-typenode-n.md) object to the native side, where NDK APIs can be used to configure the surface lifecycle and [add event listeners] (../../../ui/ndk-listen-to-component-events.md).

**Since:** 19

<!--Device-unnamed-declare interface NativeXComponentParameters--><!--Device-unnamed-declare interface NativeXComponentParameters-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

Sets an AI analysis option for the component. Through this option, you can configure the analysis type or bind an analysis controller. It takes effect only when the type is SURFACE or TEXTURE. If it is not set, no AI analysis option is configured, and AI analysis can be enabled separately through the enableAnalyzer attribute.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions--><!--Device-NativeXComponentParameters-imageAIOptions?: ImageAIOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: XComponentType
```

Type of the component.

**Type:** [XComponentType](../arkts-apis/arkts-arkui-xcomponenttype-e.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NativeXComponentParameters-type: XComponentType--><!--Device-NativeXComponentParameters-type: XComponentType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
