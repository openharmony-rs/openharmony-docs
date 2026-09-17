# UIPickerComponent

The **UIPickerComponent** container is used to implement user selection operations. It supports single selection from a limited set of options and can be applied to various scenarios such as time selection, date selection, region selection, and status selection. Its display effect is a three-dimensional wheel style, supporting customizable options including text type, image type, and text-image combination type.

NOTE

- The height of the **UIPickerComponent** container options is fixed at 40 vp, and a maximum of seven options can
be displayed. Due to the three-dimensional wheel display effect, options other than the selected one will be rotated at different angles, so the actual visible height will be less than 40 vp.

- It is recommended that the height of the **UIPickerComponent**
container be set to 200 vp. When the set height is greater than or equal to this recommended value, all 7 options can be fully displayed. Otherwise, the display area will be cropped from the top and bottom edges towards the center, and the number of displayed options will be reduced accordingly, always keeping the selected item vertically centered.

- When the **UIPickerComponent** container's width is not set, the
maximum width of the visible child components in the current view is taken as the container width. You are advised to set the width of the **UIPickerComponent** container or set the same width for each child component to avoid dynamic changes in container width during sliding, which affects the display effect.

- The alignment mode of child components in the **UIPickerComponent** container is fixed to center alignment, and
cannot be changed via the align attribute.

- Currently, the **UIPickerComponent** container does not support wearables.

- This component supports WithTheme since API version 26.0.0.

Child Components

- Multiple child components are supported.
- Supported child component types: Text, Image, Row, and
SymbolGlyph
- Supported rendering control types: [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) and
[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)

NOTE

- When the Row **container** is used as a child component, the **Row** container can contain only the **Text**,
**Image**, and **SymbolGlyph** basic components. Including other container components may affect the display effect or cause sliding functionality abnormalities.

- When counting the number of child components, the **Row** container and its child components are counted as one
child component.

- When the child component is **Text**, **Image**, or **SymbolGlyph**, the
height attribute does not take effect and is fixed at 40 vp.

- When the child component is a **Row** container, its height attribute
does not take effect and is fixed at 40 vp. The height attribute of the child components in the **Row** container takes effect. The final display effect is determined by the **Row** container.

- The text-image combination option requires that the **Row** container contain the **Text** and **Image**
components. When using the text-image combination option, you are advised to set the image's height to 40 vp or below to avoid cropping when images are large.

- The **fontSize** attribute of all text components (including the **Text** components in the **Row** container) in
the **UIPickerComponent** container is 20 fp by default. User settings will override the default value, and abnormal values will be processed according to the result of handling the text component's fontSize. You are advised to set the **fontSize** attribute to a unified value or not to set it to ensure a good display effect.

## UIPickerComponent

```TypeScript
UIPickerComponent(options?: UIPickerComponentOptions)
```

Creates a **UIPickerComponent** container, whose selected item is determined by the **selectedIndex** attribute in the **options** parameter.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [UIPickerComponentOptions](arkts-arkui-uipickercomponentoptions-i.md) | No | Parameters of the **UIPickerComponent** container. If the parameter is left empty, the component is a placeholder but the content is empty. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PickerIndicatorStyle](arkts-arkui-pickerindicatorstyle-i.md) | Sets parameters of the selected item indicator style. |
| [UIPickerComponentOptions](arkts-arkui-uipickercomponentoptions-i.md) | Describes the parameters of the **UIPickerComponent** container. |

### Types

| Name | Description |
| --- | --- |
| [OnUIPickerComponentCallback](arkts-arkui-onuipickercomponentcallback-t.md) | Defines the callback types for the [onChange](arkts-arkui-uipickercomponent-comp-attribute.md#onchange) and [onScrollStop](arkts-arkui-uipickercomponent-comp-attribute.md#onscrollstop) events. |

### Enums

| Name | Description |
| --- | --- |
| [PickerIndicatorType](arkts-arkui-pickerindicatortype-e.md) | Enumerates the types of the selected item indicator. |

## Examples

```TypeScript
### Example 1: Switching Loop Scrolling and Enabling/Disabling Haptic Feedback

Since API version 22, this example demonstrates how to switch the loop scrolling of the UIPickerComponent container and how to enable or disable haptic feedback via button clicks.


```

```TypeScript
### Example 2: Setting Event Callbacks

Since API version 22, this example implements the onChange and onScrollStop event callbacks of the UIPickerComponent container based on status selection.
```

```TypeScript
### Example 3: Setting the Selected Item Index

Since API version 22, this example implements setting the selected item index of the UIPickerComponent container.


```

```TypeScript
### Example 4: Setting the Selected Item Indicator

Since API version 22, this example implements setting the selected item indicator of the UIPickerComponent container. Specifically, when a background indicator is used, set backgroundColor and borderRadius of [PickerIndicatorStyle](arkts-arkui-pickerindicatorstyle-i.md); when a divider indicator is used, set strokeWidth, dividerColor, startMargin, and endMargin of [PickerIndicatorStyle](arkts-arkui-pickerindicatorstyle-i.md).


```

```TypeScript
### Example 5: Customizing the Month Picker

Since API version 22, this example uses the UIPickerComponent container with nested text child components to implement a month picker.


```

```TypeScript
### Example 6: Customizing the Area Picker

Since API version 22, this example uses a multi-column UIPickerComponent container combination to implement an area selector.


```

```TypeScript
### Example 7: Customizing Option Types

Since API version 22, this example uses the UIPickerComponent container to implement pickers with different option types, including a text picker, an image picker, and a combined image-text picker.


```

```TypeScript
### Example 8: Customizing the Time Picker

Since API version 22, this example implements a time picker with the following features: setting whether to loop scrolling, whether to display seconds, whether to use the 24-hour format, and whether to display leading zeros. It can also display content in the language corresponding to the current system language and adjust the display order of each column based on language habits.

> NOTE
> 
> In this example, the content of each column of the time picker is displayed in the language corresponding to the system language. For example, an English system displays AM/PM, while a Chinese system displays morning/afternoon.
> 
> In this example, the display order of each column of the time picker is adjusted according to the system language. For example, an English system displays hour/minute/second/AMPM, while a Chinese system displays morning/afternoon/hour/minute/second.

To make "morning/afternoon" switch with the system language, you need to add the corresponding language translations in the resource directory of the project. For example:

Chinese (default): Create a base directory under the resource directory, create an element directory under the base directory, and add a string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:
```

```TypeScript
English: Create the en directory under the resource directory, create the element directory under the en directory, and add the string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:
```

```TypeScript
Arabic: Create the ar directory under the resource directory, create the element directory under the ar directory, and add the string.json file under the element directory (if the file already exists, append the following "name"-"value" key-value pairs to the file instead of overwriting the original file). The file content is as follows:
```

```TypeScript
The same applies to other languages.

The sample code is as follows:


```

```TypeScript
### Example 9: Setting the Item Height

This example uses [itemHeight](#itemheight) to set the item height of the UIPickerComponent container.

Since API version 26.0.0, the [itemHeight](#itemheight) attribute is added.
```

```TypeScript
### Example 10: Setting the Number of Visible Items

This example uses [displayedItemCount](arkts-arkui-uipickercomponent-comp-attribute.md#displayeditemcount) to set the number of visible items in the UIPickerComponent container.

Since API version 26.0.0, the [displayedItemCount](arkts-arkui-uipickercomponent-comp-attribute.md#displayeditemcount) attribute is added.
```
