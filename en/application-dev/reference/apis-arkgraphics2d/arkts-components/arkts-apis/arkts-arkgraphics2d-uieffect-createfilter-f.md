# createFilter

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createFilter

```TypeScript
function createFilter(): Filter
```

Creates a Filter instance for adding multiple filter effects to a component.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns a Filter instance, which supports adding multiple filter effects. |

**Examples**

```TypeScript
// Create a Filter instance
let filter: uiEffect.Filter = uiEffect.createFilter();
```
