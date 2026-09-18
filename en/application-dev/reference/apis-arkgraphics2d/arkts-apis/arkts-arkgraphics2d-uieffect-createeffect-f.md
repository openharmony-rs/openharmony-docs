# createEffect

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createEffect

```TypeScript
function createEffect(): VisualEffect
```

Creates a VisualEffect instance for adding multiple VisualEffect effects to a component.

**Since:** 12

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | Returns a VisualEffect instance, which supports adding multiple VisualEffect effects. |

**Examples**

```TypeScript
// Create a VisualEffect instance
let visualEffect: uiEffect.VisualEffect = uiEffect.createEffect();
```
