# ArcSliderStyleOptions

```TypeScript
declare class ArcSliderStyleOptions
```

Defines the style of the arc slider.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-declare class ArcSliderStyleOptions--><!--Device-unnamed-declare class ArcSliderStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderStyleOptionsConstructorOptions)
```

A constructor used to create an **ArcSliderStyleOptions** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-constructor(options?: ArcSliderStyleOptionsConstructorOptions)--><!--Device-ArcSliderStyleOptions-constructor(options?: ArcSliderStyleOptionsConstructorOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcSliderStyleOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptionsconstructoroptions-i.md) | No | Construction information of **ArcSliderStyleOptions**. When not passed in, all sub-attributes of **ArcSliderStyleOptions** take their default values. |

## activeTrackThickness

```TypeScript
activeTrackThickness?: number
```

Stroke width of the arc slider when it is in an enlarged state, in vp.

Default value: **24**

Value range: [24, 36]. If the value is invalid, the default value is used.

**Decorator**: @Trace

**Type:** number

**Default:** 24

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-activeTrackThickness?: number--><!--Device-ArcSliderStyleOptions-activeTrackThickness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## selectedColor

```TypeScript
selectedColor?: string
```

Highlight color of the stroke.

Default value: **#FF5EA1FF**

**Decorator**: @Trace

**Type:** string

**Default:** #FF5EA1FF

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-selectedColor?: string--><!--Device-ArcSliderStyleOptions-selectedColor?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackBlur

```TypeScript
trackBlur?: number
```

Stroke background blur value, in vp.

Default value: **20**

Value range: [0, +∞). Abnormal values are handled as default.

**Decorator:*

**Type:** number

**Default:** 20

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-trackBlur?: number--><!--Device-ArcSliderStyleOptions-trackBlur?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackColor

```TypeScript
trackColor?: string
```

Background color of the stroke.

Default value: **#33FFFFFF**

**Decorator**: @Trace

**Type:** string

**Default:** #33FFFFFF

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-trackColor?: string--><!--Device-ArcSliderStyleOptions-trackColor?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackThickness

```TypeScript
trackThickness?: number
```

Stroke width of the arc slider in the normal state, in vp.

Default value: **5**

Value range: [5, 16]. If the value is invalid, the default value is used.

**Decorator**: @Trace

**Type:** number

**Default:** 5

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptions-trackThickness?: number--><!--Device-ArcSliderStyleOptions-trackThickness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
