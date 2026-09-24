# setWindowPosition

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## setWindowPosition

```TypeScript
function setWindowPosition(list: Array<WindowPositionParams>): Promise<void>
```

Adjusts the position of one or more main windows in the current application process. This API uses a promise to return the result.

The supported adjustments are as follows:  
- Place a main window below another main window.  
- Place a main window at the bottom of all application windows.  
- Place a main window at the top of all application windows.  
- Toggle a main window to the global topmost state or cancel the global topmost state.

Setting the global topmost state requires the ohos.permission.WINDOW_TOPMOST permission.

**Since:** 26.0.1

**Required permissions:** ohos.permission.WINDOW_TOPMOST

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| list | Array&lt;[WindowPositionParams](arkts-arkui-window-windowpositionparams-i.md)&gt; | Yes | List of window position options to adjust. The list must not be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window to be adjusted cannot be found: not created, has been destroyed or not belong to current process; 2. The target main window specified by insertAfter cannot be found: not created, has been destroyed or not belong to current process; |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |
