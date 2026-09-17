# minimizeAllWithExclusion (System API)

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## minimizeAllWithExclusion

```TypeScript
function minimizeAllWithExclusion(displayId: number, excludeWindowId: number): Promise<void>
```

Minimizes all main windows on a display while keeping one window open. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | Display ID. The value must be an integer. Non-integer values are rounded down. |
| excludeWindowId | number | Yes | Window ID. You can call [getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window properties, in which **id** is the window ID. If the window ID is less than or equal to 0, or the window ID is null or undefined, error code [401](../../../reference/errorcode-universal.md#401-parameter-check-failed) is thrown. If the window ID is greater than 0 but does not exist, error code 1300002 is thrown. If the window ID is greater than 0 but the window exists on another display, all main windows on the specified display are minimized. The value must be an integer. Floating-point numbers are rounded down. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A nonsystem application calls a system API. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. Window is nullptr; 2. Failed to find specified window by id. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { display, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();
let excludeWindowId = 1;

try {
  let promise = window.minimizeAllWithExclusion(displayClass.id, excludeWindowId);
  promise.then(() => {
    console.info('Succeeded in minimizing all windows.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to minimize all windows. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to minimize all windows. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
