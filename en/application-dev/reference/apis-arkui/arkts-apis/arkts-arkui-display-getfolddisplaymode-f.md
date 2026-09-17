# getFoldDisplayMode

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getFoldDisplayMode

```TypeScript
function getFoldDisplayMode(): FoldDisplayMode
```

Obtains the display mode of this foldable device.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md) | Display mode of the foldable device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
let data: display.FoldDisplayMode = display.getFoldDisplayMode();
console.info(`Succeeded in obtaining fold display mode. Data: ${data}`);
```
