# setMultiScreenMode (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## setMultiScreenMode

```TypeScript
function setMultiScreenMode(primaryScreenId: number, secondaryScreenId: number,
    secondaryScreenMode: MultiScreenMode): Promise<void>
```

Sets the display mode (mirror or extend) of the secondary screen. This API uses a promise to return the result. If both **primaryScreenId** and **secondaryScreenId** are set to **0**, the content is displayed only on the secondary screen.

**Since:** 13

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| primaryScreenId | number | Yes | ID of the primary screen. The value must be a non-negative integer. Floating- point numbers are rounded down. |
| secondaryScreenId | number | Yes | ID of the secondary screen. The value must be a non-negative integer. Floating- point numbers are rounded down. |
| secondaryScreenMode | [MultiScreenMode](arkts-arkui-screen-multiscreenmode-e-sys.md) | Yes | Display mode of the secondary screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let primaryScreenId: number = 0; // Primary screen ID.
let secondaryScreenId: number = 12; // Secondary screen ID.
let screenMode: screen.MultiScreenMode = screen.MultiScreenMode.SCREEN_MIRROR;
// Set the display mode of the secondary screen to mirror mode.
screen.setMultiScreenMode(primaryScreenId, secondaryScreenId, screenMode).then(() => {
  console.info('Succeeded in setting multi screen mode.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set multi screen mode. Code: ${err.code}, message: ${err.message}`);
});
```
