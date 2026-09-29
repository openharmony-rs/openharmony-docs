# ArcSliderValueOptionsConstructorOptions

```TypeScript
interface ArcSliderValueOptionsConstructorOptions
```

Defines the constructor information for **ArcSliderValueOptions**.

**Since:** 18

<!--Device-unnamed-interface ArcSliderValueOptionsConstructorOptions--><!--Device-unnamed-interface ArcSliderValueOptionsConstructorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## max

```TypeScript
max?: number
```

Maximum value.

Default value: **100**

**NOTE:** 

When an abnormal situation occurs where **min** &gt;= **max**, **min** takes the default value **0** and **max** takes the default value **100**.

When **progress** is not within the [min, max] range, the nearest boundary value is taken: if **progress** is less than **min**, **min** is taken; if **progress** is greater than **max**, **max** is taken.

**Type:** number

**Default:** 100

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptionsConstructorOptions-max?: number--><!--Device-ArcSliderValueOptionsConstructorOptions-max?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## min

```TypeScript
min?: number
```

Minimum value.

Default value: **0**.

**Type:** number

**Default:** 0

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptionsConstructorOptions-min?: number--><!--Device-ArcSliderValueOptionsConstructorOptions-min?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
progress?: number
```

Current progress.

Default value: same as the value of **min**.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcSliderValueOptionsConstructorOptions-progress?: number--><!--Device-ArcSliderValueOptionsConstructorOptions-progress?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
