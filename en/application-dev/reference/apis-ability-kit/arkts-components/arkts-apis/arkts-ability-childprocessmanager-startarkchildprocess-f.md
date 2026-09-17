# startArkChildProcess

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## startArkChildProcess

```TypeScript
function startArkChildProcess(srcEntry: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<number>
```

Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned.

> **NOTE:** 
> 
> The child process started by calling this API does not inherit the resources of the parent process. If the child
> process is created successfully, its PID is returned, and its
> [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart) function is executed. After the
> function is done, the child process is not automatically destroyed. Instead, it must be destroyed by calling
> [process.abort](../../apis-arkts/arkts-apis/arkts-arkts-process-abort-f.md). After the process that calls this API is destroyed, the
> created child process is also destroyed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcEntry | string | Yes | Path of the source file of the child process relative to the root directory **src/main**. The source file cannot be stored in the module of the HAR type. The value consists of a module name, a slash (/), and a file path. For example, if the child process file is **src/main/ets/process/DemoProcess.ets** in module1, then **srcEntry** is **module1/ets/process/DemoProcess.ets**.<br>In addition, ensure that the source file of the child process is referenced by other files to prevent it from being optimized by the build tool. (For details, see the sample code below.) |
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
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-too-many-child-processes) | The number of child processes exceeds the upper limit.<br>**Applicable version:** 13 and later |

**Examples**

```TypeScript
Sample code for the child process:
```

```TypeScript
Sample code for the main process is provided below. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```
