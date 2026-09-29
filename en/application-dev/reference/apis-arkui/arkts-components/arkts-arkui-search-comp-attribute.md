# Search properties/events

```TypeScript
declare class SearchAttribute extends CommonMethod<SearchAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported:

**Inheritance/Implementation:** SearchAttribute extends CommonMethod<SearchAttribute>

**Since:** 8

<!--Device-unnamed-declare class SearchAttribute extends CommonMethod<SearchAttribute>--><!--Device-unnamed-declare class SearchAttribute extends CommonMethod<SearchAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

Sets the text mode of the automatic capitalization mode. This API only provides the interface capability, and the specific implementation is subject to the input method application. When this API is not called, no capitalization conversion takes effect by default, and the specific implementation is subject to the input method application.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): SearchAttribute--><!--Device-SearchAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | Yes | Automatic capitalization mode, used to set the capitalization conversion rule of the input method. The specific implementation is subject to the input method application. |

## cancelButton

```TypeScript
cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions)
```

Sets the style of the clear button on the right. For details, see [Example 2: Setting Search and Delete Icons](../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#example-2-setting-search-and-delete-icons) and [Example 11: Setting a Custom Symbol-Type Cancel Button](../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#example-11-setting-a-custom-symbol-type-cancel-button). If this API is not used, the default clear button style is CancelButtonStyle.INPUT (input style), with an icon size of 16 vp (18 fp on wearable devices) and a color of '#99ffffff' (white with 60% opacity).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions): SearchAttribute--><!--Device-SearchAttribute-cancelButton(value: CancelButtonOptions | CancelButtonSymbolOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CancelButtonOptions](arkts-arkui-search-comp-cancelbuttonoptions-i.md) &#124; [CancelButtonSymbolOptions](arkts-arkui-search-comp-cancelbuttonsymboloptions-i.md) | Yes | Style of the clear button on the right. When style is CancelButtonStyle.CONSTANT, the clear style is displayed by default.<br>**Since:** 12 |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

Sets the cursor style. If this API is not called, the default cursor width is 2.0 vp and the default color is '#007 DFF' (blue).

> **NOTE:** 
> 
> Since API version 12, this API supports setting the text handle color, and the cursor and text handle colors
> remain consistent.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-caretStyle(value: CaretStyle): SearchAttribute--><!--Device-SearchAttribute-caretStyle(value: CaretStyle): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | Yes | Cursor style. |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

Sets whether to compress the leading punctuation at the beginning of a line. When enabled, the spacing to the left of the leading punctuation is compressed, which is suitable for CJK text scenarios such as Chinese and Japanese that pursue typographic aesthetics.

> **NOTE:** 
> 
> - Leading punctuation is not compressed by default.
> 
> - For the punctuation that can be compressed, see the leading punctuation compression range in [ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to compress the leading punctuation at the beginning of a line.<br>true means to compress the leading punctuation; false means not to compress it. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Sets whether the entered text can be copied. If this API is not called, device-local copy (CopyOptions.LocalDevice) is supported by default.

When CopyOptions.None is set, the text in the current Search component cannot be copied, cut, translated, shared, searched, or assisted, but paste and select all are supported.

When CopyOptions.None is set, dragging is not allowed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-copyOption(value: CopyOptions): SearchAttribute--><!--Device-SearchAttribute-copyOption(value: CopyOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether the entered text can be copied. <br>**Note:** <br>When copyOption is not CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE, [enableSelectedDataDetector](#enableselecteddatadetector) does not take effect. |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

Sets a custom keyboard.

When a custom keyboard is set, the system input method is not opened after the input box is activated. Instead, the specified custom component is loaded.

The height of the custom keyboard can be set through the height attribute of the root node of the custom component. The width cannot be set and the system default value is used.

The custom keyboard is presented by overlaying the original UI. When the avoidance mode is not enabled or the input box does not need to be avoided, the original UI of the application is not compressed or lifted.

The custom keyboard cannot obtain focus, but it intercepts gesture events.

By default, the custom keyboard is closed when the input control loses focus. Developers can also control the closing of the keyboard through the [stopEditing](arkts-arkui-search-comp-searchcontroller-c.md#stopediting) method.

When a custom keyboard is set, the input from a physical keyboard can be avoided by binding the [onKeyPreIme](arkts-arkui-common-comp-commonmethod-c.md#onkeypreime) event.

Since API version 23, the custom keyboard can enable continuation through [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature). When switching to another custom keyboard, the switch is performed directly without triggering the keyboard closing and opening animations.

> **NOTE:** 
> 
> This API cannot be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): SearchAttribute--><!--Device-SearchAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; ComponentContent &#124; undefined | Yes | Custom keyboard. When the value is set to undefined, the custom keyboard is disabled.<br>**Since:** 22 |
| options | [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) | No | Whether the custom keyboard supports the avoidance feature. The default configuration is used when this parameter is not passed.<br>**Since:** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

Sets the type, style, and color of the text decoration line. If this API is not called, the default decoration line type is TextDecorationType.None (no decoration line), the color is Color.Black, the style is TextDecorationStyle.SOLID, and the thickness scale is 1.0.

> **NOTE:** 
> 
> - When the lower edge outline of a character intersects with the decoration line, the underline avoidance rule is triggered, and the underline avoids the character at these positions. This commonly applies to English characters such as "g", "j", "y", "q", and "p".
> 
> - When the color of the text decoration line is set to Color.Transparent, the decoration line color follows the font color of the first character in each line. When the color of the text decoration line is set to the transparent color hexadecimal value "#00FFFFFF", the decoration line color is set to transparent.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-decoration(value: TextDecorationOptions): SearchAttribute--><!--Device-SearchAttribute-decoration(value: TextDecorationOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-common-comp-textdecorationoptions-i.md) | Yes | Text decoration line object. |

## dividerColor

```TypeScript
dividerColor(color: Optional<ColorMetrics>)
```

Sets the divider color of the input box.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-dividerColor(color: Optional<ColorMetrics>): SearchAttribute--><!--Device-SearchAttribute-dividerColor(color: Optional<ColorMetrics>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Sets the divider color.<br>By default, the system theme color is used: 0x33000000 in light mode, which indicates black (20% opacity), and 0x33FFFFFF in dark mode, which indicates white (20% opacity). |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets custom menu extension items, allowing users to set the text content, icon, and callback method of the extension items.

When [disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems) or [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems) is called to block the system service menu items in the text selection menu, the input parameter list of the callback method [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) in the editMenuOptions API does not include the blocked menu options.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-editMenuOptions(editMenu: EditMenuOptions): SearchAttribute--><!--Device-SearchAttribute-editMenuOptions(editMenu: EditMenuOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extension menu options, used to set the text content, icon, and callback method of the custom menu extension items. Use this parameter when custom options need to be added to the text selection menu. |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

Sets whether to enable automatic spacing between Chinese and Western characters. If this API is not called, automatic spacing between Chinese and Western characters is disabled by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchAttribute-enableAutoSpacing(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-enableAutoSpacing(enabled: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western characters.<br>true enables automatic spacing, and false disables it. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback. If this API is not used, haptic feedback is enabled by default.

When haptic feedback is enabled, you need to set the **requestPermissions** field in the [module.json5](../../../quick-start/module-configuration-file.md) of the project to enable the vibration permission. The configuration is as follows:

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-SearchAttribute-enableHapticFeedback(isEnabled: boolean): SearchAttribute--><!--Device-SearchAttribute-enableHapticFeedback(isEnabled: boolean): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>The value **true** means to enable haptic feedback, and **false** means the opposite. |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

Sets whether to proactively bring up the soft keyboard when Search gains focus by means other than tapping. If this API is not called, the soft keyboard is proactively brought up by default.

Since API version 10, focus gain is bound to the input method by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-enableKeyboardOnFocus(value: boolean): SearchAttribute--><!--Device-SearchAttribute-enableKeyboardOnFocus(value: boolean): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to proactively bring up the soft keyboard when Search gains focus.<br>The value **true** means to proactively bring it up, and **false** means not to. |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

Sets whether to enable input preview. If this API is not called, input preview is enabled by default.

The preview content is defined as a temporary text state, and text interception is not supported.

> **NOTE:** 
> 
> "Input preview" describes a temporary text state. The input preview feature must be enabled in the input method.
> During text input, before the candidate words are confirmed, the marked text is displayed in the text box. For
> example, when entering Chinese through Pinyin, the Pinyin letters are displayed in the input box before the
> candidate words are confirmed. This state is called input preview.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-enablePreviewText(enable: boolean): SearchAttribute--><!--Device-SearchAttribute-enablePreviewText(enable: boolean): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable input preview.<br>The value **true** means to enable input preview, and **false** means the opposite. |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to perform entity recognition on the selected text. This API depends on the text recognition capability of the underlying device; otherwise, the setting does not take effect. If this API is not called, entity recognition on the selected text is enabled by default, all types of entities are recognized, and the AI menu feature is enabled by default.

When enabled, entities such as email addresses, phone numbers, URLs, dates, and addresses in the selection can be recognized, and the corresponding AI menu items are displayed in the text selection menu.

When the AI menu feature is enabled, after text is selected in the component, the text selection menu can display the corresponding AI menu items, including url (open link), email (create email), phoneNumber (call), address (navigate to), and dateTime (create schedule) in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

When the AI menu takes effect, the selection must contain exactly one complete AI entity for the corresponding option to be displayed. This menu item does not appear together with the askAI menu item in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

This feature takes effect only when CopyOptions is CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-SearchAttribute-enableSelectedDataDetector(enable: boolean | undefined): SearchAttribute--><!--Device-SearchAttribute-enableSelectedDataDetector(enable: boolean | undefined): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable entity recognition on the selected text.<br>true: enables recognition; false: disables recognition. |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

Sets the Enter key type of the input method. If this API is not called, the default Enter key type of the input method is EnterKeyType.Search.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-enterKeyType(value: EnterKeyType): SearchAttribute--><!--Device-SearchAttribute-enterKeyType(value: EnterKeyType): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Enter key type of the input method. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

For multi-line text stacking, supports adaptive line height based on the actual text height. This API takes effect only when the line height is smaller than the actual text height. If this API is not used, the line height does not adapt to the actual text height by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-fallbackLineSpacing(enabled: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-fallbackLineSpacing(enabled: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height adapts to the actual text height.<br>This API takes effect only when the line height is smaller than the actual text height. <br>The value **true** means the line height adapts to the actual text height, and **false** means the line height does not adapt to the actual text height. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color of the input text. If this API is not called, the default font color of the input text is '#FF182431' (dark gray), and on Wearable devices the default is '#dbffffff' (white, with an opacity of 86%). fontSize,fontStyle, fontWeight, and fontFamily are set in [textFont](#textfont).

> **NOTE:** 
> 
> When both fontColor and [shaderStyle](#shaderstyle) are set, fontColor does not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-fontColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-fontColor(value: ResourceColor): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color of the input text. <br>**Note:** <br>When both fontColor and [shaderStyle](#shaderstyle) are set, fontColor does not take effect. |

## fontFeature

```TypeScript
fontFeature(value: string)
```

Sets the font feature, such as monospaced digits.

The format is: normal \| \&lt;feature-tag-value\&gt;.

The format of \&lt;feature-tag-value\&gt; is: \&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ].

There can be multiple \&lt;feature-tag-value\&gt;, separated by commas.

For example, the input format for using monospaced digits is: "ss01" on.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-fontFeature(value: string): SearchAttribute--><!--Device-SearchAttribute-fontFeature(value: string): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Font feature, used to set the advanced typographic capabilities of an OpenType font, such as ligatures and monospaced digits. <br>The format is: "ss01" on. For more supported attributes, see the [fontFeature](arkts-arkui-text-comp-attribute.md#fontfeature) attribute list. |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

Vertically centers the text within a line by evenly distributing the line spacing to the top and bottom of the line. This is applicable to scenarios where precise vertical centering of text is required in multi-line text layout, such as mixed text and icon layout and multi-language mixed layout. If this API is not called, the line spacing is not evenly distributed by default.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchAttribute-halfLeading(halfLeading: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-halfLeading(halfLeading: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to vertically center the text.<br>true means the line spacing is evenly distributed to the top and bottom of the line, and false means it is not. |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Sets whether to add spacing before the first line and after the last line to prevent text truncation. If this API is not used, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-includeFontPadding(include: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-includeFontPadding(include: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing before the first line and after the last line to prevent text truncation.<br>true indicates that spacing is added before the first line and after the last line; false indicates that spacing is not added. |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

Sets an input filter through a regular expression. Input that matches the expression is allowed to be displayed, and input that does not match is filtered out. This is applicable to scenarios where the user input format needs to be restricted, for example, allowing only letters, digits, or specific characters.

In the single-character input scenario, only single-character matching is supported. In the multi-character input scenario, string matching is supported, for example, pasting.

If inputFilter is set and the input character is not an empty character, the text filtering effect attached to the input box type (that is, the type API) becomes invalid.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Regular expression of the input filter. Input that matches the expression is allowed to be displayed, and input that does not match is filtered out. |
| error | Callback&lt;string&gt; | No | Returns the filtered content when the regular expression matching fails. This callback is not triggered if it is not passed in. |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

Sets the keyboard style displayed when the input box is pulled up. This takes effect only after the input method adapts to it. If this API is not used, the default keyboard style is KeyboardAppearance.NONE_IMMERSIVE (non- immersive mode). For details, see [Immersive Mode of the Input Method Application](../../../inputmethod/inputmethod-immersive-mode-guide.md).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SearchAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): SearchAttribute--><!--Device-SearchAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[KeyboardAppearance](../arkts-apis/arkts-arkui-keyboardappearance-e.md)&gt; | Yes | Keyboard style. |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

Sets the character spacing of the text. When this parameter is set to a percentage, the default value is used. When this parameter is set to 0, the default value is used. The string type supports the string form of a number value, with an optional unit, for example, "10" and "10fp".

When the value is negative, the text is compressed. If the negative value is too small, the content area of the component is compressed to 0, and no content is displayed.

This attribute takes effect on each character, including the character at the end of a line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-letterSpacing(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-letterSpacing(value: number | string | Resource): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Character spacing of the text. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

Sets the line height of the text. If the value is not greater than 0, the line height is not limited and the font size is adapted automatically. When the value is of the number type, the unit is fp.

> **NOTE:** 
> 
> When the font height of special characters far exceeds that of other characters in the same line, the text box
> may display unexpected anomalies such as truncation, occlusion, and changes in the relative position of content.
> In this case, developers need to adjust properties such as the component height and line height and modify the
> corresponding page layout.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-lineHeight(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-lineHeight(value: number | string | Resource): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Line height of the text.<br>When the value is of the number type, the unit is fp. When the value is of the string type, it supports the string form of a number-type value and can carry a unit, for example, "10" or "10fp". |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

Sets the maximum font scale of the text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchAttribute-maxFontScale(scale: Optional<number|Resource>): SearchAttribute--><!--Device-SearchAttribute-maxFontScale(scale: Optional<number|Resource>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Maximum font scale of the text. The value of the undefined type is supported. <br>Value range: [1, +∞) <br>**Note:** <br>If the value is less than 1, it is processed as 1. If the value is set to undefined, the original value is retained, and abnormal values do not take effect by default. <br>After the maxFontScale attribute is set, the content of the search component is scaled up to 2 times at most. <br>Before using this attribute, configure the [configuration.json](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) file and the [app.json5](../../../quick-start/app-configuration-file.md) file in the project. For details, see [Example 19: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#example-19-setting-the-minimum-and-maximum-font-scale-factors). |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

Sets the maximum font size for text display. The string type supports the string form of the value of the number type, and can carry a unit, for example, "10" or "10fp".

This attribute must be used together with [minFontSize](#minfontsize) and the layout size limit. Setting it alone does not take effect.

When the adaptive font size takes effect, the fontSize setting does not take effect.

When maxFontSize is less than or equal to 0, or maxFontSize is less than minFontSize, the adaptive font size does not take effect. In this case, the size value in the [textFont](#textfont) attribute takes effect; if it is not set, its default value takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-maxFontSize(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-maxFontSize(value: number | string | Resource): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font size for text display. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## maxLength

```TypeScript
maxLength(value: number)
```

Sets the maximum number of characters that can be entered in the text. By default, no maximum input character limit is set. When the maximum character limit is reached, no more characters can be entered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-maxLength(value: number): SearchAttribute--><!--Device-SearchAttribute-maxLength(value: number): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of characters that can be entered in the text. Value range: [0, +∞). If the value is less than 0, the default value is used, and no limit is set. |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

Sets the minimum font scale factor for text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchAttribute-minFontScale(scale: Optional<number|Resource>): SearchAttribute--><!--Device-SearchAttribute-minFontScale(scale: Optional<number|Resource>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Minimum font scale factor for text. The value **undefined** is supported. <br>Value range: [0, 1] <br>**Note:** <br>If the value is less than 0, it is processed as 0. If the value is greater than 1, it is processed as 1. If the value is **undefined**, the original value is retained, and abnormal values do not take effect by default. <br>Before use, configure the [configuration.json](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) file and the [app.json5](../../../quick-start/app-configuration-file.md) file in the project. For details, see [Example 19: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-search.md#example-19-setting-the-minimum-and-maximum-font-scale-factors). |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

Sets the minimum font size for text display. The string type supports the string form of the value of the number type, and can carry a unit, for example, "10" or "10fp".

It must be used together with [maxFontSize](#maxfontsize) and the layout size limit. Setting it alone does not take effect.

When the adaptive font size takes effect, the fontSize setting does not take effect.

When minFontSize is less than or equal to 0, the adaptive font size does not take effect. In this case, the value of size in the [textFont](#textfont) attribute takes effect; if it is not set, its default value takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-minFontSize(value: number | string | Resource): SearchAttribute--><!--Device-SearchAttribute-minFontSize(value: number | string | Resource): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font size for text display. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

Triggered when the input content changes.

In this callback, if a cursor operation is performed, the developer needs to adjust the cursor logic based on the previewText parameter in the preview scenario to adapt to the preview scenario.

> **NOTE:** 
> 
> onWillChange and onChange form a will/did timing pattern:
> 
> - onWillChange is triggered before the text changes. It can return false to intercept the change; returning true allows the change, and then onChange is triggered.
> 
> - onChange is triggered after the change is complete and cannot intercept it.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onChange(callback: EditableTextOnChangeCallback): SearchAttribute--><!--Device-SearchAttribute-onChange(callback: EditableTextOnChangeCallback): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) | Yes | Callback invoked when the current input text content changes.<br>**Since:** 12 |

## onContentScroll

```TypeScript
onContentScroll(callback: OnContentScrollCallback)
```

Triggered when the text content scrolls.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onContentScroll(callback: OnContentScrollCallback): SearchAttribute--><!--Device-SearchAttribute-onContentScroll(callback: OnContentScrollCallback): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | OnContentScrollCallback | Yes | Callback for text content scrolling. The callback parameters include totalOffsetX (horizontal scroll offset) and totalOffsetY (vertical scroll offset).<br>**Since:** 18 |

## onCopy

```TypeScript
onCopy(callback: Callback<string>)
```

Triggered when a copy operation is performed.

> **NOTE:** 
> 
> onWillCopy and onCopy form a will/did timing pattern:
> 
> - onWillCopy is triggered before the copy operation. It can return false to intercept the copy operation;returning true allows the copy, and then onCopy is triggered.
> 
> - onCopy is triggered after the copy operation is completed and cannot intercept it.
> 
> - The two can be used together: onWillCopy is used for interception control, and onCopy is used to obtain the copy result.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onCopy(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onCopy(callback: Callback<string>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string&gt; | Yes | Callback used to return the copied text content.<br>**Since:** 18 |

## onCut

```TypeScript
onCut(callback: Callback<string>)
```

Triggered when a cut operation is performed.

> **NOTE:** 
> 
> onWillCut and onCut form a will/did timing pattern:
> 
> - onWillCut is triggered before the cut operation. It can return false to intercept the cut operation; returning true allows the cut, and then onCut is triggered.
> 
> - onCut is triggered after the cut operation is completed and cannot be intercepted.
> 
> - The two can be used together: onWillCut is used for interception control, and onCut is used to obtain the cut result.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onCut(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onCut(callback: Callback<string>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string&gt; | Yes | Callback used to return the cut text content.<br>**Since:** 18 |

## onDidDelete

```TypeScript
onDidDelete(callback: Callback<DeleteValue>)
```

Triggered when the deletion is complete.

> **NOTE:** 
> 
> - Tapping the clear button does not trigger the onDidDelete callback.
> 
> - onWillDelete and onDidDelete form a will/did timing pattern:
> 
> - onWillDelete is triggered before the deletion operation and can intercept the deletion by returning false;returning true allows the deletion, after which onDidDelete is triggered.
> 
> - onDidDelete is triggered after the deletion is complete and cannot intercept it.
> 
> - The two can be used together: onWillDelete is used for interception control, and onDidDelete is used to obtain the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-onDidDelete(callback: Callback<DeleteValue>): SearchAttribute--><!--Device-SearchAttribute-onDidDelete(callback: Callback<DeleteValue>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md)&gt; | Yes | Callback invoked when the deletion is complete.<br>Supported only in the scenario where the system input method is used for input. |

## onDidInsert

```TypeScript
onDidInsert(callback: Callback<InsertValue>)
```

Triggered when input is completed.

> **NOTE:** 
> 
> onWillInsert and onDidInsert form a will/did timing pattern:
> 
> - onWillInsert is triggered before the insertion operation and can intercept the insertion by returning false;returning true allows the insertion, after which onDidInsert is triggered.
> 
> - onDidInsert is triggered after the insertion is completed and cannot intercept it.
> 
> - The two can be used together, with onWillInsert for interception control and onDidInsert for obtaining the insertion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-onDidInsert(callback: Callback<InsertValue>): SearchAttribute--><!--Device-SearchAttribute-onDidInsert(callback: Callback<InsertValue>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md)&gt; | Yes | Callback invoked when input is completed.<br>Only supported in the scenario where the system input method is used for input. |

## onEditChange

```TypeScript
onEditChange(callback: Callback<boolean>)
```

Triggered when the input state changes. The component is in editing state when the cursor is present, and in non- editing state when the cursor is absent.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-onEditChange(callback: Callback<boolean>): SearchAttribute--><!--Device-SearchAttribute-onEditChange(callback: Callback<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the editing state changes. The return value **true** indicates that text is being entered, and **false** indicates that the component has no focus and text cannot be entered. |

## onPaste

```TypeScript
onPaste(callback: OnPasteCallback)
```

Called when a paste operation is performed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onPaste(callback: OnPasteCallback): SearchAttribute--><!--Device-SearchAttribute-onPaste(callback: OnPasteCallback): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | OnPasteCallback | Yes | Executed when a paste operation is performed.Callback used to return the pasted text content.<br>**Since:** 18 |

## onSubmit

```TypeScript
onSubmit(callback: Callback<string>)
```

Triggered when the search icon or search button is clicked, or when the search button on the soft keyboard is pressed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onSubmit(callback: Callback<string>): SearchAttribute--><!--Device-SearchAttribute-onSubmit(callback: Callback<string>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string&gt; | Yes | Callback for search submission, whose return value is the text entered in the current search box.<br>**Since:** 18 |

<a id="onsubmit-1"></a>

## onSubmit

```TypeScript
onSubmit(callback: SearchSubmitCallback)
```

Triggered when the search icon or search button is clicked, or when the search button on the soft keyboard is pressed. When the event is submitted, a method is provided to keep the Search component in the editing state.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-SearchAttribute-onSubmit(callback: SearchSubmitCallback): SearchAttribute--><!--Device-SearchAttribute-onSubmit(callback: SearchSubmitCallback): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [SearchSubmitCallback](arkts-arkui-search-comp-searchsubmitcallback-t.md) | Yes | Callback invoked when the search icon or search button is clicked, or when the search button on the soft keyboard is pressed. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: OnTextSelectionChangeCallback)
```

Triggered when the text selection position or the cursor position in editing state changes.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): SearchAttribute--><!--Device-SearchAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | OnTextSelectionChangeCallback | Yes | Callback for the text selection change or cursor position change.<br>**Since:** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

Triggered before the search box is about to bind the input method.

<!--Del-->

Before the search box is about to bind the input method, you can set the keyboard style through the system API [setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig) of `UIContext`. &lt;! --DelEnd--&gt;

Since API version 22, you can call [setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig) of [IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md) to set the input method extension information. After the input method is bound successfully, the input method receives the extension information and can implement custom functions based on it.

IMEClient is valid only during the execution of onWillAttachIME and cannot be called asynchronously.

> **NOTE:** 
> 
> This API cannot be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchAttribute-onWillAttachIME(callback: Callback<IMEClient>): SearchAttribute--><!--Device-SearchAttribute-onWillAttachIME(callback: Callback<IMEClient>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; | Yes | Callback invoked before the search box is about to bind the input method. |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

Triggered when the text content is about to change.

> **NOTE:** 
> 
> - The callback timing of onWillChange is later than onWillInsert and onWillDelete, and earlier than onDidInsert and onDidDelete.
> 
> - onWillChange and onChange form a will/did timing pattern:
> 
> - onWillChange is triggered before the text changes. Returning false intercepts the change; returning true allows the change, and then onChange is triggered.
> 
> - onChange is triggered after the change is complete and cannot intercept it.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SearchAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[EditableTextChangeValue](../arkts-apis/arkts-arkui-editabletextchangevalue-i.md), boolean&gt; | Yes | Callback invoked when the text content is about to change.<br>Returning true indicates a normal modification. Returning false indicates that this trigger is intercepted. |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

Triggered before a copy operation is performed.

> **NOTE:** 
> 
> onWillCopy and onCopy form a will/did timing pattern:
> 
> - onWillCopy is triggered before the copy operation. Returning false intercepts the copy operation; returning true allows the copy, and then onCopy is triggered.
> 
> - onCopy is triggered after the copy operation is completed and cannot intercept it.
> 
> - The two can be used together: onWillCopy is used for interception control, and onCopy is used to obtain the copy result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SearchAttribute-onWillCopy(callback: Callback<string, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillCopy(callback: Callback<string, boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback invoked before the copy operation. When the callback returns a string, it indicates the text content to be copied. When the callback returns a boolean, it indicates whether the currently selected text is allowed to be copied. The value true means that the text is allowed to be copied, and false means that the text is not allowed to be copied. |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

Triggered before a cut operation is performed.

> **NOTE:** 
> 
> onWillCut and onCut form a will/did timing pattern:
> 
> - onWillCut is triggered before the cut operation. Returning false intercepts the cut operation; returning true allows the cut, after which onCut is triggered.
> 
> - onCut is triggered after the cut operation is completed and cannot intercept it.
> 
> - The two can be used together: onWillCut is used for interception control, and onCut is used to obtain the cut result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SearchAttribute-onWillCut(callback: Callback<string, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillCut(callback: Callback<string, boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback invoked before the cut operation. When the callback parameter type is string, it indicates the text content to be cut. When the callback return value is boolean, it indicates whether the currently selected text is allowed to be cut. true: the text is allowed to be cut; false: the text is not allowed to be cut. |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

Triggered when the content is about to be deleted.

> **NOTE:** 
> 
> - Tapping the clear button does not trigger the onWillDelete callback.
> 
> - onWillDelete and onDidDelete form a will/did timing pattern:
> 
> - onWillDelete is triggered before the delete operation. Returning false intercepts the delete operation;returning true allows the deletion, and then onDidDelete is triggered.
> 
> - onDidDelete is triggered after the deletion is complete and cannot intercept it.
> 
> - The two can be used together: onWillDelete is used for interception control, and onDidDelete is used to obtain the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md), boolean&gt; | Yes | Callback invoked when the content is about to be deleted.<br>Returning true indicates normal deletion, and returning false indicates no deletion. <br>This callback is not triggered during the preview delete operation. <br>Only supported for input through the system input method. |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

Triggered when input is about to be inserted.

> **NOTE:** 
> 
> onWillInsert and onDidInsert form a will/did timing pattern:
> 
> - onWillInsert is triggered before the insertion operation. It can intercept the insertion by returning false;returning true allows the insertion, after which onDidInsert is triggered.
> 
> - onDidInsert is triggered after the insertion is complete and cannot intercept it.
> 
> - The two can be used together: onWillInsert is used for interception control, and onDidInsert is used to obtain the insertion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): SearchAttribute--><!--Device-SearchAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md), boolean&gt; | Yes | Callback invoked when input is about to be inserted.<br>Returning true indicates normal insertion, and returning false indicates no insertion. <br>This callback is not triggered during preview and candidate word operations. <br>It is supported only when the input is from the system input method. |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

Sets the text color of the placeholder. If this API is not called, the default placeholder text color is '#99182431' (dark gray, with an opacity of 60%), and on Wearable devices the default is '#99ffffff' (white, with an opacityof 60%).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-placeholderColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-placeholderColor(value: ResourceColor): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Text color of the placeholder. |

## placeholderFont

```TypeScript
placeholderFont(value?: Font)
```

Sets the placeholder text style, including font size, font weight, font family, and font style.

On wearable devices, the default font size is 18fp.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register a custom font.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-placeholderFont(value?: Font): SearchAttribute--><!--Device-SearchAttribute-placeholderFont(value?: Font): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | No | Placeholder text style. If this parameter is not set, the default system font style is used. |

## searchButton

```TypeScript
searchButton(value: ResourceStr, option?: SearchButtonOptions)
```

Sets the search button at the end of the search box.

Tapping the search button triggers both the onSubmit and onClick callbacks.

On Wearable devices, the default font size is 18fp.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-searchButton(value: ResourceStr, option?: SearchButtonOptions): SearchAttribute--><!--Device-SearchAttribute-searchButton(value: ResourceStr, option?: SearchButtonOptions): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text content of the search button at the end of the search box.<br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |
| option | [SearchButtonOptions](arkts-arkui-search-comp-searchbuttonoptions-i.md) | No | Configures the style of the search button at the end of the search box.<br>Default value: <br>{<br>fontSize: '16fp', <br>fontColor: '#ff3f97e9'<br>}<br>**Since:** 10 |

## searchIcon

```TypeScript
searchIcon(value: IconOptions | SymbolGlyphModifier)
```

Sets the style of the search icon on the left. If this attribute is set together with the icon parameter, this attribute takes effect preferentially.

On Wearable devices, the default icon size is 16 vp.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-searchIcon(value: IconOptions | SymbolGlyphModifier): SearchAttribute--><!--Device-SearchAttribute-searchIcon(value: IconOptions | SymbolGlyphModifier): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IconOptions](arkts-arkui-search-comp-iconoptions-i.md) &#124; [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md) | Yes | Style of the search icon on the left. If this attribute is set together with the icon parameter, this attribute takes effect preferentially.<!--RP1--> <br>Default value in light mode: <br>{<br>size: '16vp', <br>color: '#99182431', <br>src: ' '<br>} <br>Default value in dark mode: <br>{<br>size: '16vp', <br>color: '#99ffffff', <br>src: ' '<br>} <!--RP1End--><br>**Since:** 12 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

Sets the highlight color of the selected text. If this attribute is not used, the default color is '#007DFF'(blue).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-selectedBackgroundColor(value: ResourceColor): SearchAttribute--><!--Device-SearchAttribute-selectedBackgroundColor(value: ResourceColor): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Highlight color of the selected text. If the opacity is not set or is set to fully opaque, 20% opacity is used by default. |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Sets the backplane style for text dragging in the search box.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Backplane style for text dragging.<br>When set to undefined: the backplane color follows the theme, showing white in light mode and black in dark mode. |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

Sets whether to hide the system text selection menu. If this API is not called, the system text selection menu is displayed by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-selectionMenuHidden(value: boolean): SearchAttribute--><!--Device-SearchAttribute-selectionMenuHidden(value: boolean): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the system text selection menu.<br>When set to **true**, the system text selection menu is hidden when the input box is clicked to place the cursor, long-pressed, double-tapped, triple-tapped, or right-clicked. <br>When set to **false**, the system text selection menu is displayed. |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

Sets the text shader effect, such as linear gradient and radial gradient. If this API is not called, no gradient effect is applied by default.

> **NOTE:** 
> 
> - When both shaderStyle and [strokeWidth](#strokewidth) are set, shaderStyle does not take effect.
> 
> - When both shaderStyle and [fontColor](#fontcolor) are set, fontColor does not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SearchAttribute-shaderStyle(shader: ShaderStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-shaderStyle(shader: ShaderStyle | undefined): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) &#124; undefined | Yes | Text shader effect. <br>**NOTE:** <br>When both shaderStyle and [strokeWidth](#strokewidth) are set, shaderStyle does not take effect. <br>When both shaderStyle and [fontColor](#fontcolor) are set, fontColor does not take effect. <br>When the value is undefined, no gradient effect is applied. |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

Sets whether to prevent the back key event from being propagated upward. When set to true, the back key event is intercepted and the default system back behavior is not triggered. When set to false, the back key event is propagated upward normally. This API applies to scenarios where custom back key behavior is required, for example, preventing the back key from directly exiting during a search to avoid misoperation, or displaying a confirmation prompt before exiting. If this API is not called, the back key is blocked by default.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SearchAttribute-stopBackPress(isStopped: Optional<boolean>): SearchAttribute--><!--Device-SearchAttribute-stopBackPress(isStopped: Optional<boolean>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to block the back key.<br>The value true means to block, and false means not to block. <br>An invalid value uses the default value. |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

Sets the color of the text stroke.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchAttribute-strokeColor(color: Optional<ResourceColor>): SearchAttribute--><!--Device-SearchAttribute-strokeColor(color: Optional<ResourceColor>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Stroke color. If this API is not called, the default stroke color is the font color. If an invalid value is set, the default value is used. This attribute takes effect only when the stroke width is set through [strokeWidth](#strokewidth). |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

Sets the corner style of the text stroke. This attribute takes effect only when the text stroke is set using strokeWidth.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SearchAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): SearchAttribute--><!--Device-SearchAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) &#124; undefined | Yes | Corner style of the text stroke. <br>If the value is undefined, the style is processed as StrokeJoinStyle.MITER_JOIN. For details, see [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md). In this case, the text corner is rendered as a sharp angle. |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

Sets the width of the text stroke. If this API is not called, the default value 0 is used, and no stroke is applied.

> **NOTE:** 
> 
> When both strokeWidth and [shaderStyle](#shaderstyle) are set, shaderStyle does not take
> effect.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchAttribute-strokeWidth(width: Optional<LengthMetrics>): SearchAttribute--><!--Device-SearchAttribute-strokeWidth(width: Optional<LengthMetrics>): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Width of the text stroke. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, the current setting does not take effect and the default value is used. <br>If the value is less than 0, solid characters are displayed; if the value is greater than 0, hollow characters are displayed. <br>**Note:** <br>When both strokeWidth and [shaderStyle](#shaderstyle) are set, shaderStyle does not take effect. <br>[strokeJoinStyle](#strokejoinstyle) takes effect only when strokeWidth is used to set the text stroke. |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

Sets the alignment of text in the search box. The supported alignment modes are TextAlign.Start, TextAlign.Center, TextAlign.End, TextAlign.LEFT, and TextAlign.RIGHT. TextAlign.JUSTIFY is processed as TextAlign.Start. If this API is not called, the default alignment is TextAlign.Start.

> **NOTE:** 
> 
> textAlign only adjusts the overall layout of the text and does not affect the display order of characters. To
> adjust the display order of characters, see
> [Bidirectional Text Layout and Alignment](../../../ui/arkts-internationalization.md#bidirectional-text-layout-and-alignment).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-textAlign(value: TextAlign): SearchAttribute--><!--Device-SearchAttribute-textAlign(value: TextAlign): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md) | Yes | Alignment of the text in the search box. |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

Specifies the text layout direction. If this API is not called, the default text layout direction follows the component layout direction.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SearchAttribute-textDirection(direction: TextDirection | undefined): SearchAttribute--><!--Device-SearchAttribute-textDirection(direction: TextDirection | undefined): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md) &#124; undefined | Yes | Text layout direction.<br>When set to undefined, it is processed as TextDirection.DEFAULT, meaning that the text layout direction follows the component layout direction. |

## textFont

```TypeScript
textFont(value?: Font)
```

Sets the text style of the input text in the search box, including the font size, font weight, font family, and font style.

On wearable devices, the default font size is 18fp.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register a custom font.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchAttribute-textFont(value?: Font): SearchAttribute--><!--Device-SearchAttribute-textFont(value?: Font): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | No | Text style of the input text in the search box. If this parameter is not set, the system default font style is used. |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

Sets the indentation of the first line of text. If this API is not called, the default indentation of the first line is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-textIndent(value: Dimension): SearchAttribute--><!--Device-SearchAttribute-textIndent(value: Dimension): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Indentation of the first line of text. <br>Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Value range: greater than or equal to 0. If a negative value is set, the default value is used. |

## type

```TypeScript
type(value: SearchType)
```

Sets the input box type. If this API is not called, the default input box type is SearchType.NORMAL (basic input mode without special restrictions).

Different SearchType values bring up the corresponding keyboard type and restrict the input accordingly.

> **NOTE:** 
> 
> If the [inputFilter](#inputfilter) attribute is also set and the input character is not an
> empty character, the text filtering effect attached to the type API becomes invalid, and the filtering rules of
> inputFilter prevail.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchAttribute-type(value: SearchType): SearchAttribute--><!--Device-SearchAttribute-type(value: SearchType): SearchAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SearchType](arkts-arkui-search-comp-searchtype-e.md) | Yes | Input box type. <br>When [inputFilter](#inputfilter) is also set and the input character is not an empty character, the text filtering effect attached to the type API becomes invalid. |
