# getAllMainWindowInfo

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## getAllMainWindowInfo

```TypeScript
function getAllMainWindowInfo(): Promise<Array<MainWindowInfo>>
```

获取全部主窗口信息，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CUSTOM_SCREEN_CAPTURE

<!--Device-window-function getAllMainWindowInfo(): Promise<Array<MainWindowInfo>>--><!--Device-window-function getAllMainWindowInfo(): Promise<Array<MainWindowInfo>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[MainWindowInfo](arkts-arkui-window-mainwindowinfo-i.md)&gt;&gt; | Promise对象。返回主窗口信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, UIAbility, common, Permissions } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      reqPermissionsFromUser(permissions, this.context);
      console.info('Succeeded in loading the content');
    });
    try {
      let windowInfoPromise = window.getAllMainWindowInfo();
      windowInfoPromise.then((list: Array<window.MainWindowInfo>) => {
        console.info('Get all main window info success.');
      }).catch((err: BusinessError) => {
        console.error(`Get all main window info failed. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (err) {
      console.error(`Get all main window info failed. Cause code: ${err.code}, message: ${err.message}`);
    }
  }
}

const permissions: Array<Permissions> = ['ohos.permission.CUSTOM_SCREEN_CAPTURE'];
function reqPermissionsFromUser(permissions: Array<Permissions>, context: common.UIAbilityContext): void {
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  atManager.requestPermissionsFromUser(context, permissions).then((data) => {
    console.info('requestPermissionsFromUser');
    let grantStatus: Array<number> = data.authResults;
    let length: number = grantStatus.length;
    for (let i = 0; i < length; i++) {
      if (grantStatus[i] === 0) {
        // 用户授权
      } else {
        // 用户拒绝授权
        return;
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to request permission from user. Code is ${err.code}, message is ${err.message}`);
  })
}
```

