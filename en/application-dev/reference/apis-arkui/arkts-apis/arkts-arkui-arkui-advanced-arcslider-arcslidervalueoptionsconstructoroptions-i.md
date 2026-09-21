# ArcSliderValueOptionsConstructorOptions

```TypeScript
interface ArcSliderValueOptionsConstructorOptions
```

Defines the constructor information for **ArcSliderValueOptions**.

**Since:** 18

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

If the value of **min** is greater than or equal to that of **max**, **min** is set to **0** and **max** **100**.

If the value is not within the [min, max] range, the value of **min** or **max** is used, whichever is closer.

@Trace

**Type:** number

**Default:** 100

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## min

```TypeScript
min?: number
```

Minimum value.

Default value: **0**.

@Trace

**Type:** number

**Default:** 0

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## progress

```TypeScript
progress?: number
```

Current progress.

Default value: same as the value of **min**.

@Trace

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
