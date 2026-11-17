# ImmersiveOptions (System API)

```TypeScript
interface ImmersiveOptions
```

Immersive material parameters.

**Since:** 26.0.0

<!--Device-uiMaterial-interface ImmersiveOptions--><!--Device-uiMaterial-interface ImmersiveOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## colorBlendMode

```TypeScript
colorBlendMode?: MaterialColorBlendMode
```

Material color blend mode. Default value: uiMaterial.MaterialColorBlendMode.LINEAR_MIX. Note: 1. This parameter takes effect only on the display effect of high- and medium- computing power devices that support immersive material.
2. **TINTED_GLASS** takes effect only on some components. Currently supported components include:
Button, Chip, ChipGroup, and Toggle. For other components, **TINTED_GLASS** does not take effect.

**Type:** [MaterialColorBlendMode](arkts-arkui-uimaterial-materialcolorblendmode-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImmersiveOptions-colorBlendMode?: MaterialColorBlendMode--><!--Device-ImmersiveOptions-colorBlendMode?: MaterialColorBlendMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
