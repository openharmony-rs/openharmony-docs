# WindowProxy

The proxy of the UIExtension window.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## hideNonSecureWindows

```TypeScript
hideNonSecureWindows(shouldHide: boolean): Promise<void>
```

Sets whether to hide non-secure windows. This API uses a promise to return the result.

> **NOTE:** 
> 
> - A non-secure window refers to any window that may obstruct the EmbeddedComponent or UIExtensionComponent, such as global floating windows , host subwindows, and dialog box windows created by the host application (excluding windows of these types created by system applications).
> 
> - When using the **EmbeddedComponent** or **UIExtensionComponent** to display sensitive information, call this API to hide non-secure windows and prevent information obstruction. Hidden non-secure windows will reappear when the **EmbeddedComponent** or **UIExtensionComponent** is hidden or destroyed.
> 
> - On PCs/2-in-1 devices, global floating windows within non-secure windows remain visible when
> **hideNonSecureWindows(true)** is called.

**Since:** 12

**Required permissions:** ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shouldHide | boolean | Yes | Whether to hide non-secure windows. The value **true** means to hide non-secure windows, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | Abnormal state. Possible causes: 1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS". 2. The UIExtension window proxy is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Hide non-secure windows.
    extensionHostWindow.hideNonSecureWindows(true).then(() => {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to hide the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
  }
  
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Unhide non-secure windows.
    extensionHostWindow.hideNonSecureWindows(false).then(() => {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to show the non-secure windows. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

Adds or deletes the watermark flag for this window. This API uses a promise to return the result.

> **NOTE:** 
> 
> With the watermark flag added, the watermark is applied on the full screen when the window is in the foreground
> , regardless of whether the window is displayed in full screen, floating, and split screen mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to add or delete the flag. The value **true** means to add the watermark flag, and **false** means to delete the watermark flag. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | The UIExtension window proxy is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal. |

**Examples**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Add the watermark flag.
    extensionHostWindow.setWaterMarkFlag(true).then(() => {
      console.info(`Succeeded in setting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to set water mark flag of window. Code: ${err.code}, message: ${err.message}`);
    });
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // Delete the watermark flag.
    extensionHostWindow.setWaterMarkFlag(false).then(() => {
      console.info(`Succeeded in deleting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to delete water mark flag of window. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```
