# getFoldStatus

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getFoldStatus

```TypeScript
function getFoldStatus(): FoldStatus
```

Obtains the fold status of this foldable device.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-display-function getFoldStatus(): FoldStatus--><!--Device-display-function getFoldStatus(): FoldStatus-End-->

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| [FoldStatus](arkts-arkui-display-foldstatus-e.md) | Fold status of the device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
let data: display.FoldStatus = display.getFoldStatus();
console.info(`Succeeded in obtaining fold status. Data: ${data}`);
```
