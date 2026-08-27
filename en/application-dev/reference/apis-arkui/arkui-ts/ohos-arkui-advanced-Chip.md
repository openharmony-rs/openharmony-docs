# Chip

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @weixin_45530366-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f61ce95179b4c1b9fc3671fde09ef06c73b5f91d translatedAt=2026-08-24T06:52:15.071Z pushedAt=2026-08-25T07:34:30.945Z -->

The **Chip** component is used for label display and interaction scenarios. It supports custom styles, icons, and activated states, and is suitable for scenarios such as search box history records and email recipient lists. It enables quick creation, deletion, and interaction of labels.

> **NOTE**
>
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { Chip, ChipOptions, ChipSize } from '@kit.ArkUI';
```

## Child Components

Not supported

## Chip

Chip(options:ChipOptions): void

Creates a **Chip** component.

**Decorator**: @Builder

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name   | Type                       | Mandatory| Description                |
| ------- | --------------------------- | ---- | -------------------- |
| options | [ChipOptions](#chipoptions) | Yes   | Parameters of the **Chip** component, including size, enabled state, activated state, prefix/suffix icons, text content, background color, rounded corners, accessibility attributes, etc., used to customize the style and behavior of the **Chip** component. |

## ChipOptions

Defines the style and specific style parameters of the **Chip** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name           | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| size            | [ChipSize](#chipsize) \| [SizeOptions](ts-types.md#sizeoptions) | No  | Yes  | Size of the **Chip**.<br>Default value: **ChipSize.NORMAL**<br>**Usage scenario**: **ChipSize.NORMAL** is suitable for common scenarios; **ChipSize.SMALL** is suitable for compact layout scenarios, such as tag lists and filter bars; custom **SizeOptions** is suitable for scenarios requiring specific sizes.<br>The **SizeOptions** type does not support percentage settings. Abnormal values are processed as the default value.<br>**Atomic service API:** This API can be used in atomic services since API version 12.<br>**Note:** [Aging adaptation](../../../ui/arkui-support-for-aging-adaptation.md) does not take effect when **size** specifies specific width and height, except when **size** is set to **{ height: 0, width: 0 }**. |
| enabled         | boolean                                                      | No  | Yes  | Whether the Chip is available.<br>Default value: **true**<br>**true**: The Chip is available; **false**: The Chip is unavailable.<br>**Usage scenario**: Set to **false** to disable the Chip. This is suitable for scenarios where user operations need to be prohibited, such as restricted permissions, incomplete data loading, or unmet conditions.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| activated<sup>12+</sup>    | boolean                                        | No  | Yes  | Whether the Chip is in the activated state.<br>Default value: **false**<br>**true**: The Chip is in the activated state; **false**: The Chip is in the non-activated state.<br>If the value is **undefined**, the default value is used.<br>**Usage scenario**: Commonly used in tag selection scenarios to indicate the currently selected item.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| prefixIcon      | [PrefixIconOptions](#prefixiconoptions)                      | No  | Yes  | Prefix icon of the Chip component, displayed on the left side of the component.<br>Default value: No prefix icon is displayed<br>If the value is **undefined**, the default value is used.<br>When both **prefixIcon** and **prefixSymbol** are set, **prefixSymbol** takes effect and **prefixIcon** is ignored.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| prefixSymbol<sup>12+</sup>  | [ChipSymbolGlyphOptions](#chipsymbolglyphoptions12)              | No  | Yes  | Prefix icon attribute, of the symbol type. Commonly used in scenarios requiring system standard icons or dynamic icon effects.<br>Default value: No prefix icon is displayed<br>If the value is **undefined**, the default value is used.<br>When both **prefixIcon** and **prefixSymbol** are set, **prefixSymbol** takes effect and **prefixIcon** is ignored.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| label           | [LabelOptions](#labeloptions)                                | No  | No  | Text content and style displayed on the Chip component.<br>**Atomic service API:** This API can be used in atomic services since API version 12.   |
| suffixIcon      | [SuffixIconOptions](#suffixiconoptions)                      | No  | Yes  | Suffix icon of the Chip component, displayed on the right side of the component.<br>Default value: No suffix icon is displayed<br>If the value is **undefined**, the default value is used.<br>When both **suffixIcon** and **suffixSymbol** are set, **suffixSymbol** takes effect and **suffixIcon** is ignored.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| suffixSymbol<sup>12+</sup>   | [ChipSymbolGlyphOptions](#chipsymbolglyphoptions12)              | No  | Yes  | Suffix icon attribute, of the symbol type. Commonly used in scenarios requiring system standard icons or dynamic icon effects.<br>Default value: No suffix icon is displayed<br>If the value is **undefined**, the default value is used.<br>When both **suffixIcon** and **suffixSymbol** are set, **suffixSymbol** takes effect and **suffixIcon** is ignored.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| suffixSymbolOptions<sup>14+</sup> | [ChipSuffixSymbolGlyphOptions](#chipsuffixsymbolglyphoptions14) | No | Yes | Accessibility reading function attributes and tap event callback of the symbol-type suffix icon.<br>Default value: No corresponding attribute is set<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor)                   | No  | Yes  | Background color of the Chip.<br>Default value: **$r('sys.color.ohos_id_color_button_normal')**<br>If the value is **undefined**, the default value is used. If an invalid value is assigned, the background color is transparent.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| activatedBackgroundColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor)          | No  | Yes  | Background color of the Chip in the activated state.<br>Default value: **$r('sys.color.ohos_id_color_emphasize')**<br>If the value is **undefined**, the default value is used. If an invalid value is assigned, the background color is transparent.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| backgroundSystemMaterial | [uiMaterial.Material](../arkts-apis-uimaterial.md#material) | No | Yes | System material style of the component. It is suitable for scenarios such as immersive background effects and semi-transparent frosted glass effects. Different materials have different effects and can affect visual attributes such as [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), [border](ts-universal-attributes-border.md#border), and [shadow](ts-universal-attributes-image-effect.md#shadow) of the component.<br>Default value: **undefined**<br>If the value is **undefined**, no material style is applied.<br>**Note:** When **backgroundSystemMaterial** is set, **backgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material. When **backgroundSystemMaterial** is **undefined**, the **backgroundColor** attribute takes effect.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0. |
| activatedBackgroundSystemMaterial | [uiMaterial.Material](../arkts-apis-uimaterial.md#material) | No | Yes | System material style of the component in the activated state. It is suitable for interactive scenarios where the material effect needs to be maintained or switched in the activated state, such as tag selection and state switching. Different materials have different effects and can affect visual attributes such as [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), [border](ts-universal-attributes-border.md#border), and [shadow](ts-universal-attributes-image-effect.md#shadow) of the component.<br>Default value: **undefined**<br>If the value is **undefined**, no material style is applied.<br>**Note:** When **activatedBackgroundSystemMaterial** is set, **activatedBackgroundColor** should be set to **Color.Transparent**, otherwise it will conflict with the system material. When **activatedBackgroundSystemMaterial** is **undefined**, the **activatedBackgroundColor** attribute takes effect.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0. |
| borderRadius    | [Dimension](ts-types.md#dimension10)                         | No  | Yes  | Corner radius of the Chip background. Percentage is not supported. If a percentage is passed in, the default value is used.<br>Value range: [0, +∞)<br>Default value: **$r('sys.float.ohos_id_corner_radius_button')**<br>Unit: vp<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| allowClose      | boolean                                                      | No  | Yes  | Whether the close icon is displayed.<br>Default value: **true**<br>**true**: The close icon is displayed; **false**: The close icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Note:** When **suffixSymbol** has a value passed in, **allowClose** does not take effect. When **suffixSymbol** has no value passed in but **suffixIcon** does, **allowClose** does not take effect. When neither **suffixSymbol** nor **suffixIcon** has a value passed in, **allowClose** determines whether the close icon is displayed.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onClose         | ()=>void                                                     | No  | Yes  | Default close icon tap event callback. It has no parameters or return value. This callback is triggered when the user taps the default close icon.<br>If the value is **undefined**, the close icon tap event is not triggered.<br>**Note:** This takes effect only when the close icon is displayed, that is, when neither **suffixSymbol** nor **suffixIcon** has a value passed in and **allowClose** is **true**.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onClicked<sup>12+</sup>     | Callback\<void> | No  | Yes  | Tap event callback of the **Chip** component. It has no parameters or return value. This callback is triggered when the user taps the **Chip** component.<br>If the value is **undefined**, the **Chip** cannot be tapped.<br>**Atomic service API:** This API can be used in atomic services since API version 12.        |
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction) | No | Yes | Layout direction.<br>Default value: **Direction.Auto**<br>If the value is **undefined**, the default value is used.<br>**Usage scenario**: Commonly used in internationalization scenarios to adapt to right-to-left (RTL) reading habits, such as Arabic, achieving a mirrored interface effect.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| closeOptions<sup>14+</sup> | [CloseOptions](#closeoptions14) | No | Yes | Functional attributes of the default close icon, including accessibility reading and font size attributes. This takes effect only when the default close icon is displayed, that is, when **allowClose** is **true** and neither **suffixSymbol** nor **suffixIcon** has a value passed in.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description of the Chip component. This is used to explain the current component to users in detail. Developers should provide detailed text descriptions to help users understand the operations to be performed and their results, especially when these results cannot be directly learned from the component attributes and accessibility text alone. If a component has both a text attribute and an accessibility description attribute, when the component is selected, the system first reads out the text attribute of the component, followed by the content of the accessibility description attribute.<br>Default value: empty string<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| accessibilityLevel<sup>14+</sup> | string | No | Yes | Accessibility level of the Chip component. This parameter controls whether the Chip component can be recognized by accessibility services.<br>Supported values:<br>**"auto"**: The attribute value of the component is converted to **"yes"**.<br>**"yes"**: The component can be recognized by accessibility services.<br>**"no"**: The component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.<br>Default value: **"auto"**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| accessibilitySelectedType<sup>14+</sup> | [AccessibilitySelectedType](#accessibilityselectedtype14) | No| Yes| Type of selected state for the chip.<br>Default value:<br>If the **activated** property is set but **accessibilitySelectedType** is not specified, the default type is **CHECKED**. If the **activated** property is not set, the default type is **CLICKED**.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14.|
| maxFontScale<sup>23+</sup> | number&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No | Yes | Maximum font scale factor for the text and icons of the **Chip** component.<br>Value range: [1, +∞)<br>If the set value is less than 1, the value 1 is used. Abnormal values do not take effect by default.<br>Default value: **1**<br>If the value is **undefined**, the default value is used.<br/>**Usage scenario**: Suitable for accessibility scenarios where the upper limit of font scaling needs to be restricted, preventing layout overflow caused by excessively large fonts.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |
| minFontScale<sup>23+</sup> | number&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No | Yes | Minimum font scale factor for the text and icons of the **Chip** component.<br>**Value range:** [0, 1]<br>If the set value is less than 0, the value 0 is used. If the set value is greater than 1, the value 1 is used. Abnormal values do not take effect by default.<br>Default value: **1**<br>If the value is **undefined**, the default value is used.<br/>**Usage scenario**: Suitable for scenarios where the lower limit of font scaling needs to be restricted, ensuring text readability.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |
| padding<sup>23+</sup> | [LocalizedPadding](ts-types.md#localizedpadding12) | No | Yes | Padding of the Chip component.<br>Default values:<br>- When **size** is **ChipSize.SMALL** and **activated** is **true**, the default value is: `{ start: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`<br>- When **size** is **ChipSize.SMALL** and **activated** is **false**, the default value is: `{ start: LengthMetrics.resource('sys.float.chip_small_text_padding'), end: LengthMetrics.resource('sys.float.chip_small_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`<br>- When **size** is not **ChipSize.SMALL** and **activated** is **true**, the default value is: `{ start: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_activated_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`<br>- When **size** is not **ChipSize.SMALL** and **activated** is **false**, the default value is: `{ start: LengthMetrics.resource('sys.float.chip_normal_text_padding'), end: LengthMetrics.resource('sys.float.chip_normal_text_padding'), top: LengthMetrics.vp(4), bottom: LengthMetrics.vp(4)}`<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |
| fontSize<sup>23+</sup> | [Dimension](ts-types.md#dimension10) | No | Yes | Uniform font size for the text and icons of the **Chip** component. Percentage is not supported. If a percentage is passed in, the default value is used.<br>The priority of this **fontSize** is lower than the **fontSize** attributes in **prefixSymbol**, **label**, **suffixSymbol**, and **closeOptions**.<br>Default values:<br>- When **size** is **ChipSize.SMALL**, text: `$r('sys.float.chip_small_font_size')`; icon: `$r('sys.float.chip_small_icon_size')`<br>- In other cases, text: `$r('sys.float.chip_normal_font_size')`; icon: `$r('sys.float.chip_normal_icon_size')`<br>Unit: fp<br>If the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |

> **NOTE**
>
> 1. When **suffixSymbol** is provided with an argument, **suffixIcon** and **allowClose** will not take effect. If **suffixSymbol** is not provided, but **suffixIcon** is, **allowClose** will not take effect. If neither **suffixSymbol** nor **suffixIcon** is provided, **allowClose** determines whether to display the close icon.
> 2. When **backgroundColor** and **activatedBackgroundColor** are set to **undefined**, the default background color is displayed. When they are set to invalid values, the background color is transparent.
> 3. When an icon is set for **prefixSymbol** or **suffixSymbol**, if the chip is in the inactive state, the icon color **fontColor** is `[$r('sys.color.ohos_id_color_secondary')]`; if the chip is in the activated state, the icon color **fontColor** is `[$r('sys.color.ohos_id_color_text_primary_contrary')]`. In addition, when **size** is **ChipSize.SMALL**, the default font size of the icon is `$r('sys.float.chip_small_icon_size')`; when **size** is **ChipSize.NORMAL** or a custom size, the default font size of the icon is `$r('sys.float.chip_normal_icon_size')`.
> 4. When icons are set for **prefixIcon** and **suffixIcon**, the default value of **fillColor** is `$r('sys.color.chip_usually_icon_color')`. The color parsing of **fillColor** is consistent with that of the **Image** component.
> 5. When icons are set for **prefixIcon** and **suffixIcon**, the default value of **activatedFillColor** is `$r('sys.color.chip_active_icon_color')`. The color parsing of **activatedFillColor** is consistent with that of the **Image** component.
> 6. Starting from API version 26.0.0, when **backgroundSystemMaterial** is configured as an auto-invert material, the fill color of **prefixIcon** and **suffixIcon**, as well as the text color of **prefixSymbol** and **suffixSymbol** in the inactive state, will use system resources that support color inversion. These colors will automatically match the inversion effect based on the background material. When **activatedBackgroundSystemMaterial** is configured as an auto-invert material, the activated fill color of **prefixIcon** and **suffixIcon**, as well as the text color of **prefixSymbol** and **suffixSymbol** in the activated state, will also use system resources that support color inversion, achieving automatic adaptation to the background material inversion.

## ChipSize

Enumerates the size types that can be specified for the **Chip** component, such as normal and small.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Value      | Description              |
| ------ | -------- | ------------------ |
| NORMAL | "NORMAL" | Normal-sized chip for regular display scenarios. |
| SMALL  | "SMALL"  | Small-sized chip for compact layout scenarios.  |

## AccessibilitySelectedType<sup>14+</sup>

Defines the selected state types that can be specified for **Chip**. This API is used to control how the accessibility service conveys the component's selected state to users. Different selected state types provide different semantics and user experiences.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Value| Description|
| ---- | -- | ---- |
| CLICKED | 0 | Click type. The chip acts as a regular clickable component, without reporting any selected state to accessibility services. Use this type when the chip triggers an action but does not maintain a selected state.|
| CHECKED | 1 | Checkbox type. The chip reports its selected state to accessibility services using the [accessibilityChecked](ts-universal-attributes-accessibility.md#accessibilitychecked13) attribute. Use this type for multi-select scenarios, such as tag filtering and attribute selection.|
| SELECTED | 2 | Radio type. The chip reports its selected state to accessibility services using the [accessibilitySelected](ts-universal-attributes-accessibility.md#accessibilityselected13) attribute. Use this type for single-select scenarios, such as navigation bar tabs and radio buttons.|

## IconCommonOptions

Defines the common icon options of the chip.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name     | Type                                      | Read-Only| Optional| Description                                                        |
| --------- | ------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| src       | [ResourceStr](ts-types.md#resourcestr)     | No | No | Icon source, which can be a specific image path or an image reference.|
| size      | [SizeOptions](ts-types.md#sizeoptions)     | No  | Yes  | Icon size. Percentage is not supported. Abnormal values are handled as the default value.<br>Default value:<br>- When **ChipOptions.size** is **ChipSize.SMALL**, the default value is **{width: $r('sys.float.chip_small_icon_size'), height: $r('sys.float.chip_small_icon_size')}**<br>- When **ChipOptions.size** is **ChipSize.NORMAL**, the default value is **{width: $r('sys.float.chip_normal_icon_size'), height: $r('sys.float.chip_normal_icon_size')}**<br>Unit: vp<br>If the value is **undefined**, the default value is used. |
| fillColor | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Icon fill color. This attribute takes effect only when the image format is SVG.<br>Default value: **$r('sys.color.chip_usually_icon_color')**<br>If the value is **undefined**, the default value is used. |
| activatedFillColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Icon fill color when the **Chip** is activated. This attribute takes effect only when the image format is SVG.<br>Default value: **$r('sys.color.chip_active_icon_color')**<br>If the value is **undefined**, the default value is used. |

> **NOTE**
>
> **fillColor** and **activatedFillColor** take effect only when the icon format is SVG.
>

## PrefixIconOptions

Defines the prefix icon options.

Inherits from [IconCommonOptions](#iconcommonoptions).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

## SuffixIconOptions

Defines the suffix icon options.

Inherits from [IconCommonOptions](#iconcommonoptions).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Type      | Read-Only| Optional| Description              |
| ------ | ---------- | ---- | ------------------ | ------------------ |
| action | () => void | No  | Yes  | Callback for the suffix icon tap event, with no parameters and no return value. It is triggered when the user taps the suffix icon.<br>When the value is **undefined**, no suffix icon event is set.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| accessibilityText<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility text attribute for the suffix icon. When the suffix icon does not contain a text attribute, the screen reader does not announce it upon selection, and the user cannot clearly know whether the suffix icon is currently selected. Developers can set accessibility text for such icons, which is announced by the screen reader upon selection.<br>Default value: **' '**<br>When the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Accessibility description for the suffix icon. This description is used to explain the suffix icon to users in detail. Developers should provide a relatively detailed text description to help users understand the operation to be performed and its possible consequences, especially when these consequences cannot be directly learned from the suffix icon's attributes and accessibility text alone. If the suffix icon has both a text attribute and an accessibility description attribute, when the suffix icon is selected, the system first announces the text attribute of the suffix icon, and then announces the content of the accessibility description attribute.<br>Default value: **' '**<br>When the value is **undefined**, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |
| accessibilityLevel<sup>14+</sup> | string | No | Yes | Accessibility level for the suffix icon. Controls whether the suffix icon can be recognized by accessibility services.<br>Supported values:<br>**"auto"**: Converted to **"yes"** if the component has an action, and to **"no"** otherwise.<br>**"yes"**: The component can be recognized by accessibility services.<br>**"no"**: The component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.<br>Default value: **"auto"**.<br>When the value is undefined, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 14. |

## AccessibilityOptions<sup>14+</sup>

Defines the accessibility options of the suffix icon.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| ------ | ---------- | ---- | ------------------ | ------------------ |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessibility text, that is, accessible label name. If a component does not contain text information, it will not be announced by the screen reader when selected. In this case, the screen reader user cannot know which component is selected. To solve this problem, you can set accessibility text for components without text information. When such a component is selected, the screen reader announces the specified accessibility text, informing the user which component is selected.<br>Default value: **' '**<br>If the value is **undefined**, the default value is used.|
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessibility description. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.<br>Default value: **' '**<br>If the value is **undefined**, the default value is used.|
| accessibilityLevel | string | No | Yes | Accessibility level. This attribute controls whether the component can be recognized by accessibility services.<br>Supported values:<br>**"auto"**: The attribute value of the current component is converted to **"yes"**.<br>**"yes"**: The current component can be recognized by accessibility services.<br>**"no"**: The current component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.<br>Default value: **"auto"**<br>When the value is **undefined**, the default value is used. |

## ChipSuffixSymbolGlyphOptions<sup>14+</sup>

Defines the accessibility reading functional attributes and tap event callback of the symbol-type suffix icon.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | --- | ---- | ---- |
| action | [VoidCallback](ts-types.md#voidcallback12) | No | Yes | Callback for the suffix icon tap event, with no parameters and no return value. This callback is triggered when the user taps the suffix icon.<br>When the value is **undefined**, no suffix icon event is set.<br>Default value: **undefined** |
| normalAccessibility | [AccessibilityOptions](#accessibilityoptions14) | No| Yes| Accessibility settings for the normal state.<br>Default value: **undefined**|
| activatedAccessibility | [AccessibilityOptions](#accessibilityoptions14) | No| Yes| Accessibility settings for the activated state.<br>Default value: **undefined**|

## ChipSymbolGlyphOptions<sup>12+</sup>

Defines the prefix and suffix icon options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Type      | Read-Only| Optional| Description              |
| ------ | ---------- | ---- | ------------------ | ------------------ |
| normal | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol type icon displayed for the **Chip** in the inactive state.<br>Default value: no prefix icon or suffix icon displayed<br>When the value is **undefined**, the default value is used. |
| activated | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol type icon displayed for the **Chip** in the activated state.<br>Default value: no prefix icon or suffix icon displayed<br>When the value is **undefined**, the default value is used. |

> **NOTE**
>
> The animation type cannot be modified via [SymbolEffect](ts-basic-components-symbolGlyph.md#symboleffect12) and animations cannot be set via **effectStrategy**.
>

## LabelOptions

Defines text configuration options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name       | Type                                      | Read-Only| Optional| Description                                                        |
| ----------- | ------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| text        | string                                     | No  | No  | Text content displayed by the **Chip** component. |
| fontSize    | [Dimension](ts-types.md#dimension10)       | No  | Yes  | Font size. Percentage is not supported. If a percentage is passed, the default value is used.<br>If a negative value is passed, the default value is used.<br>Default value: **$r('sys.float.ohos_id_text_size_button2')**<br>Unit: fp<br>When the value is **undefined**, the default value is used. |
| fontColor   | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Text color.<br>Default value: **$r('sys.color.ohos_id_color_text_primary')**<br>When the value is **undefined**, the default value is used. |
| activatedFontColor<sup>12+</sup>   | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Text color when the **Chip** is activated.<br>Default value: $r('sys.color.ohos_id_color_text_primary_contrary')<br>When the value is **undefined**, the default value is used. |
| fontFamily  | string                                     | No  | Yes  | Font style of the **Chip** component text.<br>Default value: **"HarmonyOS Sans"**<br>When the value is **undefined**, the default value is used. |
| labelMargin | [LabelMarginOptions](#labelmarginoptions)  | No | Yes | Spacing between the text and the left/right icons.<br>Default values:<br>When **size** is **ChipSize.SMALL**, the default value is **{ left: 4, right: 4 }**.<br>When **size** is **ChipSize.NORMAL**, the default value is **{ left: 6, right: 6 }**<br>Unit: vp<br>When the value is **undefined**, the default value is used. |
| localizedLabelMargin<sup>12+</sup> | [LocalizedLabelMarginOptions](#localizedlabelmarginoptions12) | No | Yes | Spacing between the localized text and the left/right icons.<br>Default values:<br>When **size** is **ChipSize.SMALL**:<br>`{  start: LengthMetrics.resource($r('sys.float.chip_small_text_margin')),  end: LengthMetrics.resource($r('sys.float.chip_small_text_margin')) }`<br>When **size** is **ChipSize.NORMAL**:<br>`{  start: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')),  end: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')) }`<br>When the value is **undefined**, the default value is used. |

> **NOTE**
>
> Starting from API version 26.0.0, when **backgroundSystemMaterial** is set to an auto-invert system material, **fontColor** uses a special system resource that supports color inversion, and the text color automatically adapts to the inverted color of the material background. When **activatedBackgroundSystemMaterial** is set to an auto-invert system material, **activatedFontColor** uses a special system resource that supports color inversion, and the text color of the chip in the activated state automatically adapts to the inverted color of the material background.

## CloseOptions<sup>14+</sup>

Defines the default close icon behavior attributes for the chip, including accessibility attributes. The default value of **accessibilityText** is **"Delete"**.

Inherits from [AccessibilityOptions](#accessibilityoptions14).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name | Type                                | Read-Only| Optional| Description                                                        |
| ----- | ------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
|fontSize<sup>23+</sup> | [Dimension](ts-types.md#dimension10) | No | Yes | Size of the default close icon of the **Chip** component. Percentage is not supported. If a percentage is passed, the default value is used.<br>Default value:<br> When **size** is **ChipSize.SMALL**, `$r('sys.float.chip_small_font_size')` <br> Other cases: `$r('sys.float.chip_normal_font_size')` <br>Unit: fp<br>If a negative number is passed, the default value is used. If the value is **undefined**, the default value is used.<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |

## LabelMarginOptions

Defines the spacing between the text and the left and right icons.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name | Type                                | Read-Only| Optional| Description                                                        |
| ----- | ------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| left  | [Dimension](ts-types.md#dimension10) | No   | Yes   | Spacing between the text and the left icon. Percentage is not supported.<br>Default value:<br>When **size** is **ChipSize.SMALL**, the default value of **left** is **4**<br>When **size** is **ChipSize.NORMAL**, the default value of left is **6**<br>Unit: vp<br>If the value is out of the value range, the default value is used.<br>Value range: [0, +∞) |
| right | [Dimension](ts-types.md#dimension10) | No  | Yes  | Spacing between the text and the right icon. This parameter cannot be set in percentage.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value of **right** is **4**.<br>When **size** is set to **ChipSize.NORMAL**, the default value of **right** is **6**.<br>Unit: vp.<br>If the value is out of the range, the default value is used.<br>Value range: [0, +∞)|

## LocalizedLabelMarginOptions<sup>12+</sup>

Defines the spacing between the localized text and the left and right icons.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name | Type                                                        | Read-Only| Optional| Description                                                        |
| ----- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| start | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Margin between the text and the start-side icon. Percentage values are not supported.<br>Default values:<br>When **size** is **ChipSize.SMALL**, the default value of **start** is:<br>`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`<br>When **size** is **ChipSize.NORMAL**, the default value of **start** is:<br>`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`<br>If the value is **undefined**, the default value is used. |
| end | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes | Margin between the text and the end-side icon. Percentage values are not supported.<br>Default values:<br>When **size** is **ChipSize.SMALL**, the default value of **end** is:<br>`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`<br>When **size** is **ChipSize.NORMAL**, the default value of **end** is:<br>`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`<br>If the value is **undefined**, the default value is used. |

## Example

### Example 1: Setting a Custom Suffix Icon

This example sets a custom suffix icon by configuring **suffixIcon**.

```ts
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        // Set the suffix icon.
        suffixIcon: {
          // Replace 'app.media.close' with your actual icon resource.
          src: $r('app.media.close'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        size: ChipSize.NORMAL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

![](figures/chip1.png)

### Example 2: Using the Default Suffix Icon

Set **allowClose** to **true** to display the close icon.

```ts
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        closeOptions: {fontSize: 12},
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

![](figures/chip2.png)

### Example 3: Displaying No Suffix Icon

Set **allowClose** to **false** to hide the close icon.

```ts
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.SMALL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        minFontScale: 0.2,
        maxFontScale: 2,
        padding: {
          start: LengthMetrics.vp(20),
          end: LengthMetrics.vp(20)
        },
        fontSize: 12
      })
    }
  }
}
```

![](figures/chip3.png)

### Example 4: Implementing the Activated State

This example shows how to implement the activated state for a chip by configuring **activated**.

```ts
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue,
          activatedFillColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          activatedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        enabled: true,
        activated: this.isActivated,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        activatedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        onClose: () => {
          console.info('chip on close');
        },
        onClicked: () => {
          console.info('chip on clicked');
        }
      })
      // Tap "Change Activation Status" to control the activation and deactivation of the operation block.
      Button('Activate/Deactivate')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

![](figures/chip4.gif)

### Example 5: Setting the Symbol Icon

This example demonstrates how to set the symbol-type prefix icon of the chip.

```ts
import { Chip, ChipSize, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        // Set the symbol-type prefix icon.
        prefixSymbol: {
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Red]),
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          activatedFontColor: $r('sys.color.ohos_id_color_text_primary_contrary'),
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 },
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        enabled: true,
        activated: this.isActivated,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        activatedBackgroundColor: $r('sys.color.ohos_id_color_emphasize'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button'),
        onClose: () => {
          console.info('chip on close');
        },
        onClicked: () => {
          console.info('chip on clicked');
        }
      })

      Button('Activate/Deactivate')
        .onClick(() => {
          this.isActivated = !this.isActivated;
        })
    }
  }
}
```

![](figures/chip5.gif)

### Example 6: Implementing a Mirrored Layout

This example shows how to implement a chip mirrored layout by configuring **direction**.

```ts
import { Chip, ChipSize, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ChipPage {
  build() {
    Column() {
      Chip({
        direction: Direction.Rtl,
        // Set the prefix icon.
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        // Set the text.
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          localizedLabelMargin: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) },
        },
        // Set the suffix icon.
        suffixIcon: {
          // Replace 'app.media.close' with your actual icon resource.
          src: $r('app.media.close'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        size: ChipSize.NORMAL,
        allowClose: false,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button')
      })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

![](figures/chip6.png)

### Example 7: Implementing Accessibility for an Image-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with an image-type suffix icon. Clicking the suffix icon triggers the announcement of "icon, button, usage hints."

```ts
import { Chip } from '@kit.ArkUI';

@Builder
function defaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
struct ChipExample2 {

  build() {
    NavDestination() {
      Scroll() {
        SectionGroup({ title: 'Suffix icon announcement' }) {
          SectionItem({ title: 'Custom announcement' }) {
            Chip({
              label: { text: 'Chip' },
              suffixIcon: {
                src: $r('sys.media.ohos_ic_public_cut'),
                accessibilityText: 'Icon', // Read "Icon, button, usage hints."
                accessibilityDescription: 'Usage hints',
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix icon clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }
        }
      }
    }
  }
}
```

### Example 8: Implementing Accessibility for a Symbol-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with a symbol-type suffix icon. Clicking the suffix icon triggers the announcement of "music, button, usage hints."

```ts
import { Chip, SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
function defaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 4 }) {
      Text(this.title)
        .fontColor('#FF666666')
        .fontSize(12)
      Column({ space: 8 }) {
        this.content()
      }
    }
    .alignItems(HorizontalAlign.Start)
    .width('100%')
  }
}

@Component
struct SectionItem {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = defaultFunction;

  build() {
    Column({ space: 12 }) {
      Text(this.title)
      this.content()
    }
    .backgroundColor('#FFFFFFFF')
    .borderRadius(12)
    .padding(12)
    .width('100%')
  }
}

@Entry
@Component
struct ChipExample2 {

  build() {
    NavDestination() {
      Scroll() {
        SectionGroup({ title: 'Suffix symbol announcement' }) {
          SectionItem({ title: 'activatedAccessibility' }) {
            Chip({
              label: { text: 'Chip' },
              activated: true,
              suffixSymbol: {
                activated: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                activatedAccessibility: {
                  accessibilityText: 'Music', // Read "Music, button, usage hints."
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }

          SectionItem({ title: 'normalAccessibility' }) {
            Chip({
              label: { text: 'Chip' },
              suffixSymbol: {
                normal: new SymbolGlyphModifier($r('sys.symbol.media_sound'))
                  .fontSize(72),
              },
              suffixSymbolOptions: {
                normalAccessibility: {
                  accessibilityText: 'Music', // Read "Music, button, usage hints."
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol clicked.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip clicked.'
                });
              }
            })
          }
        }
      }
    }
    .padding({
      top: 8,
      bottom: 8,
      left: 16,
      right: 16,
    })
  }
}
```

### Example 9: Implementing Chip Accessibility

This example shows the accessibility property settings of the **Chip** component, including different **accessibilitySelectedType** types and various accessibility properties.

```ts
import { AccessibilitySelectedType, Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct ChipAccessibilityExample {
  @State clickedChipActivated: boolean = false;
  @State checkedChipActivated: boolean = false;
  @State selectedChipActivated: boolean = false;

  build() {
    Column({ space: 20 }) {
      Text('Chip accessibility example').fontSize(20).fontWeight(FontWeight.Bold)

      // Clickable chip - CLICKED type
      Chip({
        label: { text: 'Clickable chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Blue
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CLICKED, // Clickable type
        accessibilityDescription: 'This is a clickable chip.', // Overall accessibility description.
        accessibilityLevel: 'yes', // Make sure it can be recognized by accessibility services.
        closeOptions: {
          accessibilityDescription: 'Delete this chip. This operation cannot be undone.' // Provide detailed description for the delete button.
        },
        activated: this.clickedChipActivated,
        onClicked: () => {
          this.clickedChipActivated = !this.clickedChipActivated;
          this.getUIContext().getPromptAction().showToast({ message: 'Clickable chip is clicked.' });
        },
        onClose: () => {
          this.getUIContext().getPromptAction().showToast({ message: 'The close icon of the clickable chip is clicked.' });
        }
      })

      // Checkbox chip - CHECKED type
      Chip({
        label: { text: 'Checkbox chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Green
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.CHECKED, // Checkbox chip
        accessibilityDescription: 'This is a checkbox chip.', // Overall accessibility description.
        activated: this.checkedChipActivated,
        onClicked: () => {
          this.checkedChipActivated = !this.checkedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.checkedChipActivated ? 'Checkbox chip is selected.' : 'Checkbox chip is deselected.'
          });
        }
      })

      // Radio chip - SELECTED type
      Chip({
        label: { text: 'Radio chip' },
        prefixIcon: {
          src: $r('sys.media.ohos_app_icon'),
          fillColor: Color.Red
        },
        size: ChipSize.NORMAL,
        accessibilitySelectedType: AccessibilitySelectedType.SELECTED, // Radio type
        accessibilityDescription: 'This is a radio chip.', // Overall accessibility description.
        activated: this.selectedChipActivated,
        onClicked: () => {
          this.selectedChipActivated = !this.selectedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.selectedChipActivated ? 'Radio chip is selected.' : 'Radio chip is deselected.'
          });
        }
      })

      // Example of setting the accessibility level
      Chip({
        label: { text: 'Accessibility level is set to no.' },
        size: ChipSize.NORMAL,
        accessibilityLevel: 'no', // This chip cannot be recognized by accessibility services.
        closeOptions: {
          accessibilityLevel: 'no'
        },
        backgroundColor: '#CCCCCC',
        onClicked: () => {
          this.getUIContext().getPromptAction().showToast({ message: 'This chip cannot be recognized by accessibility services.' });
        }
      })
    }
    .width('100%')
    .padding(16)
  }
}
```

### Example 10: Setting the System Material Style

This example implements the system material style by configuring **backgroundSystemMaterial** and **activatedBackgroundSystemMaterial**, and enables the auto-invert feature to adapt the label text color.

Starting from API version 26.0.0, the **backgroundSystemMaterial** and **activatedBackgroundSystemMaterial** attributes are added to [ChipOptions](#chipoptions).

```ts
import { Chip, ChipOptions, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct ChipMaterialExample {
  private chipOptions: ChipOptions = {
    label: {
      text: 'Chip',
      // Set fontColor to a special system resource value to enable automatic color inversion.
      fontColor: $r('sys.color.font_primary'),
      activatedFontColor: $r('sys.color.font_primary')
    },
    allowClose: false,
    // Set the background color in the normal state to transparent. Otherwise, it will conflict with the system material.
    backgroundColor: Color.Transparent,
    // Set the system material style in the normal state to ULTRA_THIN and enable automatic color inversion.
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true
    }),
    // Set the background color in the activated state to transparent. Otherwise, it will conflict with the system material.
    activatedBackgroundColor: Color.Transparent,
    // Set the system material style in the activated state.
    activatedBackgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN
    })
  }

  build() {
    Column({ space: 50 }) {
      Chip(this.chipOptions)
      Chip(this.chipOptions)
    }
    .linearGradient({
      angle: 0, // Gradient angle. 0 degrees means from left to right.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start point).
        ['#FECFEF', 0.5], // Middle color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end point).
      ]
    })
    .padding(12)
    .width('100%')
    .height(150)
  }
}
```

<!--Del--> <!--DelEnd-->