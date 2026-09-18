# BrightnessBlenderParam (System API)

Parameter list of BrightnessBlender, used to configure various properties of the brightness effect, including grayscale adjustment coefficients, saturation, and blending ratio parameters.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cubicRate

```TypeScript
cubicRate: number
```

Third-order coefficient for grayscale adjustment. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## degree

```TypeScript
degree: number
```

Grayscale adjustment ratio. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## fraction

```TypeScript
fraction: number
```

Blending ratio for the brightness effect. The value range is [0, 1]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## linearRate

```TypeScript
linearRate: number
```

Linear coefficient for grayscale adjustment. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## negativeCoefficient

```TypeScript
negativeCoefficient: [number, number, number]
```

Negative RGB adjustment coefficients based on the base saturation. The value range for each number is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** [number, number, number]

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## positiveCoefficient

```TypeScript
positiveCoefficient: [number, number, number]
```

Positive RGB adjustment coefficients based on the base saturation. The value range for each number is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** [number, number, number]

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## quadraticRate

```TypeScript
quadraticRate: number
```

Second-order coefficient for grayscale adjustment. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## saturation

```TypeScript
saturation: number
```

Base saturation for brightness. The value range is [0, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
