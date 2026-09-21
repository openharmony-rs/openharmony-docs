# ChipOptions

```TypeScript
export interface ChipOptions
```

Defines the style and specific style parameters of the **Chip** component.

> **NOTE:** 
> 
> 1. When **suffixSymbol** is provided with an argument, **suffixIcon** and **allowClose** will not take effect. If
> **suffixSymbol** is not provided, but **suffixIcon** is, **allowClose** will not take effect. If neither
> **suffixSymbol** nor **suffixIcon** is provided, **allowClose** determines whether to display the close icon.
> 
> 2. When **backgroundColor** and **activatedBackgroundColor** are set to **undefined**, the default background color is displayed. When they are set to invalid values, the background color is transparent.
> 
> 3. When an icon is set for **prefixSymbol** or **suffixSymbol**, if the chip is in the inactive state, the icon color **fontColor** is `[$r('sys.color.ohos_id_color_secondary')]`; if the chip is in the activated state, the icon color **fontColor** is `[$r('sys.color.ohos_id_color_text_primary_contrary')]`. In addition, when **size** is
> **ChipSize.SMALL**, the default font size of the icon is `$r('sys.float.chip_small_icon_size')`; when **size** is
> **ChipSize.NORMAL** or a custom size, the default font size of the icon is `$r('sys.float.chip_normal_icon_size')`.
> 
> 4. When icons are set for **prefixIcon** and **suffixIcon**, the default value of **fillColor** is `$r('sys.color.chip_usually_icon_color')`. The color parsing of **fillColor** is consistent with that of the
> **Image** component.
> 
> 5. When icons are set for **prefixIcon** and **suffixIcon**, the default value of **activatedFillColor** is `$r('sys.color.chip_active_icon_color')`. The color parsing of **activatedFillColor** is consistent with that of the **Image** component.
> 
> 6. Starting from API version 26.0.0, when **backgroundSystemMaterial** is configured as an auto-invert material,the fill color of **prefixIcon** and **suffixIcon**, as well as the text color of **prefixSymbol** and
> **suffixSymbol** in the inactive state, will use system resources that support color inversion. These colors will
> automatically match the inversion effect based on the background material. When
> **activatedBackgroundSystemMaterial** is configured as an auto-invert material, the activated fill color of
> **prefixIcon** and **suffixIcon**, as well as the text color of **prefixSymbol** and **suffixSymbol** in the
> activated state, will also use system resources that support color inversion, achieving automatic adaptation to the
> background material inversion.

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

Default close icon tap event callback. It has no parameters or return value. This callback is triggered when the user taps the default close icon.

If the value is **undefined**, the close icon tap event is not triggered.

**Note:** This takes effect only when the close icon is displayed, that is, when neither **suffixSymbol** nor **suffixIcon** has a value passed in and **allowClose** is **true**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the Chip component. This is used to explain the current component to users in detail. Developers should provide detailed text descriptions to help users understand the operations to be performed and their results, especially when these results cannot be directly learned from the component attributes and accessibility text alone. If a component has both a text attribute and an accessibility description attribute, when the component is selected, the system first reads out the text attribute of the component, followed by the content of the accessibility description attribute.

Default value: empty string

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

Accessibility level of the Chip component. This parameter controls whether the Chip component can be recognized by accessibility services.

Supported values:

**"auto"**: The attribute value of the component is converted to **"yes"**.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.

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

Whether the Chip is in the activated state.

Default value: **false**

**true**: The Chip is in the activated state; **false**: The Chip is in the non-activated state.

If the value is **undefined**, the default value is used.

**Usage scenario**: Commonly used in tag selection scenarios to indicate the currently selected item.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ResourceColor
```

Background color of the Chip in the activated state.

Default value: **$r('sys.color.ohos_id_color_emphasize')**

If the value is **undefined**, the default value is used. If an invalid value is assigned, the background color is transparent.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
activatedBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component in the activated state. It is suitable for interactive scenarios where the material effect needs to be maintained or switched in the activated state, such as tag selection and state switching. Different materials have different effects and can affect visual attributes such as [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) of the component.

Default value: **undefined**

If the value is **undefined**, no material style is applied.

**Note:** When **activatedBackgroundSystemMaterial** is set, **activatedBackgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material. When **activatedBackgroundSystemMaterial** is **undefined**, the **activatedBackgroundColor** attribute takes effect.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

Whether the close icon is displayed.

Default value: **true**

**true**: The close icon is displayed; **false**: The close icon is not displayed.

If the value is **undefined**, the default value is used.

**Note:** When **suffixSymbol** has a value passed in, **allowClose** does not take effect. When **suffixSymbol** has no value passed in but **suffixIcon** does, **allowClose** does not take effect. When neither **suffixSymbol** nor **suffixIcon** has a value passed in, **allowClose** determines whether the close icon is displayed.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the Chip.

Default value: **$r('sys.color.ohos_id_color_button_normal')**

If the value is **undefined**, the default value is used. If an invalid value is assigned, the background color is transparent.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. It is suitable for scenarios such as immersive background effects and semi- transparent frosted glass effects. Different materials have different effects and can affect visual attributes such as [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) of the component.

Default value: **undefined**

If the value is **undefined**, no material style is applied.

**Note:** When **backgroundSystemMaterial** is set, **backgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material. When **backgroundSystemMaterial** is **undefined**, the **backgroundColor** attribute takes effect.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension
```

Corner radius of the Chip background. Percentage is not supported. If a percentage is passed in, the default value is used.

Value range: [0, +∞)

Default value: **$r('sys.float.ohos_id_corner_radius_button')**

Unit: vp

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

Functional attributes of the default close icon, including accessibility reading and font size attributes. This takes effect only when the default close icon is displayed, that is, when **allowClose** is **true** and neither **suffixSymbol** nor **suffixIcon** has a value passed in.

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

**Usage scenario**: Commonly used in internationalization scenarios to adapt to right-to-left (RTL) reading habits, such as Arabic, achieving a mirrored interface effect.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the Chip is available.

Default value: **true**

**true**: The Chip is available; **false**: The Chip is unavailable.

**Usage scenario**: Set to **false** to disable the Chip. This is suitable for scenarios where user operations need to be prohibited, such as restricted permissions, incomplete data loading, or unmet conditions.

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

Uniform font size for the text and icons of the **Chip** component. Percentage is not supported. If a percentage is passed in, the default value is used.

The priority of this **fontSize** is lower than the **fontSize** attributes in **prefixSymbol**, **label**, **suffixSymbol**, and **closeOptions**.

Default values:

- When **size** is **ChipSize.SMALL**, text: `$r('sys.float.chip_small_font_size')`; icon:  
`$r('sys.float.chip_small_icon_size')`  
- In other cases, text: `$r('sys.float.chip_normal_font_size')`; icon: `$r('sys.float.chip_normal_icon_size')`

Unit: fp

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

Text content and style displayed on the Chip component.

**Type:** [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale?: number | Resource
```

Maximum font scale factor for the text and icons of the **Chip** component.

Value range: [1, +∞)

If the set value is less than 1, the value 1 is used. Abnormal values do not take effect by default.

Default value: **1**

If the value is **undefined**, the default value is used.

**Usage scenario**: Suitable for accessibility scenarios where the upper limit of font scaling needs to be restricted, preventing layout overflow caused by excessively large fonts.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
minFontScale?: number | Resource
```

Minimum font scale factor for the text and icons of the **Chip** component.

**Value range:** [0, 1]

If the set value is less than 0, the value 0 is used. If the set value is greater than 1, the value 1 is used. Abnormal values do not take effect by default.

Default value: **1**

If the value is **undefined**, the default value is used.

**Usage scenario**: Suitable for scenarios where the lower limit of font scaling needs to be restricted, ensuring text readability.

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
onClicked?: Callback<void>
```

Tap event callback of the **Chip** component. It has no parameters or return value. This callback is triggered when the user taps the **Chip** component.

If the value is **undefined**, the **Chip** cannot be tapped.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: LocalizedPadding
```

Padding of the Chip component.

Default values:

- When **size** is **ChipSize.SMALL** and **activated** is **true**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- When **size** is **ChipSize.SMALL** and **activated** is **false**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- When **size** is not **ChipSize.SMALL** and **activated** is **true**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`  
- When **size** is not **ChipSize.SMALL** and **activated** is **false**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`

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

Prefix icon of the Chip component, displayed on the left side of the component.

Default value: No prefix icon is displayed

If the value is **undefined**, the default value is used.

When both **prefixIcon** and **prefixSymbol** are set, **prefixSymbol** takes effect and **prefixIcon** is ignored.

**Type:** [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

Prefix icon attribute, of the symbol type. Commonly used in scenarios requiring system standard icons or dynamic icon effects.

Default value: No prefix icon is displayed

If the value is **undefined**, the default value is used.

When both **prefixIcon** and **prefixSymbol** are set, **prefixSymbol** takes effect and **prefixIcon** is ignored.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Size of the **Chip**.

Default value: **ChipSize.NORMAL**

**Usage scenario**: **ChipSize.NORMAL** is suitable for common scenarios; **ChipSize.SMALL** is suitable for compact layout scenarios, such as tag lists and filter bars; custom **SizeOptions** is suitable for scenarios requiring specific sizes.

The **SizeOptions** type does not support percentage settings. Abnormal values are processed as the default value.

**Note:** [Aging adaptation](../../../ui/arkui-support-for-aging-adaptation.md) does not take effect when **size** specifies specific width and height, except when **size** is set to **{ height: 0, width: 0 }**.

**Type:** [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) &#124; [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: SuffixIconOptions
```

Suffix icon of the Chip component, displayed on the right side of the component.

Default value: No suffix icon is displayed

If the value is **undefined**, the default value is used.

When both **suffixIcon** and **suffixSymbol** are set, **suffixSymbol** takes effect and **suffixIcon** is ignored.

**Type:** [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

Suffix icon attribute, of the symbol type. Commonly used in scenarios requiring system standard icons or dynamic icon effects.

Default value: No suffix icon is displayed

If the value is **undefined**, the default value is used.

When both **suffixIcon** and **suffixSymbol** are set, **suffixSymbol** takes effect and **suffixIcon** is ignored.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

Accessibility reading function attributes and tap event callback of the symbol-type suffix icon.

Default value: No corresponding attribute is set

If the value is **undefined**, the default value is used.

**Type:** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
