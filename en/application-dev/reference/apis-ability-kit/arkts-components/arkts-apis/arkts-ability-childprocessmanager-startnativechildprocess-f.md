# startNativeChildProcess

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## startNativeChildProcess

```TypeScript
function startNativeChildProcess(entryPoint: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<number>
```

Starts a [native child process](../../../application-models/ability-terminology.md#native-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned.

> **NOTE:** 
> 
> The child process started by calling this API does not inherit the resources of the parent process. After the
> child process is created, its PID is returned, the dynamic link library file specified in the parameters is
> loaded, and the entry function of the child process is executed. Once the entry function is done, the child
> process is automatically destroyed. After the process that calls this API is destroyed, the created child process
> is also destroyed.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entryPoint | string | Yes | The symbol and entry function of the dynamic link library called in the child process are separated by a colon (:), for example, **libentry.so:Main**. |
| args | [ChildProcessArgs](arkts-ability-app-ability-childprocessargs-childprocessargs-i.md) | Yes | Parameters transferred to the child process. |
| options | [ChildProcessOptions](arkts-ability-app-ability-childprocessoptions-childprocessoptions-i.md) | No | Startup configuration of the child process. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the PID of the child process. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-too-many-child-processes) | The number of child processes exceeds the upper limit. |

**Examples**

```TypeScript
For details about the child process, see Child Process Development Guide (ArkTS) - Creating a Native Child Process That Supports Parameter Passing:
```

```TypeScript
Sample code for the main process is provided below. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```
