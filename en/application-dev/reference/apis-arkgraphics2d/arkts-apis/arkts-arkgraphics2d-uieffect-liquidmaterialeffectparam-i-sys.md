# LiquidMaterialEffectParam (System API)

```TypeScript
interface LiquidMaterialEffectParam
```

Material effect parameters, used to control the display properties of the material such as refraction, reflection, perturbation, and overlay color.

**Since:** 22

<!--Device-uiEffect-interface LiquidMaterialEffectParam--><!--Device-uiEffect-interface LiquidMaterialEffectParam-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## distortFactor

```TypeScript
distortFactor : number
```

The perturbation effect coefficient. The value must be greater than or equal to 0. Values less than 0 indicate no perturbation effect.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-distortFactor : double--><!--Device-LiquidMaterialEffectParam-distortFactor : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## distortProgress

```TypeScript
distortProgress : number
```

The perturbation effect progress. The value range is [0, 1]. Values less than 0 are treated as 0; values greater than 1 are treated as 1. 0 indicates the start of perturbation, and 1 indicates the end.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-distortProgress : double--><!--Device-LiquidMaterialEffectParam-distortProgress : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## enable

```TypeScript
enable : boolean
```

Whether to enable the material effect. true means enabled, false means disabled.

**Type:** boolean

**Since:** 22

<!--Device-LiquidMaterialEffectParam-enable : boolean--><!--Device-LiquidMaterialEffectParam-enable : boolean-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## materialFactor

```TypeScript
materialFactor : number
```

The material coefficient. The value range is [0, 1]. Values less than 0 are treated as 0; values greater than 1 are treated as 1. A value of 0 means no material effect and the overlay color is used for filling; a larger value indicates a more obvious material effect.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-materialFactor : double--><!--Device-LiquidMaterialEffectParam-materialFactor : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## reflectionFactor

```TypeScript
reflectionFactor : number
```

The reflection coefficient. The value range is [0, 10]. Values less than 0 are treated as 0; values greater than 10 are treated as 10. A value of 0 means no reflection effect; a larger value indicates stronger reflection.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-reflectionFactor : double--><!--Device-LiquidMaterialEffectParam-reflectionFactor : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## refractionFactor

```TypeScript
refractionFactor : number
```

The refraction coefficient. The value range is [0, 10]. Values less than 0 are treated as 0; values greater than 10 are treated as 10. A value of 0 means no refraction effect; a larger value indicates stronger refraction.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-refractionFactor : double--><!--Device-LiquidMaterialEffectParam-refractionFactor : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## ripplePosition

```TypeScript
ripplePosition?: Array<[number, number]>
```

The positions where the ripple effect is applied. Pass this parameter when you need to trigger ripple effects at multiple specified positions simultaneously. If not passed, there are no ripple positions by default, and the ripple effect will not take effect. Each position in the array contains x and y dimensions, using normalized coordinates where [0, 0] represents the top-left corner and [1, 1] represents the bottom-right corner. A maximum of 10 position coordinates are supported; exceeding this will make the entire parameter invalid.

**Type:** Array&lt;[number, number]&gt;

**Since:** 22

<!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>--><!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rippleProgress

```TypeScript
rippleProgress : number
```

The ripple effect progress. The value must be greater than or equal to 0. Values less than 0 indicate no ripple effect.

**Type:** number

**Since:** 22

<!--Device-LiquidMaterialEffectParam-rippleProgress : double--><!--Device-LiquidMaterialEffectParam-rippleProgress : double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## tintColor

```TypeScript
tintColor : [number, number, number, number]
```

The overlay color of the material, where the four variables correspond to RGBA respectively. The value range for each is [0, 1]. Values less than 0 are treated as 0; values greater than 1 are treated as 1.

**Type:** [number, number, number, number]

**Since:** 22

<!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]--><!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
