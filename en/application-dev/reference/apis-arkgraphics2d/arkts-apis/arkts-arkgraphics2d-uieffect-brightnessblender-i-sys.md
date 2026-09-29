# BrightnessBlender (System API)

```TypeScript
interface BrightnessBlender
```

Brightness blender, used to add a brightness effect to a specified component. Before calling BrightnessBlender, you need to first create a BrightnessBlender instance through createBrightnessBlender.

**Since:** 12

<!--Device-uiEffect-interface BrightnessBlender--><!--Device-uiEffect-interface BrightnessBlender-End-->

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

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-cubicRate: double--><!--Device-BrightnessBlender-cubicRate: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## degree

```TypeScript
degree: number
```

Grayscale adjustment ratio. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-degree: double--><!--Device-BrightnessBlender-degree: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## fraction

```TypeScript
fraction: number
```

Blending ratio for the brightness effect. The value range is [0, 1]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-fraction: double--><!--Device-BrightnessBlender-fraction: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## linearRate

```TypeScript
linearRate: number
```

Linear coefficient for grayscale adjustment. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-linearRate: double--><!--Device-BrightnessBlender-linearRate: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## negativeCoefficient

```TypeScript
negativeCoefficient: [number, number, number]
```

Negative RGB adjustment coefficients based on the base saturation. The value range for each number is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** [number, number, number]

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-negativeCoefficient: [double, double, double]--><!--Device-BrightnessBlender-negativeCoefficient: [double, double, double]-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## positiveCoefficient

```TypeScript
positiveCoefficient: [number, number, number]
```

Positive RGB adjustment coefficients based on the base saturation. The value range for each number is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** [number, number, number]

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-positiveCoefficient: [double, double, double]--><!--Device-BrightnessBlender-positiveCoefficient: [double, double, double]-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## quadraticRate

```TypeScript
quadraticRate: number
```

Second-order coefficient for grayscale adjustment. The value range is [-20, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-quadraticRate: double--><!--Device-BrightnessBlender-quadraticRate: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## saturation

```TypeScript
saturation: number
```

Base saturation for brightness. The value range is [0, 20]. Values outside the range will be clamped during implementation.

**Type:** number

**Since:** 12

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 22.

<!--Device-BrightnessBlender-saturation: double--><!--Device-BrightnessBlender-saturation: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
