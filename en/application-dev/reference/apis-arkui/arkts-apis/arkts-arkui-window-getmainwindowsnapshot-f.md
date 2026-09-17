# getMainWindowSnapshot

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## getMainWindowSnapshot

```TypeScript
function getMainWindowSnapshot(windowId: Array<number>, config: WindowSnapshotConfiguration):
    Promise<Array<image.PixelMap | undefined>>
```

Obtains the screenshots of one or more main windows specified by **windowId**. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.CUSTOM_SCREEN_CAPTURE

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | Array&lt;number&gt; | Yes | Array of main window IDs. These IDs can be obtained using [window.getAllMainWindowInfo()](arkts-arkui-window-getallmainwindowinfo-f.md). If the array is null or undefined, contains any negative number, includes duplicates, or has more than 512 entries, error code 401 is returned. If the array contains any positive ID that does not match an existing window, undefined is returned. |
| config | [WindowSnapshotConfiguration](arkts-arkui-window-windowsnapshotconfiguration-i.md) | Yes | Configuration for obtaining the window screenshot. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; undefined&gt;&gt; | Promise used to return an array of PixelMap objects of the screenshots, representing the screenshots, in the order of the provided window ID array. If a window ID is valid but the corresponding main window cannot be found, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, UIAbility, common, Permissions } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause: JSON.stringify(err)`);
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
          console.error(`Get main window snapshot failed. Error info: ${JSON.stringify(err)}`);
        });
      }).catch((err: BusinessError) => {
        console.error(`Get all main window info failed. Error info: ${JSON.stringify(err)}`);
      });
    } catch (err) {
      console.error(`Get all main window info failed. Cause info: ${JSON.stringify(err)}`);
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
        // User granted permission.
      } else {
        // User denied permission.
        return;
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to request permission from user. Code is ${err.code}, message is ${err.message}`);
  })
}
```
