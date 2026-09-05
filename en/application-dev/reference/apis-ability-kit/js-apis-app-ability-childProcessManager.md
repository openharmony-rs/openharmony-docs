# @ohos.app.ability.childProcessManager (Child Process Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f0ca4679538114d37c428618ebeb98dcc5067c5b translatedAt=2026-09-03T10:08:41.384Z pushedAt=2026-09-05T10:47:30.354Z -->

The childProcessManager module provides the child process management capability. Currently, it provides APIs to create and start a child process

The created child process will exit when the parent process exits and cannot run independently.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Constraints

### Functional Limitations

- The created child process does not support creating a UI.
- The created child process does not support API calls that depend on Context (including the APIs of the Context module itself and APIs that take a Context instance as an input parameter).
- Child processes can be created only in the main process. A child process does not support creating child processes again.

### Specification Limits

- A maximum of 512 child processes can be started by using the APIs of this module and the APIs defined in [native_child_process.h](capi-native-child-process-h.md) (as long as system resources are sufficient). The child processes started by [startChildProcess](#childprocessmanagerstartchildprocess) in SELF_FORK mode are not counted.

## Modules to Import

```ts
import { childProcessManager } from '@kit.AbilityKit';
```

## StartMode

Enumerates the child process start modes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                      | Value                            | Description                             |
| --------                     |  -----------------               |  -----------------               |
| SELF_FORK |  0   | The child process is forked from the application process. The child process started in this mode inherits the resources of the parent process and cannot use Binder IPC to communicate with other processes. Otherwise, the child process will crash.|
| APP_SPAWN_FORK |  1   | The child process is forked from AppSpawn. The child process started in this mode does not inherit the resources of the parent process and can use Binder IPC to communicate with other processes.|

## childProcessManager.startChildProcess

startChildProcess(srcEntry: string, startMode: StartMode): Promise&lt;number&gt;

Starts an [ArkTS child process](../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result.

> **NOTE**
> 
> If the child process is created successfully, its PID is returned, and its [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) function is executed. Once the function is done, the child process is automatically destroyed.
>
> The child process started by calling this API does not support asynchronous ArkTS API calls. It supports only synchronous ArkTS API calls.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 16000061 is returned.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | srcEntry | string | Yes | Path of the child process source file. Only source files in the entry-type module are supported, with src/main as the root directory. For example, if the child process file is at src/main/ets/process/DemoProcess.ets in the entry module, srcEntry is "./ets/process/DemoProcess.ets".<br>In addition, ensure that the child process source file is referenced by other files to prevent it from being optimized out by the build tool. (See the example code below for details.) |
  | startMode | [StartMode](#startmode) | Yes | Startup mode of the child process. SELF_FORK (value 0): forks the child process from the app's own process, inherits the parent process resources, and cannot use Binder IPC to communicate with other processes; otherwise, the child process crashes and exits. APP_SPAWN_FORK (value 1): forks the child process from AppSpawn, does not inherit the parent process resources, and can use Binder IPC to communicate with other processes. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the PID of the child process.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16000050 | Internal error. |
| 16000061  | Operation not supported. |
| 16000062  | The number of child processes exceeds the upper limit. |

**Example**

```ts
// Create the DemoProcess.ets child process class under src/main/ets/process in the entry module.
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}
```

<!--code_no_check-->
```ts
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

## childProcessManager.startChildProcess

startChildProcess(srcEntry: string, startMode: StartMode, callback: AsyncCallback&lt;number&gt;): void

Starts an [ArkTS child process](../../application-models/ability-terminology.md#arkts-child-process). This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> If the child process is created successfully, its PID is returned, and its [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) function is executed. Once the function is done, the child process is automatically destroyed.
>
> The child process started by calling this API does not support asynchronous ArkTS API calls. It supports only synchronous ArkTS API calls.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 16000061 is returned.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | srcEntry | string | Yes | Path of the child process source file. Only source files in a module of the entry type are supported, with src/main as the root directory. For example, if the child process file is at src/main/ets/process/DemoProcess.ets in the entry module, srcEntry is "./ets/process/DemoProcess.ets".<br>In addition, ensure that the child process source file is referenced by other files to prevent it from being optimized out by the build tool. (For details, see the example code below.) |
  | startMode | [StartMode](#startmode) | Yes | Start mode of the child process. SELF_FORK (value 0): forks the child process from the app's own process, inherits the parent process resources, and cannot use Binder IPC to communicate with other processes; otherwise, the child process crashes and exits. APP_SPAWN_FORK (value 1): forks the child process from AppSpawn, does not inherit the parent process resources, and can use Binder IPC to communicate with other processes. |
  | callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the result. If the subprocess is started, **err** is **undefined** and **data** is the PID of the child process. Otherwise, **err** is an error object.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16000050 | Internal error. |
| 16000061  | Operation not supported. |
| 16000062  | The number of child processes exceeds the upper limit. |

**Example**

```ts
// Create the DemoProcess.ets child process class under src/main/ets/process in the entry module:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}
```

<!--code_no_check-->
```ts
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

## childProcessManager.startArkChildProcess<sup>12+</sup>

startArkChildProcess(srcEntry: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise&lt;number&gt;

Starts an [ArkTS child process](../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result.


> **NOTE**
>
> The child process created by calling this API does not inherit the resources of the parent process. If the child process is created successfully, its PID is returned, and its [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) function is executed. After the [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) function is executed, the child process is not automatically destroyed. The child process needs to call [process.abort](../apis-arkts/js-apis-process.md#processabort) to destroy itself. After the process that calls this API is destroyed, the created child process is also destroyed.
> The child process created by calling this API supports asynchronous ArkTS API calls.


**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | srcEntry | string | Yes | Path of the child process source file. The source file cannot be placed in a HAR-type module. The path consists of "module name" + "/" + "file path", with src/main as the root directory. For example, if the child process file is at src/main/ets/process/DemoProcess.ets in the module1 module, srcEntry is "module1/ets/process/DemoProcess.ets".<br>In addition, ensure that the child process source file is referenced by other files to prevent it from being optimized out by the build tool (see the example code below). |
  | args | [ChildProcessArgs](js-apis-app-ability-childProcessArgs.md) | Yes | Parameters passed to the child process. The object contains entryParams (string type, parameters passed to the child process) and fds (a set of file descriptor handles used for communication between the parent process and the child process). |
  | options | [ChildProcessOptions](js-apis-app-ability-childProcessOptions.md) | No | Startup configuration options of the child process. The object contains properties such as isolationMode (whether to enable the isolation mode). If this parameter is not passed, the default configuration in [ChildProcessOptions](js-apis-app-ability-childProcessOptions.md) is used. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the PID of the child process.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |
| 16000061  | Operation not supported. |
| 16000062  | The number of child processes exceeds the upper limit. <br>Applicable version: 13+ |

**Example**

Sample code for the child process:

```ts
// Create the DemoProcess.ets child process class under src/main/ets/process of the module1 module:
// module1/src/main/ets/process/DemoProcess.ets
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ..
  }
}
```

Sample code for the main process is provided below. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->
```ts
// Use the childProcessManager.startArkChildProcess method to start a child process:
// module1/src/main/ets/tool/Tool.ets
import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              DemoProcess.toString(); // Call any API of the DemoProcess class to prevent the code from being directly optimized by the compiler because it is not being referenced.
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
              let path = context.filesDir + "/test.txt";
              let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
              let args: ChildProcessArgs = {
                entryParams: "testParam",
                fds: {
                  "key1": file.fd
                }
              };
              let options: ChildProcessOptions = {
                isolationMode: false
              };
              childProcessManager.startArkChildProcess("module1/ets/process/DemoProcess.ets", args, options)
                .then((pid) => {
                  console.info(`startArkChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startArkChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                })
            } catch (err: BusinessError) {
              console.error(`startArkChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## childProcessManager.startNativeChildProcess<sup>13+</sup>

startNativeChildProcess(entryPoint: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise&lt;number&gt;

Starts a [native child process](../../application-models/ability-terminology.md#native-child-process). This API uses a promise to return the result.

**Usage scenarios**
- Requires high-performance C/C++ computing tasks.
- Requires integration with existing C/C++ code libraries or third-party libraries.
- Requires high-performance data processing, image processing, audio/video encoding and decoding, etc.

> **NOTE**
> 
> The child process started by calling this API does not inherit the resources of the parent process. After the child process is created, its PID is returned, the dynamic link library file specified in the parameters is loaded, and the entry function of the child process is executed. Once the entry function is done, the child process is automatically destroyed. After the process that calls this API is destroyed, the created child process is also destroyed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device Behavior Differences**: Starting from API version 13, this API can be called normally on PC/2in1 devices, and returns error code 801 on other device types. Starting from API version 14, this API can be called normally on PC/2in1 and Tablet devices, and returns error code 801 on other device types.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | entryPoint | string | Yes| The symbol and entry function of the dynamic link library called in the child process are separated by a colon (:), for example, **libentry.so:Main**.|
  | args | [ChildProcessArgs](js-apis-app-ability-childProcessArgs.md) | Yes | Parameters passed to the child process. The object contains entryParams (string type, parameters passed to the child process) and fds (a set of file descriptor handles used for communication between the main process and the child process). |
  | options | [ChildProcessOptions](js-apis-app-ability-childProcessOptions.md) | No | Startup configuration options of the child process. The object contains properties such as isolationMode (whether to enable the isolation mode). If this parameter is not passed, the default configuration in [ChildProcessOptions](js-apis-app-ability-childProcessOptions.md) is used. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the PID of the child process.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 16000050 | Internal error. |
| 16000061  | Operation not supported. |
| 16000062  | The number of child processes exceeds the upper limit. |

**Example**

For details about the child process, see [Child Process Development Guide (ArkTS) - Creating a Native Child Process That Supports Parameter Passing](../../application-models/arkts-child-process-development-guideline.md#creating-a-native-child-process-that-supports-parameter-passing):

```c++
#include <AbilityKit/native_child_process.h>

extern "C" {

/**
 * Entry function of a child process, which implements the service logic of the child process.
 * The function name can be customized and is specified when the main process calls the OH_Ability_StartNativeChildProcess method. In this example, the function name is Main.
 * After the function is returned, the child process exits.
 */
void Main(NativeChildProcess_Args args)
{
    // Obtain the passed-in entryParams.
    char *entryParams = args.entryParams;
    // Obtain the input FD list, corresponding to args.fds in ChildProcessArgs.
    NativeChildProcess_Fd *current = args.fdList.head;
    while (current != nullptr) {
        char *fdName = current->fdName;
        int32_t fd = current->fd;
        current = current->next;
        // Service logic
    }
}
} // extern "C"
```

Sample code for the main process is provided below. For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
// Main process:
// Use the childProcessManager.startNativeChildProcess method to start a child process:
import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
              let path = context.filesDir + "/test.txt";
              let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
              let args: ChildProcessArgs = {
                entryParams: "testParam",
                fds: {
                  "key1": file.fd
                }
              };
              let options: ChildProcessOptions = {
                isolationMode: false
              };
              childProcessManager.startNativeChildProcess("libentry.so:Main", args, options)
                .then((pid) => {
                  console.info(`startNativeChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startNativeChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                })
            } catch (err: BusinessError) {
              console.error(`startNativeChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## childProcessManager.isArkChildProcessSupported

isArkChildProcessSupported(): boolean

Checks whether the caller is allowed to create an [ArkTS child process](../../application-models/ability-terminology.md#arkts-child-process) on this device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type    | Description                                          |
| :------ | --------------------------------------------- |
| boolean | Whether the caller is allowed to create an ArkTS child process.<br>true: The caller is allowed to create an ArkTS child process.<br>false: The caller is not allowed to create an ArkTS child process.<br>Default value: false.|

**Example**

```ts
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              let isSupport: boolean = childProcessManager.isArkChildProcessSupported();
              console.info(`isArkChildProcessSupported: ${isSupport}`);
            } catch (err: BusinessError) {
              console.error(`isArkChildProcessSupported error, errorCode: ${err.code}, errorMsg: ${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## childProcessManager.isNativeChildProcessSupported

isNativeChildProcessSupported(): boolean

Checks whether the caller is allowed to create a [Native child process](../../application-models/ability-terminology.md#native-child-process) on this device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type    | Description                                          |
| :------ | --------------------------------------------- |
| boolean | Whether the caller is allowed to create a Native child process.<br>true: The caller is allowed to create a Native child process.<br>false: The caller is not allowed to create a Native child process.<br>Default value: false.|

**Example**

```ts
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              let isSupport: boolean = childProcessManager.isNativeChildProcessSupported();
              console.info(`isNativeChildProcessSupported: ${isSupport}`);
            } catch (err: BusinessError) {
              console.error(`isNativeChildProcessSupported error, errorCode: ${err.code}, errorMsg: ${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## childProcessManager.getChildProcessInfos

getChildProcessInfos(): Promise&lt;Array&lt;ChildProcessInformation&gt;&gt;

Obtains the information about all child processes of the current application. This API uses a promise to return the result. The child processes include those started in the following ways:
- [OH_Ability_CreateNativeChildProcess](capi-native-child-process-h.md#oh_ability_createnativechildprocess) / [OH_Ability_CreateNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_createnativechildprocesswithconfigs)
- [OH_Ability_StartNativeChildProcess](capi-native-child-process-h.md#oh_ability_startnativechildprocess) / [OH_Ability_StartNativeChildProcessWithConfigs](capi-native-child-process-h.md#oh_ability_startnativechildprocesswithconfigs)
- [childProcessManager.startChildProcess](#childprocessmanagerstartchildprocess) (in non-SELF_FORK mode)
- [childProcessManager.startArkChildProcess](#childprocessmanagerstartarkchildprocess12)
- [childProcessManager.startNativeChildProcess](#childprocessmanagerstartnativechildprocess13)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;Array&lt;[ChildProcessInformation](js-apis-inner-application-childProcessRunningInfo.md)&gt;&gt; | Promise used to return the child process information of the current application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code ID | Error Message |
| ------- | -------- |
| 16000050 | Failed to connect to the system service. |

**Example**

```ts
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