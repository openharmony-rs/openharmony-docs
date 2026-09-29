# LightEffectOptions

```TypeScript
interface LightEffectOptions
```

Provides the light sensing interaction feedback configuration for immersive materials. Light sensing interaction feedback refers to the visual effect of dynamic light changes on the surface of a material when a user interacts with a component through touch. The configuration is used to customize the color of the light sensing feedback.

**Since:** 26.0.0

<!--Device-uiMaterial-interface LightEffectOptions--><!--Device-uiMaterial-interface LightEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## color

```TypeScript
color?: ResourceColor
```

Custom color of the light sensing feedback.

Default value: **Color.White**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.White

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LightEffectOptions-color?: ResourceColor--><!--Device-LightEffectOptions-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
