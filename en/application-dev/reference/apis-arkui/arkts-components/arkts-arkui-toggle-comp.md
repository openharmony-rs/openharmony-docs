# Toggle

The **Toggle** component provides a clickable element of the checkbox, button, or switch type.

> **NOTE**

## Child Components

This component can contain child components only when **ToggleType** is set to **Button**.

## Toggle

```TypeScript
Toggle(options: ToggleOptions)
```

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToggleOptions](arkts-arkui-toggleoptions-i.md) | Yes | Options of the toggle. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [SwitchStyle](arkts-arkui-switchstyle-i.md) | Sets the style for the component of the **Switch** type. |
| [ToggleConfiguration](arkts-arkui-toggleconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. This API inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [ToggleOptions](arkts-arkui-toggleoptions-i.md) | Options of the toggle. |

### Enums

| Name | Description |
| --- | --- |
| [ToggleType](arkts-arkui-toggletype-e.md) | Enumerates toggle types. |

## Examples

```TypeScript
### Example 1: Setting the Toggle Style

This example demonstrates how to configure the style for different types of toggles (checkbox, switch, and button) using ToggleType.


```

```TypeScript
### Example 2: Customizing the Toggle Style

This example implements a toggle of the Switch type with custom settings, including the radius and color of the circular slider, background color in the off state, and radius of the slider track border corners.


```

```TypeScript
### Example 3: Implementing a Custom Toggle Style

This example shows how to implement a custom toggle style. The toggle button switches the background color. Clicking the blue circle changes the background to blue. Clicking the yellow circle changes it to yellow.


```

```TypeScript
### Example 4: Implementing the Immersive Light Effect for the Toggle Component

This example shows the effect comparison of the Toggle component of the Switch type before and after the immersive light effect is enabled, including the effects of not setting the system material, of setting undefined, of setting the system material, and of setting the system material together with [switchPointColor](arkts-arkui-toggle-comp-attribute.md#switchpointcolor) to set the point light color. In this example, you can use the universal attribute [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial) to implement the immersive light effect.

The immersive light effect of the component is adaptively adjusted based on the device computing power and the immersive light effect set by the user in the system, and you do not need to perform additional adaptation.

Since API version 26.0.0, the systemMaterial attribute is added.

> NOTE
> 
> The actual display effect of the system material is related to the device computing power. The same code produces different display effects on devices of different computing power levels, and a simplified material effect is displayed on low-computing-power devices. The computing power levels are automatically divided and managed by the system based on the hardware capabilities of the device. Applications do not need to be aware of them or perform additional configuration. The system automatically adapts the material display effect based on the computing power level of the current device.
```
