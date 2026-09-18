# NativeXComponentParameters

Defines the options of the **XComponent**. An XComponent created with such constructor parameters can pass its corresponding FrameNode object to the Native side, enabling the use of NDK APIs for surface lifecycle–related settings and [component event listening](../../../ui/ndk-listen-to-component-events.md).

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

AI analysis options. You can configure the analysis type or bind an analyzer controller through this parameter.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
