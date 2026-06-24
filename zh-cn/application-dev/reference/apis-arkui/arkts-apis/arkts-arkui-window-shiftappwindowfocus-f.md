# shiftAppWindowFocus

## shiftAppWindowFocus

```TypeScript
function shiftAppWindowFocus(sourceWindowId: number, targetWindowId: number): Promise<void>
```

在同应用内将窗口焦点从源窗口转移到目标窗口，仅支持应用主窗、子窗范围内的焦点转移。使用Promise异步回调。

目标窗口需确保具有获得焦点的能力（可通过
[setWindowFocusable()](arkts-arkui-window-window-i.md#setWindowFocusable-2)
设置），并确保调用[showWindow()](arkts-arkui-window-window-i.md#showWindow-1)成功且执行完毕。

> **说明：**
>
> 在调用shiftAppWindowFocus()前，建议确保目标窗口已调用
> [loadContent()](arkts-arkui-window-window-i.md#loadContent-1)
> 或[setUIContent()](arkts-arkui-window-window-i.md#setUIContent-1)并生效，
> 否则可能会导致不可见窗口获取焦点，造成功能异常或影响用户体验。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceWindowId | number | 是 | 源窗口id，必须是获焦状态。推荐使用<br/>[getWindowProperties()](arkts-arkui-window-window-i.md#getWindowProperties-1)方法获取窗口id属性。 |
| targetWindowId | number | 是 | 目标窗口id。推荐使用<br/>[getWindowProperties()](arkts-arkui-window-window-i.md#getWindowProperties-1)方法获取窗口id属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal.<br/>Possible cause: 1. The window is not created or destroyed;<br/>2. Internal task error. |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally. |
| [1300004](../../errorcode-universal.md#1300004-Unauthorized) | Unauthorized operation.<br/>Possible cause: 1. Invalid window type. Only main windows and subwindows are supported.<br/>2. The two windows are not from the same process. |

**示例：**

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
        // 获取应用主窗及ID
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

        // 创建或获取子窗及ID，此时子窗口获焦
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

          // 监听Window状态，确保已经就绪
          subWindow.on("windowEvent", (windowEvent) => {
            if (windowEvent == window.WindowEventType.WINDOW_ACTIVE) {
              // 切换焦点
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

