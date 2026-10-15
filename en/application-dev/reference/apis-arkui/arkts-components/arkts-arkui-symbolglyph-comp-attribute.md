# SymbolGlyph properties/events

```TypeScript
declare class SymbolGlyphAttribute extends CommonMethod<SymbolGlyphAttribute>
```

The [universal attributes](arkts-arkui-common-comp.md) are supported. For text attributes, only the following attributes are supported.

**Inheritance/Implementation:** SymbolGlyphAttribute extends CommonMethod&lt;SymbolGlyphAttribute&gt;

**Since:** 11

<!--Device-unnamed-declare class SymbolGlyphAttribute extends CommonMethod<SymbolGlyphAttribute>--><!--Device-unnamed-declare class SymbolGlyphAttribute extends CommonMethod<SymbolGlyphAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy(value: SymbolEffectStrategy)
```

Sets the effect strategy of the **SymbolGlyph** component. If this API is not used, the default effect strategy is **SymbolEffectStrategy.NONE**.

> **NOTE:** 
> 
> - Since API version 12, this API is supported in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).
> 
> - For animation attributes, only the **effectStrategy** attribute or a single **symbolEffect** attribute is supported. Mixing multiple animation attributes is not supported.
> 
> - This API supports only the three preset animation types: NONE, SCALE, and HIERARCHICAL. After being set, the animation plays automatically. To use richer animation types (such as appear, disappear, bounce, replacement, and pulse animations) or to control the playback state and trigger timing of the animation, use the [symbolEffect](#symboleffect1) API. The two cannot be used at the same time. For details, see the description of the [symbolEffect](#symboleffect1) API.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolEffectStrategy](arkts-arkui-symbolglyph-comp-symboleffectstrategy-e.md) | Yes | Animation strategy of the SymbolGlyph component. |

<a id="fontcolor1"></a>

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor>)
```

Sets the font color of the **SymbolGlyph** component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-fontColor(value: Array<ResourceColor>): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-fontColor(value: Array<ResourceColor>): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Font color of the SymbolGlyph component. <br> When value is undefined, the default color of the icon is used, and the default color follows the theme. <br>The color setting effect varies with the rendering strategy. For details, see [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md). |

<a id="fontcolor2"></a>

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor | ColorMetrics> | undefined)
```

Sets the font color of the **SymbolGlyph** component. Compared with the [fontColor](#fontcolor1) API, this API supports passing in a parameter of the [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md) type.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SymbolGlyphAttribute-fontColor(value: Array<ResourceColor | ColorMetrics> | undefined): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-fontColor(value: Array<ResourceColor | ColorMetrics> | undefined): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics&gt; &#124; undefined | Yes | Color of the **SymbolGlyph** component. An array of the `ResourceColor` or `ColorMetrics` type is supported. <br> When **value** is **undefined**, the default color of the icon is used, and the default color follows the theme. |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the font size of the **SymbolGlyph** component. When the string type is used, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

The display size of the icon is controlled by **fontSize**. After **width** or **height** is set, other universal attributes only take effect on the placeholder size of the component. If this API is not used, the default font size is 16fp.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-fontSize(value: number | string | Resource): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-fontSize(value: number | string | Resource): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font size of the SymbolGlyph component. <br>Value range: [0, +∞) <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Percentage strings are not supported. |

<a id="fontweight1"></a>

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the **SymbolGlyph** component. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value 400).

The **sys.symbol.ohos_lungs** icon does not support font weight setting.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-fontWeight(value: number | FontWeight | string): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-fontWeight(value: number | FontWeight | string): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the SymbolGlyph component.<br>The value of the number type ranges from 100 to 900, with an interval of 100. The default value is 400. A larger value indicates a heavier font. The string type supports the string form of the number type value, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the font may be truncated in different fonts. <br>**Note:** <br>If a value outside the value range is passed, the default value is used. If a value that does not meet the interval requirement is passed, the default value is also used (only values that are integer multiples of 100 are supported). |

<a id="fontweight2"></a>

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

Sets the font weight of the symbol glyph in the **SymbolGlyph** component. It supports configuring, through **FontWeightConfigs**, whether to enable variable font weight adjustment (after which fine-grained font weight values that are not integer multiples of 100, such as 220 and 660, can be set) and whether to automatically update the font weight based on the device font weight level (after which the component font weight is automatically adjusted with the system font weight setting). If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value 400).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SymbolGlyphAttribute-fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the symbol glyph in the **SymbolGlyph** component.<br>For the number type, the value range is [100, 900], with an interval of 100. The default value is 400. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in **FontWeight**. If the value is set too large, the font may be truncated in different fonts. <br>If the value passed in is out of the value range, the default value is used. If the value passed in does not meet the interval requirement, the passed-in value is used when **enableVariableFontWeight** of **fontWeightConfigs** is set to **true**; otherwise, the default value is used. |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | No | Font weight configuration. Pass this parameter when variable font weight adjustment (setting fine-grained font weight values that are not integer multiples of 100, such as 220 and 660) or automatic font weight update based on the device font weight level is required. The default value is inherited from [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md). |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

Sets the maximum font scale factor of the SymbolGlyph component. Applicable to scenarios where you need to prevent icons from exceeding the layout container or breaking interface consistency when the user's font scale setting is too large, for example, limiting the maximum display size of icons in a small-sized container.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SymbolGlyphAttribute-maxFontScale(scale: Optional<number|Resource>): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-maxFontScale(scale: Optional<number|Resource>): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Maximum font scale factor of the SymbolGlyph component.<br>Value range: [1, +∞) <br>**Note:** <br>If the set value is less than 1, it is processed as 1. If not set, the maximum scale factor is not limited. |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

Sets the minimum font scale factor of the SymbolGlyph component. Applicable to scenarios where you need to prevent icons from becoming unrecognizable when the user's font scale setting is too small, for example, ensuring that icons maintain a minimum readable size under any system font setting.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SymbolGlyphAttribute-minFontScale(scale: Optional<number|Resource>): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-minFontScale(scale: Optional<number|Resource>): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Minimum font scale factor of the SymbolGlyph component.<br>Value range: [0, 1] <br>When set to 0, the scale is minimized. <br>**Note:** <br>When the set value is less than 0, it is treated as 0. When the set value is greater than 1, it is treated as 1. Invalid values do not take effect by default. When not set, the minimum scale factor is not limited. |

## renderingStrategy

```TypeScript
renderingStrategy(value: SymbolRenderingStrategy)
```

Sets the rendering strategy of the **SymbolGlyph** component. If this API is not used, the default rendering strategy is **SymbolRenderingStrategy.SINGLE**.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md) | Yes | Rendering strategy of the SymbolGlyph component. |

## shaderStyle

```TypeScript
shaderStyle(shader: Array<ShaderStyle | undefined> | ShaderStyle)
```

Applies a gradient or solid color shader effect to the **SymbolGlyph** component.

Can be displayed as a radial gradient [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), a linear gradient [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), or a solid color [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md). The priority of shaderStyle is higher than that of [fontColor](#fontcolor1) and AI recognition. For solid colors, [fontColor](#fontcolor1) is recommended.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SymbolGlyphAttribute-shaderStyle(shader: Array<ShaderStyle | undefined> | ShaderStyle): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-shaderStyle(shader: Array<ShaderStyle | undefined> | ShaderStyle): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | Array&lt;[ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) &#124; undefined&gt; &#124; [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) | Yes | Radial gradient, linear gradient, or solid color. <br>When a ShaderStyle is passed in, it covers all layers. When an array is passed in, if a data item is ShaderStyle, it is applied to that layer; if an array item is undefined, that layer uses the default color of SymbolGlyph, and layers that are not set also use the default color. Based on the passed-in parameter, the radial gradient [RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md), linear gradient [LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md), or solid color [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md) is processed accordingly, and finally set on the SymbolGlyph component to display a gradient color effect. <br>**NOTE:** <br>Use a percentage for the center point. If a non-percentage value (for example, 10PX) is used, the effect is equivalent to setting 1000%. <br>It is recommended to use a percentage for the radius. <br>The percentage is based on the icon size. The recommended value range is [0, 1). |

<a id="symboleffect1"></a>

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean)
```

Sets the effect strategy and playback state of the **SymbolGlyph** component. If this API is not used, the default animation is a **SymbolEffect** object, and the default playback state is **false**.

> **NOTE:** 
> 
> For animation attributes, only the **effectStrategy** attribute or a single **symbolEffect** attribute is
> supported. Mixing multiple animation attributes is not supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md) | Yes | Animation strategy of the SymbolGlyph component. |
| isActive | boolean | No | Playback state of the SymbolGlyph component animation.<br>The value **true** means to play, and **false** means not to play. |

<a id="symboleffect2"></a>

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number)
```

Sets the effect strategy and playback trigger of the **SymbolGlyph** component. If this API is not used, the default animation is a **SymbolEffect** object, and the default trigger value is -1.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolGlyphAttribute-symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md) | Yes | Animation strategy of the SymbolGlyph component. |
| triggerValue | number | No | Trigger for playing the animation of the SymbolGlyph component. The animation is triggered when the value changes.<br>Set this parameter to -1 if you do not want to trigger the animation on the first time. |

## symbolShadow

```TypeScript
symbolShadow(shadow: Optional<ShadowOptions>)
```

Sets the shadow effect of the SymbolGlyph component. When this interface is not used to set the shadow, the default shadow effect is {radius: 0, color: Color.Black, offsetX: 0, offsetY: 0}.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-SymbolGlyphAttribute-symbolShadow(shadow: Optional<ShadowOptions>): SymbolGlyphAttribute--><!--Device-SymbolGlyphAttribute-symbolShadow(shadow: Optional<ShadowOptions>): SymbolGlyphAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shadow | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Shadow effect of the SymbolGlyph component. <br>Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>**Note:** <br>Only the radius, color, offsetX, and offsetY attributes in ShadowOptions are supported. The fill and type attributes and the ColoringStrategy enum values in color are not supported. |
