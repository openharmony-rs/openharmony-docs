# hasPrivateWindow (System API)

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## hasPrivateWindow

```TypeScript
function hasPrivateWindow(displayId: number): boolean
```

Checks whether there is a visible privacy window on a display. The window privacy mode can be set by calling setWindowPrivacyMode(). The content in the privacy window cannot be captured or recorded.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | ID of the display. The value must be an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether there is a visible privacy window on the display. **true** if yes, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
try {
  // Obtain the default Display object.
  displayClass = display.getDefaultDisplaySync();

  let hasPrivateWindow: boolean = false;
  try {
    // Check whether there is a privacy window on the default display.
    hasPrivateWindow = display.hasPrivateWindow(displayClass.id);
  } catch (exception) {
    console.error(`Failed to check has privateWindow or not. Code: ${exception.code}, message: ${exception.message}`);
  }
  if (hasPrivateWindow) {
    console.info('There has privateWindow.');
  } else if (!hasPrivateWindow) {
    console.info('There has no privateWindow.');
  }
} catch (exception) {
  console.error(`Failed to obtain the default display object. Code: ${exception.code}, message: ${exception.message}`);
}
```
