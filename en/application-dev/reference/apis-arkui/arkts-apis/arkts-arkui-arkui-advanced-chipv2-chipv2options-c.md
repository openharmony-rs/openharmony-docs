# ChipV2Options

```TypeScript
export declare class ChipV2Options
```

Defines the style and specific style parameters of the **ChipV2** component.

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: IChipV2OptionsConfig)
```

A constructor used to create a **ChipV2Options** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [IChipV2OptionsConfig](arkts-arkui-arkui-advanced-chipv2-ichipv2optionsconfig-i.md) | Yes | Style configuration of **ChipV2**, which is used to customize the appearance and behavior of the **ChipV2** component, including configuration options such as **label**, **prefixIcon**, **suffixIcon**, **allowClose**, **activated**, and **backgroundColor**. |

## onClose

```TypeScript
public onClose?: VoidCallback
```

Callback for the default close icon tap event.

When **allowClose** is **true** and no value is passed to **suffixIcon**, this callback is invoked when the close icon is tapped.

Default value: The callback is not executed.

If the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description of the **ChipV2** component. This description is used to explain the current component to users in detail. You should provide a thorough text description for this attribute to help users understand the operation to be performed and its possible results, especially when such results cannot be directly inferred from the component's attributes and accessibility text. When the component that is selected has both a text attribute and an accessibility description attribute, the system first reads the text attribute, followed by the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

Accessibility level of the **ChipV2** component. This parameter controls whether the component can be recognized by accessibility services.

Supported values:

**"auto"**: The attribute value of the component is converted to **"yes"**.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** string

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
public accessibilitySelectedType?: ChipV2AccessibilitySelectedType
```

Selected state type of the **ChipV2** component.

Default value: When the **activated** attribute is **true** but **accessibilitySelectedType** is not specified, the **CHECKED** type is used by default. When the **activated** attribute is **false** or not set, the **CLICKED** type is used by default.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [ChipV2AccessibilitySelectedType](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
public activated?: boolean
```

Whether **ChipV2** is activated.

Default value: **false**

**true**: **ChipV2** is activated. **false**: **ChipV2** is not activated.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
public activatedBackgroundColor?: ColorMetrics
```

Background color of **ChipV2** when activated.

Default value: **$r('sys.color.chip_container_activated_color')**

If the value is **undefined**, the default value is used.

If the value is invalid, the background color is transparent.

**Decorator:** @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
public activatedBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the activated component. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, meaning no material style is applied.

**Decorator:** @Trace

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
public allowClose?: boolean
```

Whether to display the close icon.

When a value is passed in **suffixIcon**, **allowClose** does not take effect. When no value is passed in **suffixIcon**, **allowClose** determines whether the close icon is displayed.

Default value: **true**

**true**: Display the close icon. **false**: The close icon is not displayed.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
public backgroundColor?: ColorMetrics
```

Background color of **ChipV2**.

Default value: **$r('sys.color.chip_background_color')**

If the value is **undefined**, the default value is used.

If the value is invalid, the background color is transparent.

**Decorator:** @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
public backgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, meaning no material style is applied.

**Decorator:** @Trace

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
public borderRadius?: LengthMetrics
```

Rounded corner radius of the **ChipV2** background. Percentage values are not supported. If a percentage value is passed, the default value is used.

Default values:

When **size** is **ChipV2Size.NORMAL**, the default **borderRadius** is **$r('sys.float.chip_border_radius_normal')**.

When **size** is **ChipV2Size.SMALL**, the default **borderRadius** is **$r('sys.float.chip_border_radius_small')**.

Unit: vp

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
public closeIcon?: ChipV2CloseIcon
```

Configuration of the close icon, including accessibility configuration. Set this attribute when you need to customize the size or accessibility of the close icon.

Default values:

- Default size: When **size** is **ChipV2Size.SMALL**, the default value is `$r('sys.float.chip_small_font_size')`.  
In other cases, the default value is `$r('sys.float.chip_normal_font_size')`.  
- Default accessibility: No accessibility description.

**fontSize** does not support percentage setting. If an invalid value is passed, the default value will be used.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [ChipV2CloseIcon](arkts-arkui-arkui-advanced-chipv2-chipv2closeicon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
public direction?: Direction
```

Layout direction.

Default value: **Direction.Auto**

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
public enabled?: boolean
```

Whether **ChipV2** is available.

Default value: **true**

**true**: **ChipV2** is available. **false**: **ChipV2** is unavailable.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
public fontSize?: LengthMetrics
```

Uniformly sets the font size of the text and icons of the **ChipV2** component. Percentage values are not supported. If a percentage value is passed, the default value is used.

The priority of this **fontSize** is lower than that of the **fontSize** attributes in **prefixIcon**, **label**, **suffixIcon**, and **closeIcon**.

Default values:

- When **size** is **ChipV2Size.SMALL**, the default text value is `$r('sys.float.chip_small_font_size')`, and the  
default icon value is `$r('sys.float.chip_small_icon_size')`.  
- In other cases, the default text value is `$r('sys.float.chip_normal_font_size')`, and the default icon value is  
`$r('sys.float.chip_normal_icon_size')`.

Unit: fp

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
public label: ChipV2Label
```

Text of **ChipV2**.

**Decorator:** @Trace

**Type:** [ChipV2Label](arkts-arkui-arkui-advanced-chipv2-chipv2label-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
public maxFontScale?: number | Resource
```

Maximum font scale factor for the text and icons of the **ChipV2** component.

Value range: [1, +∞)

If the set value is less than 1, the value **1** is used. Abnormal values do not take effect by default.

Default value: **1**

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
public minFontScale?: number | Resource
```

Minimum font scale factor for the text and icons of the **ChipV2** component.

Value range: [0, 1]

If the set value is less than 0, the value **0** is used. If the set value is greater than 1, the value **1** is used. Abnormal values do not take effect by default.

Default value: **1**

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** number &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
public onClicked?: Callback<void>
```

Callback for the **ChipV2** tap event.

When **enabled** is **true**, tapping **ChipV2** triggers the tap event. When **enabled** is **false**, the tap event is not triggered.

Default value: The callback is not executed.

If the value is **undefined**, the default value is used.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
public padding?: LocalizedPadding
```

Padding of the **ChipV2** component.

Default values:

- When **size** is **ChipV2Size.SMALL** and **activated** is **true**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`.  
- When **size** is **ChipV2Size.SMALL** and **activated** is **false**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`.  
- When **size** is not **ChipV2Size.SMALL** and **activated** is **true**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`.  
- When **size** is not **ChipV2Size.SMALL** and **activated** is **false**, the default value is:  
`{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`.

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
public prefixIcon?: ChipV2Icon
```

Prefix icon of **ChipV2**.

Default value: no prefix icon is displayed.

If the value is **undefined**, the default value is used.

For the symbol icon, the default **fontColor** values are as follows: **normalFontColor**: `[$r('sys.color.chip_usually_icon_color')]`, **activatedFontColor**: `[$r('sys.color.chip_active_icon_color')]`. The default **fontSize** is 16.

For the image icon, the default **fillColor** is `$r('sys.color.chip_usually_icon_color')`, and the default **activatedFillColor** is `$r('sys.color.chip_active_icon_color')`. The color parsing of **fillColor** and **activatedFillColor** is consistent with that of the **Image** component. The **fillColor** and **activatedFillColor** attributes take effect only when the image format is SVG; for non-SVG images, the default values are not applied.

**Decorator:** @Trace

**Type:** [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: ChipV2Size | SizeT<LengthMetrics>
```

Size of **ChipV2**.

Default value: **ChipV2Size.NORMAL**

The **SizeT&lt;LengthMetrics&gt;** type does not support percentage setting. If an invalid value is passed, the default value will be used.

**NOTE:** 

[Aging-friendly design](../../../ui/arkui-support-for-aging-adaptation.md) does not take effect when **size** specifies a specific width and height, except when **size** is set to **{ height: 0, width: 0 }**.

**Decorator:** @Trace

**Type:** [ChipV2Size](arkts-arkui-arkui-advanced-chipv2-chipv2size-e.md) &#124; [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
public suffixIcon?: ChipV2Icon
```

Suffix icon of **ChipV2**.

Default value: no suffix icon is displayed.

If the value is **undefined**, the default value is used.

Note: When a value is passed in **suffixIcon**, the **allowClose** attribute does not take effect.

For the symbol icon, the default **fontColor** values are as follows: **normalFontColor**: `[$r('sys.color.chip_usually_icon_color')]`, **activatedFontColor**: `[$r('sys.color.chip_active_icon_color')]`. The default **fontSize** is 16.

For the image icon, the default **fillColor** is `$r('sys.color.chip_usually_icon_color')`, and the default **activatedFillColor** is `$r('sys.color.chip_active_icon_color')`. The color parsing of **fillColor** and **activatedFillColor** is consistent with that of the **Image** component. The **fillColor** and **activatedFillColor** attributes take effect only when the image format is SVG.

**Decorator:** @Trace

**Type:** [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
