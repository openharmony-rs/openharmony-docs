# Slider

The **Slider** component is used to quickly adjust settings, such as the volume and brightness.

> **NOTE**

## Child Components

Not supported

## Slider

```TypeScript
Slider(options?: SliderOptions)
```

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SliderOptions](arkts-arkui-slideroptions-i.md) | No | Parameters of the slider. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColorMetricsStop](arkts-arkui-colormetricsstop-i.md) | Describes the breakpoint of the gradient color. |
| [SlideRange](arkts-arkui-sliderange-i.md) | Defines the callback type used in **SlideRange**. |
| [SliderBlockStyle](arkts-arkui-sliderblockstyle-i.md) | Describes the style of the slider in the block direction. |
| [SliderConfiguration](arkts-arkui-sliderconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [SliderCustomContentOptions](arkts-arkui-slidercustomcontentoptions-i.md) | Provides accessibility configuration of the slider prefix and suffix. |
| [SliderOptions](arkts-arkui-slideroptions-i.md) | Provides information about the slider. |
| [SliderPrefixOptions](arkts-arkui-sliderprefixoptions-i.md) | Provides accessibility configuration of the slider prefix. |
| [SliderShowStepOptions](arkts-arkui-slidershowstepoptions-i.md) | Provides accessibility text mapping for the slider step markers. |
| [SliderStepItemAccessibility](arkts-arkui-sliderstepitemaccessibility-i.md) | Provides accessibility configuration of the slider step markers. |
| [SliderSuffixOptions](arkts-arkui-slidersuffixoptions-i.md) | Provides accessibility configuration of the slider suffix. |

### Types

| Name | Description |
| --- | --- |
| [SliderTriggerChangeCallback](arkts-arkui-slidertriggerchangecallback-t.md) | Defines the callback type used in **SliderConfiguration**. |

### Enums

| Name | Description |
| --- | --- |
| [SliderBlockType](arkts-arkui-sliderblocktype-e.md) | Enumerates the types of the slider in the block direction. |
| [SliderChangeMode](arkts-arkui-sliderchangemode-e.md) | Enumerates the slider states. |
| [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | Interaction mode between the user and the slider. |
| [SliderStyle](arkts-arkui-sliderstyle-e.md) | Enumerates the display styles of the slider thumb relative to the track. For details, see [How Are the Slider Thumb and Track of the Slider Component Aligned?](../../../ui/arkts-select-component-faq.md#how-are-the-slider-thumb-and-track-of-the-slider-component-aligned). |

## Examples

```TypeScript
### Example 1: Using Basic Slider Styles

This example demonstrates how to control the display of the tooltip, current step, and slider thumb and track by configuring style, showTips, and showSteps.


```

```TypeScript
### Example 2: Using Custom Slider Styles

This example demonstrates how to customize the slider styles by setting blockBorderColor, blockSize, blockBorderWidth, and blockStyle for the slider block, stepSize and stepColor for the step, trackBorderRadius for the track's corner radius, and selectedBorderRadius for the selected part's corner radius.


```

```TypeScript
### Example 3: Implementing a Custom Slider

This example demonstrates how to customize the Slider component using a style builder to define the content area. Clicking the increase button will increment the progress bar by the step size set in the original Slider component, and clicking the decrease button will decrement the progress bar, triggering the onChange event of the original component.


```

```TypeScript
### Example 4: Applying a Color Gradient Effect and Implementing Support for Digital Crown Interactions

This example demonstrates how to set a color gradient effect to the slider using selectedColor and implement support for digital crown interactions through focusable, defaultFocus, and focusOnTouch.


```

```TypeScript
### Example 5: Setting the Slider Prefix and Suffix

This example demonstrates how to set the prefix and suffix of the slider using prefix and suffix, defining their custom content and accessibility configuration. After the accessibility configuration is specified, the screen reader announces the accessibility text accordingly.


```

```TypeScript
### Example 6: Setting Accessibility Text for Slider Step Markers

This example demonstrates how to set accessibility text for step markers using [showSteps](arkts-arkui-slider-comp-attribute.md#showsteps). The screen reader announces the set accessibility text accordingly. The options parameter is added for the [showSteps](arkts-arkui-slider-comp-attribute.md#showsteps) attribute since API version 20.


```

```TypeScript
### Example 7: Setting Two-Way Binding for the Slider

This example shows how to implement data synchronization by binding the value property of [SliderOptions](arkts-arkui-slideroptions-i.md) to a variable using the [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding operator, available since API version 11.


```

```TypeScript
### Example 8: Setting a Gradient Color for the Slider Thumb

This example demonstrates how to set a gradient color for the Slider component's thumb using the blockColor attribute.


```

```TypeScript
### Example 9: Setting the Background Color of a Slider

This example demonstrates how to set the gradient color stop of the specified color gamut using [trackColorMetrics](arkts-arkui-slider-comp-attribute.md#trackcolormetrics). In this example, colorSpace is of the ColorSpace.DISPLAY_P3 type. You need to call the setWindowColorSpace API of the corresponding window to set the current window to the wide color gamut mode. For details, see [setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace).

The trackColorMetrics API is supported since API version 23.


```

```TypeScript
### Example 10: Setting the Immersive Light Effect for the Slider

This example shows how to set the system material of the slider using the universal attribute [systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial), implementing the immersive light effect. After the system material is set, a particle animation effect is generated during the sliding of the slider.

The immersive light effect of the component is adaptively adjusted based on the device computing power and the immersive light effect set by the user in the system, and you do not need to perform additional adaptation.

The systemMaterial API is supported since API version 26.0.0.
```
