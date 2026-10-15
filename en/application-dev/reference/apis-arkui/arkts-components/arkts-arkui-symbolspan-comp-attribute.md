# SymbolSpan properties/events

```TypeScript
declare class SymbolSpanAttribute extends CommonMethod<SymbolSpanAttribute>
```

The [universal attributes](arkts-arkui-common-comp.md) are not supported. Only the following attributes are supported.

**Inheritance/Implementation:** SymbolSpanAttribute extends CommonMethod&lt;SymbolSpanAttribute&gt;

**Since:** 11

<!--Device-unnamed-declare class SymbolSpanAttribute extends CommonMethod<SymbolSpanAttribute>--><!--Device-unnamed-declare class SymbolSpanAttribute extends CommonMethod<SymbolSpanAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<SymbolSpanAttribute>)
```

Creates an attribute modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SymbolSpanAttribute-attributeModifier(modifier: AttributeModifier<SymbolSpanAttribute>): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-attributeModifier(modifier: AttributeModifier<SymbolSpanAttribute>): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-common-comp-attributemodifier-i.md)&lt;[SymbolSpanAttribute](arkts-arkui-symbolspan-comp-attribute.md)&gt; | Yes | Modifier for dynamically setting attributes on the current component. |

## effectStrategy

```TypeScript
effectStrategy(value: SymbolEffectStrategy)
```

Sets the effect strategy of the SymbolSpan. If this API is not called, the default effect strategy is SymbolEffectStrategy.NONE.

NONE indicates no effect, which is suitable for static display scenarios. SCALE indicates an overall scaling effect, which is suitable for scenarios that need to attract user attention, such as button click feedback. HIERARCHICAL indicates a hierarchical effect, which is suitable for scenarios where the layered sense of an icon needs to be highlighted.

For the effects of different effect strategies, see [Example 1: Setting Rendering and Animation Strategies](../../../reference/apis-arkui/arkui-ts/ts-basic-components-symbolSpan.md#example-1-setting-rendering-and-animation-strategies).

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolSpanAttribute-effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolEffectStrategy](arkts-arkui-symbolglyph-comp-symboleffectstrategy-e.md) | Yes | Effect strategy of SymbolSpan. |

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor>)
```

Sets the color of the **SymbolSpan** component. If this API is not called, the default color varies with [renderingStrategy](#renderingstrategy). Under the single-color rendering strategy (SINGLE), the default is a single color. Under the multi-color rendering strategy (MULTIPLE_COLOR) and the layered rendering strategy (MULTIPLE_OPACITY), the default is the preset multi-color configuration of the icon resource. For details, see [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md).

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolSpanAttribute-fontColor(value: Array<ResourceColor>): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-fontColor(value: Array<ResourceColor>): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the SymbolSpan component. For details about the specific color rendering modes and their descriptions, see [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md). |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the size of the **SymbolSpan** component. When the value is of the string type, the string form of a number type value is supported, and a unit can be attached, for example, "10" and "10fp". If this API is not called, the default component size is 16fp.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolSpanAttribute-fontSize(value: number | string | Resource): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-fontSize(value: number | string | Resource): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Size of the SymbolSpan component. <br>Value range: [0, +∞) <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

<a id="fontweight1"></a>

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

Sets the font weight of the **SymbolSpan** component. If this API is not called, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

The **sys.symbol.ohos_lungs** icon does not support font weight setting.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolSpanAttribute-fontWeight(value: number | FontWeight | string): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-fontWeight(value: number | FontWeight | string): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string | Yes | Font weight of the SymbolSpan component.<br>For the number type, the value range is [100, 900], with an interval of 100. The default value is 400. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is set too large, the font may be truncated in different fonts. If a value outside the value range or not meeting the interval requirement is passed, the default value is used. |

<a id="fontweight2"></a>

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

Sets the font weight of the SymbolSpan component. It supports configuring, through FontWeightConfigs, whether to enable variable font weight adjustment and whether to automatically update the font weight based on the device font weight level. If this API is not called, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

The sys.symbol.ohos_lungs icon does not support setting fontWeight.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SymbolSpanAttribute-fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the SymbolSpan component.<br>The number type value range is [100, 900], with an interval of 100. The default value is 400. A larger value indicates a heavier font. The string type supports only the string form of the number type values, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. Setting an excessively large value may cause truncation with different fonts. <br>If the value is out of the value range, the default value is used. If the value does not meet the interval requirement, the passed value is used when enableVariableFontWeight of fontWeightConfigs is set to true; otherwise, the default value is used. |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | No | Font weight configuration. Pass this parameter when variable font weight adjustment needs to be enabled (setting a fine-grained font weight value that is not an integer multiple of 100, such as 220 or 660) or when the font weight needs to be automatically updated based on the device font weight level.<br>Default value: { enableVariableFontWeight: false, enableDeviceFontWeightCategory: true } |

## renderingStrategy

```TypeScript
renderingStrategy(value: SymbolRenderingStrategy)
```

Sets the rendering strategy of the SymbolSpan. If this API is not called, the default rendering strategy is SymbolRenderingStrategy.SINGLE.

SINGLE indicates single-color rendering, which is suitable for scenarios where icons with a unified color are required. MULTIPLE_COLOR indicates multi-color rendering, which is suitable for scenarios where multiple layers of an icon need to be displayed in different colors. MULTIPLE_OPACITY indicates layered rendering, which is suitable for scenarios where the layered effect of an icon needs to be displayed.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-SymbolSpanAttribute-renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute--><!--Device-SymbolSpanAttribute-renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md) | Yes | Rendering strategy of SymbolSpan. |
