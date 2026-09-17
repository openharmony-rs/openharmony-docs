# Button

The **Button** component can be used to create different types of buttons.

> **NOTE**

## Child Components

This component can contain only one child component.

## Button

```TypeScript
Button()
```

Creates an empty button.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Button

```TypeScript
Button(options: ButtonOptions)
```

Creates a button that can contain a single child component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | Yes | Button settings. |

## Button

```TypeScript
Button(label: ResourceStr, options?: ButtonOptions)
```

Creates a button based on text content. In this case, the component cannot contain child components.

By default, the text content is displayed in a one line.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Button text.<br>Note: If the text is longer than the width of the button, it is truncated. |
| options | [ButtonOptions](arkts-arkui-buttonoptions-i.md) | No | Button settings. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ButtonConfiguration](arkts-arkui-buttonconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [ButtonOptions](arkts-arkui-buttonoptions-i.md) | Describes the button style. |
| [LabelStyle](arkts-arkui-labelstyle-i.md) | Label text and font style of the button. |

### Types

| Name | Description |
| --- | --- |
| [ButtonTriggerClickCallback](arkts-arkui-buttontriggerclickcallback-t.md) | Defines the callback type used in **ButtonConfiguration**. |

### Enums

| Name | Description |
| --- | --- |
| [ButtonRole](arkts-arkui-buttonrole-e.md) | Role of the button. |
| [ButtonStyleMode](arkts-arkui-buttonstylemode-e.md) | Enumerates the button importance levels. |
| [ButtonType](arkts-arkui-buttontype-e.md) | Enumerates the button types. |
| [ControlSize](arkts-arkui-controlsize-e.md) | Button size. |

## Examples

```TypeScript
### Example 1: Setting the Button Display Style

This example demonstrates two methods to create buttons, either with child components or using text content.


```

```TypeScript
### Example 2: Adding Render Control to a Button

This example uses if/else statements to control the display text of the button.


```

```TypeScript
### Example 3: Setting the Button Text Style

This example customizes the display style of button text by configuring labelStyle.


```

```TypeScript
### Example 4: Setting Importance of Different Sized Buttons

This example demonstrates how to set the importance of buttons of different sizes by configuring controlSize and buttonStyle.


```

```TypeScript
### Example 5: Setting the Button Role

This example demonstrates how to set the role of the button by configuring role.


```

```TypeScript
### Example 6: Implementing a Custom Button

This example implements a custom button in the shape of a circle. The circle is red when pressed, accompanied by the text "Pressed" in the title. It is black when not pressed, accompanied by the text "Not pressed" in the title.


```

```TypeScript
### Example 7: Setting Rounded Rectangle Buttons

This example demonstrates how to set a rounded rectangle button, and set its corner radius and the truncation effect of long text.


```

```TypeScript
### Example 8 (Setting the Horizontal Alignment Mode of the Label Text)

This example shows how to set the text alignment mode by configuring textAlign of [LabelStyle](#labelstyle10).

The textAlign API is supported since API version 23.


```

```TypeScript
### Example 9: Setting the Immersive Light Effect for a Button

This example shows how to use the universal attribute [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial) to set the system material of a component, so as to achieve the immersive light effect.

The immersive light effect of a component is adaptively adjusted based on the device computing power and the immersive light effect set by the user in the system, without requiring your additional adaptation.

Since API version 26.0.0, the systemMaterial attribute is added.
```
