# LinearGradientStyle

```TypeScript
declare class LinearGradientStyle extends ShaderStyle
```

Displays a linear gradient. **LinearGradientStyle** inherits from [ShaderStyle](arkts-arkui-shaderstyle-c.md).

**Inheritance/Implementation:** LinearGradientStyle extends [ShaderStyle](arkts-arkui-shaderstyle-c.md)

**Since:** 20

<!--Device-unnamed-declare class LinearGradientStyle extends ShaderStyle--><!--Device-unnamed-declare class LinearGradientStyle extends ShaderStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: LinearGradientOptions)
```

A constructor used to create a **LinearGradientStyle** object.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-LinearGradientStyle-constructor(options: LinearGradientOptions)--><!--Device-LinearGradientStyle-constructor(options: LinearGradientOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LinearGradientOptions](../arkts-components/arkts-arkui-common-comp-lineargradientoptions-i.md) | Yes | Options for displaying a linear gradient. <br>The default value of direction in [LinearGradientOptions](../arkts-components/arkts-arkui-common-comp-lineargradientoptions-i.md) is processed as NONE in [GradientDirection](arkts-arkui-gradientdirection-e.md). |

## options

```TypeScript
options: LinearGradientOptions
```

Options for displaying a linear gradient.

**Type:** [LinearGradientOptions](../arkts-components/arkts-arkui-common-comp-lineargradientoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-LinearGradientStyle-options: LinearGradientOptions--><!--Device-LinearGradientStyle-options: LinearGradientOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
