# Slider properties/events

All the universal attributes except **responseRegion** are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** SliderAttribute extends CommonMethod<SliderAttribute>

**Since:** 7

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Border width of the slider in the block direction.<br>**NOTE:** <br>For the string type, percentage values are not supported. |

## blockColor

```TypeScript
blockColor(value: ResourceColor)
```

Sets the color of the thumb.

When **SliderBlockType.DEFAULT** is used, **blockColor** sets the color of the round thumb.

When **SliderBlockType.IMAGE** is used, **blockColor** does not work as the thumb has no fill color.

When **SliderBlockType.SHAPE** is used, **blockColor** sets the color of the thumb in a custom shape.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the thumb.<br>Default value: **&#36;r('sys.color.ohos_id_color_foreground_contrary')** |

## blockColor

```TypeScript
blockColor(value: ResourceColor | LinearGradient)
```

Sets the color of the slider. Gradient colors are supported.

When **SliderBlockType.DEFAULT** is used, **blockColor** sets the color of the round thumb.

When **SliderBlockType.IMAGE** is used, **blockColor** does not work as the thumb has no fill color.

When **SliderBlockType.SHAPE** is used, **blockColor** sets the color of the thumb in a custom shape.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Color of the thumb.<br>Default value: **&#36;r('sys.color.ohos_id_color_foreground_contrary')** |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Size of the slider in the block direction.<br>Default value:<br>- For [SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet: **{width: 18, height: 18}**<br>- For [SliderStyle](arkts-arkui-sliderstyle-e.md).InSet: **{width: 12, height: 12}**<br>- For [SliderStyle](arkts-arkui-sliderstyle-e.md).NONE: This parameter is not effective.<br>If the set **blockSize** has different width and height values, the smaller value is taken. If one or both of the width and height values are less than or equal to 0, the default value is used instead. |

## blockStyle

```TypeScript
blockStyle(value: SliderBlockStyle)
```

Sets the style of the slider in the block direction.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SliderBlockStyle](arkts-arkui-sliderblockstyle-i.md) | Yes | Style of the slider in the block direction.<br>Default value: **SliderBlockType.DEFAULT**, indicating the round slider. |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<SliderConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[SliderConfiguration](arkts-arkui-sliderconfiguration-i.md)&gt; | Yes | Content modifier to apply to the slider.<br> **ContentModifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity to the digital crown rotation.

> **NOTE:** 
> 
> This API cannot be called within attributeModifier.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM** |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enabled: boolean)
```

Specifies whether to enable haptic feedback.

To enable haptic feedback, you must declare the **ohos.permission.VIBRATE** permission under **requestPermissions** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the project.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable haptic feedback.<br>**true**: Enable haptic feedback. **false**: Disable haptic feedback.<br>Default value: **true** |

## maxLabel

```TypeScript
maxLabel(value: string)
```

Sets the maximum value.

> **NOTE:** 
> 
> This attribute is supported since API version 7 and deprecated since API version 9. You are advised to use
> **max** instead. **max** is an attribute of [SliderOptions](arkts-arkui-slideroptions-i.md).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** max

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Maximum value. |

## minLabel

```TypeScript
minLabel(value: string)
```

Sets the minimum value.

> **NOTE:** 
> 
> This attribute is supported since API version 7 and deprecated since API version 9. You are advised to use
> **min** instead. **min** is an attribute of [SliderOptions](arkts-arkui-slideroptions-i.md).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** min

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Minimum value. |

## minResponsiveDistance

```TypeScript
minResponsiveDistance(value: number)
```

Sets the minimum distance required for the slider to respond.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum distance required for the slider to respond. The slider will only move when the sliding distance exceeds this threshold.<br>Default value: **0**<br>**NOTE:** <br>The unit is consistent with that of the **min** and **max** properties in [SliderOptions](arkts-arkui-slideroptions-i.md).<br>If the value is less than 0, greater than the result of (**max** – **min**), or invalid, the default value is used. |

## onChange

```TypeScript
onChange(callback: (value: number, mode: SliderChangeMode) => void)
```

Triggered when the slider is dragged or clicked.

The **Begin** and **End** states are triggered when the slider is clicked with a gesture. The **Moving** and **Click** states are triggered when the value of **value** changes.

If the coherent action is a drag action, the **Click** state will not be triggered.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | ComponentContent | Yes | Visual content of the slider prefix, which will be displayed at the start of the slider. |
| options | [SliderPrefixOptions](arkts-arkui-sliderprefixoptions-i.md) | No | Accessibility configuration of the slider prefix. |

## selectedBorderRadius

```TypeScript
selectedBorderRadius(value: Dimension)
```

Set the corner radius of the selected (highlighted) part of the slider.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Corner radius of the selected part of the slider.<br>Default value:<br>- For **SliderStyle.InSet** or **SliderStyle.OutSet**: same as the corner radius of the background<br>- **SliderStyle.NONE**: **0**<br>**NOTE:** <br>Percentage values are not supported. If the value is less than 0, the default value is used. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the color of the portion of the track between the minimum value and the thumb, representing the selected portion.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the portion of the track between the minimum value and the thumb.<br> Default value: **&#36;r('sys.color.ohos_id_color_emphasize')** |

## selectedColor

```TypeScript
selectedColor(selectedColor: ResourceColor | LinearGradient)
```

Sets the color of the portion of the track between the minimum value and the thumb, representing the selected portion. Compared to [selectedColor](#selectedcolor), this API supports the **LinearGradient** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedColor | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Color of the portion of the track between the minimum value and the thumb.<br>Default value: **&#36;r('sys.color.ohos_id_color_emphasize')**<br>**NOTE:** <br>With gradient color settings, if the color stop values are invalid or if the color stops are empty, the gradient effect will not be applied. |

## showSteps

```TypeScript
showSteps(value: boolean)
```

Sets whether to display the step markers along the slider track.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the step markers along the slider track.<br>**true**: Display the step markers. **false**: Do not display the step markers.<br>Default value: **false** |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the step markers along the slider track.<br>**true**: Display the step markers. **false**: Do not display the step markers.<br>Default value: **false** |
| options | [SliderShowStepOptions](arkts-arkui-slidershowstepoptions-i.md) | No | Accessibility configuration of step markers.<br>Default value: **null** |

## showTips

```TypeScript
showTips(value: boolean, content?: ResourceStr)
```

Sets whether to display a tooltip when the user drags the slider.

When **direction** is set to **Axis.Horizontal**, the tooltip is displayed right above the slider; if there is insufficient space above, it will be displayed below. When **direction** is set to **Axis.Vertical**, the tooltip is displayed on the left of the slider; if there is insufficient space on the left, it will be displayed on the right. If the margins are not set or are set to small values, the tooltip may be clipped.

The drawing area of the tooltip is the overlay of the slider.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display a tooltip when the user drags the slider.<br>**true**: Display a tooltip. **false**: Do not display a tooltip.<br>Default value: **false** |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | No | Content of the tooltip. By default, the tooltip shows the current percentage value.<br>**Since:** 10 |

## slideRange

```TypeScript
slideRange(value: SlideRange)
```

Sets the slide range.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SlideRange](arkts-arkui-sliderange-i.md) | Yes | Slide range. |

## sliderInteractionMode

```TypeScript
sliderInteractionMode(value: SliderInteraction)
```

Sets the interaction mode between the user and the slider.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | Yes | Interaction mode between the user and the slider.<br> Default value: **SliderInteraction.SLIDE_AND_CLICK** |

## stepColor

```TypeScript
stepColor(value: ResourceColor)
```

Sets the step color.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Step color.<br>Default value:<br>**&#36;r('sys.color.ohos_id_color_foreground')** mixed with **&#36;r('sys.color.ohos_id_alpha_normal_bg')** |

## stepSize

```TypeScript
stepSize(value: Length)
```

Sets the step size (diameter). If the value is 0, the step size is not displayed. If the value is less than 0, the default value is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Step size (diameter).<br>Default value: **'4vp'**<br>Value range: [0, [trackThickness](#trackthickness)) |

## suffix

```TypeScript
suffix(content: ComponentContent, options?: SliderSuffixOptions)
```

Sets the suffix of the slider.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | ComponentContent | Yes | Visual content of the slider suffix, which will be displayed at the end of the slider. |
| options | [SliderSuffixOptions](arkts-arkui-slidersuffixoptions-i.md) | No | Accessibility configuration of the slider suffix. |

## trackBorderRadius

```TypeScript
trackBorderRadius(value: Length)
```

Sets the radius of the rounded corner of the track.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Radius of the rounded corner of the track.<br>Default value:<br>**'2vp'** when **style** is **SliderStyle.OutSet**<br>**'10vp'** when **style** is **SliderStyle.InSet**<br>**NOTE:** <br>If the value is less than 0, the default value is used. |

## trackColor

```TypeScript
trackColor(value: ResourceColor | LinearGradient)
```

Sets the background color of the track.

Since API version 12, **LinearGradient** can be used to create a gradient effect for the track.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Background color of the track.<br>Default value: **&#36;r('sys.color.ohos_id_color_component_normal')**<br>**NOTE:** <br>1. With gradient color settings, if the color stop values are invalid or if the color stops are empty, the gradient effect will not be applied.<br>2. The LinearGradient type cannot be used in atomic services.<br>**Since:** 12 |

## trackColorMetrics

```TypeScript
trackColorMetrics(color: ColorMetricsLinearGradient)
```

Sets the linear gradient background color of the track.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ColorMetricsLinearGradient](arkts-arkui-colormetricslineargradient-c.md) | Yes | Linear gradient background color of the track.<br>If **color** is **undefined**, the gradient color setting is invalid. The default background color of the track is **&#36;r('sys.color.ohos_id_color_component_normal')**. |

## trackThickness

```TypeScript
trackThickness(value: Length)
```

Sets the thickness of the track. If the value is less than or equal to 0, the default value is used.

To ensure [SliderStyle](arkts-arkui-sliderstyle-e.md) works as expected for the thumb and track, [blockSize](#blocksize) should increase or decrease proportionally with **trackThickness**.

Specially, when **style** is **[SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet**, trackThickness: [blockSize](#blocksize) = 1:4; when **style** is **[SliderStyle](arkts-arkui-sliderstyle-e.md).InSet**, trackThickness: [blockSize](#blocksize) = 5:3.

If the value of **trackThickness** or [blockSize](#blocksize) exceeds the width or height of the **Slider** component, the default value is used.

When [SliderStyle](arkts-arkui-sliderstyle-e.md) is set to **OutSet**, if the specified value of [blockSize](#blocksize) exceeds the width or height of the **Slider** component, the default value is used, regardless of whether the value of **trackThickness** is valid or not.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Thickness of the track.<br>Default value: 4.0vp when **style** is set to **[SliderStyle](arkts-arkui-sliderstyle-e.md).OutSet**; 20.0vp when **style** is set to **[SliderStyle](arkts-arkui-sliderstyle-e.md).InSet** |
