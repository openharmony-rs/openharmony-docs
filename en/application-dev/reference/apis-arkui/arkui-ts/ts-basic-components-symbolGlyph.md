# SymbolGlyph
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **SymbolGlyph** component displays a preset icon symbol, which supports setting style attributes such as the color, size, thickness, rendering policy, and animation policy. It is applicable to scenarios where system icons need to be displayed in an application, such as the navigation bar icon, button icon, and status indicator icon. Compared with image resources, symbol glyphs have advantages such as small size, dynamic coloring, and support for animations.<!--RP1--><!--RP1End-->

>  **NOTE**
>
> - This component is supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Child Components

Not supported

## APIs

SymbolGlyph(value?: Resource)

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | [Resource](ts-types.md#resource)| No| Resource of the **SymbolGlyph** component, for example, **$r('sys.symbol.ohos_wifi')**. If no value is passed, the symbol is not displayed.|

>  **NOTE**
>
>  The resource referenced in **$r('sys.symbol.ohos_wifi')** is preset in the system. The **SymbolGlyph** component supports only the preset symbol resource names. If a non-symbol resource is referenced, an exception occurs.

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported. For text attributes, only the following attributes are supported.

### fontColor

fontColor(value: Array&lt;ResourceColor&gt;)

Sets the font color of the **SymbolGlyph** component.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| value  | Array\<[ResourceColor](ts-types.md#resourcecolor)\> | Yes  | Font color of the **SymbolGlyph** component.<br> When **value** is set to **undefined**, the default color of the symbol is used. The default color follows the theme.<br>The color setting effect varies depending on the rendering policy. For details, see the enumeration description of [SymbolRenderingStrategy](#symbolrenderingstrategy11).|

### fontColor

fontColor(value: Array&lt;ResourceColor | ColorMetrics&gt; | undefined)

Sets the font color of the **SymbolGlyph** component. Compared with the [fontColor](#fontcolor) API, this API supports the input of parameters of the [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) type.

> **NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Since**: 26.0.0

**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| value  | Array\<[ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)\>&nbsp;\|&nbsp;undefined | Yes  | Font color of the **SymbolGlyph** component. An array of the `ResourceColor` or `ColorMetrics` type can be passed.<br> When **value** is set to **undefined**, the default color of the symbol is used. The default color follows the theme.|

### fontSize

fontSize(value: number | string | Resource)

Sets the font size of the **SymbolGlyph** component. For the string type, numeric string values with optional units, for example, **"10"** or **"10fp"**, are supported.

The display size of the symbol glyph is controlled by the **fontSize** setting. Once **width** or **height** is specified, other universal attributes will only affect the size of the component's placeholder, not the symbol glyph itself. If this API is not used, the default font size is 16 fp.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| value  | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes  | Font size of the **SymbolGlyph** component.<br>Value range: [0, +∞)<br>Unit: [fp](ts-pixel-units.md#basic-pixel-units)<br>Percentage strings are not supported.|

### fontWeight

fontWeight(value: number | FontWeight | string)

Sets the font weight of the **SymbolGlyph** component. If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

The **sys.symbol.ohos_lungs** icon does not support font weight setting.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                               |
| ------ | ------------------------------------------------------------ | ---- | --------------------------------------------------- |
| value  | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;string | Yes  | Font weight of the **SymbolGlyph** component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts.<br>**NOTE**<br>If the input value exceeds the value range, the default value is used. If the input value does not meet the interval requirement, the default value is used (only values that are multiples of 100 integers are supported).|

### fontWeight

fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)

Sets the font weight of the symbol in the **SymbolGlyph** component. You can use **FontWeightConfigs** to configure whether to enable variable font weight adjustment (after this feature is enabled, you can set the fine font weight to a value that is not a multiple of 100 integers, for example, **220** or **660**) and whether to enable the font weight to be updated along with the device's font weight level (after this feature is enabled, the font weight of the component automatically adjusts based on the system font weight setting). If this API is not used, the default font weight is **FontWeight.Normal** (normal weight, corresponding to the value **400**).

**Since**: 26.0.0

**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ---- | ---- | ---- |
| value | number&nbsp;\|&nbsp;[FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;[ResourceStr](ts-types.md#resourcestr) | Yes| Font weight of the symbol in the **SymbolGlyph** component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**. For the string type, only strings of the number type are supported, for example, **"400"**, and **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**. If the value is too large, truncation may occur in different fonts.<br>If the input value exceeds the value range, the default value is used. If the input value does not meet the interval requirements, and **enableVariableFontWeight** of **fontWeightConfigs** is set to **true**, the input value is used. If **enableVariableFontWeight** is set to **false**, the default value is used.|
| fontWeightConfigs | [FontWeightConfigs](ts-text-common.md#fontweightconfigs24)| No| Font weight configurations. This parameter is passed when variable font weight adjustment is required (for example, setting a fine font weight value that is not a multiple of 100, such as 220 or 660) or when the font weight needs to be automatically updated based on the device's font weight setting. The default value is inherited from [FontWeightConfigs](ts-text-common.md#fontweightconfigs24).|

### renderingStrategy

renderingStrategy(value: SymbolRenderingStrategy)

Sets the rendering strategy of the **SymbolGlyph** component. If this API is not used, the default rendering strategy is **SymbolRenderingStrategy.SINGLE**.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| value  | [SymbolRenderingStrategy](#symbolrenderingstrategy11) | Yes  | Rendering strategy of the **SymbolGlyph** component.|

The figure below shows the effects of different rendering strategies.

![renderingStrategy](figures/renderingStrategy.png)

### effectStrategy

effectStrategy(value: SymbolEffectStrategy)

Sets the effect strategy of the **SymbolGlyph** component. If this API is not used, the default effect strategy is **SymbolEffectStrategy.NONE**.

> **NOTE**
>
> - This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.
>
> - When configuring the symbol effect, use the **effectStrategy** attribute or a single **symbolEffect** attribute. Mixing multiple effect attributes is not allowed.
>
> - This API supports only the **NONE**, **SCALE**, and **HIERARCHICAL** preset effect types. After the effect is set, it automatically plays. To use more diverse effect types (such as appearance, disappearance, bounce, replacement, and pulse) or control the playback state and triggering time of the effect, use the [symbolEffect](#symboleffect12) API. The two APIs cannot be used together. For details, see the description of the [symbolEffect](#symboleffect12) API.


**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| value  | [SymbolEffectStrategy](#symboleffectstrategy11) | Yes  | Effect strategy of the **SymbolGlyph** component.|

### symbolEffect<sup>12+</sup>

symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean)

Sets the symbol effect and effect state for the **SymbolGlyph** component. If this API is not used, the default effect is the **SymbolEffect** object, and the default playback state is **false**.

> **NOTE**
>
> When configuring the symbol effect, use the **effectStrategy** attribute or a single **symbolEffect** attribute. Mixing multiple effect attributes is not allowed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| symbolEffect  | [SymbolEffect](#symboleffect12) | Yes  | Effect strategy of the **SymbolGlyph** component.|
| isActive  | boolean | No  | Whether the effect is active.<br>**true**: playing. **false**: not playing.|

### symbolEffect<sup>12+</sup>

symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number)

Sets the symbol effect and effect trigger for the **SymbolGlyph** component. If this API is not used, the default effect is the **SymbolEffect** object, and the default trigger value is **-1**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| symbolEffect | [SymbolEffect](#symboleffect12) | Yes  | Effect strategy of the **SymbolGlyph** component.|
| triggerValue | number | No  | Value that, when changed, initiates the animation of the **SymbolGlyph** component.<br>To prevent the motion effect from triggering initially, set it to **-1**.|

>  **NOTE**
>
>  When configuring the symbol effect, use the **effectStrategy** attribute or a single **symbolEffect** attribute. Mixing multiple effect attributes is not allowed.

### minFontScale<sup>18+</sup>

minFontScale(scale: Optional\<number | Resource>)

Sets the minimum font scale factor for the **SymbolGlyph** component. This API is applicable to scenarios where symbols need to be prevented from becoming unrecognizable when the user's font scale is set too small. For example, it ensures that symbols retain their minimum readable sizes under any system font settings.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| scale  |[Optional](ts-universal-attributes-custom-property.md#optionalt)\<number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)>  | Yes  | Minimum font scale factor for the **SymbolGlyph** component.<br>Value range: [0, 1]<br>The value **0** results in the minimum scaling.<br>**NOTE**<br>A value less than 0 is handled as 0. Values greater than 1 are treated as **1**. Abnormal values are ineffective by default. If this parameter is not set, the minimum scale factor is not limited.  |

### maxFontScale<sup>18+</sup>

maxFontScale(scale: Optional\<number | Resource>)

Sets the maximum font scale factor for the **SymbolGlyph** component. This API is applicable to scenarios where symbols need to be prevented from exceeding the layout container or damaging the UI consistency when the user's font scale is set too large. For example, it can be used to limit the maximum display sizes of symbols in a small-size container.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| scale  |[Optional](ts-universal-attributes-custom-property.md#optionalt)\<number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)>  | Yes  | Maximum font scale factor for the **SymbolGlyph** component.<br>Value range: [1, +∞)<br>**NOTE**<br>Values less than 1 are treated as **1**. If this parameter is not set, the maximum scale factor is not limited.|

### shaderStyle<sup>20+</sup>

shaderStyle(shader: Array\<ShaderStyle | undefined\> | ShaderStyle)

Applies a gradient or solid color shader effect to the **SymbolGlyph** component.

The shader effect can be a radial gradient ([RadialGradientStyle](../arkui-ts/ts-text-common.md#radialgradientstyle20)), linear gradient ([LinearGradientStyle](../arkui-ts/ts-text-common.md#lineargradientstyle20)), or solid color ([ColorShaderStyle](../arkui-ts/ts-text-common.md#colorshaderstyle20)). The priority of **shaderStyle** is higher than that of [fontColor](#fontcolor) and AI recognition. You are advised to use [fontColor](#fontcolor) for solid colors.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                        | Mandatory                            | Description                              |
| -------------- | -------------------------------------------- | ----------------------------------- | ----------------------------------- |
| shader | Array\<[ShaderStyle](../arkui-ts/ts-text-common.md#shaderstyle20) \| undefined\> \| [ShaderStyle](../arkui-ts/ts-text-common.md#shaderstyle20) | Yes| Shader effect.<br>Input types and behavior:<br>Single **ShaderStyle** object: applies the specified effect to all layers. Array of **ShaderStyle** objects: applies the specified effect to the corresponding layer. Array of **undefined**: applies the default **SymbolGlyph** color to the corresponding layer. Layers unset retain their default color.<br> Based on the input, the system applies a radial gradient ([RadialGradientStyle](../arkui-ts/ts-text-common.md#radialgradientstyle20)), linear gradient ([LinearGradientStyle](../arkui-ts/ts-text-common.md#lineargradientstyle20)), or solid color ([ColorShaderStyle](../arkui-ts/ts-text-common.md#colorshaderstyle20)) to the **SymbolGlyph** component.<br>**NOTE**<br>Specify the center point and radius using percentages. If a non-percentage value (e.g., **10px**) is provided, it will be interpreted as 1000%.<br>You are advised to specify the radius using percentages.<br>Percentages are relative to the icon's size. The recommended value range is [0, 1).|

### symbolShadow<sup>20+</sup>

symbolShadow(shadow: Optional\<ShadowOptions\>)

Sets the shadow effect of the **SymbolGlyph** component. If this API is not used, the default shadow effect is **{radius: 0,color: Color.Black,offsetX: 0,offsetY: 0}**.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ------ | ---- | ---- | ----- |
| shadow  |[Optional](ts-universal-attributes-custom-property.md#optionalt)\<[ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)>  | Yes | Shadow effect of the **SymbolGlyph** component.<br>Unit: [vp](ts-pixel-units.md#basic-pixel-units)<br>**NOTE**<br>Only the **radius**, **color**, **offsetX**, and **offsetY** attributes in **ShadowOptions** are supported. The **fill** and **type** attributes and the **ColoringStrategy** enumeration in **color** are not supported.|

## ScaleSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| scope     | [EffectScope](#effectscope12)  |  No  | Yes| Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**   |
| direction | [EffectDirection](#effectdirection12) |  No  | Yes| Effect direction. For details about the enumerated values and their description, see the description of **EffectDirection**.<br>Default value: **EffectDirection.DOWN**|

### constructor<sup>12+</sup>

constructor(scope?: EffectScope, direction?: EffectDirection)

A constructor used to create a **ScaleSymbolEffect** instance, which comes with a scaling animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope     | [EffectScope](#effectscope12)         | No  | Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|
| direction | [EffectDirection](#effectdirection12) | No  | Effect direction. For details about the enumerated values and their description, see the description of **EffectDirection**.<br>Default value: **EffectDirection.DOWN**|

## HierarchicalSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| fillStyle | [EffectFillStyle](#effectfillstyle12) | No  | Yes| Effect fill style.<br>Default value: **EffectFillStyle.CUMULATIVE**|

### constructor<sup>12+</sup>

constructor(fillStyle?: EffectFillStyle)

A constructor used to create a **HierarchicalSymbolEffect** instance, which comes with a hierarchical animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| fillStyle | [EffectFillStyle](#effectfillstyle12) | No  | Effect fill style. For details about the enumerated values and their description, see the description of **EffectFillStyle**.<br>Default value: **EffectFillStyle.CUMULATIVE**|

## AppearSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| scope | [EffectScope](#effectscope12) | No  | Yes| Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|

### constructor<sup>12+</sup>

constructor(scope?: EffectScope)

A constructor used to create an **AppearSymbolEffect** instance, which comes with an appear animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope  | [EffectScope](#effectscope12) | No  | Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|

## DisappearSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| scope | [EffectScope](#effectscope12) | No  | Yes| Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|

### constructor<sup>12+</sup>

constructor(scope?: EffectScope)

A constructor used to create a **DisappearSymbolEffect** instance, which comes with a disappear animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope  | [EffectScope](#effectscope12) | No  | Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|

## BounceSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| scope     | [EffectScope](#effectscope12)         | No  | Yes| Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**   |
| direction | [EffectDirection](#effectdirection12) | No  | Yes| Effect direction. For details about the enumerated values and their description, see the description of **EffectDirection**.<br>Default value: **EffectDirection.DOWN**|

### constructor<sup>12+</sup>

constructor(scope?: EffectScope, direction?: EffectDirection)

A constructor used to create a **BounceSymbolEffect** instance, which comes with a bounce animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope     | [EffectScope](#effectscope12)         | No  | Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**   |
| direction | [EffectDirection](#effectdirection12) | No  | Effect direction. For details about the enumerated values and their description, see the description of **EffectDirection**.<br>Default value: **EffectDirection.DOWN**|

## ReplaceSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Attributes

| Name| Type| Read-Only| Optional| Description |
| ---- | ---- | ---- | ---- | ---- |
| scope | [EffectScope](#effectscope12) | No  | Yes| Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| replaceType<sup>20+</sup>  | [ReplaceEffectType](#replaceeffecttype20) | No  | Yes| Replacement effect type. For details about the enumerated values and their description, see the description of **ReplaceEffectType**.<br>Default value: **ReplaceEffectType.SEQUENTIAL**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

### constructor<sup>12+</sup>

constructor(scope?: EffectScope)

A constructor used to create a **ReplaceSymbolEffect** instance, which comes with a replace animation effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope  | [EffectScope](#effectscope12) | No  | Effect scope. For details about the enumerated values and their description, see the description of **EffectScope**.<br>Default value: **EffectScope.LAYER**|

### constructor<sup>20+</sup>

constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)

A constructor used to create a **ReplaceSymbolEffect** instance, which comes with a replace animation effect. The replace effect type can be specified.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description |
| ---- | ---- | ---- | ---- |
| scope  | [EffectScope](#effectscope12) | No  | Effect scope.<br>Default value: **EffectScope.LAYER**|
| replaceType  | [ReplaceEffectType](#replaceeffecttype20) | No  | Replacement effect type.<br>Default value: **ReplaceEffectType.SEQUENTIAL**|

## SymbolEffectStrategy<sup>11+</sup>

Enumerates symbol effect types. Once applied, the symbol effect becomes active instantly, eliminating the need for triggering.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                         |
| ------ | --- | ----------------------------- |
| NONE | 0 | No effect (default value).|
| SCALE | 1 | Scale effect as a whole.                |
|  HIERARCHICAL  | 2 | Hierarchical effect. |

## SymbolRenderingStrategy<sup>11+</sup>

Enumerates the rendering modes.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description                         |
| ------ | --- | ----------------------------- |
| SINGLE  | 0 | Single-color mode (default value).<br> The default color is black.<br> You can set one or multiple colors, but only the first color will be applied.|
| MULTIPLE_COLOR  | 1 | Multi-color mode.<br> A maximum of three colors can be set. If only one color is set, it updates the color of the first layer, leaving other colors at their default values.<br> The sequence of color settings matches the layering order of the symbol; any colors beyond the number of symbol layers will not take effect.|
|  MULTIPLE_OPACITY   | 2 | Layered mode.<br> The default color is black. You can set one or multiple colors, but only the first color will be applied.<br>Opacity is not related to layers. For a common symbol, the default transparency of the first layer is 100%, the second layer is 50%, and the third layer is 20%. If the specified color includes transparency, the specified transparency is combined with the default transparency of each layer.|

## SymbolEffect<sup>12+</sup>

Defines the **SymbolEffect** class.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## PulseSymbolEffect<sup>12+</sup>

Inherits from **SymbolEffect**.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## EffectDirection<sup>12+</sup>

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value  | Description            |
| ---- | ---- | ---------------- |
| DOWN | 0    | The symbol scales down and then returns to its original size.|
| UP   | 1    | The symbol scales up and then returns to its original size.|

## EffectScope<sup>12+</sup>

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value  | Description      |
| ----- | ---- | ---------- |
| LAYER | 0    | Layered mode.|
| WHOLE | 1    | Whole mode.|

## EffectFillStyle<sup>12+</sup>

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| CUMULATIVE | 0    | Cumulative style.|
| ITERATIVE  | 1    | Iterative style.|

## ReplaceEffectType<sup>20+</sup>

Enumerates symbol replacement effect types.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| SEQUENTIAL | 0    | Sequential replacement: The current symbol disappears before a new symbol appears. This is the default symbol replacement effect type.|
| CROSS_FADE | 1    | Cross-fade transition effect: The current symbol fades out while a new symbol fades in simultaneously.|
| SLASH_OVERLAY | 2    | Slash overlay effect: The current symbol is replaced with a symbol featuring diagonal slash, typically indicating disabled state.|

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

###  Example 1: Setting Rendering and Effect Strategies

This example demonstrates different rendering and effect strategies using [renderingStrategy](#renderingstrategy) and [effectStrategy](#effectstrategy), available since API version 11.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('Light')
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(FontWeight.Lighter)
            .fontSize(96)
        }

        Column() {
          Text('Normal')
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(FontWeight.Normal)
            .fontSize(96)
        }

        Column() {
          Text('Bold')
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(FontWeight.Bold)
            .fontSize(96)
        }
      }

      Row() {
        Column() {
          Text('Monochrome')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.SINGLE)
            .fontColor([Color.Black, Color.Green, Color.White])
        }

        Column() {
          Text('Multicolor')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_COLOR)
            .fontColor([Color.Black, Color.Green, Color.White])
        }

        Column() {
          Text('Multilayer')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
            .fontColor([Color.Black, Color.Green, Color.White])
        }
      }

      Row() {
        Column() {
          Text('No effect')
          SymbolGlyph($r('sys.symbol.ohos_wifi'))
            .fontSize(96)
            .effectStrategy(SymbolEffectStrategy.NONE)
        }

        Column() {
          Text('Overall scale effect')
          SymbolGlyph($r('sys.symbol.ohos_wifi'))
            .fontSize(96)
            .effectStrategy(SymbolEffectStrategy.SCALE)
        }

        Column() {
          Text('Hierarchical effect')
          SymbolGlyph($r('sys.symbol.ohos_wifi'))
            .fontSize(96)
            .effectStrategy(SymbolEffectStrategy.HIERARCHICAL)
        }
      }
    }
  }
}
```
![symbol](figures/symbolGlyph.gif)

###  Example 2: Setting Symbol and Shadow Effects

This example demonstrates various symbol effects using the [symbolEffect](#symboleffect12) attribute (available since API version 12) and shadow effects with [symbolShadow](#symbolshadow20) (available since API version 20). The slash overlay and cross-fade transition are supported since API version 20.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State isActive: boolean = true;
  @State triggerValueReplace: number = 0;
  @State triggerValueReplace1: number = 0;
  @State triggerValueReplace2: number = 0;
  @State renderMode: SymbolRenderingStrategy = SymbolRenderingStrategy.MULTIPLE_COLOR;

  replaceFlag: boolean = true;
  replaceFlag1: boolean = true;
  replaceFlag2: boolean = true;

  options: ShadowOptions = {
    radius: 10.0,
    color: Color.Blue,
    offsetX: 10,
    offsetY: 10,
  };

  build() {
    Column() {
      Row() {
        Column() {
          Text('Variable color effect')
          SymbolGlyph($r('sys.symbol.ohos_wifi'))
            .fontSize(96)
            .symbolEffect(new HierarchicalSymbolEffect(EffectFillStyle.ITERATIVE), this.isActive)
          Button(this.isActive ? 'Stop' : 'Play')
            .onClick(() => {
              this.isActive = !this.isActive;
            })
        }
        .margin({ right: 20 })
        Column() {
          Text('Replacement effect')
          SymbolGlyph(this.replaceFlag ? $r('sys.symbol.checkmark_circle') : $r('sys.symbol.repeat_1'))
            .fontSize(96)
            .symbolEffect(new ReplaceSymbolEffect(EffectScope.WHOLE), this.triggerValueReplace)
          Button('trigger')
            .onClick(() => {
              this.replaceFlag = !this.replaceFlag;
              this.triggerValueReplace = this.triggerValueReplace + 1;
            })
        }
        .margin({ right: 20 })
      }

      Row() {
        Column() {
          Text('Slash overlay')
          SymbolGlyph(this.replaceFlag1 ? $r('sys.symbol.eye_slash') : $r('sys.symbol.eye'))
            .fontSize(96)
            .renderingStrategy(this.renderMode)
            .symbolEffect(new ReplaceSymbolEffect(EffectScope.LAYER, ReplaceEffectType.SLASH_OVERLAY), this.triggerValueReplace1)
          Button('trigger')
            .onClick(() => {
              this.replaceFlag1 = !this.replaceFlag1;
              this.triggerValueReplace1 = this.triggerValueReplace1 + 1;
            })
        }
        .margin({ right: 20 })
        Column() {
          Text('Cross-fade transition')
          SymbolGlyph(this.replaceFlag2 ? $r('sys.symbol.checkmark_circle') : $r('sys.symbol.repeat_1'))
            .fontSize(96)
            .symbolEffect(new ReplaceSymbolEffect(EffectScope.WHOLE, ReplaceEffectType.CROSS_FADE), this.triggerValueReplace2)
          Button('trigger')
            .onClick(() => {
              this.replaceFlag2 = !this.replaceFlag2;
              this.triggerValueReplace2 = this.triggerValueReplace2 + 1;
            })
        }
        .margin({ right: 20 })
        Column() {
          Text('Shadow effect')
          SymbolGlyph($r('sys.symbol.ohos_wifi'))
            .fontSize(96)
            .symbolEffect(new HierarchicalSymbolEffect(EffectFillStyle.ITERATIVE), this.isActive)
            .symbolShadow(this.options)
          Button(this.isActive ? 'Stop' : 'Play')
            .onClick(() => {
              this.isActive = !this.isActive;
            })
        }
        .margin({ right: 20 })
      }
    }
    .margin({
      left: 45,
      top: 50
    })
  }
}
```
![symbol](figures/SymbolGlyph_Example2.gif)

### Example 3: Setting Gradient Color Effects

This example demonstrates how to apply gradient colors to **SymbolGlyph** components using the [shaderStyle](#shaderstyle20) API, available since API version 20.

```ts
@Entry
@Component
struct Index {

  linearGradientOptions1: LinearGradientOptions = {
    angle: 45,
    colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]]
  };

  linearGradientOptions2: LinearGradientOptions = {
    direction: GradientDirection.LeftTop,
    colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
    repeating: true,
  };

  radialGradientOptions: RadialGradientOptions = {
    center: ['50%', '50%'],
    radius: '20%',
    colors: [[Color.Red, 0.0], [Color.Blue, 0.3], [Color.Green, 0.5]],
    repeating: true,
  };

  build() {
    Column() {
      Row() {
        Column() {
          Text('Linear gradient with 45° angle')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([new LinearGradientStyle(this.linearGradientOptions1)])
        }
        .margin({ right: 20 })
        Column() {
          Text('Linear gradient from LeftTop')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([new LinearGradientStyle(this.linearGradientOptions2)])
        }
        .margin({ right: 20 })
      }

      Row() {
        Column() {
          Text('Radial gradient')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([new RadialGradientStyle(this.radialGradientOptions)])
        }
        .margin({ right: 20 })
        Column() {
          Text('Solid color')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([new ColorShaderStyle(Color.Red)])
        }
        .margin({ right: 20 })
        Column() {
          Text('Linear and radial gradient')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([
              new LinearGradientStyle(this.linearGradientOptions2),
              new LinearGradientStyle(this.linearGradientOptions2),
              new RadialGradientStyle(this.radialGradientOptions)
            ])
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
        }
        .margin({ right: 20 })
      }

      Row() {
        Column() {
          Text('Single-layer array gradient')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([
              new LinearGradientStyle(this.linearGradientOptions2),
            ])
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
        }.margin({ right: 20 })

        Column() {
          Text('Non-array covers all')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle(new RadialGradientStyle(this.radialGradientOptions))
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
        }.margin({ right: 20 })

        Column() {
          Text('First layer is default')
            .fontSize(18)
            .fontColor(0xCCCCCC)
            .textAlign(TextAlign.Center)
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .shaderStyle([
              undefined,
              new LinearGradientStyle(this.linearGradientOptions2),
            ])
            .renderingStrategy(SymbolRenderingStrategy.MULTIPLE_OPACITY)
        }.margin({ right: 20 })
      }
    }
    .margin({
      left: 20,
      top: 50
    })
  }
}
```
![symbol](figures/SymbolGlyph_Example3.jpeg)

### Example 4: Setting the Color for the SymbolGlyph Component

This example demonstrates how to use the [fontColor](#fontcolor-1) attribute to pass a parameter of the [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) type to set the color of the **SymbolGlyph** component.

[fontColor](#fontcolor-1) is supported since API version 26.0.0.

```ts
// xxx.ets
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  blueColor: ColorMetrics[] = [ColorMetrics.resourceColor(Color.Blue)];
  greenColor: ColorMetrics[] = [ColorMetrics.numeric(0x00FF00)];
  blackColor: ColorMetrics[] = [ColorMetrics.rgba(0, 0, 0, 1.0)];

  build() {
    Column() {
      Row({ space: 20 }) {
        Column() {
          Text('resourceColor blue')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.SINGLE)
            .fontColor(this.blueColor)
        }

        Column() {
          Text('numeric green')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.SINGLE)
            .fontColor(this.greenColor)
        }

        Column() {
          Text('rgba black')
          SymbolGlyph($r('sys.symbol.ohos_folder_badge_plus'))
            .fontSize(96)
            .renderingStrategy(SymbolRenderingStrategy.SINGLE)
            .fontColor(this.blackColor)
        }
      }.width('100%')
    }.width('100%')
  }
}
```

![symbol](figures/SymbolGlyph_Example4.jpeg)

### Example 5: Setting the Font Weight

This example shows how to use the [fontWeight](#fontweight-1) attribute to display the effects of **SymbolGlyph** with different font weights. The symbol in the first line displays the effect of setting the font weight to 220 and 660 after the variable font weight is enabled. The symbol in the second line displays the effect of automatically updating or not updating the font weight after the system font weight is set to bold.

The [fontWeight](#fontweight-1) attribute is added since API version 26.0.0.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Column() {
          Text('font weight: 220')
          // ohos_trash is the trash can symbol preset by the system.
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(220, { enableVariableFontWeight: true })
            .fontSize(96)
        }
        Column() {
          Text('            ')
        }
        Column() {
          Text('font weight: 660')
          // ohos_trash is the trash can symbol preset by the system.
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(660, { enableVariableFontWeight: true })
            .fontSize(96)
        }
      }
      Row() {
        Text('    ')
      }
      Row() {
        Text('After set system text weight: Bold')
      }
      Row() {
        Column() {
          Text('device category: true')
          // ohos_trash is the trash can symbol preset by the system.
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: true })
            .fontSize(96)
        }
        Column() {
          Text('    ')
        }
        Column() {
          Text('device category: false')
          // ohos_trash is the trash can symbol preset by the system.
          SymbolGlyph($r('sys.symbol.ohos_trash'))
            .fontWeight(FontWeight.Normal, { enableDeviceFontWeightCategory: false })
            .fontSize(96)
        }
      }
    }
  }
}
```

![symbolGlyphFontWeightConfigs](figures/symbolGlyphFontWeightConfigs.png)
