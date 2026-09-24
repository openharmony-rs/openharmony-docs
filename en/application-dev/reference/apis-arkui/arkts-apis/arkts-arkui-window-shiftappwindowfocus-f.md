# shiftAppWindowFocus

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## shiftAppWindowFocus

```TypeScript
function shiftAppWindowFocus(sourceWindowId: number, targetWindowId: number): Promise<void>
```

Shifts the window focus from the source window to the target window in the same application. The window focus can be shifted within the main window and child windows. This API uses a promise to return the result.

Ensure that the target window can gain focus (configurable by calling [setWindowFocusable()](arkts-arkui-window-window-i.md#setwindowfocusable-1)) and that [showWindow()](arkts-arkui-window-window-i.md#showwindow) has been successfully executed.

> **NOTE:** 
> 
> Before calling **shiftAppWindowFocus()**, ensure that the target window has called
> [loadContent()](arkts-arkui-window-window-i.md#loadcontent)
> or [setUIContent()](arkts-arkui-window-window-i.md#setuicontent)
> and these operations have been effective. Otherwise, an invisible window may gain focus, causing function
> exceptions or affecting user experience.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceWindowId | number | Yes | ID of the source window, which is having the focus. You are advised to call [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window ID. |
| targetWindowId | number | Yes | ID of the target window. You are advised to call [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed; 2. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only main windows and subwindows are supported. 2. The two windows are not from the same process. |

**Examples**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // ...
    console.info('onWindowStageCreate');
    let mainWindow: window.Window | undefined = undefined;
    let subWindow: window.Window | undefined = undefined;
    let mainWindowId: number = -1;
    let subWindowId: number = -1;

    try {
      windowStage.loadContent('pages/Index', (err) => {
        if (err.code) {
          console.error(`Failed to load content for main window. Cause code: ${err.code}, message: ${err.message}`);
        }
        // Obtain the main window and ID of the application.
        windowStage.getMainWindow().then((data) => {
          if (data == null) {
            console.error('Failed to obtain the main window. Cause: The data is empty');
            return;
          }
          mainWindow = data;
          mainWindowId = mainWindow.getWindowProperties().id;
          console.info('Succeeded in obtaining the main window');
        }).catch((err: BusinessError) => {
          console.error(`Failed to obtain the main window. Cause code: ${err.code}, message: ${err.message}`);
        });

        // Create or obtain a child window and its ID. In this case, the child window has focus.
        windowStage.createSubWindow('testSubWindow').then((data) => {
          if (data == null) {
            console.error('Failed to obtain the sub window. Cause: The data is empty');
            return;
          }
          subWindow = data;
          subWindowId = subWindow.getWindowProperties().id;
          subWindow.resize(500, 500);
          subWindow.setUIContent('pages/Index');
          subWindow.showWindow();

          // Listen for the window status and ensure that the window is ready.
          subWindow.on("windowEvent", (windowEvent) => {
            if (windowEvent == window.WindowEventType.WINDOW_ACTIVE) {
              // Switch the focus.
              window.shiftAppWindowFocus(subWindowId, mainWindowId).then(() => {
                console.info('Succeeded in shifting app window focus');
              }).catch((err: BusinessError) => {
                console.error(`Failed to shift app window focus. Cause code: ${err.code}, message: ${err.message}`);
              });
            }
          });
        });
      });
    } catch (exception) {
      console.error(`Failed to shift app focus. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```
