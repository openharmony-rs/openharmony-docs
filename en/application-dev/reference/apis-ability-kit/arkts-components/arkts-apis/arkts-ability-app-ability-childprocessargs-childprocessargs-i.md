# ChildProcessArgs

```TypeScript
export interface ChildProcessArgs
```

The module describes the parameters transferred to the child process. When starting a child process through [childProcessManager](arkts-ability-app-ability-childprocessmanager.md), you can transfer parameters to the child process through **ChildProcessArgs**.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## entryParams

```TypeScript
entryParams?: string
```

Custom parameters to be transparently transmitted to the child process. The parameters can be obtained through **args.entryParams** in [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart). The maximum data volume supported by **entryParams** is 150 KB.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## fds

```TypeScript
fds?: Record<string, number>
```

File Descriptor (FD) handles, which are used for communication between the main process and child process. They are passed to the child process in the form of key-value pairs, where **key** is a custom string and **value** is a DF handle. The FD handles can be obtained through **args.fds** in [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart).

&lt;b&gt;NOTE&lt;/b&gt;

- **fds** supports a maximum of 16 groups. In each group, **key** contains a maximum of 20 characters.  
- The ID of a handle passed to the child process may change, but the handle always points to the same file.

**Type:** Record&lt;string, number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

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
