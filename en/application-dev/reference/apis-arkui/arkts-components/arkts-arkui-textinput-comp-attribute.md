# TextInput properties/events

```TypeScript
declare class TextInputAttribute extends CommonMethod<TextInputAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported:

> **NOTE:** 
> 
> By default, the default value of the universal attribute [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) is

{

&nbsp;top: '8vp',

&nbsp;right: '16vp',

&nbsp;bottom: '8vp',

&nbsp;left: '16vp'

}

> When underline mode is enabled for the input box, the default value of the universal attribute padding is

{

&nbsp;top: '12vp',

&nbsp;right: '0vp',

&nbsp;bottom: '12vp',

&nbsp;left: '0vp'

}

> When padding is set to 0 for the input box, you can set
> [borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius) to 0 to
> prevent the cursor from being truncated. If the cursor is displayed abnormally at the edge of the text box, check
> whether this is caused by the padding and borderRadius attributes.
> 
> Since API version 10, a single-line input box can be set with .width('auto') to make the component width adapt to
> the text width. During adaptation, the component width is limited by the constraintSize attribute and the maximum
> and minimum widths passed by the parent container. For other usage, see [Sizing](arkts-arkui-common-comp.md).

**Inheritance/Implementation:** TextInputAttribute extends CommonMethod<TextInputAttribute>

**Since:** 7

<!--Device-unnamed-declare class TextInputAttribute extends CommonMethod<TextInputAttribute>--><!--Device-unnamed-declare class TextInputAttribute extends CommonMethod<TextInputAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCapitalizationMode

```TypeScript
autoCapitalizationMode(mode: AutoCapitalizationMode)
```

Sets the text mode of the auto-capitalization mode. This API only provides the interface capability, and the specific implementation is subject to the input method application. When not set through this interface, no capitalization conversion takes effect by default, and the specific implementation is subject to the input method application.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextInputAttribute--><!--Device-TextInputAttribute-autoCapitalizationMode(mode: AutoCapitalizationMode): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [AutoCapitalizationMode](../arkts-apis/arkts-arkui-autocapitalizationmode-e.md) | Yes | Auto-capitalization mode, used to set the capitalization conversion rule of the input method. The specific implementation is subject to the input method application. |

## barState

```TypeScript
barState(value: BarState)
```

Sets the display mode of the scroll bar in the inline input style editing state. When not set through this API, the default value is BarState.Auto.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-barState(value: BarState): TextInputAttribute--><!--Device-TextInputAttribute-barState(value: BarState): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Display mode of the scroll bar in the inline input style editing state. This attribute takes effect only when the inline mode is set. |

## cancelButton

```TypeScript
cancelButton(options: CancelButtonOptions)
```

Sets the style of the right-side clear button. Only image-type icons are supported. The inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) is not supported. For an example, see [Example 4: Setting the Style of the Clear Button on the Right](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-4-setting-the-style-of-the-clear-button-on-the-right). When not set through this interface, the default value is {

style: CancelButtonStyle.INPUT

}, and the default icon size on Wearable devices is 28 vp.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-cancelButton(options: CancelButtonOptions): TextInputAttribute--><!--Device-TextInputAttribute-cancelButton(options: CancelButtonOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CancelButtonOptions](arkts-arkui-search-comp-cancelbuttonoptions-i.md) | Yes | Style options of the right-side clear button.<br>**Since:** 18 |

<a id="cancelbutton-1"></a>

## cancelButton

```TypeScript
cancelButton(symbolOptions: CancelButtonSymbolOptions)
```

Sets the style of the clear button on the right. Only symbol icons are supported. The inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) is not supported. For details, see [Example 15: Setting a Symbol-Type Clear Button](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-15-setting-a-symbol-type-clear-button). When not set through this interface, the default value is {

style: CancelButtonStyle.INPUT

}.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextInputAttribute-cancelButton(symbolOptions: CancelButtonSymbolOptions): TextInputAttribute--><!--Device-TextInputAttribute-cancelButton(symbolOptions: CancelButtonSymbolOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| symbolOptions | [CancelButtonSymbolOptions](arkts-arkui-search-comp-cancelbuttonsymboloptions-i.md) | Yes | Style of the clear button on the right. |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

Sets the color of the input box caret. When not set through this API, the default value is '#007DFF' (blue), and on Wearable devices the default value is '#5EA1FF' (blue, slightly lighter than '#007DFF').

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-caretColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-caretColor(value: ResourceColor): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the input box caret. |

## caretPosition

```TypeScript
caretPosition(value: number)
```

Sets the caret position.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-caretPosition(value: number): TextInputAttribute--><!--Device-TextInputAttribute-caretPosition(value: number): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Caret position.<br>The position before the first character is 0. <br>When the value is less than 0, 0 is used; when it is greater than the text length, the caret is displayed at the end of the text. |

## caretStyle

```TypeScript
caretStyle(value: CaretStyle)
```

Sets the caret style.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-caretStyle(value: CaretStyle): TextInputAttribute--><!--Device-TextInputAttribute-caretStyle(value: CaretStyle): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CaretStyle](../arkts-apis/arkts-arkui-caretstyle-i.md) | Yes | Caret style, used to customize the display style of the caret. The configuration items include width (caret width) and color (caret color). When not set, the system default caret style is used. |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

Sets whether to enable compression of leading punctuation. When not set through this interface, compression of leading punctuation is disabled by default.

> **NOTE:** 
> 
> - For the punctuation marks that support compression, see the leading punctuation compression range of [ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextInputAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-compressLeadingPunctuation(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable compression of leading punctuation.<br>true indicates that compression of leading punctuation is enabled; false indicates that it is disabled. |

## contentType

```TypeScript
contentType(value: ContentType)
```

Sets the autofill type.<!--RP7--><!--RP7End-->

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-contentType(value: ContentType): TextInputAttribute--><!--Device-TextInputAttribute-contentType(value: ContentType): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ContentType](arkts-arkui-textinput-comp-contenttype-e.md) | Yes | Autofill type. Value range: see ContentType Enum Description. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Sets whether the input text can be copied. When CopyOptions.None is set, only paste and select all are supported. When CopyOptions.None is set, dragging is not allowed. When not set through this interface, the default value is CopyOptions.LocalDevice, which supports copying within the device.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-copyOption(value: CopyOptions): TextInputAttribute--><!--Device-TextInputAttribute-copyOption(value: CopyOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether the input text can be copied. |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions)
```

Sets a custom keyboard.

When a custom keyboard is set, the system input method is not opened after the input box is activated; instead, the specified custom component is loaded.

The height of the custom keyboard can be set through the height attribute of the root node of the custom component. The width cannot be set and uses the system default value.

The custom keyboard is presented by overlaying the original UI. When the avoidance mode is not enabled or the input box does not need avoidance, the original application UI is not compressed or lifted.

The custom keyboard cannot obtain focus, but it intercepts gesture events.

By default, the custom keyboard is closed when the input control loses focus. Developers can also control the closing of the keyboard through the [TextInputController](arkts-arkui-textinput-comp-textinputcontroller-c.md). [stopEditing](arkts-arkui-textinput-comp-textinputcontroller-c.md#stopediting) method.

When a custom keyboard is set, the input from a physical keyboard can be avoided by binding the [onKeyPreIme](arkts-arkui-common-comp-commonmethod-c.md#onkeypreime) event.

Since API version 23, a custom keyboard can enable continuation through [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature). When switching to another custom keyboard, the switch is performed directly without triggering the keyboard closing and opening animations.

> **NOTE:** 
> 
> This API cannot be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextInputAttribute--><!--Device-TextInputAttribute-customKeyboard(value: CustomBuilder | ComponentContent | undefined, options?: KeyboardOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; ComponentContent &#124; undefined | Yes | Custom keyboard. When the value is set to undefined, the custom keyboard is closed.<br>**Since:** 22 |
| options | [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) | No | Sets whether the custom keyboard supports avoidance.<br>When this parameter is not set, the custom keyboard does not support avoidance by default.<br>**Since:** 12 |

## decoration

```TypeScript
decoration(value: TextDecorationOptions)
```

Sets the type, style, and color of the text decoration line. When not set through this interface, the default value is {

&nbsp;type:&nbsp;TextDecorationType.None,

&nbsp;color:&nbsp;Color.Black,

&nbsp;style:&nbsp;TextDecorationStyle.SOLID,

&nbsp;thicknessScale:&nbsp;1.0

}.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-decoration(value: TextDecorationOptions): TextInputAttribute--><!--Device-TextInputAttribute-decoration(value: TextDecorationOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextDecorationOptions](arkts-arkui-common-comp-textdecorationoptions-i.md) | Yes | Text decoration line object. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets custom menu extension items, allowing users to set the text content, icon, and callback method of the extension items.

When [disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems) or [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems) is called to block the system service menu items in the text selection menu, the input parameter list of the callback method [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) in the editMenuOptions API does not include the blocked menu options.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute--><!--Device-TextInputAttribute-editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extended menu options. |

## ellipsisMode

```TypeScript
ellipsisMode(mode: Optional<EllipsisMode>)
```

Sets the ellipsis position. The ellipsisMode attribute takes effect only in the inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md), and must be used together with [textOverflow](#textoverflow) set to TextOverflow.Ellipsis. Setting the ellipsisMode attribute alone does not take effect. When not set through this interface, the default value is EllipsisMode.END.

It takes effect normally in the non-editing state. In the editing state, EllipsisMode.START and EllipsisMode.CENTER take effect only when maxLines is set to 1, while EllipsisMode.END, EllipsisMode.MULTILINE_START, and EllipsisMode.MULTILINE_CENTER take effect normally.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextInputAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextInputAttribute--><!--Device-TextInputAttribute-ellipsisMode(mode: Optional<EllipsisMode>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[EllipsisMode](../arkts-apis/arkts-arkui-ellipsismode-e.md)&gt; | Yes | Ellipsis position. |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

Sets whether to enable auto-fill. When not set through this interface, auto-fill is enabled by default.<!--RP6-->&lt;! --RP6End--&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-enableAutoFill(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoFill(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable auto-fill.<br>The value **true** means to enable auto-fill, and **false** means the opposite. |

## enableAutoFillAnimation

```TypeScript
enableAutoFillAnimation(enabled: Optional<boolean>)
```

Sets whether to enable the auto-fill animation. When not set through this interface, the default value is true.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-enableAutoFillAnimation(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoFillAnimation(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the auto-fill animation. <br>true indicates enabled, and false indicates disabled. <br>**NOTE:** <br>You must first set [enableAutoFill](#enableautofill) to enable the auto-fill feature. After it is enabled, the animation takes effect only when the input mode [InputType](arkts-arkui-textinput-comp-inputtype-e.md) of the input box is set to Password, NEW_PASSWORD, or NUMBER_PASSWORD during auto-fill. |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enabled: Optional<boolean>)
```

Sets whether to enable automatic spacing between Chinese and Western characters. When not set through this interface, the default value is false.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-enableAutoSpacing(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western characters.<br>The value true means to enable automatic spacing, and false means not to enable it. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback. If this attribute is not used, haptic feedback is enabled by default.

When haptic feedback is enabled, you need to set the **requestPermissions** field in the [module.json5](../../../quick-start/module-configuration-file.md) of the project to enable the vibration permission. The configuration is as follows:

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TextInputAttribute-enableHapticFeedback(isEnabled: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableHapticFeedback(isEnabled: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>The value **true** means to enable haptic feedback, and **false** means the opposite. |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(value: boolean)
```

Sets whether to actively bring up the soft keyboard when TextInput gains focus by means other than tapping. When not set through this interface, the default value is false on TV devices and true on other devices.

Since API version 10, focus gain is bound to the input method by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-enableKeyboardOnFocus(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enableKeyboardOnFocus(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to actively bring up the soft keyboard when focus is gained by means other than tapping.<br>The value true means to actively bring up the soft keyboard, and false means not to actively bring it up. |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

Sets whether to enable input preview. When this API is not used to set it, input preview is enabled by default.

Preview content is defined as a temporary text state, and the text interception feature is not supported currently.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-enablePreviewText(enable: boolean): TextInputAttribute--><!--Device-TextInputAttribute-enablePreviewText(enable: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable input preview.<br>The value **true** means to enable input preview, and **false** means not to enable input preview. |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to perform entity recognition on the selected text. This API depends on the text recognition capability of the underlying device; otherwise, the setting does not take effect. When not set through this API, entity recognition for the selected text is enabled by default, all types of entities are recognized, and the AI menu feature is enabled.

When enableSelectedDataDetector is set to true, all types of entities are recognized by default.

After being enabled, entities such as emails, phone numbers, URLs, dates, and addresses in the selection can be recognized, and the corresponding AI menu items are displayed in the text selection menu.

When the AI menu feature is enabled, after text is selected in the component, the text selection menu can display the corresponding AI menu items, including url (open link), email (create email), phoneNumber (call), address (navigate to), and dateTime (create schedule) in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

When the AI menu takes effect, the selected range must include exactly one complete AI entity for the corresponding option to be displayed. This menu item does not appear together with the askAI menu item in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

This feature takes effect only when CopyOptions is CopyOptions.LocalDevice or CopyOptions.CROSS_DEVICE.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextInputAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextInputAttribute--><!--Device-TextInputAttribute-enableSelectedDataDetector(enable: boolean | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable entity recognition for the selected text.<br>true: enables recognition; false: disables recognition. <br>When the value is undefined, the default value is used. |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

Sets the Enter key type of the input method. When not set through this interface, the default is EnterKeyType.Done.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-enterKeyType(value: EnterKeyType): TextInputAttribute--><!--Device-TextInputAttribute-enterKeyType(value: EnterKeyType): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Enter key type of the input method. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

For multi-line text stacking, supports line height adaptation based on the actual text height. This interface takes effect only when the line height is smaller than the actual text height. When not set through this interface, the line height is not adapted based on the actual text height by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextInputAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-fallbackLineSpacing(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height is adapted based on the actual text height.<br>true indicates that the line height is adapted based on the actual text height; false indicates that the line height is not adapted based on the actual text height. <br>This interface takes effect only when the line height is smaller than the actual text height. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color. When not set through this interface, the default color follows the theme. On Wearable devices, the default value is '#dbffffff' (white, with an opacity of 86%).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-fontColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-fontColor(value: ResourceColor): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color. |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

Sets the font list. When not set through this interface, the default font is 'HarmonyOS Sans'.

> **NOTE:** 
> 
> It is recommended that you use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to
> register custom fonts.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-fontFamily(value: ResourceStr): TextInputAttribute--><!--Device-TextInputAttribute-fontFamily(value: ResourceStr): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font list. When multiple fonts are used, separate them with commas ','. The font priority takes effect in order. For example: 'Arial,HarmonyOS Sans'.<br>Applications currently support the 'HarmonyOS Sans' font and custom fonts. <br>Cards currently support only the 'HarmonyOS Sans' font. <br>Wearable devices support the 'HarmonyOS Sans' font and custom fonts. |

## fontFeature

```TypeScript
fontFeature(value: string)
```

Sets the font feature of the text style, such as monospaced digits.

The format is: normal \| \&lt;feature-tag-value\&gt;

The format of \&lt;feature-tag-value\&gt; is: \&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]

There can be multiple \&lt;feature-tag-value\&gt; values, separated by commas (,).

For example, the input format for using monospaced digits is "ss01" on.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-fontFeature(value: string): TextInputAttribute--><!--Device-TextInputAttribute-fontFeature(value: string): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text feature effect, used to set the advanced typography capabilities of OpenType fonts (such as monospaced digits and ligatures). The format is normal or &lt;feature-tag-value&gt;, for example, "ss01" on. |

## fontSize

```TypeScript
fontSize(value: Length)
```

Sets the font size. When not set through this interface, the default font size is 16fp, and the default value on Wearable devices is 18fp.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-fontSize(value: Length): TextInputAttribute--><!--Device-TextInputAttribute-fontSize(value: Length): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Font size. When fontSize is of the number type, the unit fp is used. Percentage strings are not supported. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style. When not passed through this interface, the default value is FontStyle.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-fontStyle(value: FontStyle): TextInputAttribute--><!--Device-TextInputAttribute-fontStyle(value: FontStyle): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight of the text. If the value is too large, the text may be truncated under different fonts. When not set through this interface, the default value is FontWeight.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextInputAttribute--><!--Device-TextInputAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text. For the number type, the value ranges from 100 to 900, with an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight.<br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

## halfLeading

```TypeScript
halfLeading(halfLeading: Optional<boolean>)
```

Sets the text to be vertically centered within the line, evenly distributing the line spacing to the top and bottom of the line. When not set through this interface, the default value is false.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextInputAttribute-halfLeading(halfLeading: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-halfLeading(halfLeading: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| halfLeading | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Sets whether the text is vertically centered.<br>The value true evenly distributes the line spacing to the top and bottom of the line, and false does not. |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(value: TextHeightAdaptivePolicy)
```

Sets the text height adaptation mode when the component is set to the inline input style. When not set through this API, the default value is TextHeightAdaptivePolicy.MAX_LINES_FIRST.

When set to TextHeightAdaptivePolicy.MAX_LINES_FIRST, the [maxLines](#maxlines) attribute is preferentially used to adjust the text height. If the layout size using the maxLines attribute exceeds the layout constraints, the font is reduced within the range of [minFontSize](#minfontsize) and [maxFontSize](#maxfontsize) to display more text.

When set to TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST, the minFontSize attribute is preferentially used to adjust the text height. If the text can be laid out in a single line using the minFontSize attribute, the font is enlarged within the range of minFontSize and maxFontSize and the maximum font size is used.

When set to TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST, the effect is the same as that of TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST.

When the component is set to a non-inline input style, the three modes of setting the text height adaptation (TextHeightAdaptivePolicy) have the same effect, that is, the font is reduced within the range of minFontSize and maxFontSize to display more text.

> **NOTE:** 
> 
> When the component is set to the inline input style, the font size may be inconsistent between the editing state
> and the non-editing state.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute--><!--Device-TextInputAttribute-heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md) | Yes | Text height adaptation mode. This attribute takes effect only when the inline input style is set. |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Sets whether to add spacing to the first and last lines to prevent text truncation. If this API is not used to set the value, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextInputAttribute-includeFontPadding(include: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-includeFontPadding(include: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing to the first and last lines to prevent text truncation.<br>The value **true** means to add spacing to the first and last lines, and **false** means not to add spacing to the first and last lines. |

## inputFilter

```TypeScript
inputFilter(value: ResourceStr, error?: Callback<string>)
```

Sets an input filter through a regular expression. Input that matches the expression is allowed to be displayed, and input that does not match is filtered out. In single-character input scenarios, only single-character matching is supported; in multi-character input scenarios, such as pasting, string matching is supported. When not set through this interface, there is no input filtering rule by default, and all input is allowed to be displayed.

Since API version 11, setting inputFilter with a non-empty input character causes the text filtering effect attached to the [type](#type) interface to become invalid.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-inputFilter(value: ResourceStr, error?: Callback<string>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Regular expression. |
| error | Callback&lt;string&gt; | No | Returns the filtered content when the regular expression matching fails.<br>**Since:** 18 |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

Sets the style of the keyboard pulled up by the input box. This takes effect only after the input method is adapted. For details, see [Immersive Mode of the Input Method Application](../../../inputmethod/inputmethod-immersive-mode-guide.md). When not set through this interface, the default value is KeyboardAppearance.NONE_IMMERSIVE.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextInputAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextInputAttribute--><!--Device-TextInputAttribute-keyboardAppearance(appearance: Optional<KeyboardAppearance>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[KeyboardAppearance](../arkts-apis/arkts-arkui-keyboardappearance-e.md)&gt; | Yes | Keyboard style. |

## letterSpacing

```TypeScript
letterSpacing(value: number | string | Resource)
```

Sets the character spacing of the text. When this value is set to a percentage, the default value is used. When this value is set to 0, the default value is used. The string type supports the string form of the number type value, and a unit can be attached, for example, "10" and "10fp".

When the value is negative, the text is compressed. If the negative value is too small, the size of the component content area is compressed to 0, resulting in no content being displayed.

This attribute takes effect on each character, including the character at the end of a line.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-letterSpacing(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-letterSpacing(value: number | string | Resource): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Character spacing of the text. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) |

## lineBreakStrategy

```TypeScript
lineBreakStrategy(strategy: LineBreakStrategy)
```

Sets the line breaking rule. This attribute takes effect only when wordBreak is not equal to BREAK_ALL, and hyphens are not supported. When not set through this interface, the default value is LineBreakStrategy.GREEDY.

This attribute applies to scenarios where the text wrapping effect needs to be optimized: LineBreakStrategy.GREEDY is suitable for fast line breaking that fills each line first; LineBreakStrategy.HIGH_QUALITY is suitable for typesetting that pursues a better visual effect; LineBreakStrategy.BALANCED is suitable for layouts that require even distribution of content across lines.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute--><!--Device-TextInputAttribute-lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md) | Yes | Line breaking rule of the text. <br>LineBreakStrategy.GREEDY indicates greedy line breaking, which fills each line first; LineBreakStrategy.HIGH_QUALITY indicates high-quality line breaking, which balances line length; LineBreakStrategy.BALANCED indicates balanced line breaking, which optimizes typesetting aesthetics. <br>**Note:** <br>This attribute takes effect only when the inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) is set. |

## lineHeight

```TypeScript
lineHeight(value: number | string | Resource)
```

Sets the line height of the text.

When the value is not greater than 0, the text line height is not limited and adapts to the font size. For the number type, the unit is fp. For the string type, the string form of the number type value is supported, and a unit can be attached, for example, "10" and "10fp".

> **NOTE:** 
> 
> - When the font height of a special character is far greater than that of other characters in the same line, the text box may display unexpected anomalies such as truncation, occlusion, and changes in the relative positions of content. In this case, you need to adjust the component height, line height, and other attributes, and modify the corresponding page layout.
> 
> - When [Password Mode](../../../ui/arkts-common-components-text-input.md#password-mode) is set, setting the line height [lineHeight](#lineheight) through this API does not take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-lineHeight(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-lineHeight(value: number | string | Resource): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Text line height.<br>For the number type, the unit is fp. |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

Sets the maximum font scale factor of the text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextInputAttribute-maxFontScale(scale: Optional<number|Resource>): TextInputAttribute--><!--Device-TextInputAttribute-maxFontScale(scale: Optional<number|Resource>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Maximum font scale factor of the text. The undefined type is supported. <br>Value range: [1, +∞) <br>**Note:** <br>If the value set is less than 1, it is processed as 1. Abnormal values do not take effect by default. <br>After the maxFontScale attribute is set, showError can be scaled up to 2 times at most. <br>Before use, configure the [configuration.json](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) file and the [app.json5](../../../quick-start/app-configuration-file.md) file in the project. For details, see [Example 18: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-18-setting-the-minimum-and-maximum-font-scale-factors). |

## maxFontSize

```TypeScript
maxFontSize(value: number | string | Resource)
```

Sets the maximum display font size of the text. The string type supports the string form of a number value, which can carry a unit, for example, "10" and "10fp".

This attribute must be used together with [minFontSize](#minfontsize) and [maxLines](#maxlines) (used when the component is set to the inline input style and is in editing state) or layout size constraints; setting it alone does not take effect.

When adaptive font size takes effect, the fontSize setting does not take effect.

When maxFontSize is less than or equal to 0, or maxFontSize is less than minFontSize, adaptive font size does not take effect. In this case, the value of the [fontSize](#fontsize) attribute takes effect; when it is not set, its default value takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-maxFontSize(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-maxFontSize(value: number | string | Resource): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Maximum display font size of the text. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Must be greater than 0 and greater than minFontSize; otherwise, adaptive font size does not take effect, and the value of the fontSize attribute takes effect. <br>Must be used together with minFontSize; setting it alone does not take effect. |

## maxLength

```TypeScript
maxLength(value: number)
```

Sets the maximum number of characters that can be entered. When not set through this interface, unlimited input is allowed by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-maxLength(value: number): TextInputAttribute--><!--Device-TextInputAttribute-maxLength(value: number): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of characters that can be entered.<br>Value range: [0, 2^31-1] <br>**Note:** <br>When this attribute is not set or an invalid value is set, the default value is used. When a decimal is set, the integer part is used. When the set value exceeds the upper limit of the value range, the component may display or function abnormally. Do not exceed the upper limit. |

## maxLines

```TypeScript
maxLines(value: number)
```

Sets the maximum number of lines that can be displayed for text in the inline input style editing state. When not set through this interface, the default value is 3.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-maxLines(value: number): TextInputAttribute--><!--Device-TextInputAttribute-maxLines(value: number): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of lines that can be displayed for text in the inline input style editing state. This attribute takes effect only when inline mode is set and the component is in the editing state.<br>Value range: (0, UINT32_MAX]. If 0 or a negative number is passed in, the default value 3 is used; if the value exceeds UINT32_MAX, it is automatically corrected to UINT32_MAX. |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

Sets the minimum font scale factor for text.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextInputAttribute-minFontScale(scale: Optional<number|Resource>): TextInputAttribute--><!--Device-TextInputAttribute-minFontScale(scale: Optional<number|Resource>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Minimum font scale factor for text. The undefined type is supported. <br>Value range: [0, 1] <br>**Note:** <br>If the value is less than 0, it is processed as 0. If the value is greater than 1, it is processed as 1. Abnormal values do not take effect by default. <br>Before use, configure the [configuration.json](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) file and the [app.json5](../../../quick-start/app-configuration-file.md) file in the project. For details, see [Example 18: Setting the Minimum and Maximum Font Scale Factors](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-18-setting-the-minimum-and-maximum-font-scale-factors). |

## minFontSize

```TypeScript
minFontSize(value: number | string | Resource)
```

Sets the minimum display font size of the text. The string type supports the string form of the number type value, which can carry a unit, for example, "10" and "10fp".

This attribute must be used together with [maxFontSize](#maxfontsize) and [maxLines](#maxlines) (used when the component is set to the inline input style and in the editing state) or layout size constraints. Setting it alone does not take effect.

When adaptive font size takes effect, the fontSize setting does not take effect.

When minFontSize is less than or equal to 0, adaptive font size does not take effect. In this case, the value of the [fontSize](#fontsize) attribute takes effect; when it is not set, its default value takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-minFontSize(value: number | string | Resource): TextInputAttribute--><!--Device-TextInputAttribute-minFontSize(value: number | string | Resource): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Minimum display font size of the text. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Must be greater than 0. When it is less than or equal to 0, adaptive font size does not take effect, and the fontSize attribute value takes effect. <br>Must be used together with maxFontSize. Setting it alone does not take effect. |

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
> - onChange is triggered after the change is complete and cannot intercept the change.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onChange(callback: EditableTextOnChangeCallback): TextInputAttribute--><!--Device-TextInputAttribute-onChange(callback: EditableTextOnChangeCallback): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [EditableTextOnChangeCallback](../arkts-apis/arkts-arkui-editabletextonchangecallback-t.md) | Yes | Callback invoked when the current input text content changes.<br>**Since:** 12 |

## onContentScroll

```TypeScript
onContentScroll(callback: OnContentScrollCallback)
```

Called when the text content scrolls.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onContentScroll(callback: OnContentScrollCallback): TextInputAttribute--><!--Device-TextInputAttribute-onContentScroll(callback: OnContentScrollCallback): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnContentScrollCallback](arkts-arkui-textinput-comp-oncontentscrollcallback-t.md) | Yes | Callback for the text content scroll event.<br>**Since:** 18 |

## onCopy

```TypeScript
onCopy(callback: Callback<string>)
```

Triggered when a copy operation is performed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onCopy(callback: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-onCopy(callback: Callback<string>): TextInputAttribute-End-->

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

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onCut(callback: Callback<string>): TextInputAttribute--><!--Device-TextInputAttribute-onCut(callback: Callback<string>): TextInputAttribute-End-->

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
> - The two can be used together, with onWillDelete for interception control and onDidDelete for obtaining the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-onDidDelete(callback: Callback<DeleteValue>): TextInputAttribute--><!--Device-TextInputAttribute-onDidDelete(callback: Callback<DeleteValue>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md)&gt; | Yes | Callback invoked when the deletion is complete.<br>Supported only in the scenario where the input is provided by the system input method. |

## onDidInsert

```TypeScript
onDidInsert(callback: Callback<InsertValue>)
```

Triggered when input is complete.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-onDidInsert(callback: Callback<InsertValue>): TextInputAttribute--><!--Device-TextInputAttribute-onDidInsert(callback: Callback<InsertValue>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md)&gt; | Yes | Callback invoked when input is complete.<br>Only supported in the scenario where the system input method is used. |

## onEditChange

```TypeScript
onEditChange(callback: Callback<boolean>)
```

Triggered when the input state changes. The editing state is active when a cursor is present, and inactive when no cursor is present.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onEditChange(callback: Callback<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onEditChange(callback: Callback<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the input state changes. The return value **true** indicates that the input box is in the editing state (a cursor is displayed and user input can be received); the return value **false** indicates that the input box is in the non-editing state (no cursor is displayed and user input cannot be received).<br>**Since:** 18 |

## onPaste

```TypeScript
onPaste(callback: OnPasteCallback)
```

Triggered when a paste operation is performed.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onPaste(callback: OnPasteCallback): TextInputAttribute--><!--Device-TextInputAttribute-onPaste(callback: OnPasteCallback): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnPasteCallback](arkts-arkui-textinput-comp-onpastecallback-t.md) | Yes | Executed when a paste operation is performed.<br>**Since:** 18 |

## onSecurityStateChange

```TypeScript
onSecurityStateChange(callback: Callback<boolean>)
```

Triggered when the password display state changes.

> **NOTE:** 
> 
> Since API version 20, this API is supported in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-onSecurityStateChange(callback: Callback<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onSecurityStateChange(callback: Callback<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | Yes | Callback function.<br>The value **true** indicates that the password is displayed, and **false** indicates that the password is hidden. |

## onSubmit

```TypeScript
onSubmit(callback: OnSubmitCallback)
```

Triggered when the Enter key on the input method is pressed.

On non-TV devices, when the Enter key is pressed, the input box loses focus and the keyboard is collapsed by default. You can configure whether to collapse the keyboard in the OnSubmitCallback callback. For details, see [Example 2 (Set Underline)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-2-set-underline).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onSubmit(callback: OnSubmitCallback): TextInputAttribute--><!--Device-TextInputAttribute-onSubmit(callback: OnSubmitCallback): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnSubmitCallback](arkts-arkui-textinput-comp-onsubmitcallback-t.md) | Yes | Callback for submission.<br>**Since:** 18 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: OnTextSelectionChangeCallback)
```

Triggered when the position of the text selection or the cursor position in editing state changes.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): TextInputAttribute--><!--Device-TextInputAttribute-onTextSelectionChange(callback: OnTextSelectionChangeCallback): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnTextSelectionChangeCallback](arkts-arkui-textinput-comp-ontextselectionchangecallback-t.md) | Yes | Callback for the text selection change or cursor position change.<br>**Since:** 18 |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient>)
```

Triggered before the input box is about to bind to the input method.

<!--Del-->

Before the input box is about to bind to the input method, you can set the keyboard style through the system API [setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig) of `UIContext`. &lt;! --DelEnd--&gt;

Since API version 22, you can call [setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig) of [IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md) to set the input method extension information. After the input method is successfully bound, the input method receives the extension information and can implement custom functions based on it.

IMEClient is valid only during the execution of onWillAttachIME and cannot be called asynchronously.

> **NOTE:** 
> 
> This API cannot be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-onWillAttachIME(callback: Callback<IMEClient>): TextInputAttribute--><!--Device-TextInputAttribute-onWillAttachIME(callback: Callback<IMEClient>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; | Yes | Triggered before the input box is about to bind to the input method. |

## onWillChange

```TypeScript
onWillChange(callback: Callback<EditableTextChangeValue, boolean>)
```

Triggers this callback when the text content is about to change.

> **NOTE:** 
> 
> - The callback timing of onWillChange is later than onWillInsert and onWillDelete, and earlier than onDidInsert and onDidDelete.
> 
> - onWillChange and onChange form a will/did timing pattern:
> 
> - onWillChange is triggered before the text changes. Returning false intercepts the change; returning true allows the change, and onChange is then triggered.
> 
> - onChange is triggered after the change is complete and cannot intercept it.
> 
> - The two can be used together: onWillChange is used for interception control, and onChange is used to obtain the change result.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextInputAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillChange(callback: Callback<EditableTextChangeValue, boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[EditableTextChangeValue](../arkts-apis/arkts-arkui-editabletextchangevalue-i.md), boolean&gt; | Yes | Callback invoked when the text content is about to change.<br>When the callback parameter type is EditableTextChangeValue, it contains information about the text change. When the callback parameter type is boolean, it indicates whether this text change is allowed. Returning true allows the text to be modified normally and the change takes effect; returning false intercepts this text change operation and the text content does not change. Developers can use this callback to intercept and control text changes. |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean>)
```

This callback is triggered before a copy operation is performed.

> **NOTE:** 
> 
> onWillCopy and onCopy form a will/did timing pattern:
> 
> - onWillCopy is triggered before the copy operation. It can intercept the copy operation by returning false;returning true allows the copy, and onCopy is then triggered.
> 
> - onCopy is triggered after the copy operation is complete and cannot intercept it.
> 
> - The two can be used together: onWillCopy is used for interception control, and onCopy is used to obtain the copy result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextInputAttribute-onWillCopy(callback: Callback<string, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillCopy(callback: Callback<string, boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback before the copy operation. When the callback parameter type is string, it indicates the text content to be copied. When the callback parameter type is boolean, it indicates whether the currently selected text is allowed to be copied. true: the text is allowed to be copied, and the normal copy operation is performed; false: the text is not allowed to be copied, this copy operation is intercepted, and the text will not be copied to the clipboard. |

## onWillCut

```TypeScript
onWillCut(callback: Callback<string, boolean>)
```

Triggered before the cut operation is performed.

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

<!--Device-TextInputAttribute-onWillCut(callback: Callback<string, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillCut(callback: Callback<string, boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; | Yes | Callback invoked before the cut operation. When the callback parameter type is string, it indicates the text content to be cut. When the callback parameter type is boolean, it indicates whether the currently selected text is allowed to be cut. true: the text is allowed to be cut and the normal cut operation is performed; false: the text is not allowed to be cut, this cut operation is intercepted, and the text is neither cut to the clipboard nor deleted from the input box. |

## onWillDelete

```TypeScript
onWillDelete(callback: Callback<DeleteValue, boolean>)
```

Triggered when the text is about to be deleted.

> **NOTE:** 
> 
> - Tapping the clear button does not trigger the onWillDelete callback.
> 
> - onWillDelete and onDidDelete form a will/did timing pattern:
> 
> - onWillDelete is triggered before the deletion operation. You can return false to intercept the deletion operation; returning true allows the deletion, and then onDidDelete is triggered.
> 
> - onDidDelete is triggered after the deletion is complete and cannot intercept the operation.
> 
> - The two can be used together: onWillDelete is used for interception control, and onDidDelete is used to obtain the deletion result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillDelete(callback: Callback<DeleteValue, boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[DeleteValue](../arkts-apis/arkts-arkui-deletevalue-i.md), boolean&gt; | Yes | Callback invoked when the text is about to be deleted.<br>When the callback parameter type is DeleteValue, it contains information such as the text content to be deleted. When the callback parameter type is boolean, it indicates whether to allow this deletion. Returning true allows the text to be deleted normally; returning false intercepts this deletion operation, and the text will not be deleted. Developers can use this callback to intercept and control the deletion operation. <br>This callback is not triggered during the preview deletion operation. <br>It is supported only in the scenario where the system input method is used for input. |

## onWillInsert

```TypeScript
onWillInsert(callback: Callback<InsertValue, boolean>)
```

Triggered when text is about to be inserted.

> **NOTE:** 
> 
> onWillInsert and onDidInsert form a will/did timing pattern:
> 
> - onWillInsert is triggered before the input operation. You can return false to intercept the input operation;returning true allows the input, and then onDidInsert is triggered.
> 
> - onDidInsert is triggered after the input is completed and cannot intercept the operation.
> 
> - The two can be used together: onWillInsert is used for interception control, and onDidInsert is used to obtain the input result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextInputAttribute--><!--Device-TextInputAttribute-onWillInsert(callback: Callback<InsertValue, boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[InsertValue](../arkts-apis/arkts-arkui-insertvalue-i.md), boolean&gt; | Yes | Callback invoked when text is about to be inserted.<br>When the callback parameter type is InsertValue, it contains information such as the text content to be inserted. When the callback parameter type is boolean, it indicates whether to allow this insertion. Returning true allows the text to be inserted into the input box normally; returning false intercepts this insertion operation, and the text will not be inserted. Developers can use this callback to filter and intercept the input content. <br>This callback is not triggered during preview and candidate word operations. <br>It is supported only in scenarios where the system input method is used for input. |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

Sets whether to enable orphan character optimization during text layout. If this API is not used to set it, orphan character optimization is disabled by default.

When enabled, the line break points are adjusted to avoid isolated characters (the first character of the last line of a paragraph) as much as possible, improving text layout. This feature takes effect only when wordBreak is not BREAK_ALL and the [locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the first [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the text to be laid out is "zh-Hans" or "zh-Hant".

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextInputAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-orphanCharOptimization(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable orphan character optimization for the last line of a paragraph.<br>true indicates that orphan character optimization is enabled, and false indicates that it is disabled. <br>When the value is undefined or null, orphan character optimization is disabled. <br>Orphan character optimization takes effect only when wordBreak is not BREAK_ALL and the locale of the first TextStyle of the text to be laid out is "zh-Hans" or "zh-Hant". |

## passwordIcon

```TypeScript
passwordIcon(value: PasswordIcon)
```

Sets the icon at the end of the input box in password mode. When not set through this interface, the system- provided password icon is used by default. Image formats including jpg, png, bmp, heic, and webp are supported. The fixed size of this icon is 24 vp, and the default size on Wearable devices is 28 vp. If the referenced icon is too large or too small, it is displayed at the fixed size.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-passwordIcon(value: PasswordIcon): TextInputAttribute--><!--Device-TextInputAttribute-passwordIcon(value: PasswordIcon): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PasswordIcon](arkts-arkui-textinput-comp-passwordicon-i.md) | Yes | Icon at the end of the input box in password input mode. |

## passwordRules

```TypeScript
passwordRules(value: string)
```

Defines the rules for generating a password. When auto-fill is triggered, the set password rules are passed to the password vault for generating a new password.<!--RP1--><!--RP1End-->

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-passwordRules(value: string): TextInputAttribute--><!--Device-TextInputAttribute-passwordRules(value: string): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Defines the rules for generating a password. <br>**Note:** <br>You must first set [enableAutoFill](#enableautofill) to enable auto-fill and set [contentType](#contenttype) to NEW_PASSWORD. This attribute takes effect when auto-fill is triggered. |

## placeholderColor

```TypeScript
placeholderColor(value: ResourceColor)
```

Sets the placeholder text color. When not set through this interface, the default color follows the theme. On Wearable devices, the default value is '#99ffffff' (white, with an opacity of 60%).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-placeholderColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-placeholderColor(value: ResourceColor): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Placeholder text color. |

## placeholderFont

```TypeScript
placeholderFont(value?: Font)
```

Sets the placeholder text style, including font size, font weight, font family, and font style.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register a custom font.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-placeholderFont(value?: Font): TextInputAttribute--><!--Device-TextInputAttribute-placeholderFont(value?: Font): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | No | Placeholder text style.<br>When this parameter is omitted, the default system font style is used. <br>On Wearable devices, the default font size is 18fp. |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

Sets whether to enable hanging punctuation at the end of a line. If this API is not used to set this, hanging punctuation is disabled by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextInputAttribute-punctuationOverflow(enabled: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-punctuationOverflow(enabled: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable hanging punctuation at the end of a line.<br>The value **true** means to enable hanging punctuation at the end of a line, and **false** means the opposite. If this parameter is set to **undefined** or **null**, hanging punctuation is disabled. |

## selectAll

```TypeScript
selectAll(value: boolean)
```

Sets whether to select all text in the initial state. The inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) is not supported. When not set through this interface, text is not selected by default.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-selectAll(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-selectAll(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to select all text.<br>**true** indicates that all text is selected, and **false** indicates that no text is selected. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

Sets the highlight color of the selected text. If the opacity is not set or is set to fully opaque, 20% opacity is used by default. When not set through this API, the default value is '#007DFF' (blue), and on Wearable devices the default value is '#1F71FF' (blue, slightly darker than '#007DFF').

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-selectedBackgroundColor(value: ResourceColor): TextInputAttribute--><!--Device-TextInputAttribute-selectedBackgroundColor(value: ResourceColor): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Highlight color of the selected text. |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Sets the backplane style during text dragging in the text input box.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextInputAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Backplane style during text dragging.<br>When set to undefined: the backplane color follows the theme, displaying white in light mode and black in dark mode. |

## selectionMenuHidden

```TypeScript
selectionMenuHidden(value: boolean)
```

Sets whether to hide the system text selection menu. When not set through this interface, the system text selection menu is displayed by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-selectionMenuHidden(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-selectionMenuHidden(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to hide the system text selection menu.<br>When set to **true**, the system text selection menu is hidden when the input box cursor is clicked, the input box is long pressed, double-clicked, or triple-clicked, or the input box is right-clicked. <br>When set to **false**, the system text selection menu is displayed. |

## shaderStyle

```TypeScript
shaderStyle(shader: ShaderStyle | undefined)
```

Sets the text shader effect, such as linear gradient and radial gradient effects.

> **NOTE:** 
> 
> When shaderStyle and [strokeWidth](#strokewidth) are set at the same time, shaderStyle
> does not take effect.
> 
> shaderStyle has a higher priority than [fontColor](#fontcolor).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextInputAttribute-shaderStyle(shader: ShaderStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-shaderStyle(shader: ShaderStyle | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) &#124; undefined | Yes | Text shader effect, used to set the gradient or special color effect of the text. Supports linear gradient, radial gradient, solid color, and other types.<br>When shaderStyle and strokeWidth are set at the same time, shaderStyle does not take effect. <br>When the value is undefined, there is no gradient effect. |

## showCounter

```TypeScript
showCounter(value: boolean, options?: InputCounterOptions)
```

Sets whether to display the counter when the number of characters entered through InputCounterOptions exceeds the threshold. When the showCounter API is not called, the counter is not displayed by default.

Only when the value parameter is true can options be set. The text box enables the counter subscript feature, which must be used together with [maxLength](#maxlength) (which sets the maximum character limit). The character counter displays the current number of entered characters / the maximum number of enterable characters.

When the number of entered characters is greater than the maximum number of characters multiplied by the percentage value, the character counter is displayed. If the user does not set InputCounterOptions when setting the counter, the border and the counter subscript turn red when the current number of entered characters exceeds the maximum number of characters. If the user sets the value parameter to true and [InputCounterOptions](arkts-arkui-common-comp-inputcounteroptions-i.md) at the same time, when the thresholdPercentage value is within the valid range and the number of entered characters exceeds the maximum number of characters, the border and the counter subscript turn red and the box shakes. If highlightBorder is set to false, the red border is not displayed, the counter is displayed in red by default, and the box shakes.

The character counter is not displayed in the inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) or in [Password Mode](../../../ui/arkts-common-components-text-input.md#password-mode).

[Example 5 (Setting the Counter)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-5-setting-the-counter) shows the effect of setting showCounter.

> **NOTE:** 
> 
> Since API version 12, this API is supported in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextInputAttribute--><!--Device-TextInputAttribute-showCounter(value: boolean, options?: InputCounterOptions): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the counter.<br>The value true means to display the counter, and false means not to display it. |
| options | [InputCounterOptions](arkts-arkui-common-comp-inputcounteroptions-i.md) | No | Configuration options of the counter, used to set the counter threshold percentage, border highlight, and so on. This parameter is passed in when the counter display rules need to be customized. When it is not passed in, the default counter configuration is used (threshold percentage 100%, border highlight true). |

## showError

```TypeScript
showError(value?: ResourceStr | undefined)
```

Sets the error text to display in the error state or hides the error state.

When the parameter type is ResourceStr and the input content does not comply with the defined specification, the error text is displayed. When the single-line error text is too long, an ellipsis is displayed at the end. When the parameter type is undefined, the error state is not displayed. See [Example 2](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-2-set-underline).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-showError(value?: ResourceStr | undefined): TextInputAttribute--><!--Device-TextInputAttribute-showError(value?: ResourceStr | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; undefined | No | Error text to display in the error state, or no error state is displayed. <br>Not displayed by default. <br>On Wearable devices, the font size is 13fp and the alignment is center. <br>**Note:** <br>Since API version 12, value supports the Resource type. <br>The inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) is not supported.<br>**Since:** 12 |

## showPassword

```TypeScript
showPassword(visible: boolean)
```

Sets the visibility state of the password. When not set through this interface, the password is not displayed by default.

When [InputType](arkts-arkui-textinput-comp-inputtype-e.md) is set to Password, NEW_PASSWORD, or NUMBER_PASSWORD mode, the password protection feature takes effect. In non-password input modes, this feature is not triggered.

In [password mode](../../../ui/arkts-common-components-text-input.md#password-mode), the state on the backend of the input box and the state management variable on the frontend application side may become inconsistent, which may cause an abnormal state of the trailing icon. It is recommended that you add state synchronization in [onSecurityStateChange](#onsecuritystatechange). For details, see [Example 1 (Setting and Obtaining the Cursor Position)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#example-1-setting-and-obtaining-the-cursor-position).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-showPassword(visible: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showPassword(visible: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | Whether to display the password. <br>The value **true** means to display the password, and **false** means not to display the password. <br>It is recommended that you synchronize the state in the [onSecurityStateChange](#onsecuritystatechange) callback to avoid an abnormal state of the trailing icon. |

## showPasswordIcon

```TypeScript
showPasswordIcon(value: boolean)
```

Sets whether to display the icon at the end of the input box in password mode. When not set through this interface, the default value is false on TV devices and true on other devices.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-showPasswordIcon(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showPasswordIcon(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the icon at the end of the input box in password input mode.<br>true indicates display, and false indicates no display. |

## showUnderline

```TypeScript
showUnderline(value: boolean)
```

Sets whether to enable the underline. When not set through this interface, the underline is not displayed by default. The default underline color is '#33182431' (dark gray with an opacity of 20%), the default thickness is 1 px, the text box size is 48vp, and the underline supports only the InputType.Normal type. When password mode is set, the underline does not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-showUnderline(value: boolean): TextInputAttribute--><!--Device-TextInputAttribute-showUnderline(value: boolean): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the underline.<br>The value **true** means to enable the underline, and **false** means the opposite. |

## showUnit

```TypeScript
showUnit(value: CustomBuilder)
```

Sets a control as the unit of the text box. It must be used together with [showUnderline](#showunderline) and takes effect only when showUnderline is set to true.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-showUnit(value: CustomBuilder): TextInputAttribute--><!--Device-TextInputAttribute-showUnit(value: CustomBuilder): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Unit displayed in the text box during text input. |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

Sets whether to prevent the back key event from being passed to other components or the system. When set to true, TextInput intercepts the back key event and does not pass it to other components; when set to false, the back key event is passed to other components or the system normally. This applies to scenarios where custom back key behavior is required, such as intercepting the back operation and displaying a confirmation prompt when a form is not saved, custom navigation flows, and games or special interaction scenarios where back key control needs to be taken over. When not set through this interface, the default value is true, and an invalid value takes the default value.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextInputAttribute-stopBackPress(isStopped: Optional<boolean>): TextInputAttribute--><!--Device-TextInputAttribute-stopBackPress(isStopped: Optional<boolean>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to block the back key.<br>true indicates blocking, and false indicates not blocking. |

## strokeColor

```TypeScript
strokeColor(color: Optional<ResourceColor>)
```

Sets the color of the text stroke. When not set through this interface, the default value is the font color. When an invalid value is set, the default value is used.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-strokeColor(color: Optional<ResourceColor>): TextInputAttribute--><!--Device-TextInputAttribute-strokeColor(color: Optional<ResourceColor>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Stroke color. |

## strokeJoinStyle

```TypeScript
strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined)
```

Sets the corner style of the text stroke. This attribute takes effect only when the text stroke is set by using strokeWidth.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextInputAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextInputAttribute--><!--Device-TextInputAttribute-strokeJoinStyle(strokeJoinStyle: StrokeJoinStyle | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strokeJoinStyle | [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md) &#124; undefined | Yes | Sets the corner style of the text stroke. This attribute takes effect only when the text stroke is set by using strokeWidth. <br>When the value is undefined, the corner style is processed according to StrokeJoinStyle.MITER_JOIN. For details, see [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md). The text corner is displayed as a sharp angle. |

## strokeWidth

```TypeScript
strokeWidth(width: Optional<LengthMetrics>)
```

Sets the width of the text stroke. When not set through this interface, the default value is 0, and no stroke is applied.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextInputAttribute-strokeWidth(width: Optional<LengthMetrics>): TextInputAttribute--><!--Device-TextInputAttribute-strokeWidth(width: Optional<LengthMetrics>): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Width of the text stroke. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, this setting does not take effect and the default value is used.<br>If the value is less than 0, solid characters are displayed; if the value is greater than 0, hollow characters are displayed. |

## style

```TypeScript
style(value: TextInputStyle | TextContentStyle)
```

Sets the input box to the default style or inline input style. The inline input style supports only the InputType.Normal type.

For details about the input box types, see [type](#type). When not set through this interface, the default value is TextInputStyle.Default.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-style(value: TextInputStyle | TextContentStyle): TextInputAttribute--><!--Device-TextInputAttribute-style(value: TextInputStyle | TextContentStyle): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) &#124; [TextContentStyle](../arkts-apis/arkts-arkui-textcontentstyle-e.md) | Yes | Input box in the default style or inline input style. |

## textAlign

```TypeScript
textAlign(value: TextAlign)
```

Sets the horizontal alignment of text in the input box. When not set through this interface, the default value is TextAlign.Start.

TextAlign.Start, TextAlign.Center, and TextAlign.End are supported. TextAlign.JUSTIFY is processed as TextAlign.Start.

The [align](arkts-arkui-common-comp-commonmethod-c.md#align) attribute can be used to control the vertical position of the text paragraph. This component does not support controlling the horizontal position of the text paragraph through the align attribute.

- Alignment.TopStart, Alignment.Top, Alignment.TopEnd: The content is aligned to the top.  
- Alignment.Start, Alignment.Center, Alignment.End: The content is vertically centered.  
- Alignment.BottomStart, Alignment.Bottom, Alignment.BottomEnd: The content is aligned to the bottom.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-textAlign(value: TextAlign): TextInputAttribute--><!--Device-TextInputAttribute-textAlign(value: TextAlign): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md) | Yes | Horizontal alignment of the text in the input box. |

## textDirection

```TypeScript
textDirection(direction: TextDirection | undefined)
```

Specifies the text layout direction. When not set through this API, the default text layout direction follows the component layout direction.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextInputAttribute-textDirection(direction: TextDirection | undefined): TextInputAttribute--><!--Device-TextInputAttribute-textDirection(direction: TextDirection | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md) &#124; undefined | Yes | Text layout direction.<br>When set to undefined, it is processed as TextDirection.DEFAULT, meaning that the text layout direction follows the component layout direction. |

## textIndent

```TypeScript
textIndent(value: Dimension)
```

Sets the indentation of the first line of text. When not set through this interface, the default value is 0.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-textIndent(value: Dimension): TextInputAttribute--><!--Device-TextInputAttribute-textIndent(value: Dimension): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Indentation of the first line of text. <br>Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Value range: greater than or equal to 0. If a negative value is set, the default value is used. |

## textOverflow

```TypeScript
textOverflow(value: TextOverflow)
```

Sets how text is displayed when it is too long. This is supported only in the editing and non-editing states when the [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md) value is inline mode. When not set through this interface, the default value is TextOverflow.Ellipsis in the non-editing state of inline mode, and TextOverflow.Clip in the editing state of inline mode.

Text truncation is performed by character. For example, English text is truncated by word as the minimum unit. To truncate by letter, set the wordBreak attribute to WordBreak.BREAK_ALL.

When overflow is set to TextOverflow.None, the effect is the same as TextOverflow.Clip.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-textOverflow(value: TextOverflow): TextInputAttribute--><!--Device-TextInputAttribute-textOverflow(value: TextOverflow): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md) | Yes | Display mode when the text is too long. |

## type

```TypeScript
type(value: InputType)
```

Sets the input box type.

Different InputType values bring up the corresponding keyboard type and restrict input. When not set through this interface, the default value is InputType.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputAttribute-type(value: InputType): TextInputAttribute--><!--Device-TextInputAttribute-type(value: InputType): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [InputType](arkts-arkui-textinput-comp-inputtype-e.md) | Yes | Input box type. |

## underlineColor

```TypeScript
underlineColor(value: ResourceColor | UnderlineColor | undefined)
```

Sets the underline color. When not passed through this interface, the underline color configured by the theme is used by default. The default underline color configured by the theme is '#33182431' (dark gray, with an opacity of 20%).

When the input box underline [showUnderline](#showunderline) is enabled, the underline color can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-underlineColor(value: ResourceColor | UnderlineColor | undefined): TextInputAttribute--><!--Device-TextInputAttribute-underlineColor(value: ResourceColor | UnderlineColor | undefined): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [UnderlineColor](arkts-arkui-textinput-comp-underlinecolor-i.md) &#124; undefined | Yes | Sets the underline color.<br>When the underline color mode is set, the underline color is modified. When only the color in the non- special state is set, a ResourceColor can be directly input. When the value is set to undefined, null, or an invalid value, all underlines are restored to the default value. |

## wordBreak

```TypeScript
wordBreak(value: WordBreak)
```

Sets the text line break rule. This attribute takes effect when the component is set to the inline mode of [TextInputStyle](arkts-arkui-textinput-comp-textinputstyle-e.md), but it does not apply to placeholder text. When not set through this interface, the default value is WordBreak.BREAK_WORD.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextInputAttribute-wordBreak(value: WordBreak): TextInputAttribute--><!--Device-TextInputAttribute-wordBreak(value: WordBreak): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [WordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md) | Yes | Line break rule in the editing state of the inline input style. |

## onEditChanged

```TypeScript
onEditChanged(callback: (isEditing: boolean) => void)
```

Triggered when the input state changes.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onEditChange](#oneditchange)

<!--Device-TextInputAttribute-onEditChanged(callback: (isEditing: boolean) => void): TextInputAttribute--><!--Device-TextInputAttribute-onEditChanged(callback: (isEditing: boolean) => void): TextInputAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isEditing: boolean) =&gt; void | Yes | callback of the listened event. |
