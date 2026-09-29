# TextArea properties/events

```TypeScript
declare class TextAreaAttribute extends CommonMethod<TextAreaAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported:

> **NOTE:** 
> 
> The default value of the [universal attribute padding](arkts-arkui-common-comp-commonmethod-c.md#padding) is

{

&nbsp;top: '8vp',

&nbsp;right: '16vp',

&nbsp;bottom: '8vp',

&nbsp;left: '16vp'

}

> Since API version 11, the multi-line text box can be set with .width('auto') so that the component width adapts to
> the text width. When adapting, the component width is limited by the constraintSize attribute and the maximum and
> minimum widths passed by the parent container. For other usage, see [Sizing](arkts-arkui-common-comp.md).

**Inheritance/Implementation:** TextAreaAttribute extends CommonMethod<TextAreaAttribute>

**Since:** 7

<!--Device-unnamed-declare class TextAreaAttribute extends CommonMethod<TextAreaAttribute>--><!--Device-unnamed-declare class TextAreaAttribute extends CommonMethod<TextAreaAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

Sets the text mode of the auto-capitalization mode. This API only provides the interface capability, and the specific implementation is subject to the input method application. If this API is not used to set the mode, no capitalization conversion takes effect by default, and the specific implementation is subject to the input method application.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextAreaAttribute--><!--Device-TextAreaAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | Yes | Auto-capitalization mode, used to set the capitalization conversion rule of the input method. The specific implementation is subject to the input method application. |

## barState

```TypeScript
barState(value: BarState)
```

Sets the display mode of the scrollbar of the text box. If this API is not called, the display mode of the scrollbar of the text box is BarState.Auto by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-barState(value: BarState): TextAreaAttribute--><!--Device-TextAreaAttribute-barState(value: BarState): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Display mode of the scrollbar of the text box. |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

Sets the cursor color of the text box. When both the caretColor attribute and the color parameter in the caretStyle attribute are set, the one set later takes effect. For example, if caretColor is set first and then caretStyle.color, caretStyle.color takes effect; conversely, if caretStyle.color is set first and then caretColor, caretColor takes effect. If this API is not used, the default cursor color of the text box is '#007DFF' (blue).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-caretColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-caretColor(value: ResourceColor): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Cursor color of the text box. |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

Sets the cursor style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-caretStyle(value: CaretStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-caretStyle(value: CaretStyle): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | Yes | Cursor style, used to customize the display style of the cursor, including its width and color. |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

Sets whether to enable leading punctuation compression. If this API is not called, leading punctuation compression is disabled by default.

> **NOTE:** 
> 
> - Leading punctuation is not compressed by default.
> 
> - For the punctuation that can be compressed, see the leading punctuation compression range in [ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAreaAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable leading punctuation compression.<br>The value **true** means to enable leading punctuation compression, and **false** means the opposite. |

## contentType

```TypeScript
contentType(contentType: ContentType)
```

Sets the autofill type.<!--RP3--><!--RP3End-->

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-contentType(contentType: ContentType): TextAreaAttribute--><!--Device-TextAreaAttribute-contentType(contentType: ContentType): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contentType | [ContentType](arkts-arkui-textinput-comp-contenttype-e.md) | Yes | Autofill type, which specifies the type of content to be autofilled in the input box so that the system can provide correct autofill suggestions. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Sets whether the entered text can be copied. When CopyOptions.None is set, only paste and select all are supported. If this API is not used, the entered text can be copied by default (CopyOptions.LocalDevice, which supports copying within the device).

When CopyOptions.None is set, drag operations are not supported. The [enableSelectedDataDetector](#enableselecteddatadetector) feature takes effect only when CopyOptions is CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-copyOption(value: CopyOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-copyOption(value: CopyOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether the entered text can be copied. |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

Sets a custom keyboard.

When a custom keyboard is set, the input box does not open the system input method after being activated. Instead, it loads the specified custom component.

The height of the custom keyboard can be set through the **height** attribute of the root node of the custom component, while the width uses the system default value.

The custom keyboard is presented by overlaying the original UI. When the avoidance mode is not enabled or the area where the input box is located is not covered by the keyboard, the original UI of the application is not compressed or lifted.

The custom keyboard cannot obtain focus, but it intercepts gesture events.

By default, the custom keyboard is closed when the input control loses focus. Developers can also close the keyboard through the [TextAreaController](arkts-arkui-textarea-comp-textareacontroller-c.md). [stopEditing](arkts-arkui-textarea-comp-textareacontroller-c.md#stopediting) method.

When a custom keyboard is set, you can bind the [onKeyPreIme](arkts-arkui-common-comp-commonmethod-c.md#onkeypreime) event to avoid input from a physical keyboard.

Since API version 23, the custom keyboard can enable continuation through [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature). When switching to another custom keyboard, the switch is performed directly without triggering the keyboard closing and opening animations.

> **NOTE:** 
> 
> This API cannot be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; ComponentContent &#124; undefined | Yes | Custom keyboard. When the value is set to undefined, the custom keyboard is closed.<br>**Since:** 22 |
| options | [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) | No | Whether the custom keyboard supports the avoidance feature. If this parameter is not passed, the avoidance feature is not supported by default.<br>**Since:** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

Sets the type, style, and color of the text decoration line. If this API is not called, the default text decoration line object is

{

&nbsp;type:&nbsp;TextDecorationType.None,

&nbsp;color:&nbsp;Color.Black,

&nbsp;style:&nbsp;TextDecorationStyle.SOLID,

&nbsp;thicknessScale:&nbsp;1.0

}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-decoration(value: TextDecorationOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-decoration(value: TextDecorationOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-common-comp-textdecorationoptions-i.md) | Yes | Text decoration line object. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets custom extended menu items, allowing users to set the text content, icon, and callback of the extended items.

When [disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems) or [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems) is called to block the system service menu items in the text selection menu, the input parameter list of the callback [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) in editMenuOptions does not include the blocked menu options.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extended menu options used to customize the extended items of the text selection menu, allowing you to set the text content, icon, and callback of the extended items. |

## ellipsisMode

```TypeScript
ellipsisMode(mode: Optional<EllipsisMode>)
```

Sets the ellipsis position. The ellipsisMode attribute must be used together with [textOverflow](#textoverflow) set to TextOverflow.Ellipsis and [maxLines](#maxlines). Setting the ellipsisMode attribute alone does not take effect. If this API is not called, the default ellipsis position is EllipsisMode.END.

EllipsisMode.START and EllipsisMode.CENTER take effect only when [maxLines](#maxlines) is set to 1.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextAreaAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextAreaAttribute--><!--Device-TextAreaAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[EllipsisMode](../arkts-apis/arkts-arkui-ellipsismode-e.md)&gt; | Yes | Ellipsis position. It must be used together with [textOverflow](#textoverflow) set to TextOverflow.Ellipsis and [maxLines](#maxlines). Setting it alone does not take effect. <br>EllipsisMode.START and EllipsisMode.CENTER take effect only when maxLines is set to 1. |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

Sets whether to enable autofill. <!--RP2--><!--RP2End-->If this API is not used to set the value, autofill is enabled by default.

<!--RP6--><!--RP6End-->

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-enableAutoFill(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableAutoFill(value: boolean): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable autofill.<br>The value **true** means to enable autofill, and **false** means the opposite. |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

Sets whether to enable automatic spacing between Chinese and Western characters. If this API is not called, automatic spacing between Chinese and Western characters is disabled by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western characters.<br>The value **true** means to enable automatic spacing, and **false** means to disable it. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback. If this attribute is not used, haptic feedback is enabled by default.

When haptic feedback is enabled, you need to set the **requestPermissions** field in the [module.json5](../../../quick-start/module-configuration-file.md) of the project to enable the vibration permission. The configuration is as follows:

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TextAreaAttribute-enableHapticFeedback(isEnabled: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableHapticFeedback(isEnabled: boolean): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>The value **true** means to enable haptic feedback, and **false** means the opposite. |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

Sets whether to actively pull up the soft keyboard when the **TextArea** component gains focus by means other than tapping. If this API is not called, the soft keyboard is actively pulled up by default when the component gains focus by means other than tapping.

Since API version 10, the input method is bound by default when the component gains focus.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-enableKeyboardOnFocus(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enableKeyboardOnFocus(value: boolean): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to actively pull up the soft keyboard when the component gains focus by means other than tapping.<br>The value **true** means to actively pull up the soft keyboard, and **false** means the opposite. |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

Sets whether to enable input preview text. If this API is not called, input preview text is enabled by default.

Preview text is defined as a temporary text state, and text interception is not supported for it.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-enablePreviewText(enable: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-enablePreviewText(enable: boolean): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable input preview text.<br>The value **true** means to enable it, and **false** means to disable it. |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to perform entity recognition on the selected text. This API depends on the text recognition capability of the underlying device; otherwise, the setting does not take effect. If this API is not called, entity recognition on the selected text is enabled by default.

When enableSelectedDataDetector is set to true, all types of entities are recognized by default.

After this feature is enabled, entities such as email addresses, phone numbers, URLs, dates, and addresses in the selection can be recognized, and the corresponding AI menu items are displayed in the text selection menu. The AI menu feature is enabled by default.

When the AI menu feature is enabled, after text is selected in the component, the text selection menu can display the corresponding AI menu items, including url (open link), email (create email), phoneNumber (call), address (navigate to), and dateTime (create schedule) in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

When the AI menu takes effect, the selection must contain exactly one complete AI entity for the corresponding option to be displayed. This menu item does not appear together with the askAI menu item in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

This feature takes effect only when CopyOptions is CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextAreaAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to perform entity recognition on the selected text.<br>true: enables recognition; false: disables recognition. <br>This feature takes effect only when CopyOptions is CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE. |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

Sets the type of the Enter key on the input method. If this API is not called, the default type of the Enter key on the input method is EnterKeyType.NEW_LINE.

> **NOTE:** 
> 
> Since API version 12, this API is supported in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-enterKeyType(value: EnterKeyType): TextAreaAttribute--><!--Device-TextAreaAttribute-enterKeyType(value: EnterKeyType): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Type of the Enter key on the input method. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

Supports adaptive line height based on the actual text height for stacked multi-line text. This API takes effect only when the line height is smaller than the actual text height. If this API is not called, the line height does not adapt to the actual text height by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAreaAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height adapts to the actual text height.<br>The value **true** means the line height adapts to the actual text height, and **false** means the line height does not adapt to the actual text height. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color. If this API is not used, the default font color follows the theme.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-fontColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-fontColor(value: ResourceColor): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color, used to customize the color of the input text. <br>**Note:** When [shaderStyle](#shaderstyle) is also set, shaderStyle takes precedence and fontColor does not take effect. |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

Sets the font list.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register a custom font.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-fontFamily(value: ResourceStr): TextAreaAttribute--><!--Device-TextAreaAttribute-fontFamily(value: ResourceStr): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font list. The default font is 'HarmonyOS Sans'.<br>When multiple fonts are used, separate them with commas (','). The fonts take effect in the order of priority. For example: 'Arial,HarmonyOS Sans'. |

## fontFeature

```TypeScript
fontFeature(value: string)
```

Sets the font feature, such as monospaced digits.

The format is: normal \| \&lt;feature-tag-value\&gt;

The format of \&lt;feature-tag-value\&gt; is: \&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]

There can be multiple \&lt;feature-tag-value\&gt;, separated by commas (,).

For example, the input format for monospaced digits is: "ss01" on.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-fontFeature(value: string): TextAreaAttribute--><!--Device-TextAreaAttribute-fontFeature(value: string): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Font feature, used to set the special display effect of text, such as monospaced digits. The format is: normal &#124; &lt;feature-tag-value&gt;. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size. If this API is not called, the default font size is 16fp. On Wearable devices, the default font size is 18fp.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-fontSize(value: Length): TextAreaAttribute--><!--Device-TextAreaAttribute-fontSize(value: Length): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. When fontSize is of the number type, the unit fp is used. Percentage strings are not supported. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style. If this API is not called, the default font style is FontStyle.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-fontStyle(value: FontStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-fontStyle(value: FontStyle): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight of the text. If the value is too large, the text may be truncated under certain fonts. If this API is not called, the default font weight is FontWeight.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAreaAttribute--><!--Device-TextAreaAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text.<br>For the number type, the value ranges from 100 to 900 at an interval of 100. A larger value indicates a heavier font weight. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight. If the value is too large, the text may be truncated under certain fonts. If the value is out of the valid range or does not meet the interval requirement, 400 is used. <br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

Sets the text to be vertically centered within a line, evenly distributing the line spacing to the top and bottom of the line. If this API is not called, the line spacing is not evenly distributed by default.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextAreaAttribute-halfLeading(halfLeading: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-halfLeading(halfLeading: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Sets whether the text is vertically centered.<br>The value **true** means to evenly distribute the line spacing to the top and bottom of the line, and **false** means the opposite. |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

Sets how the text height is adapted. If this API is not called, the text height is adapted by default in the manner of TextHeightAdaptivePolicy.MAX_LINES_FIRST.

When this parameter is set to TextHeightAdaptivePolicy.MAX_LINES_FIRST, the [maxLines](#maxlines) attribute is preferentially used to adjust the text height. If the layout size obtained by using the maxLines attribute exceeds the layout constraint, the font size is reduced within the range of [minFontSize](#minfontsize) and [maxFontSize](#maxfontsize) to display more text.

When the component is set to the inline input style, the font size in the editing state may differ from that in the non-editing state.

When this parameter is set to TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST, the minFontSize attribute is preferentially used to adjust the text height. If the text can be laid out in a single line by using the minFontSize attribute, the font size is increased within the range of minFontSize and maxFontSize, and the largest possible font size is used.

When this parameter is set to TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST, the layout constraint is preferentially used to adjust the text height. If the layout size exceeds the layout constraint, the font size is reduced within the range of minFontSize and maxFontSize to meet the layout constraint.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute--><!--Device-TextAreaAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | Yes | How the text height is adapted.<br>MAX_LINES_FIRST preferentially uses maxLines to adjust the height, and reduces the font size within the range of minFontSize and maxFontSize when the layout constraint is exceeded; MIN_FONT_SIZE_FIRST preferentially uses minFontSize to adjust the height; LAYOUT_CONSTRAINT_FIRST preferentially uses the layout constraint to adjust the height, and reduces the font size when the constraint is exceeded. |

## horizontalScrolling

```TypeScript
horizontalScrolling(enabled: Optional<boolean>)
```

Sets whether to enable horizontal scrolling when the text width exceeds the width of the content area. If this API is not called, horizontal scrolling is disabled.

> **NOTE:** 
> 
> Horizontal scrolling is not supported in <!--Del-->any of <!--DelEnd-->the following:
> [TextContentStyle](../arkts-apis/arkts-arkui-textcontentstyle-e.md) is INLINE, that is, the polymorphic style of the text box is inline
> mode<!--Del-->; and [voiceButton](#voicebutton) is enabled<!--DelEnd-->.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-TextAreaAttribute-horizontalScrolling(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-horizontalScrolling(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable horizontal scrolling.<br>The value **true** means to enable horizontal scrolling, and **false** means to disable horizontal scrolling, in which case the text wraps automatically. |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Sets whether to add spacing to the first and last lines to avoid text truncation. If this API is not called, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAreaAttribute-includeFontPadding(include: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-includeFontPadding(include: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing to the first and last lines to avoid text truncation.<br>true indicates that spacing is added to the first and last lines; false indicates that no spacing is added to the first and last lines. |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: (value: string) => void)
```

Sets an input filter through a regular expression. Input that matches the expression is allowed to be displayed, and input that does not match is filtered out.

In the single-character input scenario, only single-character matching is supported. In the multi-character input scenario, string matching is supported, for example, pasting.

Since API version 11, if inputFilter is set and the input character is not an empty character, the text filtering effect attached to the [type](#type) API becomes invalid.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-inputFilter(value: ResourceStr, error?: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-inputFilter(value: ResourceStr, error?: (value: string) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Regular expression. |
| error | (value: string) =&gt; void | No | Callback invoked to return the filtered content when the regular expression matching fails. No value is returned when the matching succeeds. If this parameter is not passed, the filtered content is not processed. |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

Sets the style of the keyboard that is pulled up for the input box. This takes effect only after the input method adapts to it. For details, see [Immersive Mode of the Input Method Application](../../../inputmethod/inputmethod-immersive-mode-guide.md). If this API is not called, the default keyboard style is KeyboardAppearance.NONE_IMMERSIVE.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextAreaAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextAreaAttribute--><!--Device-TextAreaAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[KeyboardAppearance](../arkts-apis/arkts-arkui-keyboardappearance-e.md)&gt; | Yes | Keyboard style.<br>When set to KeyboardAppearance.NONE_IMMERSIVE, a non-immersive keyboard is displayed; when set to KeyboardAppearance.IMMERSIVE, an immersive keyboard is displayed. |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

Sets the character spacing of the text. When this value is set to a percentage, the default value is used. When this value is set to 0, the default value is used. The string type supports the string form of a number value, with an optional unit, for example, "10" and "10fp". If this API is not called, the default character spacing is 0fp.

When the value is negative, the text is compressed. If the negative value is too small, the component content area is compressed to 0, resulting in no content being displayed.

This attribute takes effect on each character, including the character at the end of a line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-letterSpacing(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-letterSpacing(value: number | string | Resource): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Character spacing of the text. <br>When set to a percentage, the default value is used; when set to 0, the default value is used; a negative value compresses the text, and if it is too small, no content may be displayed. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

Sets the line breaking rule. This attribute applies to scenarios where the line breaking effect of multi-line text needs to be optimized. For example, the GREEDY strategy is suitable for fast typesetting of general text, the HIGH_QUALITY strategy is suitable for formal documents that require high typesetting quality, and the BALANCED strategy is suitable for display scenarios where the width of each line needs to be balanced. This attribute takes effect only when [wordBreak](#wordbreak) is not equal to WordBreak.BREAK_ALL, and hyphenation is not supported. If this attribute is not set, the default line breaking rule is LineBreakStrategy.GREEDY.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute--><!--Device-TextAreaAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | Yes | Line breaking rule of the text. This attribute takes effect only when [wordBreak](#wordbreak) is not equal to WordBreak.BREAK_ALL, and hyphenation is not supported. |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

Sets the line height of the text. If the value is not greater than 0, the line height is not limited and adapts to the font size.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-lineHeight(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-lineHeight(value: number | string | Resource): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Line height of the text. A [pixel unit](arkts-arkui-common-comp.md) must be explicitly specified, for example, '10px'. A percentage string can also be set, for example, '100%'. <br>**Note:** If no pixel unit is specified, the default unit fp is used. For example, '10' is equivalent to 10. |

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics)
```

Sets the line spacing of the text. If the value is not greater than 0, the default value 0 is used. If this API is not called, the default line spacing of the text is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics): TextAreaAttribute--><!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Line spacing of the text. |

<a id="linespacing-1"></a>

## lineSpacing

```TypeScript
lineSpacing(value: LengthMetrics, options?: LineSpacingOptions)
```

Sets the line spacing of the text. When LineSpacingOptions is not configured, line spacing is applied by default above the first line and below the last line. When this API is not used, the default line spacing of the text is 0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-lineSpacing(value: LengthMetrics, options?: LineSpacingOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | LengthMetrics | Yes | Line spacing of the text. If the value is not greater than 0, the default value 0 is used. |
| options | [LineSpacingOptions](../arkts-apis/arkts-arkui-linespacingoptions-i.md) | No | Line spacing configuration options. |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

Sets the maximum font scale factor of the text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextAreaAttribute-maxFontScale(scale: Optional<number|Resource>): TextAreaAttribute--><!--Device-TextAreaAttribute-maxFontScale(scale: Optional<number|Resource>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Maximum font scale factor of the text. The undefined type is supported. <br>Value range: [1, +∞) <br>**Note:** <br>If the value is less than 1, it is processed as 1. Abnormal values do not take effect by default. <br>Before using this API, configure the configuration.json file and app.json5 file in the project. For details, see [Example 17: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#example-17-setting-the-minimum-and-maximum-font-scale-factors). |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

Sets the maximum font size for text display. The string type supports the string form of the value that the number type accepts, and can carry a unit, for example, "10" or "10fp".

It must be used together with [minFontSize](#minfontsize) and [maxLines](#maxlines) or a layout size limit. Setting it alone does not take effect.

When adaptive font size takes effect, the fontSize setting does not take effect.

When maxFontSize is less than or equal to 0, or maxFontSize is less than minFontSize, adaptive font size does not take effect. In this case, the value of the [fontSize](#fontsize) attribute takes effect; if fontSize is not set, its default value takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-maxFontSize(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-maxFontSize(value: number | string | Resource): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum font size for text display. <br>It must be used together with minFontSize and maxLines or a layout size limit. Setting it alone does not take effect. <br>Value range: (0, +∞). If the value is out of range, the value of the fontSize attribute takes effect. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## maxLength

```TypeScript
maxLength(value: number)
```

Sets the maximum number of characters that can be entered. When the maximum number of characters is reached, no more characters can be entered. If this API is not called, no maximum character limit is set by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-maxLength(value: number): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLength(value: number): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of characters that can be entered.<br>Value range: [0, UINT32_MAX]. If value is less than 0, no limit is set. |

## maxLines

```TypeScript
maxLines(value: number)
```

Sets the maximum number of lines that can be displayed for the text. You can optionally set the behavior when the text exceeds the maximum number of lines to scrolling or truncation. If this API is not called, the maximum number of lines that can be displayed for the text is 3 by default in the inline input style editing state, and the default value is UINT32_MAX in non-inline mode.

> **NOTE:** 
> 
> When textOverflow is configured:
> 
> - maxLines specifies the maximum number of lines that can be displayed for the text, and the excess part is directly truncated.
> 
> When textOverflow is not configured:
> 
> - Inline mode (focused state): when the content exceeds maxLines, the text can be scrolled for display.
> 
> - Inline mode (unfocused state): maxLines does not take effect.
> 
> - Non-inline mode: the text is truncated by the number of lines specified by maxLines.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-maxLines(value: number): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLines(value: number): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of lines that can be displayed for the text in the inline input style editing state.<br>When textOverflow is configured, the excess part is truncated. When textOverflow is not configured, the text can be scrolled for display in the focused state in inline mode, and this parameter does not take effect in the unfocused state. In non-inline mode, the text is truncated by line. <br>Value range: (0, UINT32_MAX]. If 0 or a negative number is passed in, the default value is used. |

<a id="maxlines-1"></a>

## maxLines

```TypeScript
maxLines(lines: number, options: MaxLinesOptions)
```

Sets the maximum number of lines that can be displayed for the text, and optionally sets the behavior when the maximum number of lines is exceeded to scrolling or truncation. If this API is not called, the maximum number of lines that can be displayed for the text in the editing state of the inline input style is 3 by default, and the default value in non-inline mode is UINT32_MAX.

> **NOTE:** 
> 
> When textOverflow is configured:
> 
> - maxLines specifies the maximum number of lines that can be displayed for the text, and the excess part is directly truncated.
> 
> When textOverflow is not configured:
> 
> - Inline mode (focused state): when the content exceeds maxLines, the text can be scrolled for display.
> 
> - Inline mode (unfocused state): maxLines does not take effect.
> 
> - Non-inline mode: the text is truncated by the number of lines specified by maxLines.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-maxLines(lines: number, options: MaxLinesOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-maxLines(lines: number, options: MaxLinesOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lines | number | Yes | Maximum number of lines that can be displayed for the text in the editing state of the inline input style.<br>When textOverflow is configured, the excess part can be configured to be truncated or scrolled. When textOverflow is not configured, the text can be scrolled for display in the focused state of inline mode, and this parameter does not take effect in the unfocused state. In non-inline mode, the text is truncated by line. <br>Value range: (0, +∞). If 0 or a negative number is passed in, the default value is used. |
| options | [MaxLinesOptions](../arkts-apis/arkts-arkui-maxlinesoptions-i.md) | Yes | Display effect when the text is too long. |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

Sets the minimum font scale factor of the text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextAreaAttribute-minFontScale(scale: Optional<number|Resource>): TextAreaAttribute--><!--Device-TextAreaAttribute-minFontScale(scale: Optional<number|Resource>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Minimum font scale factor of the text. The value **undefined** is supported. <br>Value range: [0, 1] <br>**Note:** <br>If the value is less than 0, it is processed as 0. If the value is greater than 1, it is processed as 1. An invalid value does not take effect by default. <br>Before using this API, configure the configuration.json file and app.json5 file in the project. For details, see [Example 17: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#example-17-setting-the-minimum-and-maximum-font-scale-factors). |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

Sets the minimum font size for the text. The string type supports the string form of the value of the number type, and can carry a unit, for example, "10" or "10fp".

This attribute must be used together with [maxFontSize](#maxfontsize) and [maxLines](#maxlines) or a layout size limit. Setting it alone does not take effect.

When the adaptive font size takes effect, the fontSize setting does not take effect.

When minFontSize is less than or equal to 0, the adaptive font size does not take effect. In this case, the value of the [fontSize](#fontsize) attribute takes effect, or its default value takes effect if fontSize is not set.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-minFontSize(value: number | string | Resource): TextAreaAttribute--><!--Device-TextAreaAttribute-minFontSize(value: number | string | Resource): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum font size for the text. <br>This attribute must be used together with maxFontSize and maxLines or a layout size limit. Setting it alone does not take effect. <br>Value range: (0, maxFontSize]. If the value is out of range, the value of the fontSize attribute takes effect. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## minLines

```TypeScript
minLines(lines: Optional<number>)
```

Sets the minimum number of lines. The component height is automatically adjusted based on lines to ensure that the displayed height is not lower than the height corresponding to lines. If [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) is set, the final displayed height of the component is within the constraints of [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize). If this API is not called, the default minimum number of lines is 1.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-minLines(lines: Optional<number>): TextAreaAttribute--><!--Device-TextAreaAttribute-minLines(lines: Optional<number>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lines | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Minimum number of lines.<br>Value range: [1, INT32_MAX] <br>If the value of lines is less than 1, the default value is used. |

## onChange

```TypeScript
onChange(callback: EditableTextOnChangeCallback)
```

Triggered when the input content changes.

In this callback, if a cursor operation is performed, the developer needs to adjust the cursor logic based on the previewText parameter of [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) in the preview text scenario, so as to adapt to the preview text scenario.

> **NOTE:** 
> 
> onWillChange and onChange form a will/did timing pattern:
> 
> - onWillChange is triggered before the text changes. It can intercept the change by returning false; returning true allows the change, and then onChange is triggered.
> 
> - onChange is triggered after the change is complete and cannot intercept it.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onChange(callback: EditableTextOnChangeCallback): TextAreaAttribute--><!--Device-TextAreaAttribute-onChange(callback: EditableTextOnChangeCallback): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) | Yes | Callback invoked when the current input text content changes.<br>**Since:** 12 |

## onContentScroll

```TypeScript
onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void)
```

Triggered when the text content scrolls.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onContentScroll(callback: (totalOffsetX: number, totalOffsetY: number) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (totalOffsetX: number, totalOffsetY: number) =&gt; void | Yes | callback of the listened event. |

## onCopy

```TypeScript
onCopy(callback: (value: string) => void)
```

Triggered when a copy operation is performed.

> **NOTE:** 
> 
> onWillCopy and onCopy form a will/did timing pattern:
> 
> - onWillCopy is triggered before the copy operation. It can intercept the copy operation by returning false;returning true allows the copy operation, after which onCopy is triggered.
> 
> - onCopy is triggered after the copy operation is complete and cannot intercept it.
> 
> - The two can be used together: onWillCopy is used for interception control, and onCopy is used to obtain the copy result.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onCopy(callback: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onCopy(callback: (value: string) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string) =&gt; void | Yes | Called when using the Clipboard menu. |

## onCut

```TypeScript
onCut(callback: (value: string) => void)
```

Triggers this callback when a cut operation is performed.

> **NOTE:** 
> 
> onWillCut and onCut form a will/did timing pattern:
> 
> - onWillCut is triggered before the cut operation and can intercept the cut operation by returning **false**;returning **true** allows the cut, and then onCut is triggered.
> 
> - onCut is triggered after the cut operation is complete and cannot intercept it.
> 
> - The two can be used together: onWillCut is used for interception control, and onCut is used to obtain the cut result.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onCut(callback: (value: string) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onCut(callback: (value: string) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string) =&gt; void | Yes | Called when using the Clipboard menu. |

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
> - onWillDelete is triggered before the deletion operation. Returning false intercepts the deletion operation;returning true allows the deletion, and then onDidDelete is triggered.
> 
> - onDidDelete is triggered after the deletion is complete and cannot intercept the operation.
> 
> - The two can be used together: onWillDelete is used for interception control, and onDidDelete is used to obtain the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-onDidDelete(callback: Callback<DeleteValue>): TextAreaAttribute--><!--Device-TextAreaAttribute-onDidDelete(callback: Callback<DeleteValue>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md)&gt; | Yes | Callback invoked when the deletion is complete.<br>Tapping the clear button does not trigger the onDidDelete callback. <br>Only supported in the scenario where the system input method is used for input. |

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
> - The two can be used together: onWillInsert is used for interception control, and onDidInsert is used to obtain the insertion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-onDidInsert(callback: Callback<InsertValue>): TextAreaAttribute--><!--Device-TextAreaAttribute-onDidInsert(callback: Callback<InsertValue>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md)&gt; | Yes | Callback invoked when input is completed.<br>Only supported for input from the system input method. |

## onEditChange

```TypeScript
onEditChange(callback: (isEditing: boolean) => void)
```

Triggered when the input state changes. The component is in editing state when a cursor is present, and in non- editing state when no cursor is present.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onEditChange(callback: (isEditing: boolean) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onEditChange(callback: (isEditing: boolean) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isEditing: boolean) =&gt; void | Yes | Triggered when the text area status changes. |

## onPaste

```TypeScript
onPaste(callback: (value: string, event: PasteEvent) => void)
```

Triggered when a paste operation is performed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onPaste(callback: (value: string, event: PasteEvent) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onPaste(callback: (value: string, event: PasteEvent) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: string, event: PasteEvent) =&gt; void | Yes | Called when using the Clipboard menu. |

## onSubmit

```TypeScript
onSubmit(callback: (enterKey: EnterKeyType) => void)
```

Triggered when the Enter key on the soft keyboard is pressed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (enterKey: EnterKeyType) =&gt; void | Yes | callback of the listened event. |

<a id="onsubmit-1"></a>

## onSubmit

```TypeScript
onSubmit(callback: TextAreaSubmitCallback)
```

Triggered when the Enter key on the soft keyboard is pressed. The callback parameter provides a method for keeping the TextArea in the editing state.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextAreaAttribute-onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute--><!--Device-TextAreaAttribute-onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TextAreaSubmitCallback](arkts-arkui-textarea-comp-textareasubmitcallback-t.md) | Yes | Callback invoked when the Enter key on the soft keyboard is pressed. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void)
```

Triggered when the position of the selected text or the cursor position in editing state changes.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAreaAttribute--><!--Device-TextAreaAttribute-onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (selectionStart: number, selectionEnd: number) =&gt; void | Yes | callback of the listened event. |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient> | undefined)
```

Triggered before the input box is about to attach the input method.

<!--Del-->

Before the input box is about to attach the input method, you can set the keyboard style through the system API [setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig) of `UIContext`. &lt;! --DelEnd--&gt;

Since API version 22, you can call [setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig) of [IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md) to set the extended information of the input method. After the input method is attached successfully, the input method receives the extended information and can implement custom functions based on it.

IMEClient is valid only during the execution of onWillAttachIME and cannot be called asynchronously.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextAreaAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillAttachIME(callback: Callback<IMEClient> | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; &#124; undefined | Yes | Triggered before the input box is about to attach the input method. |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

Triggered when the text content is about to change.

> **NOTE:** 
> 
> - The callback timing of onWillChange is later than that of onWillInsert and onWillDelete, and earlier than that of onDidInsert and onDidDelete.
> 
> - onWillChange and onChange form a will/did timing pattern:
> 
> - onWillChange is triggered before the text changes. You can return false to intercept the change; returning true allows the change, and then onChange is triggered.
> 
> - onChange is triggered after the change is complete and cannot intercept the change.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.The callback timing of onWillChange is later than that of onWillInsert and onWillDelete, and earlier than that of onDidInsert and onDidDelete.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextAreaAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[EditableTextChangeValue](../arkts-apis/arkts-arkui-editabletextchangevalue-i.md), boolean&gt; | Yes | Callback invoked when the text content is about to change.<br>If true is returned, the change is applied normally. If false is returned, the current trigger is intercepted. |

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
> - onCopy is triggered after the copy operation is complete and cannot intercept it.
> 
> - The two can be used together: onWillCopy is used for interception control, and onCopy is used to obtain the copy result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-onWillCopy(callback: Callback<string, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillCopy(callback: Callback<string, boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback invoked before the copy operation. The callback parameter is the text content to be copied (string type). The callback returns a boolean value: true indicates that the text is allowed to be copied, and false indicates that the text is not allowed to be copied. |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

Triggered before a cut operation is performed.

> **NOTE:** 
> 
> onWillCut and onCut form a will/did timing pattern:
> 
> - onWillCut is triggered before the cut operation. Returning false intercepts the cut operation; returning true allows the cut, and then onCut is triggered.
> 
> - onCut is triggered after the cut operation is completed and cannot be intercepted.
> 
> - The two can be used together: onWillCut is used for interception control, and onCut is used to obtain the cut result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-onWillCut(callback: Callback<string, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillCut(callback: Callback<string, boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback invoked before the cut operation. The callback parameter is the text content to be cut (string type). The callback returns a boolean value: true indicates that the text is allowed to be cut, and false indicates that the text is not allowed to be cut. |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

Triggered when a deletion is about to occur.

Tapping the clear button does not trigger the onWillDelete callback.

> **NOTE:** 
> 
> - Tapping the clear button does not trigger the onWillDelete callback.
> 
> - onWillDelete and onDidDelete form a will/did timing pattern:
> 
> - onWillDelete is triggered before the deletion operation. Returning false intercepts the deletion; returning true allows the deletion, after which onDidDelete is triggered.
> 
> - onDidDelete is triggered after the deletion is complete and cannot intercept it.
> 
> - The two can be used together: onWillDelete is used for interception control, and onDidDelete is used to obtain the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md), boolean&gt; | Yes | Callback invoked when a deletion is about to occur.<br>Returning true indicates a normal deletion, and returning false indicates that the deletion is not performed. <br>This callback is not triggered during preview and candidate word operations. Tapping the clear button does not trigger the onDidDelete callback. <br>Only supported in the scenario where the system input method is used. |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

Triggers this callback when text is about to be inserted.

> **NOTE:** 
> 
> onWillInsert and onDidInsert form a will/did timing pattern:
> 
> - onWillInsert is triggered before the insertion operation. Returning false intercepts the insertion; returning true allows the insertion, after which onDidInsert is triggered.
> 
> - onDidInsert is triggered after the insertion is complete and cannot intercept it.
> 
> - The two can be used together: onWillInsert is used for interception control, and onDidInsert is used to obtain the insertion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md), boolean&gt; | Yes | Callback invoked when text is about to be inserted.<br>Returning true indicates normal insertion, and returning false indicates no insertion. <br>This callback is not triggered during preview and candidate word operations. <br>It is supported only in the scenario of input through the system input method. |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

Sets whether to enable orphan character optimization during text layout. If this API is not called, orphan character optimization is disabled by default.

Orphan character optimization improves text layout by handling orphan characters (the first character of the last line of a paragraph) more efficiently. When enabled, it adjusts the line break points to avoid orphan characters as much as possible. The orphan character optimization feature takes effect only when [wordBreak](#wordbreak) is not BREAK_ALL and the [locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the first [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the text to be laid out is "zh-Hans" or "zh-Hant".

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable orphan character optimization for the last line of a paragraph.<br>The value true means to enable orphan character optimization, and false means to disable it. <br>If the value is undefined or null, orphan character optimization is disabled. |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

Sets the color of the placeholder text. If this API is not called, the placeholder text color follows the theme by default, which is #ffffff (white) in dark mode and #000000 (black) in light mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-placeholderColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-placeholderColor(value: ResourceColor): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the placeholder text. |

## placeholderFont

```TypeScript
placeholderFont(value: Font)
```

Sets the placeholder text style, including the font size, font weight, font family, and font style. If this API is not called, the default placeholder text style is as follows: font size 14fp, font weight FontWeight.Normal, font family HarmonyOS Sans, and font style FontStyle.Normal.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register a custom font.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-placeholderFont(value: Font): TextAreaAttribute--><!--Device-TextAreaAttribute-placeholderFont(value: Font): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Placeholder text style, including the font size, font weight, font family, and font style. Used to customize the display style of the placeholder text. |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

Sets whether to enable hanging punctuation at the end of a line. If this API is not used, punctuation is not hung by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-punctuationOverflow(enabled: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable hanging punctuation at the end of a line.<br>The value **true** means to enable hanging punctuation at the end of a line, and **false** means the opposite. If the value is **undefined** or **null**, hanging punctuation is not enabled. |

## scrollBarColor

```TypeScript
scrollBarColor(thumbColor: ColorMetrics | undefined)
```

Sets the color of the scrollbar. If this API is not called, the default scrollbar color is '#66182431', which is dark gray (with 40% opacity) and appears gray.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextAreaAttribute-scrollBarColor(thumbColor: ColorMetrics | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-scrollBarColor(thumbColor: ColorMetrics | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| thumbColor | ColorMetrics &#124; undefined | Yes | Color of the scrollbar. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

Sets the highlight color of the selected text. If the opacity is not set or is set to fully opaque, 20% opacity is used by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-selectedBackgroundColor(value: ResourceColor): TextAreaAttribute--><!--Device-TextAreaAttribute-selectedBackgroundColor(value: ResourceColor): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Highlight color of the selected text. |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Sets the backplane style of the text being dragged in the multi-line text input box.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAreaAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Backplane style of the text being dragged.<br>When set to undefined, the backplane color follows the theme: white in light mode and black in dark mode. |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

Sets whether to hide the system text selection menu. If this API is not called, the system text selection menu is displayed by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-selectionMenuHidden(value: boolean): TextAreaAttribute--><!--Device-TextAreaAttribute-selectionMenuHidden(value: boolean): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the system text selection menu. <br>When set to **true**, the system text selection menu is not displayed when the input box is clicked to place the cursor, long-pressed, double-tapped, triple-tapped, or right-clicked. <br>When set to **false**, the system text selection menu is displayed. <br>**Note:** When set to **true**, the menu is not displayed even if **options** in [setTextSelection](arkts-arkui-textarea-comp-textareacontroller-c.md#settextselection) is set to **MenuPolicy.SHOW**. |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

Sets the text shader effect, such as linear gradient and radial gradient effects.

> **NOTE:** 
> 
> When both shaderStyle and [strokeWidth](#strokewidth) are set, shaderStyle does not take
> effect.
> 
> shaderStyle takes precedence over [fontColor](#fontcolor).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-shaderStyle(shader: ShaderStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-shaderStyle(shader: ShaderStyle | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) &#124; undefined | Yes | Text shader effect, used to set the text gradient effect (such as linear gradient and radial gradient).<br>When the value is undefined, no gradient effect is applied. |

## showCounter

```TypeScript
showCounter(value: boolean, options?: InputCounterOptions)
```

Sets whether to display the counter when the number of characters entered through InputCounterOptions exceeds the threshold. If showCounter is not called, the counter is not displayed by default.

The options can be set only when the value of the parameter **value** is **true**. To enable the counter function of the text box, this API must be used together with **maxLength** (which sets the maximum character limit). If **maxLength** is not set, the counter function does not take effect. The character counter displays the current number of entered characters / the maximum number of characters that can be entered.

When the number of entered characters is greater than the maximum number of characters multiplied by the percentage value, the character counter is displayed. If the user does not set InputCounterOptions when setting the counter, the border and the counter subscript turn red when the current number of entered characters reaches the maximum number of characters. If the user sets both the parameter **value** to **true** and InputCounterOptions, when the value of **thresholdPercentage** is within the valid range and the number of entered characters exceeds the maximum number of characters, the border and the counter subscript turn red and the box shakes. The counter displays a red border by default. When **highlightBorder** is set to **false**, the red border is not displayed. In inline mode, the character counter is not displayed.

[Example 2 (Setting the Counter)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md#example-2-setting-the-counter) shows the effect of setting showCounter.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextAreaAttribute--><!--Device-TextAreaAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the counter.<br>**true** indicates that the counter is displayed, and **false** indicates that it is not displayed. |
| options | [InputCounterOptions](arkts-arkui-common-comp-inputcounteroptions-i.md) | No | Configuration options of the counter, used to customize the display threshold (**thresholdPercentage**) and the red border (**highlightBorder**) of the counter. If this parameter is not passed, the counter is displayed when the number of entered characters reaches the maximum number of characters, and the border and the counter subscript turn red by default.<br>**Since:** 11 |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

Sets whether to block the back key event from being passed to other components or the system. When set to true, TextArea intercepts the back key event and does not pass it to other components. When set to false, the back key event is passed to other components or the system as usual. This applies to scenarios where custom back key behavior is required, such as intercepting the back operation and displaying a confirmation prompt when a form has unsaved changes, custom navigation flows, and games or special interaction scenarios where back key control needs to be taken over. If this API is not called, the back key is blocked by default.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextAreaAttribute-stopBackPress(isStopped: Optional<boolean>): TextAreaAttribute--><!--Device-TextAreaAttribute-stopBackPress(isStopped: Optional<boolean>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to block the back key.<br>true means to block it, and false means not to block it. The default value is used for an invalid value. |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

Sets the color of the text stroke. If this API is not called, the default stroke color is the font color.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-strokeColor(color: Optional<ResourceColor>): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeColor(color: Optional<ResourceColor>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Stroke color. The default value is used if an invalid value is set. |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

Sets the corner style of the text stroke.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextAreaAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) &#124; undefined | Yes | Corner style of the text stroke. <br>If the value is undefined, it is processed as StrokeJoinStyle.MITER_JOIN. For details, see [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md). The text corner appears as a sharp angle. |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

Sets the width of the text stroke. When both the strokeWidth attribute and [shaderStyle](#shaderstyle) are set, shaderStyle does not take effect. If this API is not called, the default value is 0, and no stroke is applied.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextAreaAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAreaAttribute--><!--Device-TextAreaAttribute-strokeWidth(width: Optional<LengthMetrics>): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Width of the text stroke. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, this setting does not take effect and the default value is used.<br>If the value is less than 0, solid text is displayed; if the value is greater than 0, hollow text is displayed. |

## style

```TypeScript
style(value: TextContentStyle)
```

Sets the polymorphic style of the text box. The inline input style is supported only for the TextAreaType.NORMAL type. If this API is not called, the default polymorphic style of the text box is TextContentStyle.DEFAULT.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-style(value: TextContentStyle): TextAreaAttribute--><!--Device-TextAreaAttribute-style(value: TextContentStyle): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextContentStyle](../arkts-apis/arkts-arkui-textcontentstyle-e.md) | Yes | Polymorphic style of the text box. |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

Sets the horizontal alignment of the text in the input box. If this API is not called, the text is aligned to the start of the input box by default, that is, TextAlign.Start.

TextAlign.Start, TextAlign.Center, and TextAlign.End are supported. Since API version 11, TextAlign.JUSTIFY is also supported.

The [align](arkts-arkui-common-comp-commonmethod-c.md#align) attribute can be used to control the vertical position of the text paragraph. In this component, the align attribute cannot be used to control the horizontal position of the text paragraph.

- Alignment.TopStart, Alignment.Top, and Alignment.TopEnd: the content is aligned to the top.  
- Alignment.Start, Alignment.Center, and Alignment.End: the content is vertically centered.  
- Alignment.BottomStart, Alignment.Bottom, and Alignment.BottomEnd: the content is aligned to the bottom.

When textAlign is set to TextAlign.JUSTIFY, the last line of text is not justified; instead, it is aligned to the start.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaAttribute-textAlign(value: TextAlign): TextAreaAttribute--><!--Device-TextAreaAttribute-textAlign(value: TextAlign): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md) | Yes | Horizontal alignment of the text in the input box. |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

Sets the text layout direction. If this API is not called, the text layout direction follows the component layout direction by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextAreaAttribute-textDirection(direction: TextDirection | undefined): TextAreaAttribute--><!--Device-TextAreaAttribute-textDirection(direction: TextDirection | undefined): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md) &#124; undefined | Yes | Text layout direction.<br>If this parameter is set to **undefined**, it is processed as **TextDirection.DEFAULT**, which means the text layout direction follows the component layout direction. |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

Sets the indentation of the first line of text. If this API is not called, the default indentation of the first line is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-textIndent(value: Dimension): TextAreaAttribute--><!--Device-TextAreaAttribute-textIndent(value: Dimension): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Indentation of the first line of text. <br>Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Value range: greater than or equal to 0. If a negative value is set, the default value is used. |

## textOverflow

```TypeScript
textOverflow(value: TextOverflow)
```

Sets how the text is displayed when it is too long. If this API is not called, the default display mode for overlong text is TextOverflow.Clip.

In inline mode, the truncation effect of [maxLines](#maxlines) takes effect only when textOverflow is actively configured. If it is not configured, the text is not truncated by default.

Text is truncated by character. For example, English text is truncated by word as the minimum unit. To truncate by letter, set wordBreak to WordBreak.BREAK_ALL.

When textOverflow is set to TextOverflow.None, TextOverflow.Clip, or TextOverflow.Ellipsis, it must be used together with [maxLines](#maxlines); setting it alone does not take effect. Setting TextOverflow.None has the same effect as TextOverflow.Clip.

> **NOTE:** 
> 
> The TextArea component does not support the TextOverflow.MARQUEE mode. When it is set to TextOverflow.MARQUEE,
> the text is displayed as TextOverflow.Clip.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-textOverflow(value: TextOverflow): TextAreaAttribute--><!--Device-TextAreaAttribute-textOverflow(value: TextOverflow): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md) | Yes | Display mode for overlong text.<br>In inline mode, it takes effect only when actively configured. When set to None, Clip, or Ellipsis, it must be used together with maxLines; setting it alone does not take effect. <br>The TextOverflow.MARQUEE mode is not supported. When set to MARQUEE, the text is displayed as Clip. |

## type

```TypeScript
type(value: TextAreaType)
```

Sets the input box type. If this API is not called, the default input box type is TextAreaType.NORMAL.

Different TextAreaType values bring up the corresponding keyboard type and restrict the input. Since API version 11, when [inputFilter](#inputfilter) is set and the input character is not an empty character, the text filtering effect attached to the type API becomes invalid.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-type(value: TextAreaType): TextAreaAttribute--><!--Device-TextAreaAttribute-type(value: TextAreaType): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAreaType](arkts-arkui-textarea-comp-textareatype-e.md) | Yes | Input box type. |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

Sets the text line breaking rule. This attribute does not take effect on placeholder text. When it is set to WordBreak.BREAK_ALL, the [lineBreakStrategy](#linebreakstrategy) attribute does not take effect, and the [orphanCharOptimization](#orphancharoptimization) feature does not take effect either. If this API is not called, the default text line breaking rule is WordBreak.BREAK_WORD.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextAreaAttribute-wordBreak(value: WordBreak): TextAreaAttribute--><!--Device-TextAreaAttribute-wordBreak(value: WordBreak): TextAreaAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [WordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md) | Yes | Text line breaking rule. |
