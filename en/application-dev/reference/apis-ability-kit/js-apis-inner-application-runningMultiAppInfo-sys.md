# RunningMultiAppInfo (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T12:03:17.761Z pushedAt=2026-09-05T10:47:30.867Z -->

Defines the runtime structural information of app multi-open, including the app bundle name, multi-open mode (app clone mode or multi-instance mode), and the corresponding running instance information. It applies to scenarios where the multi-open status of apps needs to be managed and monitored. For guides on app multi-open modes, see [Creating an App Clone](../../quick-start/app-clone.md) and [Creating Multiple App Instances](../../quick-start/multiInstance.md).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## How to Use

Obtain the information through [getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12) of appManager. This API queries the multi-open runtime information of an app by its bundle name. The returned RunningMultiAppInfo structure contains the multi-open mode ([MultiAppMode](js-apis-inner-application-multiAppMode-sys.md#multiappmode)) of the app and the corresponding running instance information: when the app is in app clone mode (APP_CLONE), the runningAppClones field returns the app clone information; when the app is in multi-instance mode (MULTI_INSTANCE), the runningMultiInstances field returns the multi-instance app information.

## RunningMultiAppInfo

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                     | Type  | Read-Only | Optional | Description      |
| ------------------------- | ------ | ---- | ---- | --------- |
| bundleName | string | No | No | Bundle name of the application.|
| mode | [MultiAppMode](js-apis-inner-application-multiAppMode-sys.md) | No | No | Multi-app mode.|
| runningAppClones | Array<[RunningAppClone](js-apis-inner-application-runningAppClone-sys.md)> | No | Yes | Information about application clones with the specific bundle name in the running state.|
| runningMultiInstances<sup>14+</sup> | Array<[RunningMultiInstanceInfo](js-apis-inner-application-runningMultiInstanceInfo-sys.md)> | No | Yes | Information about a multi-instance application with the specific bundle name in the running state.|

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  // Obtain the running state information of the multi-open app.
  appManager.getRunningMultiAppInfo(bundleName)
    .then((info: appManager.RunningMultiAppInfo) => {
      console.info(`getRunningMultiAppInfo success, data: ${JSON.stringify(info)}`);
    }).catch((err: BusinessError) => {
      console.error(`getRunningMultiAppInfo failed, code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  // Handle the input parameter error exception.
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getRunningMultiAppInfo error, code: ${code}, message: ${msg}`);
}
```
