# addVirtualScreenBlocklist (System API)

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## addVirtualScreenBlocklist

```TypeScript
function addVirtualScreenBlocklist(windowIds: Array<number>): Promise<void>
```

Adds windows to the list of windows that are not allowed to be displayed during casting. This API takes effect only for the main window of an application or system windows. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowIds | Array&lt;number&gt; | Yes | List of window IDs. If a child window ID is passed in, it will not take effect. The window ID is an integer greater than 0. You are advised to call getWindowProperties() to obtain the window ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { display, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage) {
    // ...
    let windowId = windowStage.getMainWindowSync().getWindowProperties().id; // Obtain the window IDs.
    let windowIds = [windowId];

    // Add windows to the list of windows that are not allowed to be displayed during casting.
    let promise = display.addVirtualScreenBlocklist(windowIds);
    promise.then(() => {
      console.info('Succeeded in adding virtual screen blocklist.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to add virtual screen blocklist. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```
