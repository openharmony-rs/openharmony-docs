# getChildProcessInfos

## 导入模块

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## getChildProcessInfos

```TypeScript
function getChildProcessInfos(): Promise<Array<ChildProcessInformation>>
```

获取当前应用的所有子进程信息，使用Promise异步回调。包括通过以下方式启动的子进程：[startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md) (在APP_SPAWN_FORK模式)，[startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md)，以及[startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md).【OH_Ability_CreateNativeChildProcess】【OH_Ability_CreateNativeChildProcessWithConfigs】【OH_Ability_StartNativeChildProcess】【OH_Ability_StartNativeChildProcessWithConfigs】

> **说明：** 
> 
> 
> 在返回的列表中不包含在以FORK方式启动的子进程。
> 如果不存在子进程，则返回空数组。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-childProcessManager-function getChildProcessInfos(): Promise<Array<ChildProcessInformation>>--><!--Device-childProcessManager-function getChildProcessInfos(): Promise<Array<ChildProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ChildProcessInformation](arkts-ability-childprocessmanager-childprocessinformation-t.md)&gt;&gt; | Promise返回当前应用的子进程信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system service failed. |

**示例**

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
