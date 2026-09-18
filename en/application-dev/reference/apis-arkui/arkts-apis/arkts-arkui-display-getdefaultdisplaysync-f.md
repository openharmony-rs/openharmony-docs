# getDefaultDisplaySync

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getDefaultDisplaySync

```TypeScript
function getDefaultDisplaySync(): Display
```

Obtains the **Display** object of the screen where the application is located. If multiple abilities of an application are on different screens, the **Display** object of the main screen is returned. If multiple abilities of an application are on the same screen, the **Display** object of the screen is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Display](arkts-arkui-display-display-i.md) | Default Display object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. Possible cause: Display is not created or destroyed. |

**Examples**

```TypeScript
let displayClass: display.Display | null = null;
try {
  displayClass = display.getDefaultDisplaySync();
} catch (exception) {
  console.error(`Failed to get default display. Code: ${exception.code}, message: ${exception.message}`);
}
```
