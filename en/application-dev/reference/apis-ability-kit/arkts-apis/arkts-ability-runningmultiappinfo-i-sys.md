# RunningMultiAppInfo (System API)

```TypeScript
export interface RunningMultiAppInfo
```

Defines the structure information of application multi-app in the running state.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## mode

```TypeScript
mode: MultiAppMode
```

Multi-app mode.

**Type:** [MultiAppMode](arkts-ability-multiappmode-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## runningAppClones

```TypeScript
runningAppClones?: Array<RunningAppClone>
```

Information about application clones with the specific bundle name in the running state.

**Type:** Array&lt;[RunningAppClone](arkts-ability-runningappclone-i-sys.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## runningMultiInstances

```TypeScript
runningMultiInstances?: Array<RunningMultiInstanceInfo>
```

Information about a multi-instance application with the specific bundle name in the running state.

**Type:** Array&lt;[RunningMultiInstanceInfo](arkts-ability-runningmultiinstanceinfo-i-sys.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Examples**

```TypeScript
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
