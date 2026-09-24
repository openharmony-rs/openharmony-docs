# ChildProcessOptions

```TypeScript
export interface ChildProcessOptions
```

The module describes the startup configuration of a child process. When starting a child process through [childProcessManager](arkts-ability-app-ability-childprocessmanager.md), you can configure the startup configuration of the child process through **ChildProcessOptions**.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ChildProcessOptions } from '@kit.AbilityKit';
```

## isolationMode

```TypeScript
isolationMode?: boolean
```

Controls the sandbox isolation level and network access permissions of the child process. **true** if the child process runs in an independent sandbox environment and cannot access the network; **false** if the child process shares the sandbox and network environment with the main process. The default value is **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isolationUid

```TypeScript
isolationUid?: boolean
```

Whether the child process uses an independent UID. **true** if the child process uses an independent UID; **false** if the child process and the main process share the same UID. The default value is **false**. This parameter is valid only when **isolationMode** is set to **true**.

**Type:** boolean

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

Sample code for the child process:

```TypeScript
// Create the DemoProcess.ets child process class under src/main/ets/process in the entry module:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // Child process code logic
  }
}
```

Sample code for the main process:

```TypeScript
// Use the childProcessManager.startArkChildProcess method to start a child process.
// entry/src/main/ets/pages/Index.ets
import { ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
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
              let options: ChildProcessOptions = {
                isolationMode: true,
                isolationUid: false
              };
              let args: ChildProcessArgs = {
                entryParams: 'testParam',
              };
              childProcessManager.startArkChildProcess("entry/ets/process/DemoProcess.ets", args, options)
                .then((pid) => {
                  console.info(`startChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                });
            } catch (err) {
              console.error(`startChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
