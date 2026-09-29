# ArcSliderLayoutOptionsConstructorOptions

```TypeScript
interface ArcSliderLayoutOptionsConstructorOptions
```

Defines the construction information of **ArcSliderLayoutOptions**.

**Since:** 18

<!--Device-unnamed-interface ArcSliderLayoutOptionsConstructorOptions--><!--Device-unnamed-interface ArcSliderLayoutOptionsConstructorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## position

```TypeScript
position?: ArcSliderPosition
```

Position of the arc slider on the screen.

Default value: **ArcSliderPosition.RIGHT**

**Type:** [ArcSliderPosition](arkts-arkui-arkui-advanced-arcslider-arcsliderposition-e.md)

**Default:** ArcSliderPosition.RIGHT

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderLayoutOptionsConstructorOptions-position?: ArcSliderPosition--><!--Device-ArcSliderLayoutOptionsConstructorOptions-position?: ArcSliderPosition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## reverse

```TypeScript
reverse?: boolean
```

Whether to reverse the sliding direction of the arc slider. The value **false** means sliding from top to bottom.

Default value: **true**, meaning sliding from bottom to top.

**Type:** boolean

**Default:** true

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderLayoutOptionsConstructorOptions-reverse?: boolean--><!--Device-ArcSliderLayoutOptionsConstructorOptions-reverse?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
