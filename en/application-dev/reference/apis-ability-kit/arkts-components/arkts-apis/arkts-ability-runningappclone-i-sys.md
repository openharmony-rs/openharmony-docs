# RunningAppClone (System API)

```TypeScript
export interface RunningAppClone
```

The RunningAppClone module defines the information of an application clone in the running state.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## appCloneIndex

```TypeScript
appCloneIndex: number
```

Index of an application clone.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pids

```TypeScript
pids: Array<number>
```

Process ID set of the application.

**Type:** Array&lt;number&gt;

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

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
