# RunningMultiInstanceInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel; @Luobniz21-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8e4ee7947dfeb3a89be0dfff4e576f69a510a94f translatedAt=2026-09-03T12:03:40.482Z pushedAt=2026-09-05T10:47:30.864Z -->

Defines the runtime state structure information of a multi-instance application, including the instance identifier, application UID, and process ID. It is obtained through [getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12) of appManager, and is used to monitor and manage the runtime state of multi-instance applications. For details about the development guide for application multi-instance, see [Creating a Multi-instance Application](../../quick-start/multiInstance.md).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## RunningMultiInstanceInfo

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                     | Type  | Read-Only| Optional | Description      |
| ------------------------- | ------ | ---- | ---- | --------- |
| instanceKey | string | No| No | Unique instance ID of a multi-instance application.|
| uid | number | No | No | UID of the application. |
| pids | Array\<number> | No| No | Process ID set of the application.|

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      console.info(`getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      console.error(`getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    });
} catch (err: BusinessError) {
  console.error(`getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
}
```
