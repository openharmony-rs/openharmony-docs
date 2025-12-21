# Chip
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xieziang-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

The **Chip** component is designed for scenarios including search history display and email recipient lists.

> **NOTE**
>
> This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>

## Modules to Import

```ts
import { Chip, ChipOptions, ChipSize } from '@kit.ArkUI';
```

## Child Components

Not supported

## Chip

Chip(options:ChipOptions): void

**Decorator**: @Builder

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name   | Type                       | Mandatory| Description                |
| ------- | --------------------------- | ---- | -------------------- |
| options | [ChipOptions](#chipoptions) | Yes  | Parameters of the chip.|

## ChipOptions

Defines the type and style parameters of the chip.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name           | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| size            | [ChipSize](#chipsize) \| [SizeOptions](ts-types.md#sizeoptions) | No | Yes | Chip size.<br>Default value: **ChipSize.NORMAL**.<br>The SizeOptions type parameter does not support percentage values. If an invalid value is provided, the system will use the default value instead.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>Note: [Aging-friendly design implementation](../../../ui/arkui-support-for-aging-adaptation.md) does not take effect when size specifies specific width and height, except when size is set to { height: 0, width: 0 }.|
| enabled         | boolean                                                      | No | Yes | Whether the chip can be selected.<br>Default value: **true**.<br>**true**: The chip can be selected.<br>**false**: The chip cannot be selected.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| activated<sup>12+</sup>    | boolean                                        | No | Yes | Whether the chip is activated.<br>Default value: **false**<br>**true**: The chip is activated.<br>**false**: The chip is not activated.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| prefixIcon      | [PrefixIconOptions](#prefixiconoptions)                      | No | Yes | Prefix icon of the chip.<br>Default value: The prefix icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| prefixSymbol<sup>12+</sup>  | [ChipSymbolGlyphOptions](#chipsymbolglyphoptions12)              | No | Yes | Symbol-type prefix icon of the chip.<br>Default value: The prefix icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| label           | [LabelOptions](#labeloptions)                                | No | No | Text of the chip.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| suffixIcon      | [SuffixIconOptions](#suffixiconoptions)                      | No | Yes | Suffix icon of the chip.<br>Default value: The suffix icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| suffixSymbol<sup>12+</sup>   | [ChipSymbolGlyphOptions](#chipsymbolglyphoptions12)              | No | Yes | Symbol-type suffix icon of the chip.<br>Default value: The suffix icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| suffixSymbolOptions<sup>14+</sup> | [ChipSuffixSymbolGlyphOptions](#chipsuffixsymbolglyphoptions14) | No| Yes| Accessibility settings of the symbol-type suffix icon.<br>Default value: The suffix icon is not displayed.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor)                   | No | Yes | Chip background color.<br>Default value: **$r('sys.color.ohos_id_color_button_normal')**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| activatedBackgroundColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor)          | No | Yes | Background color of the chip when it is activated.<br>Default value: **$r('sys.color.ohos_id_color_emphasize').**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| borderRadius    | [Dimension](ts-types.md#dimension10)                         | No | Yes | Radius of the rounded corner of the chip background. Percentage is not supported.<br>Default value: **$r('sys.float.ohos_id_corner_radius_button')**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| allowClose      | boolean                                                      | No | Yes | Whether to display the close icon.<br>Default value: **true**.<br>The value **true** means to show the delete icon, and **false** means the opposite.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onClose         | ()=>void                                                     | No | Yes | Event triggered when the close icon is clicked.<br>If the value is **undefined**, clicking the close icon will not trigger any event.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onClicked<sup>12+</sup>     | Callback\<void> | No | Yes | Chip click event.<br>If the value is **undefined**, the chip cannot be clicked.<br>**Atomic service API**: This API can be used in atomic services since API version 12.       |
| direction<sup>12+</sup> | [Direction](ts-appendix-enums.md#direction) | No| Yes| Layout direction.<br>Default value: **Direction.Auto**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| closeOptions<sup>14+</sup> | [CloseOptions](#closeoptions14) | No| Yes| Accessibility settings of the default close icon.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessible description of the chip. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.<br>The default value is an empty string.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| accessibilityLevel<sup>14+</sup> | string | No| Yes| Accessibility level of the chip. It determines whether the component can be recognized by accessibility services.<br>The options are as follows:<br>**"auto"**: It is treated as "yes" by the system.<br>**"yes"**: The component can be recognized by accessibility services.<br>**"no"**: The component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.<br>Default value: **"auto"**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| accessibilitySelectedType<sup>14+</sup> | [AccessibilitySelectedType](#accessibilityselectedtype14) | No| Yes| Type of selected state for the chip.<br>Default value:<br>If the **activated** property is set but **accessibilitySelectedType** is not specified, the default type is **CHECKED**. If the **activated** property is not set, the default type is **CLICKED**.<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

> **NOTE**
>
> 1. When **suffixSymbol** is provided with an argument, **suffixIcon** and **allowClose** will not take effect. If **suffixSymbol** is not provided, but **suffixIcon** is, **allowClose** still will not take effect. When neither **suffixSymbol** nor **suffixIcon** is provided with arguments, **allowClose** determines whether the deletion icon is displayed.
>2. If **undefined** is assigned to **backgroundColor** or **activatedBackgroundColor**, the default background color is used. If an invalid value is specified, the background color is transparent.
> 3. Default font colors for **prefixSymbol** and **suffixSymbol**: **normalFontColor**: **[$r('sys.color.ohos_id_color_primary')]**; **activatedFontColor**: **[$r('sys.color.ohos_id_color_text_primary_contrary')]**. The default value of **fontColor** is **16**.
>
> 4. The default value of **fillColor** is **$r('sys.color.ohos_id_color_secondary')** for **prefixIcon** and **$r('sys.color.ohos_id_color_primary')** for **suffixIcon**. The color parsing of **fillColor** is the same as that of the **Image** component.
>5. The default value of **activatedFillColor** in **prefixIcon** and **suffixIcon** is **$r('sys.color.ohos_id_color_text_primary_contrary')**. The color parsing of **activatedFillColor** is the same as that of the **Image** component.

## ChipSize

Enumerates the size types of the chip.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Value      | Description              |
| ------ | -------- | ------------------ |
| NORMAL | "NORMAL" | Normal size.|
| SMALL  | "SMALL"  | Small size. |

## AccessibilitySelectedType<sup>14+</sup>

Enumerates the selected state types of the chip. It allows you to specify how accessibility services convey the component's selected state to users. Different selected state types provide distinct semantics and user experiences.

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
| size      | [SizeOptions](ts-types.md#sizeoptions)     | No | Yes | Icon size. This parameter cannot be set in percentage.<br>Default value: **{width: 16, height: 16}**.<br>If the value is **undefined**, the default value is used.|
| fillColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Icon fill color.<br>Default value: **$r('sys.color.chip_usually_icon_color')**<br>If the value is **undefined**, the default value is used.|
| activatedFillColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Icon fill color when the chip is activated.<br>Default value: **$r('sys.color.chip_active_icon_color')**<br>If the value is **undefined**, the default value is used.|

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
| action | () => void | No | Yes | Action of the suffix icon.<br>If the value is **undefined**, no action is configured for the suffix icon.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| accessibilityText<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessibility text, that is, accessibility label name, of the suffix icon. If a component does not contain text information, it will not be announced by the screen reader when selected. In this case, the screen reader user cannot know which component is selected. To solve this problem, you can set accessibility text for components without text information. When such a component is selected, the screen reader announces the specified accessibility text, informing the user which component is selected.<br>Default value: ''<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| accessibilityDescription<sup>14+</sup> | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessible description of the suffix icon. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the chip's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.<br>Default value: ''<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| accessibilityLevel<sup>14+</sup> | string | No| Yes| Accessibility importance of the suffix icon. It is used to control whether the suffix icon can be identified by the accessibility assistance service.<br>The options are as follows:<br>**"auto"**: It is treated as "yes" when **action** is set for the component and as "no" otherwise.<br>**"yes"**: The component can be recognized by accessibility services.<br>**"no"**: The component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.<br>Default value: **"auto"**<br>If the value is **undefined**, the default value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

## AccessibilityOptions<sup>14+</sup>

Defines the accessibility options of the suffix icon.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| ------ | ---------- | ---- | ------------------ | ------------------ |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessibility text, that is, accessible label name. If a component does not have a text attribute, the screen reader does not broadcast the component when it is selected. As a result, the user cannot clearly understand the selected component. Developers can set accessibility text for such components. When the screen reader is used, the text is broadcast to help users clearly understand the selected component.<br>Default value: ''<br>If the value is **undefined**, the default value is used.|
| accessibilityDescription | [ResourceStr](ts-types.md#resourcestr) | No| Yes| Accessibility description. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.<br>Default value: ''<br>If the value is **undefined**, the default value is used.|
| accessibilityLevel | string | No| Yes| Accessibility level. It determines whether the component can be recognized by accessibility services.<br>The options are as follows:<br>**"auto"**: It is treated as "yes" by the system.<br>**"yes"**: The component can be recognized by accessibility services.<br>**"no"**: The component cannot be recognized by accessibility services.<br>**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.<br>Default value: **"auto"**<br>If the value is **undefined**, the default value is used.|

## ChipSuffixSymbolGlyphOptions<sup>14+</sup>

Defines the accessibility options of the symbol-type suffix icon.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | --- | ---- | ---- |
| action | [VoidCallback](ts-types.md#voidcallback12) | No| Yes| Action of the suffix icon.<br>Default value: **undefined**.|
| normalAccessibility | [AccessibilityOptions](#accessibilityoptions14) | No| Yes| Accessibility settings for the normal state.<br>Default value: **undefined**.|
| activatedAccessibility | [AccessibilityOptions](#accessibilityoptions14) | No| Yes| Accessibility settings for the activated state.<br>Default value: **undefined**.|

## ChipSymbolGlyphOptions<sup>12+</sup>

Defines the prefix and suffix icon options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Type      | Read-Only| Optional| Description              |
| ------ | ---------- | ---- | ------------------ | ------------------ |
| normal | [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | No | Yes | Sets the icon in the inactive state.<br>Default value: The prefix or suffix icon is not displayed.<br>If the value is **undefined**, the default value is used.|
| activated | [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | No | Yes | Icon settings for the activated state.<br>Default value: The prefix or suffix icon is not displayed.<br>If the value is **undefined**, the default value is used.|

> **NOTE**
>
> symbolEffect cannot be used to modify the animation type and effectStrategy cannot be used to set the animation.
>

## LabelOptions

LabelOptions defines text attributes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name       | Type                                      | Read-Only| Optional| Description                                                        |
| ----------- | ------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| text        | string                                     | No | No | Text content.|
| fontSize    | [Dimension](ts-types.md#dimension10)       | No | Yes | Font size. This parameter cannot be set in percentage.<br>Default value: **$r('sys.float.ohos_id_text_size_button2')**<br>If the value is **undefined**, the default value is used.|
| fontColor   | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Font color.<br>Default value: **$r('sys.color.ohos_id_color_text_primary')**<br>If the value is **undefined**, the default value is used.|
| activatedFontColor<sup>12+</sup>   | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Font color when the chip is activated.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_contrary').**<br>If the value is **undefined**, the default value is used.|
| fontFamily  | string                                     | No | Yes | Font family.<br>Default value: **"HarmonyOS Sans"**<br>If the value is **undefined**, the default value is used.|
| labelMargin | [LabelMarginOptions](#labelmarginoptions)  | No | Yes | Spacing between the text and the left and right icons.<br>Default value:<br>When size is ChipSize.SMALL, the default value is { left: 4, right: 4 }.<br>When size is ChipSize.NORMAL, the default value is { left: 6, right: 6 }.<br>If the value is **undefined**, the default value is used.|
| localizedLabelMargin<sup>12+</sup> | [LocalizedLabelMarginOptions](#localizedlabelmarginoptions12) | No| Yes| Spacing between the localized text and the left and right icons.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value is as follows:<br>`{  start: LengthMetrics.resource($r('sys.float.chip_small_text_margin')),  end: LengthMetrics.resource($r('sys.float.chip_small_text_margin')) }`<br>When **size** is set to **ChipSize.NORMAL**, the default value is as follows:<br>`{  start: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')),  end: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')) }`<br>If the value is **undefined**, the default value is used.|

## CloseOptions<sup>14+</sup>

Defines the accessibility settings of the close icon. The default value of **accessibilityText** is **Delete**.

Inherits from [AccessibilityOptions](#accessibilityoptions14).

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

## LabelMarginOptions

Defines the spacing between the text and the left and right icons.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name | Type                                | Read-Only| Optional| Description                                                        |
| ----- | ------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| left  | [Dimension](ts-types.md#dimension10) | No  | Yes  | Spacing between the text and the left icon. This parameter cannot be set in percentage.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value of **left** is **4**.<br>When **size** is set to **ChipSize.NORMAL**, the default value of **left** is **6**.<br>If the value is **undefined**, the default value is used.<br>Value range: [0, +∞).<br>Unit: vp.|
| right | [Dimension](ts-types.md#dimension10) | No  | Yes  | Spacing between the text and the right icon. This parameter cannot be set in percentage.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value of **right** is **4**.<br>When **size** is set to **ChipSize.NORMAL**, the default value of **right** is **6**.<br>If the value is **undefined**, the default value is used.<br>Value range: [0, +∞).<br>Unit: vp.|

## LocalizedLabelMarginOptions<sup>12+</sup>

Defines the spacing between the localized text and the left and right icons.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name | Type                                                        | Read-Only| Optional| Description                                                        |
| ----- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| start | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes  | Spacing between the text and the left icon. This parameter cannot be set in percentage.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value of **start** is as follows:<br>`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`<br>When **size** is set to **ChipSize.NORMAL**, the default value of **start** is as follows:<br>`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`<br>If the value is **undefined**, the default value is used.|
| end   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes  | Spacing between the text and the right icon. This parameter cannot be set in percentage.<br>Default value:<br>When **size** is set to **ChipSize.SMALL**, the default value of **end** is as follows:<br>`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`<br>When **size** is set to **ChipSize.NORMAL**, the default value of **end** is as follows:<br>`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`<br>If the value is **undefined**, the default value is used.|

## Example

### Example 1: Setting a Custom Suffix Icon

Configure suffixIcon to customize the suffix icon of the operation block.

```ts
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red
        },
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
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
        borderRadius: $r('sys.float.ohos_id_corner_radius_button')
      })
    }
  }
}
```


![](figures/chip1.png)

### Example 2: Using the Default Suffix Icon

Set allowClose to true to display the suffix removal icon.

```ts
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          labelMargin: { left: 20, right: 30 }
        },
        size: ChipSize.NORMAL,
        allowClose: true,
        enabled: true,
        backgroundColor: $r('sys.color.ohos_id_color_button_normal'),
        borderRadius: $r('sys.float.ohos_id_corner_radius_button')
      })
    }
  }
}
```


![](figures/chip2.png)

### Example 3: Displaying No Suffix Icon

Set allowClose to false to hide the suffix removal icon.

```ts
import { Chip, ChipSize } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Chip({
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue
        },
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
        onClose: () => {
          console.info('chip on close');
        }
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
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue,
          activatedFillColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
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

      Button('Activate/Deactivate').onClick(() => {
        this.isActivated = !this.isActivated;
      })
    }
  }
}
```


![](figures/chip4.gif)

### Example 5: Setting the Symbol Icon

This example implements symbol-type prefix and suffix icons for the **Chip** component.

```ts
import { Chip, ChipSize, SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State isActivated: boolean = false;

  build() {
    Column({ space: 10 }) {
      Chip({
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Blue,
          activatedFillColor: $r('sys.color.ohos_id_color_text_primary_contrary')
        },
        prefixSymbol: {
          normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Green]),
          activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontSize(16).fontColor([Color.Red]),
        },
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

      Button('Activate/Deactivate').onClick(() => {
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
        prefixIcon: {
          // Replace 'app.media.chips' with your actual icon resource.
          src: $r('app.media.chips'),
          size: { width: 16, height: 16 },
          fillColor: Color.Red,
        },
        label: {
          text: 'Chip',
          fontSize: 12,
          fontColor: Color.Blue,
          fontFamily: 'HarmonyOS Sans',
          localizedLabelMargin: { start: LengthMetrics.vp(20), end: LengthMetrics.vp(20) },
        },
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
    }.justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```


![](figures/chip6.png)

### Example 7: Implementing Accessibility for an Image-Type Suffix Icon

This example implements the accessibility feature for a chip with an image-type suffix icon.

```ts
import { Chip } from '@kit.ArkUI';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

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
  content: () => void = DefaultFunction;

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
  @State activated: boolean = false;

  build() {
    NavDestination() {
      Scroll() {
        SectionGroup({ title: 'Suffix icon announcement' }) {
          SectionItem({ title: 'Custom announcement' }) {
            Chip({
              label: { text: 'Chip' },
              suffixIcon: {
                src: $r('sys.media.ohos_ic_public_cut'),
                accessibilityText: 'Icon',
                accessibilityDescription: 'Usage hints',
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix icon touched.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip touched.'
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

This example implements the accessibility feature for a chip with a symbol-type suffix icon.

```ts
import { Chip, SymbolGlyphModifier } from '@kit.ArkUI';

@Builder
function DefaultFunction(): void {
}

@Component
struct SectionGroup {
  @Prop
  @Require
  title: ResourceStr;
  @BuilderParam
  @Require
  content: () => void = DefaultFunction;

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
  content: () => void = DefaultFunction;

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
  @State activated: boolean = false;

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
                  accessibilityText: 'Music',
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol touched.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip touched.'
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
                  accessibilityText: 'Music',
                  accessibilityDescription: 'Usage hints'
                },
                action: () => {
                  this.getUIContext().getPromptAction().showToast({
                    message: 'Suffix symbol touched.'
                  });
                }
              },
              onClicked: () => {
                this.getUIContext().getPromptAction().showToast({
                  message: 'Chip touched.'
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

This example demonstrates how to set accessibility properties for the chip, including different selected state types.

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
        accessibilityDescription: 'This is a clickable chip', // Overall accessibility description
        accessibilityLevel: 'yes', // Make sure it can be recognized by accessibility services.
        closeOptions: {
          accessibilityDescription: 'Delete this chip. This operation cannot be undone.' // Provide detailed description for the delete button.
        },
        activated: this.clickedChipActivated,
        onClicked: () => {
          this.clickedChipActivated = !this.clickedChipActivated;
          this.getUIContext().getPromptAction().showToast({ message: 'Clickable chip is clicked' });
        },
        onClose: () => {
          this.getUIContext().getPromptAction().showToast({ message: 'The close icon of the clickable chip is clicked' });
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
        accessibilityDescription: 'This is a checkbox chip', // Overall accessibility description
        activated: this.checkedChipActivated,
        onClicked: () => {
          this.checkedChipActivated = !this.checkedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.checkedChipActivated ? 'Checkbox chip is selected' : 'Checkbox chip is deselected'
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
        accessibilityDescription: 'This is a radio chip', // Overall accessibility description
        activated: this.selectedChipActivated,
        onClicked: () => {
          this.selectedChipActivated = !this.selectedChipActivated;
          this.getUIContext().getPromptAction().showToast({
            message: this.selectedChipActivated ? 'Radio chip is selected' : 'Radio chip is deselected'
          });
        }
      })

      // Example of setting the accessibility level
      Chip({
        label: { text: 'Accessibility level is set to no' },
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
