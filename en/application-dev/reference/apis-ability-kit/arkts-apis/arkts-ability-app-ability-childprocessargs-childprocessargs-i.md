# ChildProcessArgs

```TypeScript
export interface ChildProcessArgs
```

The module describes the parameters transferred to the child process. When starting a child process through [childProcessManager](arkts-ability-app-ability-childprocessmanager.md), you can transfer parameters to the child process through **ChildProcessArgs**.

**Since:** 12

<!--Device-unnamed-export interface ChildProcessArgs--><!--Device-unnamed-export interface ChildProcessArgs-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## entryParams

```TypeScript
entryParams?: string
```

Developer-defined parameters passed through to the child process. They can be obtained through args.entryParams in the [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart) method. If not passed in, the child process cannot obtain the developer-defined parameters. entryParams is transmitted over IPC. The maximum amount of data transmitted over IPC is 200 KB, part of which is occupied by the system. It is recommended that the data size of entryParams not exceed 150 KB; otherwise, the child process may fail to be created.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChildProcessArgs-entryParams?: string--><!--Device-ChildProcessArgs-entryParams?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## fds

```TypeScript
fds?: Record<string, number>
```

A collection of file descriptor handles used for communication between the main process and the child process. If not passed in, the child process cannot obtain the file handles passed by the main process. This parameter is passed to the child process in key-value pairs, where key is a custom string and value is a file descriptor handle. The fd handle can be obtained through args.fds in the [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart) method.

> **NOTE:** 
> 
> - fds supports a maximum of 16 groups, and the maximum length of each key is 20 characters.
> - The handle number passed to the child process may change, but the file it points to remains the same.

**Type:** Record&lt;string, number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChildProcessArgs-fds?: Record<string, int>--><!--Device-ChildProcessArgs-fds?: Record<string, int>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
// In the main process:
import { common, ChildProcessArgs, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let path = context.filesDir + '/test.txt';
            let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
            let args: ChildProcessArgs = {
              entryParams: 'testParam',
              fds: {
                'key1': file.fd
              }
            };
            childProcessManager.startArkChildProcess('entry/./ets/process/DemoProcess.ets', args);
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// In the child process:
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ...
  }
}
```
