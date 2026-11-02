# RunningAppClone (System API)

```TypeScript
export interface RunningAppClone
```

The RunningAppClone module defines the information of an application clone in the running state.

**Since:** 12

<!--Device-unnamed-export interface RunningAppClone--><!--Device-unnamed-export interface RunningAppClone-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## How to Use

The RunningAppClone struct is obtained from [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md) of **appManager**.

## appCloneIndex

```TypeScript
appCloneIndex: number
```

Index of the app clone, used to identify different clone instances. The index starts from 0 and increments in the order in which clones are created. 0 indicates the primary app instance, and 1 or greater indicates a clone instance.

**Type:** number

**Since:** 12

<!--Device-RunningAppClone-appCloneIndex: int--><!--Device-RunningAppClone-appCloneIndex: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pids

```TypeScript
pids: Array<number>
```

Set of process IDs of the application, including the process IDs of all running processes of the application. An application may run multiple processes, so an array is returned.

**Type:** Array&lt;number&gt;

**Since:** 12

<!--Device-RunningAppClone-pids: Array<int>--><!--Device-RunningAppClone-pids: Array<int>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 12

<!--Device-RunningAppClone-uid: int--><!--Device-RunningAppClone-uid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

<!--Del-->
**Examples**

```TypeScript
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

<!--DelEnd-->
