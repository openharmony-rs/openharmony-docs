# SearchParams

```TypeScript
export interface SearchParams
```

Provides optional attributes for the search area.

**Since:** 18

<!--Device-unnamed-export interface SearchParams--><!--Device-unnamed-export interface SearchParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: EditableTextOnChangeCallback
```

Callback triggered when the content in the text box changes. Default value: **undefined**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onChange?: EditableTextOnChangeCallback--><!--Device-SearchParams-onChange?: EditableTextOnChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onContentScroll

```TypeScript
onContentScroll?: OnContentScrollCallback
```

Callback triggered when the text content is scrolled. Default value: **undefined**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onContentScroll?: OnContentScrollCallback--><!--Device-SearchParams-onContentScroll?: OnContentScrollCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPaste

```TypeScript
onPaste?: OnPasteCallback
```

Callback triggered when a paste operation is performed. Default value: **undefined**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onPaste?: OnPasteCallback--><!--Device-SearchParams-onPaste?: OnPasteCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTextSelectionChange

```TypeScript
onTextSelectionChange?: OnTextSelectionChangeCallback
```

Callback triggered when the position of the text selection changes or when the cursor position changes during the editing state. Default value: **undefined**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onTextSelectionChange?: OnTextSelectionChangeCallback--><!--Device-SearchParams-onTextSelectionChange?: OnTextSelectionChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelIcon

```TypeScript
cancelIcon?: IconOptions
```

Style of the cancel button on the right. Default value: **{style: CancelButtonStyle.INPUT, icon: {size: '16vp', color: '#99ffffff', src:' '}}**.

When style is set to **CancelButtonStyle.CONSTANT**, the cancel button is displayed in a default style.

**Type:** IconOptions

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-cancelIcon?: IconOptions--><!--Device-SearchParams-cancelIcon?: IconOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## caretStyle

```TypeScript
caretStyle?: CaretStyle
```

Pointer style. Default value: **{width: '1.5vp', color: '#007DFF'}**.

**Type:** [CaretStyle](arkts-arkui-caretstyle-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-caretStyle?: CaretStyle--><!--Device-SearchParams-caretStyle?: CaretStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## componentBackgroundColor

```TypeScript
componentBackgroundColor?: ResourceColor
```

Background color of a component. Default value: **$r('sys.color.ohos_id_color_text_field_sub_bg')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-componentBackgroundColor?: ResourceColor--><!--Device-SearchParams-componentBackgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## copyOptions

```TypeScript
copyOptions?: CopyOptions
```

Whether the input text can be copied. Default value: **CopyOptions.LocalDevice**.

**Type:** [CopyOptions](arkts-arkui-copyoptions-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-copyOptions?: CopyOptions--><!--Device-SearchParams-copyOptions?: CopyOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: TextDecorationOptions
```

Text decorative line options. Default value: **{type: TextDecorationType.None, color: Color.Black, style: TextDecorationStyle.SOLID}**.

**Type:** [TextDecorationOptions](../arkts-components/arkts-arkui-common-comp-textdecorationoptions-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-decoration?: TextDecorationOptions--><!--Device-SearchParams-decoration?: TextDecorationOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## editMenuOptions

```TypeScript
editMenuOptions?: EditMenuOptions
```

Extended options of the custom context menu on selection, including the text content, icon, and callback. Default value: **undefined**.

**Type:** [EditMenuOptions](arkts-arkui-editmenuoptions-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-editMenuOptions?: EditMenuOptions--><!--Device-SearchParams-editMenuOptions?: EditMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable haptic feedback. The value **true** means to enable haptic feedback. Default value: **true**.

**Type:** boolean

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-enableHapticFeedback?: boolean--><!--Device-SearchParams-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableKeyboardOnFocus

```TypeScript
enableKeyboardOnFocus?: boolean
```

Whether to automatically open the soft keyboard when the **Search** component gains focus. The value **true** means to automatically open the soft keyboard when the **Search** component gains focus. Default value: **true**.

**Type:** boolean

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-enableKeyboardOnFocus?: boolean--><!--Device-SearchParams-enableKeyboardOnFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewText

```TypeScript
enablePreviewText?: boolean
```

Whether to enable preview text. The value **true** means to enable preview text. Default value: **true**.

Preview text of the input method should be enabled. Preview text is in a temporary state and does not support text interception. As such, it does not trigger **onWillInsert** and **onDidInsert** callbacks.

**Type:** boolean

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-enablePreviewText?: boolean--><!--Device-SearchParams-enablePreviewText?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enterKeyType

```TypeScript
enterKeyType?: EnterKeyType
```

Type of the Enter key. Default value: **EnterKeyType.Search**.

**Type:** [EnterKeyType](../arkts-components/arkts-arkui-textinput-comp-enterkeytype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-enterKeyType?: EnterKeyType--><!--Device-SearchParams-enterKeyType?: EnterKeyType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color of the input text. Default value: **$r('sys.color.ohos_id_color_text_secondary')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-fontColor?: ResourceColor--><!--Device-SearchParams-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: ResourceStr
```

Font feature, for example, monospaced digits.

Format: normal | &lt;feature-tag-value&gt;

Syntax for **&lt;feature-tag-value&gt;**: &lt;string&gt; [ &lt;integer&gt; | on | off ]

There can be multiple **&lt;feature-tag-value&gt;** values, which are separated by commas (,).

For example, the input format for monospaced digits is "ss01" on. Default value: **undefined**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-fontFeature?: ResourceStr--><!--Device-SearchParams-fontFeature?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hideSelectionMenu

```TypeScript
hideSelectionMenu?: boolean
```

Whether to hide the system text selection menu.

**true**: The system text selection menu does not appear under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box. **false**: The system text selection menu appears under the following circumstances: clicking the text box cursor, long-pressing the text box, double-tapping the text box, triple-tapping the text box, or right-clicking the text box. Default value: **false**.

**Type:** boolean

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-hideSelectionMenu?: boolean--><!--Device-SearchParams-hideSelectionMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inputFilter

```TypeScript
inputFilter?: InputFilterParams
```

Regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. The specified regular expression can match single characters, but not strings. Default value: **undefined**.

- **value**: regular expression.  
- **error**: Filtered-out content to return when regular expression matching fails.

**Type:** [InputFilterParams](arkts-arkui-atomicservice-atomicservicesearch-inputfilterparams-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-inputFilter?: InputFilterParams--><!--Device-SearchParams-inputFilter?: InputFilterParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string | Resource
```

Letter spacing. A positive value causes characters to spread farther apart, and a negative value bring characters closer together. The value for floating point numbers is **0.0**, in units of px. If the input is not a number and cannot be parsed as a number, the default value will be used.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-letterSpacing?: number | string | Resource--><!--Device-SearchParams-letterSpacing?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | string | Resource
```

Maximum font size. For the setting to take effect, this attribute must be used together with **minFontSize** or layout constraint settings. Default value: **undefined**.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-maxFontSize?: number | string | Resource--><!--Device-SearchParams-maxFontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLength

```TypeScript
maxLength?: number
```

Maximum number of characters in the text input. By default, there is no maximum number of characters. When the maximum number is reached, no more characters can be entered. Default value: **-1**.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-maxLength?: number--><!--Device-SearchParams-maxLength?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | string | Resource
```

Minimum font size. For the setting to take effect, this attribute must be used together with **maxFontSize** or layout constraint settings. Default value: **undefined**.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-minFontSize?: number | string | Resource--><!--Device-SearchParams-minFontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCopy

```TypeScript
onCopy?: Callback<string>
```

Callback triggered when a copy operation is performed. Default value: **undefined**.

**Type:** Callback&lt;string&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onCopy?: Callback<string>--><!--Device-SearchParams-onCopy?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCut

```TypeScript
onCut?: Callback<string>
```

Callback triggered when a cut operation is performed. Default value: **undefined**.

**Type:** Callback&lt;string&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onCut?: Callback<string>--><!--Device-SearchParams-onCut?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDelete

```TypeScript
onDidDelete?: Callback<DeleteValue>
```

Callback triggered when text is deleted. Default value: **undefined**.

**Type:** Callback&lt;[DeleteValue](arkts-arkui-deletevalue-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onDidDelete?: Callback<DeleteValue>--><!--Device-SearchParams-onDidDelete?: Callback<DeleteValue>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidInsert

```TypeScript
onDidInsert?: Callback<InsertValue>
```

Callback triggered when text is inserted. Default value: **undefined**.

**Type:** Callback&lt;[InsertValue](arkts-arkui-insertvalue-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onDidInsert?: Callback<InsertValue>--><!--Device-SearchParams-onDidInsert?: Callback<InsertValue>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEditChange

```TypeScript
onEditChange?: Callback<boolean>
```

Callback triggered when the input status changes. If a cursor is displayed, that is, the value of **isEditing** is **true**, the text box is in the editing state. Default value: **undefined**.

**Type:** Callback&lt;boolean&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onEditChange?: Callback<boolean>--><!--Device-SearchParams-onEditChange?: Callback<boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSubmit

```TypeScript
onSubmit?: Callback<string> | SearchSubmitCallback
```

Callback triggered when users click the search icon or the search button, or touch the search button on a soft keyboard. Default value: **undefined**.

**Type:** Callback&lt;string&gt; &#124; [SearchSubmitCallback](../arkts-components/arkts-arkui-search-comp-searchsubmitcallback-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onSubmit?: Callback<string> | SearchSubmitCallback--><!--Device-SearchParams-onSubmit?: Callback<string> | SearchSubmitCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDelete

```TypeScript
onWillDelete?: Callback<DeleteValue, boolean>
```

Callback triggered when text is about to be deleted. **true**: Delete the text. **false**: Do not delete the text. Default value: **undefined**.

**Type:** Callback&lt;[DeleteValue](arkts-arkui-deletevalue-i.md), boolean&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onWillDelete?: Callback<DeleteValue, boolean>--><!--Device-SearchParams-onWillDelete?: Callback<DeleteValue, boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillInsert

```TypeScript
onWillInsert?: Callback<InsertValue, boolean>
```

Callback triggered when text is about to be inserted. **true**: Insert the input content into the result string. **false**: Do not insert the input content into the result string. Default value: **undefined**.

**Type:** Callback&lt;[InsertValue](arkts-arkui-insertvalue-i.md), boolean&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-onWillInsert?: Callback<InsertValue, boolean>--><!--Device-SearchParams-onWillInsert?: Callback<InsertValue, boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholderColor

```TypeScript
placeholderColor?: ResourceColor
```

Placeholder text color. Default value: **$r('sys.color.ohos_id_color_text_secondary')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-placeholderColor?: ResourceColor--><!--Device-SearchParams-placeholderColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholderFont

```TypeScript
placeholderFont?: Font
```

Placeholder text style, including the font size, font weight, font family, and font style. Default value: **{size: $r('sys_float.ohos_id_text_size_body1')}**.

**Type:** Font

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-placeholderFont?: Font--><!--Device-SearchParams-placeholderFont?: Font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pressedBackgroundColor

```TypeScript
pressedBackgroundColor?: ResourceColor
```

Background color of the pressed component. Default value: **$r('sys.color.ohos_id_color_click_effect')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-pressedBackgroundColor?: ResourceColor--><!--Device-SearchParams-pressedBackgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## searchButton

```TypeScript
searchButton?: SearchButtonParams
```

Search button located next to the search text box. Clicking the search button triggers both **onSubmit** and **onClick** callbacks.

- **value**: Text on the search button located next to the search text box.  
- **option**: Font of the search text box. Default value: **{fontSize: '16fp', fontColor: '#ff3f97e9'}**

**Type:** [SearchButtonParams](arkts-arkui-atomicservice-atomicservicesearch-searchbuttonparams-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-searchButton?: SearchButtonParams--><!--Device-SearchParams-searchButton?: SearchButtonParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## searchIcon

```TypeScript
searchIcon?: IconOptions | SymbolGlyphModifier
```

Style of the search icon on the left.

Default value in light mode: **{size: '16vp', color: '#99182431', src:' '}**.

Default value in dark mode: **{size: '16vp', color: '#99ffffff', src:' '}**.

**Type:** IconOptions &#124; [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-searchIcon?: IconOptions | SymbolGlyphModifier--><!--Device-SearchParams-searchIcon?: IconOptions | SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## searchKey

```TypeScript
searchKey?: ResourceStr
```

Search key used to find a unique **search** component. Default value: **undefined**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-searchKey?: ResourceStr--><!--Device-SearchParams-searchKey?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

Background color of the selected text. By default, a 20% opacity is applied.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-selectedBackgroundColor?: ResourceColor--><!--Device-SearchParams-selectedBackgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Text alignment mode in the search text box. Default value: **TextAlign.Start**.

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-textAlign?: TextAlign--><!--Device-SearchParams-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textFont

```TypeScript
textFont?: Font
```

Style of the text entered in the search box, including the font size, font width, font family, and font style. Currently, only the default font family is supported. Default value: **{size: $r('sys_float.ohos_id_text_size_body1')}**.

**Type:** Font

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-textFont?: Font--><!--Device-SearchParams-textFont?: Font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: Dimension
```

Indent of the first line text. Default value: **0**.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-textIndent?: Dimension--><!--Device-SearchParams-textIndent?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: SearchType
```

Text box type. Default value: **SearchType.Normal**.

**Type:** [SearchType](../arkts-components/arkts-arkui-search-comp-searchtype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SearchParams-type?: SearchType--><!--Device-SearchParams-type?: SearchType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
