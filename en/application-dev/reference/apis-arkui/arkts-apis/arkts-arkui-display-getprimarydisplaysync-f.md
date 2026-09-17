# getPrimaryDisplaySync

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getPrimaryDisplaySync

```TypeScript
function getPrimaryDisplaySync(): Display
```

Obtains the information about the primary display. For devices other than 2-in-1 devices, the Display object obtained is the built-in screen. For 2-in-1 devices with an external screen, the Display object obtained is the primary screen. For 2-in-1 devices without an external screen, the Display object obtained is the built-in screen.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Display](arkts-arkui-display-display-i.md) | Display object of the primary screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. Possible cause: Invalid display id. |

**Examples**

```TypeScript
let displayClass: display.Display | null = null;

displayClass = display.getPrimaryDisplaySync();
```
