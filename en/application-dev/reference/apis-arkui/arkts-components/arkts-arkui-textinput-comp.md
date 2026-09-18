# TextInput

The **TextInput** component provides single-line text input.

> **NOTE** > > This component supports plain text only. For rich text, use the RichEditor component.

## Child Components

Not supported

## TextInput

```TypeScript
TextInput(value?: TextInputOptions)
```

Defines the constructor of TextInput.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextInputOptions](arkts-arkui-textinputoptions-i.md) | No | Parameters of the **TextInput** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PasswordIcon](arkts-arkui-passwordicon-i.md) | PasswordIcon object. |
| [SubmitEvent](arkts-arkui-submitevent-i.md) | Defines the user submission event. |
| [TextInputOptions](arkts-arkui-textinputoptions-i.md) | **TextInput** initialization parameters. |
| [UnderlineColor](arkts-arkui-underlinecolor-i.md) | Defines the underline color width property. |

### Types

| Name | Description |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | Defines the callback for text content scrolling. |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | Defines the callback used to return the pasted text content. |
| [OnSubmitCallback](arkts-arkui-onsubmitcallback-t.md) | Defines the callback for submission. |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | Defines the callback for text selection changes or caret position changes. |

### Enums

| Name | Description |
| --- | --- |
| [ContentType](arkts-arkui-contenttype-e.md) | Enumerates the content types for autofill. |
| [EnterKeyType](arkts-arkui-enterkeytype-e.md) | Type of the Enter key. |
| [InputType](arkts-arkui-inputtype-e.md) | Sets the single-line text box type. |
| [TextInputStyle](arkts-arkui-textinputstyle-e.md) | Text input style. |

## Examples

```TypeScript
### Example 1 (Setting and Obtaining the Cursor Position)

Since API version 8, this example implements the setting and obtaining of the cursor position through [controller](arkts-arkui-textinputcontroller-c.md). In addition, the two-way data binding of the text parameter can be implemented using !! (since API version 18).


```

```TypeScript
### Example 2 (Set Underline)

Supported since API version 10, this example uses the [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline), [showError](#showerror10), [showUnit](arkts-arkui-textinput-comp-attribute.md#showunit), and [passwordIcon](#passwordicon10) attributes to demonstrate the effect of the underline in different scenarios. In addition, the underline color can be configured through [underlineColor](#underlinecolor12) (supported since API version 12).


```

```TypeScript
### Example 3 (Setting a Custom Keyboard)

This example uses the [customKeyboard](#customkeyboard10) attribute (available since API version 10) to set the input parameter type in value to [CustomBuilder](ts-types.md#custombuilder8) and ComponentContent, respectively, implementing a custom keyboard.

Since API version 22, the [customKeyboard](#customkeyboard10) attribute adds the input parameter type ComponentContent.


```

```TypeScript
### Example 4: Setting the Style of the Clear Button on the Right

This example uses the [cancelButton](#cancelbutton11) attribute to demonstrate the effect of customizing the style of the clear button on the right.


```

```TypeScript
### Example 5 (Setting the Counter)

This example implements the counter function through the [maxLength](#maxlength), [showCounter](#showcounter11) (available since API version 11), and [showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline) (available since API version 10) attributes.


```

```TypeScript
### Example 6 (Phone Number Formatting)

This example uses the [onChange](#onchange) callback to format a phone number as XXX XXXX XXXX.


```

```TypeScript
### Example 7 (Setting Text Line Break Rules)

Starting from API version 12, this example uses the [wordBreak](#wordbreak12) attribute to demonstrate the effects of different line break rules for TextInput.


```

```TypeScript
### Example 8 (Set Text Style)

Since API version 12, this example demonstrates text effects in different styles through the [lineHeight](#lineheight12), [letterSpacing](#letterspacing12), and [decoration](#decoration12) attributes.


```

```TypeScript
### Example 9 (Setting the Text Feature Effect)

Since API version 12, this example uses the [fontFeature](#fontfeature12) attribute to implement the display effect of text under different text features.


```

```TypeScript
### Example 10 (Custom Keyboard Avoidance)

This example uses the [customKeyboard](#customkeyboard10) (available since API version 10) attribute to configure the [KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12) (available since API version 12) interface to implement custom keyboard avoidance.


```

```TypeScript
### Example 11 (Setting Text Auto-fit)

Since API version 12, this example implements the text adaptive font size feature through the [minFontSize](#minfontsize12), [maxFontSize](#maxfontsize12), and [heightAdaptivePolicy](#heightadaptivepolicy12) attributes.


```

```TypeScript
### Example 12 (Setting the Line Break Rule)

Since API version 12, this example implements the effects of TextInput under different line break rules through the [lineBreakStrategy](#linebreakstrategy12) attribute.


```

```TypeScript
### Example 13 (Supporting Insert and Delete Callbacks)

Since API version 12, this example implements the insert and delete effects through the [onWillInsert](#onwillinsert12), [onDidInsert](#ondidinsert12), [onWillDelete](#onwilldelete12), and [onDidDelete](#ondiddelete12) interfaces.


```

```TypeScript
### Example 14 (Text Extension Custom Menu)

Since API version 12, this example uses the [editMenuOptions](#editmenuoptions12) interface to set the text content, icon, and callback of custom menu extension items. In addition, menu data can be set in the [onPrepareMenu](ts-text-common.md#properties-1) callback (since API version 20).


```

```TypeScript
### Example 15: Setting a Symbol-Type Clear Button

Starting from API version 18, this example uses the [cancelButton](#cancelbutton18) attribute to demonstrate the effect of customizing the style of the symbol-type clear button on the right.


```

```TypeScript
### Example 16 (Setting the Text Ellipsis Mode)

This example uses the [textOverflow](#textoverflow12), [ellipsisMode](#ellipsismode18), and [style](#style9) attributes to demonstrate the effect of truncating overlong text and adjusting the ellipsis position. Through the MULTILINE_START and MULTILINE_CENTER types, it implements the effect of placing the ellipsis at the beginning and in the middle of the line in single-line and multi-line text scenarios.

Since API version 9, the style of the input box can be set through [style](#style9).

Since API version 12, the display mode of overlong text can be set through [textOverflow](#textoverflow12).

Since API version 18, the ellipsis position can be set through [ellipsisMode](#ellipsismode18).

Since API version 24, the MULTILINE_START and MULTILINE_CENTER enums are added to [EllipsisMode](ts-appendix-enums.md#ellipsismode11).


```

```TypeScript
### Example 17 (Input Box Supporting Callbacks Such as Input State Change)

Since API version 8, this example uses the [onEditChange](#oneditchange8), [onCopy](#oncopy8), [onCut](#oncut8), [onPaste](#onpaste8), [onContentScroll](#oncontentscroll10) (since API version 10), [onWillCopy](#onwillcopy), and [onWillCut](#onwillcut) APIs to implement the effects of monitoring input state changes, copy, cut, paste, and text content scroll callbacks in the input box, how to block the system copy function, and how to block the system cut function. In addition, you can set the [selectAll](#selectall11) (since API version 11) attribute to determine whether all text is selected in the initial state of the input box.

Since API version 26.0.0, the [onWillCopy](#onwillcopy) and [onWillCut](#onwillcut) APIs are added.


```

```TypeScript
### Example 18: Setting the Minimum and Maximum Font Scale Factors

Since API version 18, this example uses [minFontScale](#minfontscale18) and [maxFontScale](#maxfontscale18) to set the minimum and maximum font display range (this example uses system APIs, so the application type must be adjusted to a system application; see [Available APIs](../../../reference/development-intro-api.md#available-apis) in HarmonyAppProvision).
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
// xxx.ets
import { abilityManager, Configuration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TextInputExample {
  @State currentFontSizeScale: number = 1;
  @State minFontScale: number = 0.85;
  @State maxFontScale: number = 2;

  // Set the font size.
  async setFontScale(scale: number): Promise<void> {
    let configInit: Configuration = {
      fontSizeScale: scale
    };
    // Update the configuration - font size, and call the system API to update the font configuration.
    // Configure the ohos.permission.UPDATE_CONFIGURATION permission in the requestPermissions field of the module.json5 file of the project.
    abilityManager.updateConfiguration(configInit, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to update configuration. Code: ${err.code}, message: ${err.message}`);
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
        TextInput({
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
            this.setFontScale(1);
          }).margin(10)
          Button('1.75x').onClick(() => {
            this.setFontScale(1.75);
          }).margin(10)
        }

        Row() {
          Button('2x').onClick(() => {
            this.setFontScale(2);
          }).margin(10)
          Button('3.2x').onClick(() => {
            this.setFontScale(3.2);
          }).margin(10)
        }
      }.margin({ top: 50 })
    }
  }
}
```

```TypeScript
### Example 19 (Setting the Text Content of a Selected Area)

Since API version 10, this example uses the [setTextSelection](#settextselection10) method to demonstrate how to set the text content of a selected area and the show/hide policy of the menu.


```

```TypeScript
### Example 20 (Setting Text Stroke)

Since API version 20, this example sets the stroke width and color of text through the [strokeWidth](#strokewidth20) and [strokeColor](#strokecolor20) attributes.

Since API version 26.0.0, the [strokeJoinStyle](#strokejoinstyle) interface is added to support setting the corner style of text stroke.


```

```TypeScript
### Example 21 (Setting Auto Spacing Between Chinese and Western Text)

Since API version 20, this example sets auto spacing between Chinese and Western text through the [enableAutoSpacing](#enableautospacing20) attribute.


```

```TypeScript
### Example 22 (Setting Character Count Color and Overflow Character Color)

Since API version 22, this example uses the counterTextColor and counterTextOverflowColor of the [showCounter](#showcounter11) attribute to set the character count color and the overflow character color.


```

```TypeScript
### Example 23 (Setting the Placeholder Rich Text Style)

Since API version 22, this example sets the placeholder rich text style through the [setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22) API.


```

```TypeScript
### Example 24 (Setting Input Method Extension Information)

Since API version 22, this example uses [IMEClient](ts-text-common.md#imeclient20)'s setExtraConfig to set the input method extension information.
```

```TypeScript
### Example 25 (Setting the Display Mode of the Scrollbar in the Editing State of Inline Input Style)

Since API version 10, this example uses [barState](#barstate10) to set whether the scrollbar is displayed or hidden in the editing state of inline input style.


```

```TypeScript
### Example 26 (Setting Leading Punctuation Compression and Trailing Punctuation Hanging)

This example uses the [compressLeadingPunctuation](#compressleadingpunctuation23) API to set leading punctuation compression, and the [punctuationOverflow](#punctuationoverflow) API to set trailing punctuation hanging.

When a punctuation mark with spacing on the left is at the beginning of a line, the punctuation is directly compressed to the left boundary.

After the text is automatically wrapped, the remaining content (including punctuation marks) must fit into the previous line for punctuation hanging to take effect.

Since API version 23, the compressLeadingPunctuation API is added.

Since API version 26.0.0, the punctuationOverflow API is added.


```

```TypeScript
### Example 27 (Setting Adaptive Spacing)

This example uses the [includeFontPadding](#includefontpadding23) API to increase the spacing of the first and last lines, and the [fallbackLineSpacing](#fallbacklinespacing23) API to set adaptive line spacing.

Since API version 23, the [includeFontPadding](#includefontpadding23) and [fallbackLineSpacing](#fallbacklinespacing23) APIs are added.


```

```TypeScript
### Example 28 (Setting the Backplate Style During Text Dragging)

This example uses the [selectedDragPreviewStyle](#selecteddragpreviewstyle23) interface to set the backplate style during text dragging.

Since API version 23, the selectedDragPreviewStyle interface is added.


```

```TypeScript
### Example 29 (Deleting the Last Character in the Text Box)

This example calls the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API to delete the last character in the text box.

Since API version 23, the [deleteBackward](ts-universal-attributes-text-style.md#deletebackward23) API is added.


```

```TypeScript
### Example 30 (Setting the Text Layout Direction)

This example sets the text layout direction through the [textDirection](#textdirection23) API.

Since API version 23, the textDirection API is added.


```

```TypeScript
### Example 31 (Scrolling Text in a Specified Range into the Visible Area)

This example uses [scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23) to scroll text outside the visible area into the visible area.

Since API version 23, the scrollToVisible API is added.


```

```TypeScript
### Example 32 (Whether to Enable Orphan Character Optimization When Setting Text Layout)

This example uses the [orphanCharOptimization](#orphancharoptimization) API to enable orphan character optimization, ensuring that no orphan character appears on the last line of a paragraph.

Since API version 26.0.0, the orphanCharOptimization API is added.

The effect shown in the figure may vary depending on the device size and is for reference only.

Orphan character optimization disabled:



Orphan character optimization enabled:


```

```TypeScript
### Example 33 (Setting the Text Shader Effect)

This example uses the [shaderStyle](#shaderstyle) API to apply a shader effect to the text in the TextInput component.

The shaderStyle API is added since API version 26.0.0.


```

```TypeScript
### Example 34 (Setting the AI Menu for Text Selection)

This example configures the AI menu for text selection through [enableSelectedDataDetector](#enableselecteddatadetector22).

Since API version 22, enableSelectedDataDetector is added.
```
