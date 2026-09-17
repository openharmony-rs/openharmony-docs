# TextPicker

**TextPicker** is a component that allows users to select text, images, or hybrid content through scrolling. It supports three usage modes: single-column picker, multi-column independent picker, and multi-column cascading picker.

> **NOTE**

> - Avoid changing the attribute data during the animation process of this component. > > - The maximum number of rows that can be displayed varies by screen orientation: In portrait mode, the default > number of rows is 5. In landscape mode, the number of rows depends on the system configuration. If no system > configuration is set, the default is 3 rows. To check the specific system configuration value for landscape mode, > use **$r('sys.float.ohos_id_picker_show_count_landscape')**. > > - Multi-column independent pickers and multi-column cascading pickers are collectively referred to as multi-column > pickers in this document.

Child Components

Not supported

## TextPicker

```TypeScript
TextPicker(options?: TextPickerOptions)
```

Creates a text picker based on the specified data list.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) | No | Parameters of the text picker. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DividerOptions](arkts-arkui-divideroptions-i.md) | Define the divider configuration options. |
| [PickerBackgroundStyle](arkts-arkui-pickerbackgroundstyle-i.md) | Defines the background style configuration for selected picker items. |
| [TextCascadePickerRangeContent](arkts-arkui-textcascadepickerrangecontent-i.md) | Defines the content for multi-column picker options. |
| [TextPickerDialogOptions](arkts-arkui-textpickerdialogoptions-i.md) | Defines the TextPickerDialogOptions for Text Picker Dialog. |
| [TextPickerDialogOptionsExt](arkts-arkui-textpickerdialogoptionsext-i.md) | Defines the TextPickerDialogOptionsExt for Text Picker Dialog. |
| [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) | Defines the configuration options of the text picker. |
| [TextPickerRangeContent](arkts-arkui-textpickerrangecontent-i.md) | Defines the content for single-column picker options. |
| [TextPickerResult](arkts-arkui-textpickerresult-i.md) | Defines the struct of TextPickerResult. |
| [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md) | Defines the text style options for the text picker. Inherits from [PickerTextStyle](arkts-arkui-pickertextstyle-i.md). |

### Types

| Name | Description |
| --- | --- |
| [OnTextPickerChangeCallback](arkts-arkui-ontextpickerchangecallback-t.md) | Defines the **onChange** event callback signature. |
| [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpickerenterselectedareacallback-t.md) | Defines the **onEnterSelectedArea** event callback signature. |
| [TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md) | Defines the **onScrollStop** event callback signature. |

## Examples

```TypeScript
### Example 1: Setting the Number of Columns in the Picker

This example demonstrates how to configure single-column and multi-column text pickers by setting range and customizing the width of each column using columnWidths.

The columnWidths attribute of [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) is added since API version 18.


```

```TypeScript
### Example 2: Setting the Text Style

This example demonstrates how to configure [disappearTextStyle](#disappeartextstyle10), [textStyle](#textstyle10), and [selectedTextStyle](#selectedtextstyle10) to customize the text style in the text picker.


```

```TypeScript
### Example 3: Using the No-Divider Style

This example demonstrates how to configure a text picker with no divider by setting [divider](#divider12) to null.


```

```TypeScript
### Example 4: Using the Divider Style

This example demonstrates how to set the divider style for the text picker by configuring DividerOptions for divider.


```

```TypeScript
### Example 5: Setting the Fade Effect

This example shows how to set the gradient effect height for the text picker by configuring [gradientHeight](#gradientheight12).


```

```TypeScript
### Example 6: Setting the Item Height

This example demonstrates how to set the height of the picker items by configuring [defaultPickerItemHeight](#defaultpickeritemheight).


```

```TypeScript
### Example 7: Setting Loop Scrolling

This example demonstrates how to set whether to enable loop scrolling using [canLoop](#canloop10).


```

```TypeScript
### Example 8: Setting the Selected Item Index

This example demonstrates how to set the index of the default selected item by configuring [selectedIndex](#selectedindex10).


```

```TypeScript
### Example 9: Disabling the Text Style Animation and Setting the Corresponding Text Style

This example demonstrates how to disable the text style change animation for the text picker and set the text style by configuring [disableTextStyleAnimation](#disabletextstyleanimation15) and [defaultTextStyle](#defaulttextstyle15).

The disableTextStyleAnimation and defaultTextStyle APIs are supported since API version 15.


```

```TypeScript
### Example 10: Setting the Background Style of the Selected Item

This example shows how to set the background style of the selected item by configuring [selectedBackgroundStyle](#selectedbackgroundstyle20).


```

```TypeScript
### Example 11: Setting the Font Size Range and Text Overflow Mode

This example shows how to set the text color, maximum font size, minimum font size, and text overflow mode by configuring [disappearTextStyle](#disappeartextstyle20), [textStyle](#textstyle20), and [selectedTextStyle](#selectedtextstyle20).

The disappearTextStyle, textStyle, and selectedTextStyle APIs are supported since API version 20.
```
