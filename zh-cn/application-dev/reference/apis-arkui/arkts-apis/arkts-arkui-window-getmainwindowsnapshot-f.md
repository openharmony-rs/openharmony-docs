# getMainWindowSnapshot

## getMainWindowSnapshot

```TypeScript
function getMainWindowSnapshot(windowId: Array<int>, config: WindowSnapshotConfiguration):
    Promise<Array<image.PixelMap | undefined>>
```

获取一个或多个指定windowId的主窗口截图，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CUSTOM_SCREEN_CAPTURE

<!--Device-window-function getMainWindowSnapshot(windowId: Array<int>, config: WindowSnapshotConfiguration):    Promise<Array<image.PixelMap | undefined>>--><!--Device-window-function getMainWindowSnapshot(windowId: Array<int>, config: WindowSnapshotConfiguration):    Promise<Array<image.PixelMap | undefined>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | Array&lt;int&gt; | 是 | 需要获取截图的主窗口ID列表。可通过 [window.getAllMainWindowInfo()](arkts-arkui-window-getallmainwindowinfo-f.md#getAllMainWindowInfo)获取到主窗口windowId。当windowId为null、undefined、小于0、存 在重复值或数量超过512个时，返回错误码401；当windowId大于0但不存在对应窗口时，返回undefined。 |
| config | [WindowSnapshotConfiguration](arkts-arkui-window-windowsnapshotconfiguration-i.md) | 是 | 获取窗口截图时的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;image.PixelMap \| undefined&gt;&gt; | Promise对象。截图的PixelMap列表，按传入的窗口ID数组的顺序排列。当窗口ID合法但无法找到对应的主窗口时 ，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, UIAbility, common, Permissions } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      }
      reqPermissionsFromUser(permissions, this.context);
      console.info('Success in loading the content');
    });
    try {
      let windowIds: number[] = [];
      let configs: window.WindowSnapshotConfiguration = {
        useCache: false
      }
      let windowInfoPromise = window.getAllMainWindowInfo();
      windowInfoPromise.then((mainWindowInfoList: Array<window.MainWindowInfo>) => {
        for (let i = 0; i < mainWindowInfoList.length; i++) {
          windowIds[i] = mainWindowInfoList[i].windowId;
        }
        let promise = window.getMainWindowSnapshot(windowIds, configs);
        promise.then((list: Array<image.PixelMap | undefined>) => {
          for (let i = 0; i < list.length; i++) {
            console.info(`Get main window snapshot, getBytesNumberPerRow: ${list[i]?.getBytesNumberPerRow()}`);
          }
        }).catch((err: BusinessError) => {
          console.error(`Get main window snapshot failed. Cause code: ${err.code}, message: ${err.message}`);
        });
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

ArkTS-Sta示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, UIAbility, common, Permissions } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err: BusinessError<void> | null): void => {
      if (err?.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
      }
      reqPermissionsFromUser(permissions, this.context);
      console.info('Success in loading the content');
    });
    try {
      let windowIds: int[] = [];
      let configs: window.WindowSnapshotConfiguration = {
        useCache: false
      }
      let windowInfoPromise = window.getAllMainWindowInfo();
      windowInfoPromise.then((mainWindowInfoList: Array<window.MainWindowInfo>) => {
        for (let i = 0; i < mainWindowInfoList.length; i++) {
          windowIds[i] = mainWindowInfoList[i].windowId;
        }
        let promise = window.getMainWindowSnapshot(windowIds, configs);
        promise.then((list: Array<image.PixelMap | undefined>) => {
          for (let i = 0; i < list.length; i++) {
            console.info(`Get main window snapshot, getBytesNumberPerRow: ${list[i]?.getBytesNumberPerRow()}`);
          }
        }).catch((err: Error) => {
          console.error(`Get main window snapshot failed. Cause code: ${err.code}, message: ${err.message}`);
        });
      }).catch((err: Error) => {
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
  atManager.requestPermissionsFromUser(context, permissions).then((data: PermissionRequestResult): void => {
    console.info('requestPermissionsFromUser');
    let grantStatus: Array<int> = data.authResults;  
    let length: number = grantStatus.length;
    for (let i = 0; i < length; i++) {
      if (grantStatus[i] === 0) {
        // 用户授权
      } else {
        // 用户拒绝授权
        return;
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to request permission from user. Code is ${err.code}, message is ${err.message}`);
  })
}
```

