# XComponentOptions

Defines the options of the **XComponent**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: XComponentController
```

Controller bound to the component, which can be used to invoke methods of the component. This parameter is effective only when **type** is **SURFACE** or **TEXTURE**.

**Type:** [XComponentController](arkts-arkui-xcomponentcontroller-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

AI analysis options. You can configure the analysis type or bind an analyzer controller through this parameter.

**Type:** [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
