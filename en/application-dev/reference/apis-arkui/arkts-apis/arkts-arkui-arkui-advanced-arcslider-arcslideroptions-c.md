# ArcSliderOptions

```TypeScript
declare class ArcSliderOptions
```

Defines the properties of the arc slider.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-declare class ArcSliderOptions--><!--Device-unnamed-declare class ArcSliderOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderOptionsConstructorOptions)
```

A constructor used to create an **ArcSliderOptions** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)--><!--Device-ArcSliderOptions-constructor(options?: ArcSliderOptionsConstructorOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | No | Construction information of **ArcSliderOptions**. When not passed in, all sub-attributes of **ArcSliderOptions** take their default values. |

## onChange

```TypeScript
onChange?: ArcSliderChangeHandler
```

Callback triggered when the progress value of the arc slider changes.

Default value: no callback when not passed in.

**Decorator:*

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-onChange?: ArcSliderChangeHandler--><!--Device-ArcSliderOptions-onChange?: ArcSliderChangeHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onEnlarge

```TypeScript
onEnlarge?: ArcSliderEnlargeHandler
```

Callback triggered when the arc slider is enlarged or shrunk.

Default value: no callback when not passed in.

**Decorator:*

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-onEnlarge?: ArcSliderEnlargeHandler--><!--Device-ArcSliderOptions-onEnlarge?: ArcSliderEnlargeHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: ArcSliderTouchHandler
```

Callback triggered when the arc slider is touched.

Default value: no callback when not passed in.

**Decorator:*

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-onTouch?: ArcSliderTouchHandler--><!--Device-ArcSliderOptions-onTouch?: ArcSliderTouchHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity?: CrownSensitivity
```

Sensitivity to the digital crown rotation.

Default value: **CrownSensitivity.MEDIUM**

**Decorator**: @Trace

**Type:** [CrownSensitivity](arkts-arkui-crownsensitivity-e.md)

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-digitalCrownSensitivity?: CrownSensitivity--><!--Device-ArcSliderOptions-digitalCrownSensitivity?: CrownSensitivity-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## layoutOptions

```TypeScript
layoutOptions?: ArcSliderLayoutOptions
```

Layout of the arc slider.

Default value: default values of all properties of [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**Decorator**: @Trace

**Type:** [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-layoutOptions?: ArcSliderLayoutOptions--><!--Device-ArcSliderOptions-layoutOptions?: ArcSliderLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## styleOptions

```TypeScript
styleOptions?: ArcSliderStyleOptions
```

Style of the arc slider.

Default value: default values of all properties of [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**Decorator**: @Trace

**Type:** [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-styleOptions?: ArcSliderStyleOptions--><!--Device-ArcSliderOptions-styleOptions?: ArcSliderStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## valueOptions

```TypeScript
valueOptions?: ArcSliderValueOptions
```

Value of the arc slider.

Default value: default values of all properties of [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**Decorator**: @Trace

**Type:** [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptions-valueOptions?: ArcSliderValueOptions--><!--Device-ArcSliderOptions-valueOptions?: ArcSliderValueOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
