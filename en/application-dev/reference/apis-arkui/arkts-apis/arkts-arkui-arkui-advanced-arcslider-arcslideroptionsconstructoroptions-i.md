# ArcSliderOptionsConstructorOptions

```TypeScript
interface ArcSliderOptionsConstructorOptions
```

Defines the constructor information for **ArcSliderOptions**.

**Since:** 18

<!--Device-unnamed-interface ArcSliderOptionsConstructorOptions--><!--Device-unnamed-interface ArcSliderOptionsConstructorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: ArcSliderChangeHandler
```

Callback triggered when the progress value of the arc slider changes.

Default value: no callback when not passed in.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-onChange?: ArcSliderChangeHandler--><!--Device-ArcSliderOptionsConstructorOptions-onChange?: ArcSliderChangeHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onEnlarge

```TypeScript
onEnlarge?: ArcSliderEnlargeHandler
```

Callback triggered when the arc slider is enlarged or shrunk.

Default value: no callback when not passed in.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-onEnlarge?: ArcSliderEnlargeHandler--><!--Device-ArcSliderOptionsConstructorOptions-onEnlarge?: ArcSliderEnlargeHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: ArcSliderTouchHandler
```

Callback triggered when the arc slider is touched.

Default value: no callback when not passed in.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-onTouch?: ArcSliderTouchHandler--><!--Device-ArcSliderOptionsConstructorOptions-onTouch?: ArcSliderTouchHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity?: CrownSensitivity
```

Sensitivity to the digital crown rotation.

Default value: **CrownSensitivity.MEDIUM**

**Type:** [CrownSensitivity](arkts-arkui-crownsensitivity-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-digitalCrownSensitivity?: CrownSensitivity--><!--Device-ArcSliderOptionsConstructorOptions-digitalCrownSensitivity?: CrownSensitivity-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## layoutOptions

```TypeScript
layoutOptions?: ArcSliderLayoutOptions
```

Layout of the arc slider.

Default value: default values of all properties of [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**Type:** [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-layoutOptions?: ArcSliderLayoutOptions--><!--Device-ArcSliderOptionsConstructorOptions-layoutOptions?: ArcSliderLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## styleOptions

```TypeScript
styleOptions?: ArcSliderStyleOptions
```

Style of the arc slider.

Default value: default values of all properties of [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**Type:** [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-styleOptions?: ArcSliderStyleOptions--><!--Device-ArcSliderOptionsConstructorOptions-styleOptions?: ArcSliderStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## valueOptions

```TypeScript
valueOptions?: ArcSliderValueOptions
```

Value of the arc slider.

Default value: default values of all properties of [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**Type:** [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderOptionsConstructorOptions-valueOptions?: ArcSliderValueOptions--><!--Device-ArcSliderOptionsConstructorOptions-valueOptions?: ArcSliderValueOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
