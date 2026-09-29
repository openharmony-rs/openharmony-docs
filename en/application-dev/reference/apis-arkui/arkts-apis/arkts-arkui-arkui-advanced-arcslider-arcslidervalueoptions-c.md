# ArcSliderValueOptions

```TypeScript
declare class ArcSliderValueOptions
```

Defines the value of the arc slider.

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-declare class ArcSliderValueOptions--><!--Device-unnamed-declare class ArcSliderValueOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ArcSliderValueOptionsConstructorOptions)
```

A constructor used to create an **ArcSliderValueOptions** instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)--><!--Device-ArcSliderValueOptions-constructor(options?: ArcSliderValueOptionsConstructorOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ArcSliderValueOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptionsconstructoroptions-i.md) | No | Construction information of **ArcSliderValueOptions**. When not passed in, each sub-attribute of **ArcSliderValueOptions** takes its default value. |

## max

```TypeScript
max?: number
```

Maximum value.

Default value: **100**

**NOTE:** 

When an abnormal situation occurs where **min** &gt;= max, **min** takes the default value **0** and max takes the default value **100**.

When progress is not within the range of [min, max], the nearest boundary value is taken: if **progress** is less than **min**, **min** is taken; if **progress** is greater than **max**, **max** is taken.

**Decorator:*

**Type:** number

**Default:** 100

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptions-max?: number--><!--Device-ArcSliderValueOptions-max?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## min

```TypeScript
min?: number
```

Minimum value.

Default value: **0**.

**Decorator**: @Trace

**Type:** number

**Default:** 0

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptions-min?: number--><!--Device-ArcSliderValueOptions-min?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
progress?: number
```

Current progress.

Default value: same as the value of **min**.

**Decorator**: @Trace

**Type:** number

**Since:** 18

**Decorator:** @Trace

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptions-progress?: number--><!--Device-ArcSliderValueOptions-progress?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
