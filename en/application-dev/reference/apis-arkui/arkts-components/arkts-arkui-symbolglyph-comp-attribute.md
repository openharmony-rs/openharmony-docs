# SymbolGlyph properties/events

```TypeScript
declare class SymbolGlyphAttribute extends CommonMethod<SymbolGlyphAttribute>
```

The [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported. For text attributes, only the following attributes are supported.

The [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

**Inheritance/Implementation:** SymbolGlyphAttribute extends CommonMethod<SymbolGlyphAttribute>

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy(value: SymbolEffectStrategy)
```

Sets the effect strategy of the **SymbolGlyph** component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolEffectStrategy](arkts-arkui-symbolglyph-comp-symboleffectstrategy-e.md) | Yes | Effect strategy of the **SymbolGlyph** component.<br>Default value: **SymbolEffectStrategy.NONE** |

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor>)
```

Sets the color of the **SymbolGlyph** component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the **SymbolGlyph** component.<br> Default value: depending on the rendering strategy |

<a id="fontcolor-1"></a>

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor | ColorMetrics> | undefined)
```

Called when the SymbolGlyph color is set.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics&gt; &#124; undefined | Yes |  |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the size of the **SymbolGlyph** component. When using the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

The display size of the symbol glyph is controlled by the **fontSize** setting. Once **width** or **height** is specified, other universal attributes will only affect the size of the component's placeholder, not the symbol glyph itself.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Size of the **SymbolGlyph** component.<br>Default value: **16fp**<br> Unit: fp<br>Percentage strings are not supported. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the **SymbolGlyph** component. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.

The **sys.symbol.ohos_lungs** icon does not support font weight setting.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the **SymbolGlyph** component.<br>Default value: **FontWeight.Normal** |

<a id="fontweight-1"></a>

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

Used to set the font weight of symbolGlyph.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | the symbolGlyph font weight. For the number type, the value range is [100, 900]. When enableVariableFontWeight in fontWeightConfigs is **false**, the value must be a multiple of 100; when **true**, any integer within [100, 900] is supported. The default value is **FontWeight.Normal**. |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | No | the configuration of font weight. If not specified, the default values of FontWeightConfigs are used: enableVariableFontWeight defaults to **false**, and enableDeviceFontWeightCategory defaults to **true**. |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

Sets the maximum font scale factor for the **SymbolGlyph** component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Maximum font scale factor for the **SymbolGlyph** component.<br>Value range: [1, +∞)<br>**NOTE:** <br>A value less than 1 is handled as **1**. Abnormal values are ineffective by default. |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

Sets the minimum font scale factor for the **SymbolGlyph** component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Minimum font scale factor for the **SymbolGlyph** component.<br>Value range: [0, 1]<br>The value **0** results in the minimum scaling.<br>**NOTE:** <br>A value less than 0 is handled as 0. A value greater than 1 is handled as 1. Abnormal values are ineffective by default. |

## renderingStrategy

```TypeScript
renderingStrategy(value: SymbolRenderingStrategy)
```

Sets the rendering strategy of the **SymbolGlyph** component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md) | Yes | Rendering strategy of the **SymbolGlyph** component.<br>Default value: **SymbolRenderingStrategy.SINGLE** |

## shaderStyle

```TypeScript
shaderStyle(shader: Array<ShaderStyle | undefined> | ShaderStyle)
```

Applies a gradient or solid color shader effect to the **SymbolGlyph** component.

This API supports [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), and [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md). When set, **shaderStyle** takes precedence over [fontColor](arkts-arkui-symbolspan-comp-attribute.md#fontcolor) and any AI-based styling. To apply a simple solid color, using [fontColor](arkts-arkui-symbolspan-comp-attribute.md#fontcolor) is recommended.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | Array&lt;[ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) &#124; undefined&gt; &#124; [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) | Yes | Shader effect.<br>Input types and behavior:<br> Single **ShaderStyle** object: applies the specified effect to all layers. Array of **ShaderStyle** objects: applies the specified effect to the corresponding layer. Array of **undefined**: applies the default **SymbolGlyph** color to the corresponding layer. Layers unset retain their default color.<br> Based on the input, the system applies a radial gradient ([RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md)), linear gradient ([LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md)), or solid color ([ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md)) to the **SymbolGlyph** component.<br>**NOTE:** <br>Unit: vp<br>Specify the center point and radius using percentages. If a non-percentage value (e.g., **10px**) is provided, it will be interpreted as 1000%.<br>You are advised to specify the radius using percentages.<br>Percentages are relative to the icon's size. The recommended value range is [0, 1). |

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean)
```

Sets the symbol effect and effect state for the **SymbolGlyph** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md) | Yes | Symbol effect of the **SymbolGlyph** component.<br>Default value: [SymbolEffect](#symboleffect) |
| isActive | boolean | No | Whether the effect is active.<br>**true**: playing. **false**: not playing.<br> Default value: **false**. |

<a id="symboleffect-1"></a>

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number)
```

Sets the symbol effect and effect trigger for the **SymbolGlyph** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md) | Yes | Symbol effect of the **SymbolGlyph** component.<br>Default value: [SymbolEffect](#symboleffect) |
| triggerValue | number | No | Value that, when changed, initiates the animation of the **SymbolGlyph** component.<br>To prevent the motion effect from triggering initially, set it to **-1**. |

## symbolShadow

```TypeScript
symbolShadow(shadow: Optional<ShadowOptions>)
```

Sets the shadow effect of the **SymbolGlyph** component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shadow | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Shadow effect of the **SymbolGlyph** component.<br>Unit: vp<br>Default value: {<br>radius: 0,<br>color: Color.Black<br>offsetX: 0,<br>offsetY: 0<br>} <br>The **fill** and **type** attributes, as well as the enumerated values of **ColoringStrategy** within the **color **attribute, are not supported. |
