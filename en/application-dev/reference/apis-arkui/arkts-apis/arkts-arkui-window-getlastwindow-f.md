# getLastWindow

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void
```

Obtains the topmost layer child window of the current application. This API uses an asynchronous callback to return the result.

If no child window exists or the child window is not displayed by calling [showWindow()](arkts-arkui-window-window-i.md#showwindow), the main window of the application is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current application context. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the top window obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. Top window or main window is not created or destroyed; 2. Stage mode without context. |
| [1300006](../errorcode-window.md#1300006-abnormal-window-context) | This window context is abnormal. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.loadContent('pages/Index', (err: BusinessError) => {
      if (err.code) {
        console.error(`Failed to load content for main window. Cause code: ${err.code}, message: ${err.message}`);
      }
      windowStage.createSubWindow('TestSubWindow').then((subWindow) => {
        let storage: LocalStorage = new LocalStorage();
        subWindow.loadContent('pages/Index', storage, (err: BusinessError) => {
          if (err.code) {
            console.error(`Failed to load content for sub window. Cause code: ${err.code}, message: ${err.message}`);
          }
          subWindow.showWindow().then(() => {
            try {
              window.getLastWindow(this.context, (err: BusinessError, data) => {
                const errCode: number = err.code;
                if (errCode) {
                  console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
                  return;
                }
                windowClass = data;
                console.info(`Succeeded in obtaining the top window. Window id: ${windowClass.getWindowProperties().id}`);
              });
            } catch (exception) {
              console.error(`Failed to obtain the top window. Cause code: ${exception.code}, message: ${exception.message}`);
            }
          });
        });
      });
    });
  }
  // ...
}
```

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    windowStage.loadContent('pages/Index', (err: BusinessError) => {
      if (err.code) {
        console.error(`Failed to load content for main window. Cause code: ${err.code}, message: ${err.message}`);
      }
      windowStage.createSubWindow('TestSubWindow').then((subWindow) => {
        let storage: LocalStorage = new LocalStorage();
        subWindow.loadContent('pages/Index', storage, (err: BusinessError) => {
          if (err.code) {
            console.error(`Failed to load content for sub window. Cause code: ${err.code}, message: ${err.message}`);
          }
          subWindow.showWindow().then(() => {
            try {
              window.getLastWindow(this.context).then((topWindow) => {
                windowClass = topWindow;
                console.info(`Succeeded in obtaining the top window. Window id: ${topWindow.getWindowProperties().id}`);
              }).catch((err: BusinessError) => {
                console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
              });
            } catch (exception) {
              console.error(`Failed to obtain the top window. Cause code: ${exception.code}, message: ${exception.message}`);
            }
          });
        });
      });
    });
  }
  // ...
}
```


## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext): Promise<Window>
```

Obtains the topmost layer child window of the current application. This API uses a promise to return the result.

If no child window exists or the child window is not displayed by calling [showWindow()](arkts-arkui-window-window-i.md#showwindow), the main window of the application is returned.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current application context. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the topmost layer window obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. Top window or main window is not created or destroyed; 2. Stage mode without context. |
| [1300006](../errorcode-window.md#1300006-abnormal-window-context) | This window context is abnormal. |

**Examples**

See [getLastWindow](#getlastwindow)
