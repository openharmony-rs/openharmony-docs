# findWindow

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## findWindow

```TypeScript
function findWindow(name: string): Window
```

Finds a window based on the name.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Window name. When searching for a child window or system window, use the window name in [Configuration](arkts-arkui-window-configuration-i.md). When searching for the main window, use [getWindowName](arkts-arkui-arkui-uicontext-uicontext-c.md#getwindowname) to obtain the window name of the current instance. |

**Return value:**

| Type | Description |
| --- | --- |
| [Window](arkts-arkui-window-window-i.md) | Window found. If the window with the specified name does not exist, error code 1300002 is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. |

**Examples**

```TypeScript
let windowClass: window.Window | undefined = undefined;
try {
  windowClass = window.findWindow('test');
} catch (exception) {
  console.error(`Failed to find the Window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
