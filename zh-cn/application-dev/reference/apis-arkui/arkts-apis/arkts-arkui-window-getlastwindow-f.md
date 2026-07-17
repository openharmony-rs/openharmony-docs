# getLastWindow

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void
```

获取当前应用内层级最高的子窗口，使用callback异步回调。

若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)进行显示，则返回应用主窗口。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void--><!--Device-window-function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | Current application context. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Window> | 是 | Callback used to return the top window obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. Top window or main window is null or destroyed;2. This window context is abnormal. |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |

**示例：**

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


## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext): Promise<Window>
```

获取当前应用内层级最高的子窗口，使用Promise异步回调。

若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-1)进行显示，则返回应用主窗口。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getLastWindow(ctx: BaseContext): Promise<Window>--><!--Device-window-function getLastWindow(ctx: BaseContext): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用上下文信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Window> | Promise对象。返回当前应用内层级最高的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. Top window or main window is null or destroyed;2. This window context is abnormal. |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |

**示例：**

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

