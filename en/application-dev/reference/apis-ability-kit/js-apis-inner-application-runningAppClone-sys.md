# RunningAppClone (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T12:03:10.411Z pushedAt=2026-09-05T10:47:30.862Z -->

Defines the structural information of an app clone in the running state, which is contained in [RunningMultiAppInfo](js-apis-inner-application-runningMultiAppInfo-sys.md). Through this struct, you can obtain information such as the index, UID, and process ID of the app clone. It applies to scenarios where app clones need to be distinguished and managed, facilitating application isolation and resource management for system-level applications.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## How to Use

The RunningAppClone struct is obtained from [getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12) of **appManager**.

## RunningAppClone

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                     | Type  | Read-Only | Optional | Description      |
| ------------------------- | ------ | ---- |  ---- | --------- |
| appCloneIndex | number | No  | No  | Index of the app clone, used to identify different clone instances. The index starts from 0 and increments in the order in which clones are created. 0 indicates the primary app instance, and 1 or greater indicates a clone instance. |
| uid | number | No  | No  | UID of the application. |
| pids | Array\<number> | No  | No  | Set of process IDs of the application, including the process IDs of all running processes of the application. An application may run multiple processes, so an array is returned. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName: string = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      hilog.info(0x0000, 'testTag', `getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err: BusinessError) {
  hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
}
```
