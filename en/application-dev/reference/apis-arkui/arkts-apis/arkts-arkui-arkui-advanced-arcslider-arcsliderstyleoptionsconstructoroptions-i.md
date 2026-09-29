# ArcSliderStyleOptionsConstructorOptions

```TypeScript
interface ArcSliderStyleOptionsConstructorOptions
```

Defines the constructor information for **ArcSliderStyleOptions**.

**Since:** 18

<!--Device-unnamed-interface ArcSliderStyleOptionsConstructorOptions--><!--Device-unnamed-interface ArcSliderStyleOptionsConstructorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## activeTrackThickness

```TypeScript
activeTrackThickness?: number
```

Stroke width of the arc slider when it is in an enlarged state, in vp.

Default value: **24**

Value range: [24, 36]. If the value is invalid, the default value is used.

**Type:** number

**Default:** 24

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptionsConstructorOptions-activeTrackThickness?: number--><!--Device-ArcSliderStyleOptionsConstructorOptions-activeTrackThickness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## selectedColor

```TypeScript
selectedColor?: string
```

Highlight color of the stroke.

Default value: **#FF5EA1FF**

**Type:** string

**Default:** #FF5EA1FF

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptionsConstructorOptions-selectedColor?: string--><!--Device-ArcSliderStyleOptionsConstructorOptions-selectedColor?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackBlur

```TypeScript
trackBlur?: number
```

Stroke background blur value. Unit: vp.

Default value: **20**

Value range: [0, +∞). Abnormal values are handled as default.

**Type:** number

**Default:** 20

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptionsConstructorOptions-trackBlur?: number--><!--Device-ArcSliderStyleOptionsConstructorOptions-trackBlur?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackColor

```TypeScript
trackColor?: string
```

Background color of the stroke.

Default value: **#33FFFFFF**

**Type:** string

**Default:** #33FFFFFF

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptionsConstructorOptions-trackColor?: string--><!--Device-ArcSliderStyleOptionsConstructorOptions-trackColor?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## trackThickness

```TypeScript
trackThickness?: number
```

Stroke width of the arc slider in the normal state, in vp.

Default value: **5**

Value range: [5, 16]. If the value is invalid, the default value is used.

**Type:** number

**Default:** 5

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderStyleOptionsConstructorOptions-trackThickness?: number--><!--Device-ArcSliderStyleOptionsConstructorOptions-trackThickness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
