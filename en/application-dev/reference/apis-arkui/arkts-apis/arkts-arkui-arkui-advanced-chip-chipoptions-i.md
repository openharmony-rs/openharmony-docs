# ChipOptions

Defines the type and style parameters of the chip.

> **NOTE:** 
> 
> 1. When **suffixSymbol** is provided with an argument, **suffixIcon** and **allowClose** will not take effect. If
> **suffixSymbol** is not provided, but **suffixIcon** is, **allowClose** still will not take effect. When neither
> **suffixSymbol** nor **suffixIcon** is provided with arguments, **allowClose** determines whether the deletion icon
> is displayed.
> 
> 2. If **undefined** is assigned to **backgroundColor** or **activatedBackgroundColor**, the default background color is used. If an invalid value is specified, the background color is transparent.
> 
> 3. Default font colors for **prefixSymbol** and **suffixSymbol**: **normalFontColor**:
> **[&#36;r('sys.color.ohos_id_color_primary')]**; **activatedFontColor**:
> **[&#36;r('sys.color.ohos_id_color_text_primary_contrary')]**. The default value of **fontColor** is **16**.
> 
> 4. The default value of **fillColor** is **&#36;r('sys.color.ohos_id_color_secondary')** for **prefixIcon** and
> **&#36;r('sys.color.ohos_id_color_primary')** for **suffixIcon**. The color parsing of **fillColor** is the same as
> that of the **Image** component.
> 
> 5. The default value of **activatedFillColor** in **prefixIcon** and **suffixIcon** is
> **&#36;r('sys.color.ohos_id_color_text_primary_contrary')**. The color parsing of **activatedFillColor** is the same as
> that of the **Image** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## onClose

```TypeScript
onClose?: () => void
```

Event triggered when the close icon is clicked.

If the value is **undefined**, clicking the close icon will not trigger any event.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessible description of the chip. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.

The default value is an empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the chip. It determines whether the component can be recognized by accessibility services.

The options are as follows:

**"auto"**: It is treated as "yes" by the system.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** "auto"

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
accessibilitySelectedType?: AccessibilitySelectedType
```

Type of selected state for the chip.

Default value:

If the **activated** property is set but **accessibilitySelectedType** is not specified, the default type is **CHECKED**. If the **activated** property is not set, the default type is **CLICKED**.

If the value is **undefined**, the default value is used.

**Type:** [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
activated?: boolean
```

Whether the chip is activated.

Default value: **false**

**true**: The chip is activated.

**false**: The chip is not activated.

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ResourceColor
```

Background color of the chip when it is activated.

Default value: **&#36;r('sys.color.ohos_id_color_emphasize')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
activatedBackgroundSystemMaterial?: uiMaterial.Material
```

Set system-styled materials for the component which is activated. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of the component.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

Whether to display the close icon.

Default value: **true**

The value **true** means to show the delete icon, and **false** means the opposite.

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Chip background color.

Default value: **&#36;r('sys.color.ohos_id_color_button_normal')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

Set system-styled materials for the component. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of the component.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension
```

Radius of the rounded corner of the chip background. Percentage is not supported.

Default value: **&#36;r('sys.float.ohos_id_corner_radius_button')**

If the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

Accessibility settings of the default close icon.

If the value is **undefined**, the default value is used.

**Type:** [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction.

Default value: **Direction.Auto**

If the value is **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the chip can be selected.

Default value: **true**

**true**: The chip can be selected.

**false**: The chip cannot be selected.

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

Uniform font size for both text and icons in the chip. Percentage values are not supported.

The priority of **fontSize** is lower than the **fontSize** property in **prefixSymbol**, **label**, **suffixSymbol**, and **closeOptions**.

Default value:

- When **size** is **ChipSize.SMALL**: **&#36;r('sys.float.chip_small_font_size')** for text and  
**&#36;r('sys.float.chip_small_icon_size')** for icons.  
- Other cases: **&#36;r('sys.float.chip_normal_font_size')** for text and **&#36;r('sys.float.chip_normal_icon_size')** for  
icons.

If the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: LabelOptions
```

Text of the chip.

**Type:** [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale?: number | Resource
```

Maximum font scale factor for the text and icon of the chip. Value range: [1, +∞).

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
minFontScale?: number | Resource
```

Minimum font scale factor for the text and icon of the chip. Value range: [0, 1].

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
onClicked?: Callback<void>
```

Chip click event.

If the value is **undefined**, the chip cannot be clicked.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: LocalizedPadding
```

Padding of the chip.

Default value:

- When **size** is **ChipSize.SMALL** and **activated** is **true**:  
**{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}**.  
- When **size** is **ChipSize.SMALL** and **activated** is **false**:  
**{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}**.  
- When **size** is not **ChipSize.SMALL** and **activated** is **true**:  
**{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}**.  
- When **size** is not **ChipSize.SMALL** and **activated** is **false**:  
**{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}**.

If the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: PrefixIconOptions
```

Prefix icon of the chip.

Default value: The prefix icon is not displayed.

If the value is **undefined**, the default value is used.

If both **prefixIcon** and **prefixSymbol** are set, the effect specified by **prefixSymbol** will be displayed, and **prefixIcon** will be ignored.

**Type:** [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

Symbol-type prefix icon of the chip.

Default value: The prefix icon is not displayed.

If the value is **undefined**, the default value is used.

If both **prefixIcon** and **prefixSymbol** are set, the effect specified by **prefixSymbol** will be displayed, and **prefixIcon** will be ignored.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Chip size.

Default value: **ChipSize.NORMAL**

The SizeOptions type parameter does not support percentage values. If an invalid value is provided, the system will use the default value instead.

Note: [Aging-friendly design implementation](../../../ui/arkui-support-for-aging-adaptation.md) does not take effect when size specifies specific width and height, except when size is set to { height: 0, width: 0 }.

**Type:** [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) &#124; [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: SuffixIconOptions
```

Suffix icon of the chip.

Default value: The suffix icon is not displayed.

If the value is **undefined**, the default value is used.

If both **suffixIcon** and **suffixSymbol** are set, the effect specified by **suffixSymbol** will be displayed, and **suffixIcon** will be ignored.

**Type:** [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

Symbol-type suffix icon of the chip.

Default value: The suffix icon is not displayed.

If the value is **undefined**, the default value is used.

If both **suffixIcon** and **suffixSymbol** are set, the effect specified by **suffixSymbol** will be displayed, and **suffixIcon** will be ignored.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

Accessibility settings of the symbol-type suffix icon.

Default value: The suffix icon is not displayed.

If the value is **undefined**, the default value is used.

**Type:** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
