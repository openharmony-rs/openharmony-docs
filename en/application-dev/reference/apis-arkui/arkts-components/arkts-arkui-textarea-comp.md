# TextArea

The **TextArea** component provides multi-line text input and automatically wraps text to ensure that no line extends beyond the component's width.

If the component does not have its height set, it adapts its height to the content. If the component does not have its width set, it stretches to fill the maximum available width.

## Child Components

Not supported

## TextArea

```TypeScript
TextArea(value?: TextAreaOptions)
```

Defines the constructor of TextArea.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | No | Parameters of the **TextArea** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | Describes the initialization options of the **TextArea** component. |

### Types

| Name | Description |
| --- | --- |
| [TextAreaSubmitCallback](arkts-arkui-textareasubmitcallback-t.md) | Represents the callback invoked when the Enter key on the soft keyboard is pressed. |

### Enums

| Name | Description |
| --- | --- |
| [TextAreaType](arkts-arkui-textareatype-e.md) | Multi-line text input box type. |

## Examples

```TypeScript
### Example 1 (Setting and Obtaining the Cursor Position)

Since API version 8, this example implements the setting and obtaining of the cursor position through [controller](arkts-arkui-textareacontroller-c.md).


```

```TypeScript
### Example 2 (Setting the Counter)

Since API version 10, this example implements the counter feature through the [maxLength](#maxlength10) and [showCounter](#showcounter10) attributes.


```

```TypeScript
### Example 3 (Setting a Custom Keyboard)

This example uses the [customKeyboard](#customkeyboard10) attribute (available since API version 10) to set the input parameter type in value to [CustomBuilder](ts-types.md#custombuilder8) and ComponentContent, respectively, thereby implementing a custom keyboard.

Since API version 22, the [customKeyboard](#customkeyboard10) attribute supports the input parameter type ComponentContent.


```

```TypeScript
### Example 4 (Setting the Enter Key Type of the Input Method)

Since API version 11, this example uses the [enterKeyType](#enterkeytype11) attribute to dynamically switch the Enter key type of the input method.


```

```TypeScript
### Example 5 (Setting Text Line Break Rules)

Since API version 12, this example uses the [wordBreak](#wordbreak12) attribute to implement the effects of TextArea under different line break rules.


```

```TypeScript
### Example 6 (Setting Text Style)

Since API version 12, this example demonstrates text effects in different styles through the [lineHeight](#lineheight12), [letterSpacing](#letterspacing12), and [decoration](#decoration12) attributes.


```

```TypeScript
### Example 7 (Setting Font Feature Effects)

Since API version 12, this example uses the [fontFeature](#fontfeature12) attribute to implement the display effect of text under different font features.


```

```TypeScript
### Example 8 (Custom Keyboard Avoidance)

This example uses the [customKeyboard](#customkeyboard10) (available since API version 10) attribute to configure the [KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12) (available since API version 12) interface to implement custom keyboard avoidance.


```

```TypeScript
### Example 9 (Setting Text Auto-Adaptation)

Since API version 12, this example demonstrates the effect of auto-adaptive font size through the [minFontSize](#minfontsize12), [maxFontSize](#maxfontsize12), and [heightAdaptivePolicy](#heightadaptivepolicy12) attributes.


```

```TypeScript
### Example 10 (Setting Text Line Spacing)

Since API version 12, this example uses the [lineSpacing](#linespacing12) attribute to show how text is displayed under different line spacing. In addition, by configuring the onlyBetweenLines attribute (since API version 20) in [LineSpacingOptions](ts-text-common.md#linespacingoptions20), you can set whether the line spacing of text takes effect only between lines.


```

```TypeScript
### Example 11 (Setting Auto-Fill)

Since API version 12, this example implements text auto-fill through the [contentType](#contenttype12) and [enableAutoFill](#enableautofill12) attributes.
```

```TypeScript
### Example 12 (Setting the Line Breaking Rule)

Since API version 12, this example uses the [lineBreakStrategy](#linebreakstrategy12) attribute to implement the effects of TextArea under different line breaking rules.


```

```TypeScript
### Example 13 (Supporting Insert and Delete Callbacks)

Since API version 12, this example implements the insert and delete functions through the [onWillInsert](#onwillinsert12), [onDidInsert](#ondidinsert12), [onWillDelete](#onwilldelete12), and [onDidDelete](#ondiddelete12) APIs.


```

```TypeScript
### Example 14 (Custom Menu for Text Extension)

Since API version 12, this example uses the [editMenuOptions](#editmenuoptions12) API to set the text content, icon, and callback of custom menu extension items. In addition, menu data can be set in the [onPrepareMenu](ts-text-common.md#properties-1) callback (since API version 20).


```

```TypeScript
### Example 15 (Setting the Text Ellipsis Mode)

This example uses the [textOverflow](#textoverflow12), [ellipsisMode](#ellipsismode18), and [maxLines](#maxlines10) attributes to demonstrate the effect of truncating overlong text and adjusting the ellipsis position. Through the MULTILINE_START and MULTILINE_CENTER types, it implements the effect of placing the ellipsis at the beginning and in the middle of a line in single-line and multi-line text scenarios.

Since API version 10, the [maxLines](#maxlines10) attribute is used to set the maximum number of lines for text display.

Since API version 12, the [textOverflow](#textoverflow12) attribute is used to set how text is displayed when it is overlong.

Since API version 18, the [ellipsisMode](#ellipsismode18) attribute is used to set the ellipsis position.

Since API version 24, [EllipsisMode](ts-appendix-enums.md#ellipsismode11) has added the MULTILINE_START and MULTILINE_CENTER enums.


```

```TypeScript
### Example 16 (Customizing Copy, Cut, and Paste)

This example uses [onCopy](#oncopy8), [onCut](#oncut8), [onPaste](#onpaste), [onWillCopy](#onwillcopy), and [onWillCut](#onwillcut) to demonstrate how to listen for the copy, cut, and paste buttons in the text selection menu, how to block the system paste function and implement a custom paste capability, how to block the system copy function, and how to block the system cut function. In addition, the [maxFontScale](#maxfontscale18) and [minFontScale](#minfontscale18) attributes can be used to set the maximum and minimum font scale factors of the text.

Since API version 26.0.0, the [onWillCopy](#onwillcopy) and [onWillCut](#onwillcut) APIs are added.


```

```TypeScript
### Example 17: Setting the Minimum and Maximum Font Scale Factors

Since API version 18, this example uses [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18) to set the minimum and maximum font display range (this example uses system APIs, so the application type must be changed to a system application; for details, see [Available APIs](../../../reference/development-intro-api.md#available-apis)).
```

```TypeScript
// Modify the following code in AppScope/app.json5.
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
// xxx.ets
import { abilityManager, Configuration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TextAreaExample {
  @State currentFontSizeScale: number = 1;
  @State minFontScale: number = 0.85;
  @State maxFontScale: number = 2;

  // Set the font size.
  async setFontScale(scale: number): Promise<void> {
    let configInit: Configuration = {
      fontSizeScale: scale
    };
    // Update the configuration - font size, and call the system API to update the font configuration.
    // Configure the ohos.permission.UPDATE_CONFIGURATION permission in the requestPermissions field of the module.json5 file in the project.
    abilityManager.updateConfiguration(configInit, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to updateConfiguration. Code: ${err.code}, message: ${err.message}`);
      } else {
        this.currentFontSizeScale = scale;
        console.info('updateConfiguration success.');
      }
    });
  }

  build() {
    Column() {
      Column({ space: 30 }) {
        Text('Adjust the maximum and minimum font scale factors for text display through minFontScale and maxFontScale.')
        TextArea({
          placeholder: 'The text area can hold an unlimited amount of text. input your word...',
          text: 'Adjust the maximum and minimum font scale factors for text display through minFontScale and maxFontScale.'
        })
          .minFontScale(this.minFontScale)// Set the minimum font scale factor. If the parameter is undefined, the system default scale factor is used.
          .maxFontScale(this.maxFontScale) // Set the maximum font scale factor. If the parameter is undefined, the system default scale factor is used.
      }.width('100%')
      // The following buttons are used only to adjust the font scale factor and are not shown in the sample figure.
      Column() {
        Row() {
          Button('1x').onClick(() => {
            this.setFontScale(1)
          }).margin(10)
          Button('1.75x').onClick(() => {
            this.setFontScale(1.75)
          }).margin(10)
        }

        Row() {
          Button('2x').onClick(() => {
            this.setFontScale(2)
          }).margin(10)
          Button('3.2x').onClick(() => {
            this.setFontScale(3.2)
          }).margin(10)
        }
      }.margin({ top: 50 })
    }
  }
}
```

```TypeScript
### Example 18 (Setting the Text Content of a Selected Area)

Since API version 10, this example uses [setTextSelection](#settextselection10) to show how to set the text content of a selected area and the menu visibility policy.


```

```TypeScript
### Example 19 (Setting Text Stroke)

Since API version 20, this example sets the stroke width and color of text through the [strokeWidth](#strokewidth20) and [strokeColor](#strokecolor20) attributes.

Since API version 26.0.0, the [strokeJoinStyle](#strokejoinstyle) API is added to set the text stroke join style.


```

```TypeScript
### Example 20 (Setting Auto Spacing Between Chinese and Western Text)

Since API version 20, this example sets auto spacing between Chinese and Western text through the [enableAutoSpacing](#enableautospacing20) attribute.


```

```TypeScript
### Example 21 (Setting the Maximum Number of Lines)

Since API version 20, this example uses the [maxLines](#maxlines20) attribute to set the maximum number of lines to display. When the content exceeds the maximum number of lines, it can be scrolled.


```

```TypeScript
### Example 22 (Setting the Minimum Number of Lines)

Since API version 20, this example sets the minimum number of lines to display through the [minLines](#minlines20) attribute.


```

```TypeScript
### Example 23 (Setting the Character Count Color and Overflow Character Color)

Since API version 22, this example uses the counterTextColor and counterTextOverflowColor of [showCounter](#showcounter10) to set the character count color and the overflow character color.


```

```TypeScript
### Example 24 (Setting the Scrollbar Color)

Since API version 22, this example sets the scrollbar color through the [scrollBarColor](#scrollbarcolor22)22 attribute.


```

```TypeScript
### Example 25 (Setting the Placeholder Rich Text Style)

Since API version 22, this example sets the placeholder rich text style through the [setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22) API.

The original text supports multiple languages. For content in different languages, the style start index subscript start and length may differ. The following uses Chinese as an example to set the rich text style.


```

```TypeScript
### Example 26 (Setting IME Extension Information)

Since API version 22, this example uses [IMEClient](ts-text-common.md#imeclient20) to set the IME extension information through setExtraConfig.
```

```TypeScript
### Example 27 (Setting Leading Punctuation Compression and Trailing Punctuation Overhang)

This example uses the [compressLeadingPunctuation](#compressleadingpunctuation23) API to set leading punctuation compression, and the [punctuationOverflow](#punctuationoverflow) API to set trailing punctuation overhang.

When a punctuation mark with spacing on its left is at the beginning of a line, the spacing is compressed directly to the left boundary.

After the text wraps automatically, if the remaining content (including the punctuation mark) can fit into the previous line, the punctuation overhang takes effect.

Since API version 23, the compressLeadingPunctuation API is added.

Since API version 26.0.0, the punctuationOverflow API is added.


```

```TypeScript
### Example 28 (Setting Adaptive Spacing)

This example uses the [includeFontPadding](#includefontpadding23) API to increase the spacing of the first and last lines, and the [fallbackLineSpacing](#fallbacklinespacing23) API to set adaptive line spacing.

Since API version 23, the [includeFontPadding](#includefontpadding23) and [fallbackLineSpacing](#fallbacklinespacing23) APIs are added.


```

```TypeScript
### Example 29 (Setting the Backplate Style During Text Dragging)

This example uses the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) API to set the backplate style during text dragging.

Since API version 23, the selectedDragPreviewStyle API is added.


```

```TypeScript
### Example 30 (Deleting the Last Character in the Text Box)

This example calls the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API to delete the last character in the text box.

Since API version 23, the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API is added.


```

```TypeScript
### Example 31 (Setting the Text Direction)

This example uses [textDirection](#textdirection23) to set the text direction.

The textDirection API is available since API version 23.


```

```TypeScript
### Example 32 (Scrolling Text in a Specified Range into the Visible Area)

This example uses [scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23) to scroll text outside the visible area into the visible area.

Since API version 23, the scrollToVisible API is added.


```

```TypeScript
### Example 33 (Setting Horizontal Scrolling)

This example sets horizontal scrolling through [horizontalScrolling](#horizontalscrolling24).

Since API version 24, the horizontalScrolling API is added.


```

```TypeScript
### Example 34 (Setting Whether to Enable Orphan Character Optimization During Text Layout)

This example uses the [orphanCharOptimization](#orphancharoptimization) API to enable orphan character optimization, ensuring that no orphan character appears on the last line of a paragraph.

Since API version 26.0.0, the orphanCharOptimization API is added.

The effect shown in the figure may vary depending on the device size and is for reference only.


```

```TypeScript
### Example 35 (Setting the Text Shader Effect)

This example uses the [shaderStyle](#shaderstyle) API to apply a shader effect to the text in the TextArea component.

Since API version 26.0.0, the shaderStyle API is added.


```

```TypeScript
### Example 36 (Setting the AI Menu for Text Selection)

This example configures the AI menu for text selection through [enableSelectedDataDetector](#enableselecteddatadetector22).

Since API version 22, enableSelectedDataDetector is added.
```
