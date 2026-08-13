# getLastWindow

## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void
```

获取当前应用内层级最高的子窗口，使用callback异步回调。 若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-window-i.md#showWindow)进行显示，则返回应用主 窗口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void--><!--Device-window-function getLastWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | Current application context. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | 是 | Callback used to return the top window obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. Top window or main window is null or destroyed; 2. This window context is abnormal. |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import common from '@ohos.app.ability.common';
import { LocalStorage } from '@ohos.arkui.stateManagement'

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
        if (err?.code) {
          console.error(`Failed to load content for main window. Cause code: ${err?.code}, message: ${err?.message}`);
        }
      // 创建子窗
      windowStage.createSubWindow('testSubWindow').then((subWindow: window.Window) => {
        let storage: LocalStorage = new LocalStorage();
        subWindow.loadContent('pages/Index', storage, (err: BusinessError): void => {
          subWindow.showWindow().then(() => {
            try{
              window.getLastWindow(this.context as common.UIAbilityContext, (err: BusinessError<void>|null, topWindow: window.Window|undefined) => {
                if (err?.code) {
                  console.error(`Failed to obtain the top window. Cause code: ${err?.code}, message: ${err?.message}`);
                } else {
                  console.info(`Succeeded in obtaining the top window. Window id: ${topWindow?.getWindowProperties().id}`);
                }
              });
            }catch(exception){
              let err = exception as BusinessError;
              console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
            }
          });
        });
      });
    });
  }
}
```


## getLastWindow

```TypeScript
function getLastWindow(ctx: BaseContext): Promise<Window>
```

获取当前应用内层级最高的子窗口，使用Promise异步回调。 若无应用子窗口或子窗口未调用[showWindow()](arkts-arkui-window-window-i.md#showWindow)进行显示，则返回应用主 窗口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getLastWindow(ctx: BaseContext): Promise<Window>--><!--Device-window-function getLastWindow(ctx: BaseContext): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 当前应用上下文信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise对象。返回当前应用内层级最高的窗口对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. Top window or main window is null or destroyed; 2. This window context is abnormal. |
| [1300006](../errorcode-window.md#1300006-窗口上下文异常) | This window context is abnormal. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import common from '@ohos.app.ability.common';
import { LocalStorage } from '@ohos.arkui.stateManagement'

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
        if (err?.code) {
          console.error(`Failed to load content for main window. Cause code: ${err?.code}, message: ${err?.message}`);
        }
      // 创建子窗
      windowStage.createSubWindow('testSubWindow').then((subWindow: window.Window) => {
        let storage: LocalStorage = new LocalStorage();
        subWindow.loadContent('pages/Index', storage, (err: BusinessError): void => {
          subWindow.showWindow().then(() => {
            try {
              window.getLastWindow(this.context as common.UIAbilityContext ).then((topWindow :window.Window | undefined ) => {
                let windowClass = topWindow;
                console.info(`Succeeded in obtaining the top window. Window id: ${topWindow?.getWindowProperties().id}`);
              }).catch((Err: Error) => {
                let err = Err as BusinessError;
                console.error(`Failed to obtain the top window. Cause code: ${err?.code}, message: ${err?.message}`);
              });
            } catch (exception) {
              let err = exception as BusinessError;
              console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
            }
          });
        });
      });
    });
  }
}
```

