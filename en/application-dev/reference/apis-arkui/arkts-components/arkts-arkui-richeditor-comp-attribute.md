# RichEditor properties/events

```TypeScript
declare class RichEditorAttribute extends CommonMethod<RichEditorAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md#common), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md#common), [OnDidChangeCallback](../arkts-apis/arkts-arkui-ondidchangecallback-t.md), [StyledStringChangedListener](../arkts-apis/arkts-arkui-styledstringchangedlistener-i.md), [StyledStringChangeValue](../arkts-apis/arkts-arkui-styledstringchangevalue-i.md), and the following events are supported.

**Inheritance/Implementation:** RichEditorAttribute extends CommonMethod<RichEditorAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToDelete

```TypeScript
aboutToDelete(callback: Callback<RichEditorDeleteValue, boolean>)
```

Triggered when content is about to be deleted via the IME.

It is suitable for scenarios where deletion operations need to be intercepted, such as preventing the deletion of key content and saving the history before deletion to support undo. Together with [onDeleteComplete](#ondeletecomplete), it forms a will/did timing pattern: **aboutToDelete** is triggered before deletion, and **onDeleteComplete** is triggered after deletion is complete. When **aboutToDelete** returns **false**, the component does not perform the deletion operation, and **onDeleteComplete** is not triggered. The two can be used at the same time.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorDeleteValue](arkts-arkui-richeditor-comp-richeditordeletevalue-i.md), boolean&gt; | Yes | [RichEditorDeleteValue](arkts-arkui-richeditor-comp-richeditordeletevalue-i.md) is the text or image Span information where the content to be deleted is located. <br>**true** indicates that the component performs the deletion operation, and **false** indicates that the component does not perform the deletion operation. <br>Callback before the input method deletes content. This callback is executed when the English preview text is tapped to select a candidate word.<br>**Since:** 12 |

## aboutToIMEInput

```TypeScript
aboutToIMEInput(callback: Callback<RichEditorInsertValue, boolean>)
```

Triggered when content is about to be entered in the input method.

It can be used in scenarios where input content needs to be intercepted, such as filtering sensitive words, restricting the input format, and validating the input in real time.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorInsertValue](arkts-arkui-richeditor-comp-richeditorinsertvalue-i.md), boolean&gt; | Yes | [RichEditorInsertValue](arkts-arkui-richeditor-comp-richeditorinsertvalue-i.md) is the content information to be input by the input method. <br>The value true means that the component performs the content addition operation, and false means that the component does not perform the content addition operation. <br>Callback invoked before the input method inputs content.<br>**Since:** 12 |

## barState

```TypeScript
barState(state: BarState)
```

Display mode of the RichEditor scroll bar.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Display mode of the RichEditor scroll bar.<br>Default value: BarState.Auto |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: RichEditorSpanType, content: CustomBuilder, responseType: ResponseType | RichEditorResponseType,
    options?: SelectionMenuOptions)
```

Sets a custom selection menu. It supports custom menu styles and trigger conditions, and is suitable for scenarios that require deep menu customization. When the custom menu is too long, it is recommended to nest a [Scroll](arkts-arkui-scroll-comp.md#scroll) component inside to prevent the keyboard from being obscured.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanType | [RichEditorSpanType](arkts-arkui-richeditor-comp-richeditorspantype-e.md) | Yes | Type of the menu.<br>Default value: RichEditorSpanType.TEXT |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Menu content. |
| responseType | [ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md) &#124; [RichEditorResponseType](arkts-arkui-richeditor-comp-richeditorresponsetype-e.md) | Yes | Response type of the menu.<br> Default value: <br>ResponseType.LongPress<br>**Since:** 11 |
| options | [SelectionMenuOptions](arkts-arkui-richeditor-comp-selectionmenuoptions-i.md) | No | Options of the menu.<br>Pass this parameter when you need to customize the menu pop-up/close callback, specify the menu type, and other information. If this parameter is not passed, the default selection menu options are used. |

## caretColor

```TypeScript
caretColor(value: ResourceColor)
```

Sets the color of the caret and selection handle in the text box.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the caret and selection handle in the text box.<br>Default value: **'#007DFF'** |

## compressLeadingPunctuation

```TypeScript
compressLeadingPunctuation(enabled: Optional<boolean>)
```

Sets whether to enable leading punctuation compression.

This is applicable to scenarios where leading punctuation needs to be aligned with the body text.

> **NOTE:** 
> 
> Leading punctuation is not compressed by default.
> 
> For the range of punctuation marks that support leading compression, see
> [ParagraphStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable leading punctuation compression.<br>true indicates that leading punctuation compression is enabled, and false indicates that it is disabled. <br>Default value: false. <br>When set to undefined or null, the default value is used. |

## copyOptions

```TypeScript
copyOptions(value: CopyOptions)
```

Sets whether the component supports copying and pasting text content.

Since API version 20, copied or cut text from the **RichEditor** component includes HTML-formatted content in the pasteboard.

- Only [TextSpan](arkts-arkui-richeditor-comp-richeditortextspanoptions-i.md) and [ImageSpan](arkts-arkui-richeditor-comp-richeditorimagespanoptions-i.md) support adding  
HTML content to the pasteboard. Other span types, such as [BuilderSpan](arkts-arkui-richeditor-comp-richeditorbuilderspanoptions-i.md), [SymbolSpan](arkts-arkui-richeditor-comp-richeditorsymbolspanoptions-i.md), and [CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md), cannot add HTML content.  
- For styled strings, refer to [toHtml](../arkts-apis/arkts-arkui-styledstring-c.md#tohtml) for supported HTML conversion scope.

When **copyOptions** is not set to **CopyOptions.None**, long-pressing the component content brings up the text selection menu. If a custom text selection menu is defined through [bindSelectionMenu](#bindselectionmenu) or other means, the custom menu is displayed instead.

When **copyOptions** is set to **CopyOptions.None**, the copy, cut, translate, share, search, and Celia Writer features are disabled, and drag-and-drop operations are not supported. In addition, the entity recognition menu of [enableDataDetector](#enabledatadetector) and the AI menu of [enableSelectedDataDetector](#enableselecteddatadetector) are restricted.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Whether the text content supports copy and paste.<br>Default value: CopyOptions.LocalDevice |

## customKeyboard

```TypeScript
customKeyboard(value: CustomBuilder | ComponentContent | undefined,
                 options?: KeyboardOptions | undefined)
```

Sets a custom keyboard.

When a custom keyboard is set, activating the text box opens the specified custom component, instead of the system input method.

The height of the custom keyboard can be set through the **height** attribute of the root node of the custom component. The width cannot be set, and the default system keyboard width is used.

The custom keyboard cannot obtain the focus, but it blocks gesture events.

By default, the custom keyboard is closed when the input component loses the focus.

The custom keyboard supports the continue function. You can call the [setCustomKeyboardContinueFeature](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#setcustomkeyboardcontinuefeature) API to set whether the custom keyboard remains persistent during input field switches.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 23.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; ComponentContent &#124; undefined | Yes | Custom keyboard.<br>When **undefined** is passed, the system keyboard is used by default.<br>**Since:** 23 |
| options | [KeyboardOptions](arkts-arkui-richeditor-comp-keyboardoptions-i.md) &#124; undefined | No | Sets whether the custom keyboard supports the avoidance feature.<br>When undefined is passed in or the parameter is omitted, avoidance is not supported by default.<br>**Since:** 23 |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

Configures text special entity recognition settings, including detectable entity types, entity display styles, and long-press preview availability.

This API must be used together with [enableDataDetector](#enabledatadetector). It takes effect only when **enableDataDetector** is set to **true**.

When entities A and B overlap, the following rules are followed:

1. If A ⊂ B, retain B. Otherwise, retain A.
2. When A ⊄ B and B ⊄ A: If A.start &lt; B.start, retain A; otherwise, retain B.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [TextDataDetectorConfig](../arkts-apis/arkts-arkui-textdatadetectorconfig-i.md) | Yes | Text recognition configuration. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

Sets the extended options for the default system menu, including text content, icons, and callback methods.

Difference from [bindSelectionMenu](#bindselectionmenu): editMenuOptions adds extension items on top of the system default menu style, with the trigger conditions unchanged, and is suitable for scenarios where only menu item extension is needed; bindSelectionMenu fully customizes the menu style and trigger conditions, and is suitable for scenarios where deep menu customization is needed.

When [disableMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablemenuitems) or [disableSystemServiceMenuItems](../arkts-apis/arkts-arkui-arkui-uicontext-textmenucontroller-c.md#disablesystemservicemenuitems) is used to disable system service menu items in the text selection menu, the disabled menu options will be excluded from the parameter list in the [onCreateMenu](../arkts-apis/arkts-arkui-editmenuoptions-i.md#oncreatemenu) callback of **editMenuOptions**.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../arkts-apis/arkts-arkui-editmenuoptions-i.md) | Yes | Extended options of the custom menu. |

## enableAutoSpacing

```TypeScript
enableAutoSpacing(enable: Optional<boolean>)
```

Whether to enable automatic spacing between Chinese and Western characters. This is applicable to scenarios such as mixed Chinese and English content (for example, news articles and technical documents) that require an improved reading experience between Chinese and Western characters. When enabled, spacing is automatically inserted between Chinese and Western characters; when disabled, no spacing is inserted.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable automatic spacing between Chinese and Western text.<br>true indicates that automatic spacing is enabled, and false indicates that it is disabled. <br>Default value: false |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

Sets whether to recognize special entities in the text, including phone numbers, email addresses, URL links, dates, and addresses. The specific recognition types can be configured through the [dataDetectorConfig](#datadetectorconfig) attribute.

This API depends on the device system's text entity recognition capability. Otherwise, the setting does not take effect.

When **enableDataDetector** is set to **true** and the [dataDetectorConfig](#datadetectorconfig) attribute is not specified, the system recognizes all types of entities by default, and changes the color and decoration of these entities to the preset style.

Touching or right-clicking an entity opens a context menu with actions based on entity type, while left-clicking triggers the first menu option directly.

This feature does not take effect on the node text of [addBuilderSpan](arkts-arkui-richeditor-comp-richeditorcontroller-c.md#addbuilderspan).

When **copyOptions** is set to **CopyOptions.None**, the menu displayed after an entity is clicked does not provide the text selection or copy functionality.

&lt;!--RP1--&gt;&lt;!--RP1End--&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable text recognition.<br>true indicates that special entity recognition is enabled, and false indicates that special entity recognition is disabled. <br>Default value: false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean)
```

Sets whether to enable haptic feedback.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable haptic feedback.<br>Default value: true. The value true means to enable haptic feedback, and false means to disable it. <br>**Note:** <br>Haptic feedback takes effect only when the application has the ohos.permission.VIBRATE permission, the user has enabled haptic feedback, and the system hardware supports it. <br>Different device types vary in their support for vibration hardware. Haptic feedback is unavailable on device types without vibration hardware. |

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus(isEnabled: boolean)
```

Sets whether to enable the input method when the **RichEditor** component obtains focus in a way other than clicking.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to pop up the soft keyboard when the **TextInput** component obtains focus in a way other than clicking.<br>**true**: yes; **false**: no <br>Default value: **true** |

## enablePreviewText

```TypeScript
enablePreviewText(enable: boolean)
```

Sets whether to enable preview text.

After this feature is enabled, the pinyin and stroke characters entered during input method input are displayed in the component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the preview feature.<br>The value true means to enable it, and false means to disable it. <br>Default value: true |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean | undefined)
```

Sets whether to enable the AI menu feature for text selection. After this feature is enabled, the entities such as email address, phone number, website URL, date, and address in the selection area can be recognized, and the corresponding AI menu items can be displayed in the text selection menu. By default, the AI menu feature is enabled.

When the AI menu feature is enabled, after text is selected in the component, the text selection menu can display the corresponding AI menu items, including url (open link), email (create email), phoneNumber (call), address (navigate to), and dateTime (create schedule) in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

When the AI menu is active, the corresponding menu item is displayed only if the selected range contains exactly one complete AI entity. This menu item does not appear at the same time as the **askAI** menu item in [TextMenuItemId](../arkts-apis/arkts-arkui-textmenuitemid-c.md).

This feature takes effect only when [copyOptions](#copyoptions) is set to **CopyOptions.LocalDevice** or **CopyOptions.CROSS_DEVICE**.

This API depends on the text recognition capability of the device; otherwise, the setting does not take effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean &#124; undefined | Yes | Whether to enable the text selection AI menu function. The value **true** indicates enabled, and **false** indicates disabled.<br>Default value: **true**. <br>When set to **undefined** or **null**, the default value is used. |

## enterKeyType

```TypeScript
enterKeyType(value: EnterKeyType)
```

Sets the Enter key type of the soft keyboard.

After this attribute is set, the icon and trigger behavior of the Enter key on the soft keyboard change according to the specified type, and different EnterKeyType values correspond to different Enter key styles.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Type of the Enter key on the soft keyboard.<br>The default value is EnterKeyType.NEW_LINE. <br>For the applicable scenarios of each enum value, see the EnterKeyType enum description. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: Optional<boolean>)
```

Whether the line height is adaptively based on the actual text height in multi-line text overlay scenarios.

This is applicable to scenarios such as mixed text with different font sizes and chat message bubbles that need to avoid text overlap. If this API is not used, the line height is not adapted based on the actual text height by default.

This API depends on the **lineHeight** property of [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md). When the value of **lineHeight** is less than the actual height of the text rendered under the current font size, the **fallbackLineSpacing** attribute takes effect.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the line height adapts based on the actual text height.<br>true indicates that the line height adapts based on the actual text height, and false indicates the opposite. <br>Default value: false. <br>When set to undefined or null, the default value is used. |

## horizontalScrolling

```TypeScript
horizontalScrolling(enabled: Optional<boolean>)
```

Sets whether to enable horizontal scrolling when the text width exceeds the content area width. This is applicable to scenarios where long text content (such as code snippets and long URLs) needs to be displayed without automatic line wrapping. If this API is not used for configuration, horizontal scrolling is disabled by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable horizontal scrolling.<br>The value true means to enable horizontal scrolling, and the value false means to disable horizontal scrolling, in which case the text wraps automatically. <br>Default value: false. When this parameter is set to undefined or null, horizontal scrolling is not enabled. |

## includeFontPadding

```TypeScript
includeFontPadding(include: Optional<boolean>)
```

Whether to add spacing to the first and last lines to avoid text truncation. This is applicable to scenarios such as text being clipped due to a small custom font line height and compact typesetting. If this API is not used, no spacing is added by default.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| include | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to add spacing to the first and last lines to avoid text truncation.<br>The value true means to add spacing to the first and last lines, and false means not to add spacing to the first and last lines. <br>Default value: false <br>If this parameter is set to undefined or null, the default value is used. |

## keyboardAppearance

```TypeScript
keyboardAppearance(appearance: Optional<KeyboardAppearance>)
```

Sets the keyboard appearance.

Applicable to scenarios where the keyboard visual style needs to be adjusted based on the application theme or immersive scenarios, such as using the DARK appearance in dark mode.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appearance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[KeyboardAppearance](../arkts-apis/arkts-arkui-keyboardappearance-e.md)&gt; | Yes | Keyboard appearance.<br>Default value: KeyboardAppearance.NONE_IMMERSIVE. <br>For the applicable scenarios of each enum value, see the KeyboardAppearance enum description. <br>When set to undefined or null, the default value is used. |

## maxLength

```TypeScript
maxLength(maxLength: Optional<number>)
```

Sets the maximum length of the component content.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxLength | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Maximum input length of the content. When the total length of the content (including text, images, symbols, and builders) reaches this value, no more content can be added.<br>Default value: Infinity, which means unlimited input. <br>**NOTE:** <br>Value range: [0, +∞). If this attribute is not set or is set to undefined or a negative number, the default value Infinity is used. If it is set to 0, no content can be entered. If it is set to a decimal, the integer part is used. |

## maxLines

```TypeScript
maxLines(maxLines: Optional<number>)
```

Sets the maximum number of lines that the component can display.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxLines | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Sets the maximum number of lines that the rich text can display. maxLines is the number of displayable lines. When maxLines is set, the content beyond the limit can be scrolled for display. If both the component height and the maximum number of lines are set, the component height takes effect first.<br>Value range: (0, UINT32_MAX]. <br>Default value: UINT32_MAX, which means unlimited input. <br>When set to 0, a negative number, undefined, or null, the default value is used. |

## onCopy

```TypeScript
onCopy(callback: Callback<CopyEvent>)
```

Triggered on copy operations. You can use this method to override the system's default behavior and implement the copying of text and images.

The **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) supports text and image copying by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[CopyEvent](arkts-arkui-richeditor-comp-copyevent-i.md)&gt; | Yes | User copy event. |

## onCut

```TypeScript
onCut(callback: Callback<CutEvent>)
```

Triggered on cut operations. You can use this method to override the system's default behavior and implement the cutting of text and images.

The **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) supports text and image cutting by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[CutEvent](arkts-arkui-richeditor-comp-cutevent-i.md)&gt; | Yes | Defines a custom cut event. |

## onDeleteComplete

```TypeScript
onDeleteComplete(callback: Callback<void>)
```

Triggered when content is deleted via the IME.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | Yes | Triggered when deletion in the input method is completed.<br>**Since:** 12 |

## onDidChange

```TypeScript
onDidChange(callback: OnDidChangeCallback) : RichEditorAttribute
```

Triggered after an addition or deletion operation is performed on the component. This callback is not executed if there is no actual addition or deletion of text.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnDidChangeCallback](../arkts-apis/arkts-arkui-ondidchangecallback-t.md) | Yes | Callback triggered after text and image changes, used to obtain the content range before and after the change. |

## onDidIMEInput

```TypeScript
onDidIMEInput(callback: Callback<TextRange>)
```

Triggered when text input is completed via the input method editor.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[TextRange](../arkts-apis/arkts-arkui-textrange-i.md)&gt; | Yes | **TextRange** indicates the text range for the current input.<br>Callback invoked when IME input is completed. |

## onEditingChange

```TypeScript
onEditingChange(callback: Callback<boolean>)
```

Triggered when the content editing state in the component changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the editing state changes.<br>true indicates the editing state, and false indicates the non-editing state. |

## onIMEInputComplete

```TypeScript
onIMEInputComplete(callback: Callback<RichEditorTextSpanResult>)
```

Triggered when text input is completed via the input method editor.

This API can return information about only one text span. You are advised to use the [onDidIMEInput](#ondidimeinput) API if the edit operation involves returning information about multiple text spans.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md)&gt; | Yes | [RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md) indicates the text span information after text input is complete. <br>Callback invoked after IME input is completed.<br>**Since:** 12 |

## onPaste

```TypeScript
onPaste(callback: PasteEventCallback)
```

Triggered before pasting is complete.

Developers can use this method to override the default system behavior and implement pasting of images and text.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PasteEventCallback](arkts-arkui-richeditor-comp-pasteeventcallback-t.md) | Yes | Callback used to subscribe to the pasted content.<br>**Since:** 12 |

## onReady

```TypeScript
onReady(callback: Callback<void>)
```

Triggered after the rich text component is initialized. After initialization, the component can respond to input and interaction normally.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when the initialization of the **RichEditor** component is complete.<br>**Since:** 12 |

## onSelect

```TypeScript
onSelect(callback: Callback<RichEditorSelection>)
```

Triggered when content is selected via left mouse button double-click and triggered again upon left mouse button release.

Triggered when content is selected via long press, and triggered again upon finger release.

The **onSelect** callback is not invoked during continuous selection adjustment with mouse or touch gestures, or during triple-click paragraph selection.

If the selection area needs to be detected in real time or the **RichEditor** component is built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md), use the **onSelectionChange** API.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorSelection](arkts-arkui-richeditor-comp-richeditorselection-i.md)&gt; | Yes | [RichEditorSelection](arkts-arkui-richeditor-comp-richeditorselection-i.md) indicates information about all the selected spans. <br>Callback invoked when content is selected.<br>**Since:** 12 |

## onSelectionChange

```TypeScript
onSelectionChange(callback: Callback<RichEditorRange>)
```

Triggered when the selection area or caret position changes in the editing state. When the caret position changes, the start and end positions of the selection area are the same.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md)&gt; | Yes | [RichEditorRange](arkts-arkui-richeditor-comp-richeditorrange-i.md) indicates the start and end positions of the content selection area. <br>Callback invoked when the content selection area changes or the caret position changes in the editing state. |

## onSubmit

```TypeScript
onSubmit(callback: SubmitCallback)
```

Triggered when the Enter key on the soft keyboard is pressed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [SubmitCallback](arkts-arkui-richeditor-comp-submitcallback-t.md) | Yes | Callback invoked when the Enter key on the soft keyboard is pressed, used to receive the Enter key type and submit event information. |

## onWillAttachIME

```TypeScript
onWillAttachIME(callback: Callback<IMEClient> | undefined)
```

Triggered before the component is bound to the IME.

Applies to scenarios that require customizing the input method behavior, such as setting input method extension configurations to implement specific input modes and custom input method functions.

Call the [setExtraConfig](../arkts-apis/arkts-arkui-imeclient-i.md#setextraconfig) method of [IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md) to set input method extension information. After the input method is bound, it receives this extension information which can be used to implement custom functionality.

<!--Del-->

Since API version 26.0.0, before the input box is about to bind the input method, you can set the keyboard style through the system API [setKeyboardAppearanceConfig](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#setkeyboardappearanceconfig) of `UIContext`. &lt;! --DelEnd--&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[IMEClient](../arkts-apis/arkts-arkui-imeclient-i.md)&gt; &#124; undefined | Yes | Callback invoked before the component is bound to the input method.<br>When the value is undefined, the bound callback event is cleared. |

## onWillChange

```TypeScript
onWillChange(callback: Callback<RichEditorChangeValue, boolean>) : RichEditorAttribute
```

Triggers the callback before the component performs an add or delete operation. Together with [onDidChange](#ondidchange), it forms a will/did timing pattern: onWillChange is triggered before the add or delete operation, and onDidChange is triggered after the add or delete operation. When onWillChange returns false, the component does not perform the add or delete operation, and onDidChange is not triggered. The two can be used at the same time.

This callback is not supported when the **RichEditor** component built with [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;[RichEditorChangeValue](arkts-arkui-richeditor-comp-richeditorchangevalue-i.md), boolean&gt; | Yes | [RichEditorChangeValue](arkts-arkui-richeditor-comp-richeditorchangevalue-i.md) indicates the image and text change information. The **boolean** value indicates whether the image and text can be modified. **true**: The image and text can be modified. **false**: The image and text cannot be modified. |

## orphanCharOptimization

```TypeScript
orphanCharOptimization(enabled: Optional<boolean>)
```

Whether to enable orphan character optimization during text typesetting.

This is applicable to scenarios such as long-text typesetting and e-book reading where a paragraph's last line containing only one character affects the reading experience. If this API is not used, orphan character optimization is disabled by default.

Orphan character optimization improves text layout by processing orphan characters (the first character of the last line of a paragraph) more efficiently. When enabled, it adjusts line break points to avoid orphan characters as much as possible. The orphan character optimization feature takes effect only when the wordBreak attribute of [RichEditorParagraphStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md) is not BREAK_ALL and the [locale](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the first [TextStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-textstyle-i.md) of the text to be laid out is "zh-Hans" or "zh-Hant".

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable orphan word optimization for the last line of a paragraph.<br>The value true means to enable orphan word optimization, and false means the opposite. <br>Default value: false. When set to undefined or null, orphan word optimization is not enabled. |

## placeholder

```TypeScript
placeholder(value: ResourceStr, style?: PlaceholderStyle)
```

Sets the prompt text displayed when there is no input.

After this attribute is set, the prompt text is displayed when the component has no content, and it automatically disappears after the user starts entering content.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Placeholder text. |
| style | [PlaceholderStyle](arkts-arkui-richeditor-comp-placeholderstyle-i.md) | No | Font style of the prompt text.<br>Pass this parameter when you need to customize the color, font size, and other styles of the placeholder; if omitted, the theme style is used by default. |

## punctuationOverflow

```TypeScript
punctuationOverflow(enabled: Optional<boolean>)
```

Sets whether to enable hanging punctuation at the end of a line.

When enabled, a single punctuation mark at the end of a line is allowed to exceed the typesetting width without wrapping. This is suitable for scenarios where you need to prevent a punctuation mark at the end of a line from wrapping to the beginning of the next line, so as to improve the typesetting aesthetics. If this API is not called, punctuation marks are not hung by default.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable hanging punctuation at the end of a line.<br>The value **true** means to enable hanging punctuation at the end of a line, and **false** means the opposite. <br>Default value: **false**. When this parameter is set to **undefined** or **null**, hanging punctuation is not enabled. |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

Sets the color of the scrollbar.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Color of the scrollbar.<br>Default value: **'#66182431'**, displayed as gray. <br>Note: Invalid values are treated as the default value. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

Sets the highlight color of the selected text. If the opacity is not set or is set to fully opaque, a 20% opacity is used by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Highlight color of the selected text.<br>The default value is 20% opacity. |

## selectedDragPreviewStyle

```TypeScript
selectedDragPreviewStyle(value: SelectedDragPreviewStyle | undefined)
```

Sets the drag preview style. This is applicable to scenarios where the appearance of dragged content needs to be customized, such as a drag preview effect that matches the application theme style.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedDragPreviewStyle](../arkts-apis/arkts-arkui-selecteddragpreviewstyle-i.md) &#124; undefined | Yes | Drag preview style. If it is set to **undefined**, the style will be reset. |

## singleLine

```TypeScript
singleLine(isEnable: boolean | undefined)
```

Sets whether to enable single-line mode. The single-line mode is disabled by default when this API is not specified.

> **NOTE:** 
> 
> In single-line mode, line breaks are displayed as spaces.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnable | boolean &#124; undefined | Yes | Whether to enable single-line mode.<br>The value true means to enable single-line mode, and false means the opposite. <br>If this parameter is set to undefined or null, it is processed as false, and single-line mode is not enabled. |

## stopBackPress

```TypeScript
stopBackPress(isStopped: Optional<boolean>)
```

Sets whether to prevent the back key from being passed through. This is applicable to scenarios such as preventing the back action to avoid data loss when edited content is not saved, and preventing users from accidentally exiting editing in dialog box editing.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isStopped | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to prevent the back key event from being propagated.<br>**true**: Propagation is prevented. **false**: Propagation is allowed. <br>Default value: **true** Invalid values are treated as the default value. |

## undoStyle

```TypeScript
undoStyle(style: Optional<UndoStyle>)
```

Sets whether to retain the original content style upon undo operations.

When the [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md) is used to build the **RichEditor** component, the original content style is retained by default upon undo operations, and is not affected by the attribute set by this API.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[UndoStyle](arkts-arkui-richeditor-comp-undostyle-e.md)&gt; | Yes | Option for whether to retain the original style when undoing or restoring.<br>Default value: UndoStyle.CLEAR_STYLE. <br>If this parameter is set to undefined or null, the default value is used. |
