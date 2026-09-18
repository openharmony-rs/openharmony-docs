# getChildProcessInfos

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## getChildProcessInfos

```TypeScript
function getChildProcessInfos(): Promise<Array<ChildProcessInformation>>
```

Obtains the information about the child processes of the current application. This API uses a promise to return the result. The returned child processes include those created through [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md) (in APP_SPAWN_FORK mode), [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md), and [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md). [OH_Ability_CreateNativeChildProcess] [OH_Ability_CreateNativeChildProcessWithConfigs] [OH_Ability_StartNativeChildProcess] [OH_Ability_StartNativeChildProcessWithConfigs]

> **NOTE:** 
> 
> The child process started in SELF_FORK mode is not included in the returned list.
> If no child processes exist, an empty array is returned.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ChildProcessInformation](arkts-ability-childprocessmanager-childprocessinformation-t.md)&gt;&gt; | Promise used to return the information about the child processes of the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system service failed. |

**Examples**

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

childProcessManager.getChildProcessInfos().then((data) => {
  console.info(`getChildProcessInfos success, count: ${data.length}`);
  for (let info of data) {
    console.info(`pid: ${info.pid}, parentPid: ${info.parentPid}, processName: ${info.processName}`);
  }
}).catch((err: BusinessError) => {
  console.error(`getChildProcessInfos failed, code: ${err.code}, msg: ${err.message}`);
});
```
