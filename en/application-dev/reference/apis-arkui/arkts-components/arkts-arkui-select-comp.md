# Select

The **Select** component provides a drop-down menu that allows users to select among multiple options.

> **NOTE**

## Child Components

Not supported

## Select

```TypeScript
Select(options: Array<SelectOption>)
```

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | Array&lt;[SelectOption](arkts-arkui-selectoption-i.md)&gt; | Yes | Options of the drop-down menu. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [MenuItemConfiguration](arkts-arkui-menuitemconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [MenuOutlineOptions](arkts-arkui-menuoutlineoptions-i.md) | Defines the outline of the drop-down menu. |
| [SelectOption](arkts-arkui-selectoption-i.md) | Provides information about the drop-down menu options. |

### Types

| Name | Description |
| --- | --- |
| [OnSelectCallback](arkts-arkui-onselectcallback-t.md) | Defines the callback invoked when a drop-down menu option is selected. |

### Enums

| Name | Description |
| --- | --- |
| [ArrowPosition](arkts-arkui-arrowposition-e.md) | Enumerates arrow positions. |
| [AvoidanceMode](arkts-arkui-avoidancemode-e.md) | Enumerates the drop-down menu avoidance modes. |
| [MenuAlignType](arkts-arkui-menualigntype-e.md) | Enumerates drop-down menu alignment modes. |

## Examples

```TypeScript
### Example 1: Creating a Drop-down Menu

This example demonstrates how to create a drop-down menu by configuring [SelectOption](arkts-arkui-selectoption-i.md) and how to implement menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.


```

```TypeScript
### Example 2: Setting the Symbol Icon

This example demonstrates how to create a drop-down menu with symbol icons in the Select component and implement menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.


```

```TypeScript
### Example 3: Implementing a Custom Drop-down Menu

This example implements a custom drop-down menu, each option of which consists of text + symbol + blank area + text + drawn triangle. After a menu option is clicked, the text content of the menu option is displayed.


```

```TypeScript
### Example 4: Using the Divider Style

This example uses DividerOptions to create a divider-style drop-down menu and implements menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.


```

```TypeScript
### Example 5: Using the No-Divider Style

This example sets the divider attribute to null to remove dividers, and implements menu avoidance using the [avoidance](arkts-arkui-select-comp-attribute.md#avoidance) attribute, available since API version 19.


```

```TypeScript
### Example 6: Setting the Text and Arrow Styles of the Select Component

This example illustrates how to configure the text and arrow styles of the Select component using the [textModifier](#textmodifier20) and [arrowModifier](arkts-arkui-select-comp-attribute.md#arrowmodifier) attributes, available since API version 20.


```

```TypeScript
### Example 7: Setting the Text Styles of Selected and Unselected Drop-Down Menu Options

This example demonstrates how to use the [optionTextModifier](arkts-arkui-select-comp-attribute.md#optiontextmodifier) and [selectedOptionTextModifier](arkts-arkui-select-comp-attribute.md#selectedoptiontextmodifier) attributes to set text styles for unselected and selected drop-down menu options, available since API version 20.


```

```TypeScript
### Example 8: Setting the Divider Mode

This example shows how to set the divider mode by configuring the mode property of [DividerStyleOptions](ts-types.md#dividerstyleoptions12), supported since API version 19.


```

```TypeScript
### Example 9: Setting the Outline Style of the Drop-Down Menu

This example shows how to set the outline style of the drop-down menu using the width and color properties of menuOutline, supported since API version 20.


```

```TypeScript
### Example 10: Setting the Pop-Up Menu of Select to Avoid the Soft Keyboard

This example demonstrates how to configure the drop-down menu to avoid the soft keyboard and customize the minimum distance for avoiding the soft keyboard by calling the [keyboardAvoidMode](#keyboardavoidmode23) and [minKeyboardAvoidDistance](#minkeyboardavoiddistance23) APIs.

The keyboardAvoidMode and minKeyboardAvoidDistance APIs are added since API version 23.


```

```TypeScript
### Example 11: Setting the Immersive Light Effect for the Select Component and Drop-Down Menu

This example shows how to call [menuSystemMaterial](arkts-arkui-select-comp-attribute.md#menusystemmaterial) to set the system material of the drop-down menu to achieve the immersive light effect, and call [SystemUiMaterial](ts-universal-attributes-image-effect.md#systemuimaterial) to set the system material of the Select component to achieve the immersive light effect.

The figures in this example show the strong immersive light effects on a high-computing device. The immersive light effect of the component automatically adapts to the device's computing power and the immersive light effect set by the user in the system. No additional adaptation is required.

Since API version 26.0.0, the menuSystemMaterial API is added.
```
