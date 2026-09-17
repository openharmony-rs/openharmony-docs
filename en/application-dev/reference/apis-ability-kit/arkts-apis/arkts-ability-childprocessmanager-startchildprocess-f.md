# startChildProcess

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## startChildProcess

```TypeScript
function startChildProcess(srcEntry: string, startMode: StartMode): Promise<number>
```

Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 160 00061 is returned.

> **NOTE:** 
> 
> If the child process is created successfully, its PID is returned, and its
> [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart) function is executed. Once the
> function is done, the child process is automatically destroyed.
> 
> The child process started by calling this API does not support asynchronous ArkTS API calls. It supports only
> synchronous ArkTS API calls.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcEntry | string | Yes | Path of the source file of the child process relative to the root directory **src/main**. The source file can be stored only in the module of the entry type. For example, if the source file of a child process is **src/main/ets/process/DemoProcess.ets** in the entry module, then **srcEntry** is **./ets/process/ DemoProcess.ets**.<br>In addition, ensure that the source file of the child process is referenced by other files to prevent it from being optimized by the build tool. (For details, see the sample code below.) |
| startMode | [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | Yes | Start mode of the child process. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the PID of the child process. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-too-many-child-processes) | The number of child processes exceeds the upper limit. |

**Examples**

```TypeScript
// Create the DemoProcess.ets child process class under src/main/ets/process in the entry module.
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}
```

```TypeScript
// Start the child process by calling childProcessManager.startChildProcess.
// entry/src/main/ets/tool/Tool.ets
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

try {
  DemoProcess.toString(); // Call any API of the DemoProcess class to prevent the code from being directly optimized by the compiler because it is not being referenced.
  childProcessManager.startChildProcess("./ets/process/DemoProcess.ets", childProcessManager.StartMode.SELF_FORK)
    .then((data) => {
      console.info(`startChildProcess success, pid: ${data}`);
    }, (err: BusinessError) => {
      console.error(`startChildProcess error, errorCode: ${err.code}`);
    })
} catch (err: BusinessError) {
  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg: ${(err as BusinessError).message}.`);
}
```

```TypeScript
// Create the DemoProcess.ets child process class under src/main/ets/process in the entry module:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}
```

```TypeScript
// Start a child process by calling childProcessManager.startChildProcess:
// entry/src/main/ets/tool/Tool.ets
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

try {
  DemoProcess.toString(); // Call any API of the DemoProcess class to prevent the code from being directly optimized by the compiler because it is not being referenced.
  childProcessManager.startChildProcess("./ets/process/DemoProcess.ets", childProcessManager.StartMode.SELF_FORK, (err, data) => {
    if (err) {
      console.error(`startChildProcess error. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`startChildProcess success, pid: ${data}`);
    }
  });
} catch (err: BusinessError) {
  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg: ${(err as BusinessError).message}.`);
}
```


## startChildProcess

```TypeScript
function startChildProcess(srcEntry: string, startMode: StartMode, callback: AsyncCallback<number>): void
```

Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses an asynchronous callback to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 160 00061 is returned.

> **NOTE:** 
> 
> If the child process is created successfully, its PID is returned, and its
> [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart) function is executed. Once the
> function is done, the child process is automatically destroyed.
> 
> The child process started by calling this API does not support asynchronous ArkTS API calls. It supports only
> synchronous ArkTS API calls.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcEntry | string | Yes | Path of the source file of the child process relative to the root directory **src/main**. The source file can be stored only in the module of the entry type. For example, if the source file of a child process is **src/main/ets/process/DemoProcess.ets** in the entry module, then **srcEntry** is **./ets/process/ DemoProcess.ets**.<br>In addition, ensure that the source file of the child process is referenced by other files to prevent it from being optimized by the build tool. (For details, see the sample code below.) |
| startMode | [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | Yes | Start mode of the child process. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the subprocess is started, **err** is **undefined** and **data** is the PID of the child process. Otherwise, **data** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-too-many-child-processes) | The number of child processes exceeds the upper limit. |

**Examples**

See [startChildProcess](#startchildprocess)
