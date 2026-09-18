# BrightnessInfo

Describes the screen brightness information. The information comes from the underlying screen data.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## brightnessPosition

```TypeScript
readonly brightnessPosition?: number
```

Position of the brightness bar corresponding to the current screen brightness. The value is a floating-point number ranging from 0.0 to 1.0. The default value is 0.0. The value 0.0 indicates the lowest screen brightness, and 1.0 indicates the highest screen brightness. The returned brightness bar position may have an error of 0.01 compared with the actual brightness bar position. Value range: [0.0,1.0]. Default value: 0.0.

@readonly

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

## currentHeadroom

```TypeScript
readonly currentHeadroom: number
```

Dynamic brightness headroom. The value is a floating-point number greater than 0. The default value is **1.0**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

## maxHeadroom

```TypeScript
readonly maxHeadroom: number
```

Maximum brightness headroom. The value is a floating-point number greater than 0. The default value is **1.0**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

## sdrNits

```TypeScript
readonly sdrNits: number
```

Screen brightness, in nit. The value is a floating-point number greater than 0. The default value is **500.0**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager
