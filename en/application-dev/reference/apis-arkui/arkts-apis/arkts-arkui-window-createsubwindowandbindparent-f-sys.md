# createSubWindowAndBindParent (System API)

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## createSubWindowAndBindParent

```TypeScript
function createSubWindowAndBindParent(name: string, parentId: number, ctx: BaseContext,
    parentWindowEventListener: WindowEventListener): Promise<Window>
```

Create a subwindow with a specific name and bind parent. The parent window only supports main window. The subwindow follows the parent window to show/hide, but does not follow the parent window to destroy. The subwindow listens to the parent window lifecycle changes through the callback function.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates window name. |
| parentId | number | Yes | Indicates parent window id. The window id is a non-negative number and exists. |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Indicates the context on which the window depends. |
| parentWindowEventListener | [WindowEventListener](arkts-arkui-windoweventlistener-t.md) | Yes | Indicates the event listener of parent window. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | The interface for creating a window returns a promise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. This cannot work correctly due to limited device capabilities. |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. Possible cause: The window has been created and cannot be created again. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. Internal task error. 2. The number of windows has reached the limit. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. Possible cause: 1. The parent window does not exist or has been destroyed. 2. Invalid window type. Only main windows are supported. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    const parentWindowEventListener = (windowId: number, event: window.WindowEventType) => {
      // ...
    }
    try {
      // It is recommended that parentId be obtained using the getWindowProperties API. The following is only an example.
      let promise = window.createSubWindowAndBindParent('test', 100, this.context, parentWindowEventListener);
      promise.then((data) => {
        console.info('Succeeded in creating the window. Data:' + JSON.stringify(data));
        windowClass = data;
      }).catch((err: BusinessError) => {
        console.error(`Failed to create the Window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```
