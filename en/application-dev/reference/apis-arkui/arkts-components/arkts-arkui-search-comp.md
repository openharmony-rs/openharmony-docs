# Search

The **Search** component provides an area for users to enter search queries.

> **NOTE** > > This component supports plain text only. For rich text, use the RichEditor component.

## Child Components

Not supported

## Search

```TypeScript
Search(options?: SearchOptions)
```

Defines the constructor of Search.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SearchOptions](arkts-arkui-searchoptions-i.md) | No | Initialization options of the **Search** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) | Defines the CancelButton options. |
| [CancelButtonSymbolOptions](arkts-arkui-cancelbuttonsymboloptions-i.md) | Defines the CancelButton symbol options. |
| [IconOptions](arkts-arkui-iconoptions-i.md) | Defines the icon options. |
| [SearchButtonOptions](arkts-arkui-searchbuttonoptions-i.md) | Defines the SearchButton options. |
| [SearchOptions](arkts-arkui-searchoptions-i.md) | Describes the initialization options of the **Search** component. |

### Types

| Name | Description |
| --- | --- |
| [SearchSubmitCallback](arkts-arkui-searchsubmitcallback-t.md) | Called when the search icon, search button, or soft keyboard search button is clicked. |

### Enums

| Name | Description |
| --- | --- |
| [CancelButtonStyle](arkts-arkui-cancelbuttonstyle-e.md) | Enum for the style of cancel button. |
| [SearchType](arkts-arkui-searchtype-e.md) | Enumerates the text input types of a search box. |

## Examples

```TypeScript
### Example 1 (Setting and Obtaining the Cursor Position)

Since API version 8, this example implements the setting and obtaining of the cursor position through [controller](arkts-arkui-searchcontroller-c.md).


```

```TypeScript
### Example 2 (Setting the Search and Delete Icons)

This example demonstrates the effect of setting the search and delete icons through the [searchButton](#searchbutton) (from API version 8), [searchIcon](#searchicon10) (from API version 10), and [cancelButton](#cancelbutton10) (from API version 10) attributes.


```

```TypeScript
### Example 3 (Setting a Custom Keyboard)

This example uses the [customKeyboard](#customkeyboard10) (from API version 10) attribute to set the input parameter type in value to [CustomBuilder](ts-types.md#custombuilder8) and ComponentContent, respectively, implementing the custom keyboard feature.

From API version 22, the [customKeyboard](#customkeyboard10) attribute adds the input parameter type ComponentContent.


```

```TypeScript
### Example 4 (Setting the Enter Key Type of the Input Method)

This example uses the [enterKeyType](#enterkeytype12) (from API version 12) attribute to dynamically switch the Enter key type of the input method.


```

```TypeScript
### Example 5 (Setting the Text Style)

Since API version 12, this example shows text effects in different styles through the [lineHeight](#lineheight12), [letterSpacing](#letterspacing12), and [decoration](#decoration12) attributes.


```

```TypeScript
### Example 6 (Setting Text Feature Effects)

This example uses the [fontFeature](#fontfeature12) (since API version 12) attribute to implement the display effect of text under different font features.


```

```TypeScript
### Example 7 (Custom Keyboard Avoidance)

This example uses the [customKeyboard](#customkeyboard10) (since API version 10) attribute to configure the [KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12) (since API version 12) interface to implement custom keyboard avoidance.


```

```TypeScript
### Example 8 (Setting Text Auto-Adaptation)

Since API version 12, this example demonstrates the effect of adaptive font size through the [minFontSize](#minfontsize12) and [maxFontSize](#maxfontsize12) attributes.


```

```TypeScript
### Example 9 (Supports Insert and Delete Callbacks)

Since API version 12, this example implements the insert and delete effects through the [onWillInsert](#onwillinsert12), [onDidInsert](#ondidinsert12), [onWillDelete](#onwilldelete12), and [onDidDelete](#ondiddelete12) APIs. Since API version 15, it shows the specific information when the text content is about to change through the [onWillChange](#onwillchange15) API.


```

```TypeScript
### Example 10 (Custom Menu for Text Extension)

Since API version 12, this example uses the [editMenuOptions](#editmenuoptions12) API to set the text content, icon, and callback of custom menu extension items. In addition, menu data can be set in the [onPrepareMenu](ts-text-common.md#attributes-1) callback (since API version 20).


```

```TypeScript
### Example 11 (Setting a Symbol-Type Clear Button)

Since API version 10, this example uses the [searchIcon](#searchicon10) and [cancelButton](#cancelbutton10) attributes to demonstrate the effect of customizing the style of the symbol-type clear button on the right.


```

```TypeScript
### Example 12 (Setting Whether Text Can Be Copied)

This example uses the [copyOption](#copyoption9), [onWillCopy](#onwillcopy), and [onWillCut](#onwillcut) APIs to show how to set text copying, how to intercept system copying, and how to intercept system cutting.

Since API version 26.0.0, the [onWillCopy](#onwillcopy) and [onWillCut](#onwillcut) APIs are added.


```

```TypeScript
### Example 13 (Setting Text Horizontal Alignment/Cursor Style/Selected Background Color)

This example uses the [textAlign](#textalign9) (since API version 9), [caretStyle](#caretstyle10) (since API version 10), and [selectedBackgroundColor](#selectedbackgroundcolor12) (since API version 12) attributes to demonstrate how to set the horizontal alignment of text, the cursor style, and the selected background color.


```

```TypeScript
### Example 14 (Setting Default Focus and Bringing Up the Soft Keyboard)

This example shows how to set default focus and bring up the soft keyboard by using the [defaultFocus](ts-universal-attributes-focus.md#defaultfocus9) (from API version 9) and [enableKeyboardOnFocus](#enablekeyboardonfocus10) (from API version 10) attributes.


```

```TypeScript
### Example 15 (Disabling the System Text Selection Menu)

This example shows how to disable the system text selection menu through the [selectionMenuHidden](#selectionmenuhidden10) attribute (from API version 10).


```

```TypeScript
### Example 16 (Filtering the Input Text)

Since API version 12, this example uses the [inputFilter](#inputfilter12) attribute to show how to filter the input text to restrict the input content.


```

```TypeScript
### Example 17 (Selecting Text Content in a Specified Range)

This example uses [setTextSelection](#settextselection12) (from API version 12) to demonstrate how to select text content in a specified range and the show/hide policy of the menu.


```

```TypeScript
### Example 18 (Setting the Text Scroll Event)

Since API version 10, this example shows how to set the callback for the text scroll event through the [onContentScroll](#oncontentscroll10) event.


```

```TypeScript
### Example 19 (Setting the Minimum and Maximum Font Ranges)

Since API version 18, this example uses [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18) to set the minimum and maximum font display ranges. After the system font size is adjusted, the text font size will not exceed the ranges set by [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18). The following example shows the zoom-in and zoom-out effects of the Search component after the system font is adjusted under different font size limit conditions.
```

```TypeScript
// In AppScope/app.json5, modify the following code.
{
  "app": {
    "bundleName": "com.example.myapplication",
    "vendor": "example",
    "versionCode": 1000000,
    "versionName": "1.0.0",
    "icon": "$media:app_icon",
    "label": "$string:app_name",
    "configuration": "$profile:configuration"
  }
}
```

```TypeScript
 
```

```TypeScript
### Example 20 (Setting Text Stroke)

Since API version 20, this example uses the [strokeWidth](#strokewidth20) and [strokeColor](#strokecolor20) attributes to set the stroke width and color of the text.

Since API version 26.0.0, the [strokeJoinStyle](#strokejoinstyle) API is added to set the corner style of the text stroke.


```

```TypeScript
### Example 21 (Setting Automatic Spacing Between Chinese and Western Characters)

Since API version 20, this example sets automatic spacing between Chinese and Western characters through the [enableAutoSpacing](#enableautospacing20) attribute.


```

```TypeScript
### Example 22 (Setting the placeholder rich text style)

Since API version 22, this example sets the placeholder rich text style through the [setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22) API.


```

```TypeScript
### Example 23 (Setting IME Extension Information)

Since API version 22, this example uses [IMEClient](ts-text-common.md#imeclient20)'s setExtraConfig to set the IME extension information.
```

```TypeScript
### Example 24 (Setting the Search Box Divider Color)

Since API version 23, this example sets the search box divider color through the [dividerColor](#dividercolor23) API.


```

```TypeScript
### Example 25 (Setting Leading Punctuation Compression)

This example uses the [compressLeadingPunctuation](#compressleadingpunctuation23) API to set leading punctuation compression. When a punctuation mark with spacing on the left is at the beginning of a line, the punctuation directly compresses the spacing to the left boundary.

Since API version 23, the compressLeadingPunctuation API is supported.


```

```TypeScript
### Example 26 (Setting Adaptive Spacing)

This example uses the [includeFontPadding](#includefontpadding23) API to increase the spacing of the first and last lines, and the [fallbackLineSpacing](#fallbacklinespacing23) API to set adaptive line spacing.

Since API version 23, the [includeFontPadding](#includefontpadding23) and [fallbackLineSpacing](#fallbacklinespacing23) APIs are added.


```

```TypeScript
### Example 27 (Setting the Backplate Style for Text Dragging)

This example uses the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API to set the backplate style for text dragging.

The selectedDragPreviewStyle API is added from API version 23.


```

```TypeScript
### Example 28 (Deleting the Last Character in the Text Box)

This example calls the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API to delete the last character in the text box.

The [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API is available from API version 23.


```

```TypeScript
### Example 29 (Setting the Text Layout Direction)

This example sets the text layout direction through the [textDirection](#textdirection23) API.

Since API version 23, the textDirection API is added.


```

```TypeScript
### Example 30 (Scroll the Specified Range of Text into the Visible Area)

This example uses [scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23) to scroll the text outside the visible area into the visible area.

Since API version 23, the scrollToVisible API is added.


```

```TypeScript
### Example 31 (Setting the Text Shader Effect)

This example uses the [shaderStyle](#shaderstyle) API to apply a shader effect to the text in the Search component.

Since API version 26.0.0, the shaderStyle API is added.


```

```TypeScript
### Example 32 (Setting the AI Menu for Text Selection)

This example configures the AI menu feature for text selection through [enableSelectedDataDetector](#enableselecteddatadetector22).

Since API version 22, enableSelectedDataDetector is added.
```
