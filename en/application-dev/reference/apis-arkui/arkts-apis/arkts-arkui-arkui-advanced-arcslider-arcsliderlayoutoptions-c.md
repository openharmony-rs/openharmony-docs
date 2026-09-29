# ArcSliderLayoutOptions

```TypeScript
declare class ArcSliderLayoutOptions
```

Defines the layout of the arc slider.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-declare class ArcSliderLayoutOptions--><!--Device-unnamed-declare class ArcSliderLayoutOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderLayoutOptionsConstructorOptions)
```

A constructor used to create an **ArcSliderLayoutOptions** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)--><!--Device-ArcSliderLayoutOptions-constructor(options?: ArcSliderLayoutOptionsConstructorOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcSliderLayoutOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptionsconstructoroptions-i.md) | No | Construction information of **ArcSliderLayoutOptions**. When not passed in, all sub-attributes of **ArcSliderLayoutOptions** take their default values. |

## position

```TypeScript
position?: ArcSliderPosition
```

Position of the arc slider on the screen.

Default value: **ArcSliderPosition.RIGHT**

**Decorator**: @Trace

**Type:** [ArcSliderPosition](arkts-arkui-arkui-advanced-arcslider-arcsliderposition-e.md)

**Default:** ArcSliderPosition.RIGHT

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderLayoutOptions-position?: ArcSliderPosition--><!--Device-ArcSliderLayoutOptions-position?: ArcSliderPosition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## reverse

```TypeScript
reverse?: boolean
```

Whether to reverse the sliding direction of the arc slider. The value **false** means sliding from top to bottom.

Default value: **true**, meaning sliding from bottom to top.

**Decorator:*

**Type:** boolean

**Default:** true

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderLayoutOptions-reverse?: boolean--><!--Device-ArcSliderLayoutOptions-reverse?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
