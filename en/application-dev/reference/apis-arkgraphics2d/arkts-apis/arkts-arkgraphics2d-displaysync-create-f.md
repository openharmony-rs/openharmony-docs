# create

## Modules to Import

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
function create(): DisplaySync
```

Creates a **DisplaySync** object, through which you can set the frame rate of the custom UI content.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.2.0.

<!--Device-displaySync-function create(): DisplaySync--><!--Device-displaySync-function create(): DisplaySync-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-displaysync-i.md) | **DisplaySync** object created. |

**Examples**

```TypeScript
// Create a DisplaySync object.
let backDisplaySync: displaySync.DisplaySync = displaySync.create();
```
