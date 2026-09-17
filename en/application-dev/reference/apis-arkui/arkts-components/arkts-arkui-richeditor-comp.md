# RichEditor

**RichEditor** is a component that supports interactive text editing and mixture of text and imagery.

> **NOTE** > > - This component is supported since API version 10. Newly added content in later versions is marked with a > superscript to indicate the version in which it was introduced. > > - This component supports WithTheme since API version 26.0.0.

## Child Components

Not supported

## RichEditor

```TypeScript
RichEditor(value: RichEditorOptions)
```

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorOptions](arkts-arkui-richeditoroptions-i.md) | Yes | Options for initializing the component. |

## RichEditor

```TypeScript
RichEditor(options: RichEditorStyledStringOptions)
```

Called when create RichEditor.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | Yes | Options for initializing the component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md) | Defines the identity and position information of a BuilderSpan in **RichEditor**. |
| [CopyEvent](arkts-arkui-copyevent-i.md) | User copy event. |
| [CutEvent](arkts-arkui-cutevent-i.md) | Defines a custom cut event. |
| [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) | Whether to support keyboard avoidance. |
| [LeadingMarginPlaceholder](arkts-arkui-leadingmarginplaceholder-i.md) | Describes the leading margin placeholder, which dictates the distance between the left edges of the paragraph and the component. |
| [PasteEvent](arkts-arkui-pasteevent-i.md) | Defines a user paste event. |
| [PlaceholderStyle](arkts-arkui-placeholderstyle-i.md) | Sets the style of the placeholder text. |
| [PreviewMenuOptions](arkts-arkui-previewmenuoptions-i.md) | Defines the options of the preview menu. |
| [RichEditorBuilderSpan](arkts-arkui-richeditorbuilderspan-i.md) | Defines the BuilderSpan object of **RichEditor**, providing identity recognition and lifecycle awareness capabilities. |
| [RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md) | Sets the offset position and style of the inserted builder. |
| [RichEditorChangeValue](arkts-arkui-richeditorchangevalue-i.md) | Defines image and text change information. |
| [RichEditorDeleteValue](arkts-arkui-richeditordeletevalue-i.md) | Defines information about the deletion operation and the content to be deleted. |
| [RichEditorGesture](arkts-arkui-richeditorgesture-i.md) | Defines a user gesture event. |
| [RichEditorImageSpan](arkts-arkui-richeditorimagespan-i.md) | Image span information. |
| [RichEditorImageSpanOptions](arkts-arkui-richeditorimagespanoptions-i.md) | Sets the offset and style of an image span. |
| [RichEditorImageSpanResult](arkts-arkui-richeditorimagespanresult-i.md) | Provides the image information returned by the backend. |
| [RichEditorImageSpanStyle](arkts-arkui-richeditorimagespanstyle-i.md) | Image style. |
| [RichEditorImageSpanStyleResult](arkts-arkui-richeditorimagespanstyleresult-i.md) | Provides the image span style information returned by the backend. |
| [RichEditorInsertValue](arkts-arkui-richeditorinsertvalue-i.md) | Defines information about the text to be inserted. |
| [RichEditorLayoutStyle](arkts-arkui-richeditorlayoutstyle-i.md) | Defines image layout information. |
| [RichEditorOptions](arkts-arkui-richeditoroptions-i.md) | Defines the options for initializing the **RichEditor** component. |
| [RichEditorParagraphResult](arkts-arkui-richeditorparagraphresult-i.md) | Describes the returned paragraph information. |
| [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md) | Defines the paragraph style. |
| [RichEditorParagraphStyleOptions](arkts-arkui-richeditorparagraphstyleoptions-i.md) | Defines the paragraph style options. |
| [RichEditorRange](arkts-arkui-richeditorrange-i.md) | Defines the range of the **RichEditor**. |
| [RichEditorSelection](arkts-arkui-richeditorselection-i.md) | Defines information about the selected content. |
| [RichEditorSpanPosition](arkts-arkui-richeditorspanposition-i.md) | Defines span position information. |
| [RichEditorSpanStyleOptions](arkts-arkui-richeditorspanstyleoptions-i.md) | Defines the text span style options. |
| [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md) | Defines the options for initializing the **RichEditor** component. |
| [RichEditorSymbolSpanOptions](arkts-arkui-richeditorsymbolspanoptions-i.md) | Sets the offset and style of the **SymbolSpan** component. |
| [RichEditorSymbolSpanStyle](arkts-arkui-richeditorsymbolspanstyle-i.md) | Sets the symbol span style. |
| [RichEditorSymbolSpanStyleResult](arkts-arkui-richeditorsymbolspanstyleresult-i.md) | Provides the symbol span style information returned by the backend. |
| [RichEditorTextSpan](arkts-arkui-richeditortextspan-i.md) | Defines text span information. |
| [RichEditorTextSpanOptions](arkts-arkui-richeditortextspanoptions-i.md) | Defines the options for adding a text span. |
| [RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md) | Defines text span information. |
| [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | Provides text style information. |
| [RichEditorTextStyleResult](arkts-arkui-richeditortextstyleresult-i.md) | Provides the text span style information returned by the backend. |
| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditorupdateimagespanstyleoptions-i.md) | Defines the image span style options. |
| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditorupdatesymbolspanstyleoptions-i.md) | Defines the symbol span style options. |
| [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditorupdatetextspanstyleoptions-i.md) | Defines the text span style options. |
| [RichEditorUrlStyle](arkts-arkui-richeditorurlstyle-i.md) | URL information. |
| [SelectionMenuOptions](arkts-arkui-selectionmenuoptions-i.md) | Sets menu options. |

### Types

| Name | Description |
| --- | --- |
| [MenuCallback](arkts-arkui-menucallback-t.md) | Represents the callback invoked when the custom context menu on selection is shown or hidden. |
| [MenuOnAppearCallback](arkts-arkui-menuonappearcallback-t.md) | Represents the callback invoked when the custom context menu on selection appears. |
| [OnHoverCallback](arkts-arkui-onhovercallback-t.md) | Defines the callback triggered on hover. |
| [PasteEventCallback](arkts-arkui-pasteeventcallback-t.md) | Represents the callback invoked when a paste operation is about to complete. |
| [RichEditorSpan](arkts-arkui-richeditorspan-t.md) | Provides the span information of the **RichEditor** component. |
| [SubmitCallback](arkts-arkui-submitcallback-t.md) | Represents the callback invoked when the Enter key on the soft keyboard is pressed. |

### Enums

| Name | Description |
| --- | --- |
| [RichEditorDeleteDirection](arkts-arkui-richeditordeletedirection-e.md) | Defines the deletion direction. |
| [RichEditorResponseType](arkts-arkui-richeditorresponsetype-e.md) | Enumerates the response types of the menu. |
| [RichEditorSpanType](arkts-arkui-richeditorspantype-e.md) | Enumerates span types. |
| [UndoStyle](arkts-arkui-undostyle-e.md) | Enumerates the options for whether to retain the original style upon undo operations. |

## Examples

```TypeScript
### Example 1: Updating the Text Style

This example demonstrates how to update the text style using the [updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle) API. After modifying the style, you can use [getSpans](arkts-arkui-richeditorcontroller-c.md#getspans) to obtain the updated style information of the text.


```

```TypeScript
### Example 2: Binding a Custom Keyboard

This example shows how to bind a custom keyboard to the component using [customKeyboard](#customkeyboard).


```

```TypeScript
### Example 3: Binding a Custom Menu

This example illustrates how to bind a custom menu to the component using [bindSelectionMenu](#bindselectionmenu).

The paste menu item in this example involves reading pasteboard data. Therefore, you need to [request permissions to access the pasteboard](../../../basic-services/pasteboard/get-pastedata-permission-guidelines.md) as required.

> NOTE
> 
> The system does not provide preset icons such as bold and italic. The sample code uses the default system icons. When using them, developers need to replace the resources in icons with their own.


```

```TypeScript
### Example 4: Updating the Image Style

This example demonstrates how to update the image style using the [updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle) API.


```

```TypeScript
### Example 5: Binding a Gesture Event to a Span

This example shows how to bind a [gesture](arkts-arkui-richeditorgesture-i.md) callback to a span.


```

```TypeScript
### Example 6: Updating and Obtaining Paragraph Styles

This example demonstrates how to update paragraph styles using the [updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle) API and obtain paragraph information within a specified range using the [getParagraphs](#getparagraphs11) API.


```

```TypeScript
### Example 7: Updating the Preset Style and Indent

This example demonstrates how to update the preset text style using the [setTypingStyle](arkts-arkui-richeditorbasecontroller-c.md#settypingstyle) API and set paragraph indents using the [updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle) API.


```

```TypeScript
### Example 8: Setting Text Weight and Shadow

Sets the font weight and shadow of the text through the [updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle) API.


```

```TypeScript
### Example 9: Adding Custom Layout Spans

This example shows how to add custom layout spans using the [addBuilderSpan](arkts-arkui-richeditorcontroller-c.md#addbuilderspan) API.


```

```TypeScript
### Example 10: Using and Managing BuilderSpan in a Component

This example demonstrates how to add a custom layout span using the [addBuilderSpan](arkts-arkui-richeditorcontroller-c.md#addbuilderspan) API. APIs, such as [getSpans](arkts-arkui-richeditorcontroller-c.md#getspans) and [onWillChange](#onwillchange12), do not return the internal information of BuilderSpan. You need to manage the BuilderSpan state and update it when the component content changes.


```

```TypeScript
### Example 11: Configuring Text Recognition

This example demonstrates how to enable text recognition by setting [enableDataDetector](#enabledatadetector11) to true and configuring text recognition settings using the [dataDetectorConfig](#datadetectorconfig11) API.
```

```TypeScript
### Example 12: Setting Cursor, Handle, and Highlight Colors

Sets the cursor and handle colors of the input box through the [caretColor](#caretcolor12) attribute, and sets the highlight color of selected text through the [selectedBackgroundColor](#selectedbackgroundcolor12) attribute.


```

```TypeScript
### Example 13: Setting Line Height and Letter Spacing

This example demonstrates how to configure text line height ([lineHeight](arkts-arkui-richeditortextstyle-i.md)) and letter spacing ([letterSpacing](arkts-arkui-richeditortextstyle-i.md)) using the [updateSpanStyle](arkts-arkui-richeditorcontroller-c.md#updatespanstyle) API.


```

```TypeScript
### Example 14: Adding a Custom Paste Event

This example shows how to add a custom paste event to the component using the [onPaste](#onpaste11) event and customize user paste behavior using the [PasteEvent](arkts-arkui-pasteevent-i.md) API.


```

```TypeScript
### Example 15: Setting Text Feature Effects

This example sets the font feature effect ([fontFeature](arkts-arkui-richeditortextstyle-i.md)) through the [addTextSpan](arkts-arkui-richeditorcontroller-c.md#addtextspan) API. When the FontFeature attribute with the "ss01" feature is added, the number "0" changes from the original oval shape to a shape with rounded corners. In addition, the stroke join style of the text is set through the strokeJoinStyle API of [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md).

Since API version 26.0.0, the strokeJoinStyle API is added to [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md).


```

```TypeScript
### Example 16: Setting Custom Keyboard Avoidance

This example shows how to bind a custom keyboard using the [customKeyboard](#customkeyboard) attribute and configure whether the custom keyboard supports keyboard avoidance using the [KeyboardOptions](arkts-arkui-keyboardoptions-i.md) parameter.


```

```TypeScript
### Example 17: Viewing the Editing State

This example demonstrates how to obtain the current editing state of the rich text using the [isEditing](#isediting12) API. The [onEditingChange](arkts-arkui-richeditor-comp-attribute.md#oneditingchange) event can be added to the component to log whether the component is currently in editing mode.


```

```TypeScript
### Example 18: Configuring Text Change Callback

This example shows how to add the [onWillChange](#onwillchange12) event to the component, which triggers a callback before the component performs any insert or delete operations.


```

```TypeScript
### Example 19: Configuring the Enter Key Function of the Input Method

This example demonstrates how to set the Enter key type of the soft keyboard using the [enterKeyType](#enterkeytype12) attribute.


```

```TypeScript
### Example 20: Setting the Paragraph Line Break Rule

This example shows how to set the line break rule ([lineBreakStrategy](arkts-arkui-richeditorparagraphstyle-i.md)) using the [updateParagraphStyle](arkts-arkui-richeditorcontroller-c.md#updateparagraphstyle) API and obtain the current line break rule using the [getParagraphs](#getparagraphs11) API.


```

```TypeScript
### Example 21: Using Basic Functionality of Styled Strings

This example demonstrates how to bind a [styled string](./ts-universal-styled-string.md) to a RichEditor component using the [setStyledString](#setstyledstring12) API in [RichEditorStyledStringController](arkts-arkui-richeditorstyledstringcontroller-c.md). This feature is available since API version 20. The [getStyledString](#getstyledstring12) API can be used to obtain the styled string displayed by the RichEditor component.


```

```TypeScript
### Example 22: Obtaining Layout Information

This example shows how to obtain layout information using the [getLayoutManager](#getlayoutmanager12) API. It includes obtaining the total number of lines for the component content or [placeholder](#placeholder12) using [getLineCount](ts-text-common.md#getlinecount12), the glyph position closest to a given coordinate using [getGlyphPositionAtCoordinate](ts-text-common.md#getglyphpositionatcoordinate12), and line metrics, text style information, and font properties using [getLineMetrics](ts-text-common.md#getlinemetrics12).


```

```TypeScript
### Example 23: Configuring Extended Options for the System Default Menu

This example demonstrates how to configure extended options for the system default menu via the [editMenuOptions](#editmenuoptions12) attribute. You can customize the text labels, icons, and callback methods of menu extended options. This feature is available since API version 20.


```

```TypeScript
### Example 24: Setting Common Component Attributes

Since API version 18, this example uses the [barState](#barstate13) attribute to set the display mode of the component scrollbar. It uses the [enableKeyboardOnFocus](#enablekeyboardonfocus12) attribute to set whether to proactively pull up the soft keyboard when the component gains focus by means other than tapping. It uses the [enableHapticFeedback](#enablehapticfeedback13) attribute to set whether the component supports haptic feedback. It uses the [getPreviewText](#getpreviewtext12) API to obtain the preview text of the component. It uses the [stopBackPress](#stopbackpress18) attribute to set whether to prevent the back key from being passed to other components or the application side.Since API version 21, this example uses the [scrollBarColor](#scrollbarcolor21) attribute to set the scrollbar color of the RichEditor component.


```

```TypeScript
### Example 25: Obtaining the Caret's Relative Position Rectangle in the Component

This example shows how to obtain the caret's relative position rectangle in the component using the [getCaretRect](arkts-arkui-richeditorbasecontroller-c.md#getcaretrect) method of RichEditorBaseController, available since API version 18.


```

```TypeScript
### Example 26: Setting the Maximum Number of Lines and Maximum Number of Characters

This example shows how to set the maximum number of characters using [maxLength](#maxlength18) and the maximum number of lines using [maxLines](#maxlines18), available since API version 18.


```

```TypeScript
### Example 27: Setting the URL Style for Text

This example demonstrates how to implement text hyperlink using [UrlStyle](arkts-arkui-richeditorurlstyle-i.md), which is supported by the addTextSpan and updateSpanStyle APIs. When users tap the formatted text, the app navigates to the specified URL. This feature is available since API version 19.


```

```TypeScript
### Example 28: Configuring Style Behavior for Undo Operations

This example demonstrates how to retain original content styles upon undo operations for RichEditor components that do not use styled strings. You can enable this behavior by setting [undoStyle](#undostyle20) (available since API version 20) to UndoStyle.KEEP_STYLE.


```

```TypeScript
### Example 29: Setting the Preset Paragraph Style

This example demonstrates how to set the preset paragraph style using the [setTypingParagraphStyle](arkts-arkui-richeditorbasecontroller-c.md#settypingparagraphstyle) API, available since API version 20.


```

```TypeScript
### Example 30: Setting Text Decoration Thickness and Multiple Decorations

This example demonstrates how to use [thicknessScale](ts-universal-styled-string.md#decorationstyle) to set the thickness of text decoration and [enableMultiType](ts-universal-styled-string.md#decorationoptions20) to set multiple decorations, available since API version 20.


```

```TypeScript
### Example 31: Enabling Automatic Spacing Between Chinese and Western Text

This example demonstrates how to configure automatic spacing between Chinese and Western characters using the [enableAutoSpacing](#enableautospacing20) attribute, available since API version 20.


```

```TypeScript
### Example 32: Setting an AI Menu for Text Selection

This example demonstrates how to configure the AI menu for text selection using the [enableSelectedDataDetector](#enableselecteddatadetector22) API, available since API version 22.
```

```TypeScript
### Example 33: Listening for the Input Method Binding Event

This example demonstrates how to use the [onWillAttachIME](#onwillattachime22) event to listen for the input method binding event, available since API version 22.


```

```TypeScript
### Example 34: Deleting the Character at the End of the Text Box

This example demonstrates how to call [deleteBackward](#deletebackward23) to delete the character before the caret in the editing state with a custom keyboard, available since API version 23.


```

```TypeScript
### Example 35: Optimizing the Display of Minority Languages

This example uses the [includeFontPadding](#includefontpadding23) attribute to add font padding at the top of the first line and the bottom of the last line of text. It also uses the [fallbackLineSpacing](#fallbacklinespacing23) attribute to implement adaptive line spacing which adjusts dynamically according to the actual text height.

The includeFontPadding and fallbackLineSpacing attributes are added since API version 23.


```

```TypeScript
### Example 36 (Setting Leading Punctuation Compression and Trailing Punctuation Hanging)

This example uses [compressLeadingPunctuation](#compressleadingpunctuation23) to set leading punctuation compression, and [punctuationOverflow](#punctuationoverflow) to set trailing punctuation hanging.

After the text wraps automatically, the remaining content (including punctuation) must fit into the previous line for punctuation hanging to take effect.

Since API version 23, the compressLeadingPunctuation API is added.

Since API version 26.0.0, the punctuationOverflow API is added.


```

```TypeScript
### Example 37: Setting the Drag Preview Style

This example demonstrates how to set the drag preview style using the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API.

The selectedDragPreviewStyle API is supported since API version 23.


```

```TypeScript
### Example 38: Setting Single-Line Mode

This example demonstrates how to set single-line mode using the [singleLine](arkts-arkui-richeditor-comp-attribute.md#singleline) API.

The singleLine API is added since API version 23.


```

```TypeScript
### Example 39: Setting the Placeholder Text of the Styled String

This example demonstrates how to set the placeholder text of the styled string using the [setStyledPlaceholder](#setstyledplaceholder24) API.

The setStyledPlaceholder API is added since API version 24.


```

```TypeScript
### Example 40: Enabling/Disabling Orphan Character Optimization

This example uses the [orphanCharOptimization](#orphancharoptimization) API to enable orphan character optimization, ensuring that no orphan character appears on the last line of a paragraph.

The orphanCharOptimization API is supported since API version 26.0.0.


```

```TypeScript
### Example 41: Setting Horizontal Scrolling

This example demonstrates how to set horizontal scrolling using [horizontalScrolling](#horizontalscrolling).

The horizontalScrolling API is added since API version 26.0.0.


```

```TypeScript
### Example 42 (Setting a Text Shader Effect)

This example implements a text shader effect through the shaderStyle API in [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md).

Since API version 26.0.0, RichEditorParagraphStyle adds the shaderStyle API.


```

```TypeScript
### Example 43 (Scroll Text in a Specified Range into the Visible Area)

This example uses [scrollToVisible](#scrolltovisible) to scroll text outside the visible area into the visible area.

Since API version 26.0.0, the scrollToVisible API is added.


```

```TypeScript
### Example 44 (Setting Image Stretching)

This example stretches an image in different directions by setting the resizable attribute of [RichEditorImageSpanStyle](arkts-arkui-richeditorimagespanstyle-i.md).

Since API version 26.1.0, the resizable attribute is added to RichEditorImageSpanStyle.
```
