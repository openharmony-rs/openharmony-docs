# resizeVirtualScreen (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## resizeVirtualScreen

```TypeScript
function resizeVirtualScreen(screenId:number, width: number, height: number): Promise<void>
```

Resizes the virtual screen. This API uses a promise to return the result.

**Since:** 24

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| screenId | number | Yes | ID of the virtual screen to be resized. The value is a positive integer within the range of [1000, 2147483647]. If the value is not within the valid range, error code 1400004 is returned. |
| width | number | Yes | New width of the virtual screen, in px. The value is a positive integer within the range of [1, 65536]. If the value is not within the valid range, error code 1400004 is returned. |
| height | number | Yes | New height of the virtual screen, in px. The value is a positive integer within the range of [1, 65536]. If the value is not within the valid range, error code 1400004 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the virtual screen ID from the return value of createVirtualScreen().
let screenId: number = 1000; // Virtual screen ID.
let width: number = 1920;
let height: number = 1080;
// Resize the virtual screen.
screen.resizeVirtualScreen(screenId, width, height).then(() => {
  console.info(`Succeeded in resizing virtual screen: screenId=${screenId}, width=${width}, height=${height}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to resize virtual screen. Code: ${err.code}, message: ${err.message}`);
});
```
