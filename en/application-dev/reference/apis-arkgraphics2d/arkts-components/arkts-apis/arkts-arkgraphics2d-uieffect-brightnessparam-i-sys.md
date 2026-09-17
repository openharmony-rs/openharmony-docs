# BrightnessParam (System API)

Detailed description of the material brightness parameters.

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cubicCoeff

```TypeScript
cubicCoeff : number
```

Third-order coefficient for grayscale adjustment. The value range is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value results in a stronger grayscale adjustment effect.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## fraction

```TypeScript
fraction : number
```

Blending ratio for the brightness effect. The value range is [0, 1]. Values less than 0 are treated as 0; values greater than 1 are treated as 1. A larger value indicates a weaker brightness effect.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## lightUpDegree

```TypeScript
lightUpDegree : number
```

Grayscale adjustment ratio. The value range is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value results in a stronger grayscale adjustment effect.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## negRgb

```TypeScript
negRgb : [number, number, number]
```

Negative adjustment coefficients based on the base saturation. The value range for each number is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value indicates lower saturation.

**Type:** [number, number, number]

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## posRgb

```TypeScript
posRgb : [number, number, number]
```

Positive adjustment coefficients based on the base saturation. The value range for each number is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value indicates higher saturation.

**Type:** [number, number, number]

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## quadCoeff

```TypeScript
quadCoeff : number
```

Second-order coefficient for grayscale adjustment. The value range is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value results in a stronger grayscale adjustment effect.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rate

```TypeScript
rate : number
```

Linear coefficient for grayscale adjustment. The value range is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. A larger value results in a stronger grayscale adjustment effect.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## saturation

```TypeScript
saturation : number
```

Base saturation for brightness. The value range is [0, 1]. Values less than 0 are treated as 0; values greater than 1 are treated as 1. A larger value indicates a higher base saturation.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
