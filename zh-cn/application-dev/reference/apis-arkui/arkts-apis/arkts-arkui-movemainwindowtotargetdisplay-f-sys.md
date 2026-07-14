# moveMainWindowToTargetDisplay（系统接口）

## moveMainWindowToTargetDisplay

```TypeScript
function moveMainWindowToTargetDisplay(displayId: number, windowId: number): Promise<void>
```

将指定的主窗口迁移到指定的屏幕上。使用Promise异步回调。

- 对于[主屏](../../../../displaymanager/display-terminology.md#主屏)/
[扩展屏](../../../../displaymanager/display-terminology.md#扩展屏)与
[虚拟屏](../../../../displaymanager/display-terminology.md#虚拟屏)之间以及虚拟屏与虚拟屏之间的窗口迁移，仅主窗及其子窗会一起被迁移到对应屏幕上且被抬升，如果存在子窗，最上层可获焦子
窗会获取焦点，否则主窗口获焦。
- 对于主屏与扩展屏之间的窗口迁移，只会将主窗口迁移到对应屏幕，抬升并获取焦点。

<!--RP3--><!--RP3End-->

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 目标屏幕的ID，用于指定要迁移到的屏幕。该参数应为非负整数，可通过[getWindowProperties](arkts-arkui-window-i.md#getwindowproperties-1)接口获取到[properties](arkts-arkui-windowproperties-i.md)后，再通过properties.displayId获取；也可通过获取[Display](arkts-arkui-displaystate-e.md)对象的[id](../../../../reference/apis-arkui/js-apis-display.md#属性)属性获取此参数。 |
| windowId | number | 是 | 目标主窗口的ID，用于指定要迁移的窗口。该参数应为大于0的整数，通过[getWindowProperties](arkts-arkui-window-i.md#getwindowproperties-1)接口获取到[properties](arkts-arkui-windowproperties-i.md)后，再通过properties.id获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: The window is not found or has been destoryed. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: The window is not a main window. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | Invalid display. Possible cause:1. DisplayId is a negative number or not exist. |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { display, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  // ...
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err: BusinessError) => {
      if (err.code) {
        console.error(`Failed to load content for main window. Cause code: ${err.code}, message: ${err.message}`);
      }
      let displayClass: display.Display | null = null;
      displayClass = display.getDefaultDisplaySync();
      let mainWindow = windowStage.getMainWindowSync();
      try {
        window.moveMainWindowToTargetDisplay(displayClass.id, mainWindow.getWindowProperties().id).then(() => {
          console.info(`Succeeded in moving window id: ${mainWindow.getWindowProperties().id} to target display id: ${mainWindow.getWindowProperties().displayId}`);
        }).catch((err: BusinessError) => {
          console.error(`Failed to move window to target display. Cause code: ${err.code}, message: ${err.message}`);
        });
      } catch (exception) {
        console.error(`Failed to move window to target display. Cause code: ${exception.code}, message: ${exception.message}`);
      }
    });
  }
}

```

