# Slider properties/events

```TypeScript
declare class SliderAttribute extends CommonMethod<SliderAttribute>
```

All the [universal attributes](arkts-arkui-common-comp.md) except **responseRegion** are supported.

**Inheritance/Implementation:** SliderAttribute extends CommonMethod<SliderAttribute>

**Since:** 7

<!--Device-unnamed-declare class SliderAttribute extends CommonMethod<SliderAttribute>--><!--Device-unnamed-declare class SliderAttribute extends CommonMethod<SliderAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blockBorderColor

```TypeScript
blockBorderColor(value: ResourceColor)
```

Sets the border color of the slider in the block direction.

When **SliderBlockType.DEFAULT** is used, **blockBorderColor** sets the border color of the round slider.

When **SliderBlockType.IMAGE** is used, **blockBorderColor** does not work as the slider has no border.

When **SliderBlockType.SHAPE** is used, **blockBorderColor** sets the border color of the slider in a custom shape.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-blockBorderColor(value: ResourceColor): SliderAttribute--><!--Device-SliderAttribute-blockBorderColor(value: ResourceColor): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Border color of the slider in the block direction.<br>Default value: **'#00000000'** |

## blockBorderWidth

```TypeScript
blockBorderWidth(value: Length)
```

Sets the border width of the slider in the block direction.

When **SliderBlockType.DEFAULT** is used, **blockBorderWidth** sets the border width of the round slider.

When **SliderBlockType.IMAGE** is used, **blockBorderWidth** does not work as the slider has no border.

When **SliderBlockType.SHAPE** is used, **blockBorderWidth** sets the border width of the slider in a custom shape.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-blockBorderWidth(value: Length): SliderAttribute--><!--Device-SliderAttribute-blockBorderWidth(value: Length): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Border width of the slider.<br>**Note:** <br>For the string type, percentage values are not supported. |

## blockColor

```TypeScript
blockColor(value: ResourceColor)
```

Sets the color of the thumb.

When **SliderBlockType.DEFAULT** is used, **blockColor** sets the color of the round thumb.

When **SliderBlockType.IMAGE** is used, **blockColor** does not work as the thumb has no fill color.

When **SliderBlockType.SHAPE** is used, **blockColor** sets the color of the thumb in a custom shape.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-blockColor(value: ResourceColor): SliderAttribute--><!--Device-SliderAttribute-blockColor(value: ResourceColor): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the thumb.<br>Default value: **$r('sys.color.ohos_id_color_foreground_contrary')** |

<a id="blockcolor-1"></a>

## blockColor

```TypeScript
blockColor(value: ResourceColor | LinearGradient)
```

Sets the color of the slider. Gradient colors are supported. Compared with **blockColor**, it supports the **LinearGradient** type.

When **SliderBlockType.DEFAULT** is used, **blockColor** sets the color of the round thumb.

When **SliderBlockType.IMAGE** is used, **blockColor** does not work as the thumb has no fill color.

When **SliderBlockType.SHAPE** is used, **blockColor** sets the color of the thumb in a custom shape.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-SliderAttribute-blockColor(value: ResourceColor | LinearGradient): SliderAttribute--><!--Device-SliderAttribute-blockColor(value: ResourceColor | LinearGradient): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Color of the slider. <br>Default value: `$r('sys.color.ohos_id_color_foreground_contrary')`<br>**Note:** <br>When the slider shape is set to **SliderBlockType.IMAGE**, the slider has no fill, and setting **blockColor** does not take effect. |

## blockSize

```TypeScript
blockSize(value: SizeOptions)
```

Sets the size of the slider in the block direction.

When the slider type is set to **SliderBlockType.DEFAULT**, the smaller of the width and height values is used as the radius of the circle.

When the slider type is set to **SliderBlockType.IMAGE**, this API sets the size of the image, which is scaled using the **ObjectFit.Cover** strategy.

When the slider type is set to **SliderBlockType.SHAPE**, this API sets the size of the custom shape, which is also scaled using the **ObjectFit.Cover** strategy.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-blockSize(value: SizeOptions): SliderAttribute--><!--Device-SliderAttribute-blockSize(value: SizeOptions): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Slider size.<br>Default value: When the value of the **style** parameter is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).OutSet, the default value is {width: 18, height: 18}; when the value of the **style** parameter is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).InSet, the default value is {width: 12, height: 12}; when the value of the **style** parameter is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).NONE, this parameter does not take effect.<br>If the set **blockSize** has different width and height values, the smaller value is taken. If one or both of the width and height values are less than or equal to 0, the default value is used instead. |

## blockStyle

```TypeScript
blockStyle(value: SliderBlockStyle)
```

Sets the style of the slider in the block direction.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-blockStyle(value: SliderBlockStyle): SliderAttribute--><!--Device-SliderAttribute-blockStyle(value: SliderBlockStyle): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SliderBlockStyle](arkts-arkui-slider-comp-sliderblockstyle-i.md) | Yes | Slider style.<br>The default value is **SliderBlockType.DEFAULT**, indicating a circular slider. |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<SliderConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderAttribute-contentModifier(modifier: ContentModifier<SliderConfiguration>): SliderAttribute--><!--Device-SliderAttribute-contentModifier(modifier: ContentModifier<SliderConfiguration>): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[SliderConfiguration](arkts-arkui-slider-comp-sliderconfiguration-i.md)&gt; | Yes | Content modifier to apply to the **Slider** component.<br>**ContentModifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity to the digital crown rotation.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SliderAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): SliderAttribute--><!--Device-SliderAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM** |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enabled: boolean)
```

Specifies whether to enable haptic feedback.

To enable haptic feedback, you must declare the **ohos.permission.VIBRATE** permission under **requestPermissions** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the project.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SliderAttribute-enableHapticFeedback(enabled: boolean): SliderAttribute--><!--Device-SliderAttribute-enableHapticFeedback(enabled: boolean): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable haptic feedback.<br>**true**: enable haptic feedback; **false**: disable haptic feedback.<br>Default value: **true** |

## minResponsiveDistance

```TypeScript
minResponsiveDistance(value: number)
```

Sets the minimum response distance for the slider to start sliding.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderAttribute-minResponsiveDistance(value: number): SliderAttribute--><!--Device-SliderAttribute-minResponsiveDistance(value: number): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum response distance for the slider to start sliding.<br>Default value: **0**&lt;br/ &gt;**Note:** <br>The unit is the same as that of the **min** and **max** attributes in [SliderOptions](arkts-arkui-slider-comp-slideroptions-i.md).<br>If the value is less than 0, greater than **max** – **min**, **NaN**, or of a non-numeric type, the default value is used. |

## onChange

```TypeScript
onChange(callback: (value: number, mode: SliderChangeMode) => void)
```

Triggered when the slider is dragged or clicked.

The **Begin** and **End** states are triggered when the slider is clicked with a gesture. The **Moving** and **Click** states are triggered when the value of **value** changes.

If the coherent action is a drag action, the **Click** state will not be triggered.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-onChange(callback: (value: number, mode: SliderChangeMode) => void): SliderAttribute--><!--Device-SliderAttribute-onChange(callback: (value: number, mode: SliderChangeMode) => void): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: number, mode: SliderChangeMode) =&gt; void | Yes |  |

## prefix

```TypeScript
prefix(content: ComponentContent, options?: SliderPrefixOptions)
```

Sets the prefix of the slider.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderAttribute-prefix(content: ComponentContent, options?: SliderPrefixOptions): SliderAttribute--><!--Device-SliderAttribute-prefix(content: ComponentContent, options?: SliderPrefixOptions): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | ComponentContent | Yes | Visual content of the slider prefix, which will be displayed at the start of the slider. |
| options | [SliderPrefixOptions](arkts-arkui-slider-comp-sliderprefixoptions-i.md) | No | Configuration options of the slider prefix, used to set accessibility- related attributes.<br>Default value: **null** |

## selectedBorderRadius

```TypeScript
selectedBorderRadius(value: Dimension)
```

Set the corner radius of the selected (highlighted) part of the slider.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderAttribute-selectedBorderRadius(value: Dimension): SliderAttribute--><!--Device-SliderAttribute-selectedBorderRadius(value: Dimension): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Corner radius of the selected part of the slider.<br>Default value: When **style** is set to **SliderStyle.InSet** or **SliderStyle.OutSet**, the default value follows the corner radius of the track; when **style** is set to **SliderStyle.NONE**, the default value is **0**.<br>**Note:** <br> Percentage values are not supported. If the value is less than 0, the default value is used. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the color of the portion of the track between the minimum value and the thumb, representing the selected portion.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-selectedColor(value: ResourceColor): SliderAttribute--><!--Device-SliderAttribute-selectedColor(value: ResourceColor): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the portion of the track between the minimum value and the thumb.<br>Default value: **$r('sys.color.ohos_id_color_emphasize')** |

<a id="selectedcolor-1"></a>

## selectedColor

```TypeScript
selectedColor(selectedColor: ResourceColor | LinearGradient)
```

Sets the color of the portion of the track between the minimum value and the thumb, representing the selected portion. Compared to [selectedColor](#selectedcolor), this API supports the **LinearGradient** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-SliderAttribute-selectedColor(selectedColor: ResourceColor | LinearGradient): SliderAttribute--><!--Device-SliderAttribute-selectedColor(selectedColor: ResourceColor | LinearGradient): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedColor | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Color of the portion of the track between the minimum value and the thumb.<br>Default value: **$r('sys.color.ohos_id_color_emphasize')** <br>**NOTE:** <br>With gradient color settings, if the color stop values are invalid or if the color stops are empty, the gradient effect will not be applied. |

## showSteps

```TypeScript
showSteps(value: boolean)
```

Sets whether to display the step markers.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-showSteps(value: boolean): SliderAttribute--><!--Device-SliderAttribute-showSteps(value: boolean): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the step markers.<br>**true**: display the step markers; **false**: do not display the step markers.<br>Default Value: **false** |

<a id="showsteps-1"></a>

## showSteps

```TypeScript
showSteps(value: boolean, options?: SliderShowStepOptions)
```

Sets whether to display the step markers along the slider track.

You can set custom accessibility text for each step value. If no accessibility text is provided, the numeric values are used.

The accessibility text settings take effect only when the step markers are displayed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-SliderAttribute-showSteps(value: boolean, options?: SliderShowStepOptions): SliderAttribute--><!--Device-SliderAttribute-showSteps(value: boolean, options?: SliderShowStepOptions): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the step markers.<br>**true**: display the step markers; **false**: do not display the step markers.<br>Default value: **false** |
| options | [SliderShowStepOptions](arkts-arkui-slider-comp-slidershowstepoptions-i.md) | No | Configuration options of the accessibility text of the step markers.<br>Default value: **null** |

## showTips

```TypeScript
showTips(value: boolean, content?: ResourceStr)
```

Sets whether to display a tooltip when the user drags the slider.

When **direction** is set to **Axis.Horizontal**, the tooltip is displayed above the block. If the space above is insufficient to display the complete tooltip, it is displayed below. When **direction** is set to **Axis.Vertical**, the tooltip is displayed to the left of the slider. If the space on the left is insufficient to display the complete tooltip, it is displayed on the right. When no surrounding margin is set, or the margin is smaller than the space required by the tooltip, the tooltip is truncated.

The drawing area of the tooltip is the overlay of the slider.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-showTips(value: boolean, content?: ResourceStr): SliderAttribute--><!--Device-SliderAttribute-showTips(value: boolean, content?: ResourceStr): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display a tooltip when the user drags the slider.<br>**true**: Display a tooltip. **false**: Do not display a tooltip. <br>Default value: **false** |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | No | Text content of the tooltip. When passed in, custom text is displayed (used when a specific format or additional information needs to be shown); when not passed in, the current percentage value is displayed by default.<br><br>**Since:** 10 |

## slideRange

```TypeScript
slideRange(value: SlideRange)
```

Sets the valid sliding range. After this attribute is set, the sliding range of the slider is limited to [from, to]. Taps and gestures outside this range do not trigger sliding. If the initial value of **value** exceeds the range, it is automatically adjusted to the boundary of the range.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderAttribute-slideRange(value: SlideRange): SliderAttribute--><!--Device-SliderAttribute-slideRange(value: SlideRange): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SlideRange](arkts-arkui-slider-comp-sliderange-i.md) | Yes | Valid sliding range. |

## sliderInteractionMode

```TypeScript
sliderInteractionMode(value: SliderInteraction)
```

Sets the interaction mode between the user and the slider.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SliderAttribute-sliderInteractionMode(value: SliderInteraction): SliderAttribute--><!--Device-SliderAttribute-sliderInteractionMode(value: SliderInteraction): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SliderInteraction](arkts-arkui-slider-comp-sliderinteraction-e.md) | Yes | Interaction mode between the user and the slider.<br>Default value: **SliderInteraction.SLIDE_AND_CLICK**. |

## stepColor

```TypeScript
stepColor(value: ResourceColor)
```

Sets the step color.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-stepColor(value: ResourceColor): SliderAttribute--><!--Device-SliderAttribute-stepColor(value: ResourceColor): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Step color.<br>Default value:<br>The `$r('sys.color.ohos_id_color_foreground')` color mixed with the transparency of `$r('sys.color.ohos_id_alpha_normal_bg')`. |

## stepSize

```TypeScript
stepSize(value: Length)
```

Sets the step size (diameter). If the value is 0, the step size is not displayed. If the value is less than 0, the default value is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-stepSize(value: Length): SliderAttribute--><!--Device-SliderAttribute-stepSize(value: Length): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Step size (diameter). <br>Default value: **'4vp'**<br>Value range: [0, [trackThickness](#trackthickness)), in vp |

## suffix

```TypeScript
suffix(content: ComponentContent, options?: SliderSuffixOptions)
```

Sets the suffix of the slider.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SliderAttribute-suffix(content: ComponentContent, options?: SliderSuffixOptions): SliderAttribute--><!--Device-SliderAttribute-suffix(content: ComponentContent, options?: SliderSuffixOptions): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | ComponentContent | Yes | Visual content of the slider suffix, which will be displayed at the end position of the slider. |
| options | [SliderSuffixOptions](arkts-arkui-slider-comp-slidersuffixoptions-i.md) | No | Configuration options of the slider suffix, used to set accessibility- related attributes.<br>Default value: **null** |

## trackBorderRadius

```TypeScript
trackBorderRadius(value: Length)
```

Sets the radius of the rounded corner of the track.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SliderAttribute-trackBorderRadius(value: Length): SliderAttribute--><!--Device-SliderAttribute-trackBorderRadius(value: Length): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Radius of the rounded corner of the track.<br>Default value:<br>The default value is **2vp** when **style** is set to **SliderStyle.OutSet**.<br>The default value is **10vp** when **style** is set to **SliderStyle.InSet**.<br>**Note:** <br>If the value is less than 0, the default value is used. |

## trackColor

```TypeScript
trackColor(value: ResourceColor | LinearGradient)
```

Sets the background color of the track.

Since API version 12, the **LinearGradient** type can be used to set the gradient color of the track.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-trackColor(value: ResourceColor | LinearGradient): SliderAttribute--><!--Device-SliderAttribute-trackColor(value: ResourceColor | LinearGradient): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Background color of the track.<br>Default value: `$r('sys.color.ohos_id_color_component_normal')`<br>**Note:** <br>1. When a gradient color is set, if the color value of a color stop is invalid or the gradient color stop is empty, the gradient color does not take effect.<br>2. The **LinearGradient** type in this API is not supported in atomic services.<br>**Since:** 12 |

## trackColorMetrics

```TypeScript
trackColorMetrics(color: ColorMetricsLinearGradient)
```

Sets the linear gradient background color of the track. Compared with **trackColor**, it uses the **ColorMetricsLinearGradient** type to support gradients in a specified color gamut.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SliderAttribute-trackColorMetrics(color: ColorMetricsLinearGradient): SliderAttribute--><!--Device-SliderAttribute-trackColorMetrics(color: ColorMetricsLinearGradient): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ColorMetricsLinearGradient](arkts-arkui-slider-comp-colormetricslineargradient-c.md) | Yes | Linear gradient background color of the track.<br>When a gradient color is set, if the value of **color** is **undefined**, the gradient color setting does not take effect, and the default background color of the track is `$r('sys.color.ohos_id_color_component_normal')`. |

## trackThickness

```TypeScript
trackThickness(value: Length)
```

Sets the thickness of the track. If the value is less than or equal to 0, the default value is used.

To ensure [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md) works as expected for the thumb and track, [blockSize](#blocksize) should increase or decrease proportionally with **trackThickness**.

When **style** is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).OutSet, trackThickness: [blockSize](#blocksize)=1:4. When **style** is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).InSet, trackThickness:[blockSize](#blocksize)=5:3.

If the value of **trackThickness** or [blockSize](#blocksize) exceeds the width or height of the **Slider** component, the default value is used.

When [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md) is set to **OutSet**, if the specified value of [blockSize](#blocksize) exceeds the width or height of the **Slider** component, the default value is used, regardless of whether the value of **trackThickness** is valid or not.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SliderAttribute-trackThickness(value: Length): SliderAttribute--><!--Device-SliderAttribute-trackThickness(value: Length): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Thickness of the track.<br>Default value: **4.0vp** when **style** is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md).OutSet, and **20.0vp** when style is set to [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md). InSet. |

## maxLabel

```TypeScript
maxLabel(value: string)
```

Sets the text content of the maximum value label.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** max

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SliderAttribute-maxLabel(value: string): SliderAttribute--><!--Device-SliderAttribute-maxLabel(value: string): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text of the maximum value label. |

## minLabel

```TypeScript
minLabel(value: string)
```

Sets the text content of the minimum value label.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** min

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SliderAttribute-minLabel(value: string): SliderAttribute--><!--Device-SliderAttribute-minLabel(value: string): SliderAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text of the minimum value label. |
