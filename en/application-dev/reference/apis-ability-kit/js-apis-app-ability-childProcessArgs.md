# @ohos.app.ability.ChildProcessArgs (Child Process Arguments)

The module describes the parameters transferred to the child process. When starting a child process through [childProcessManager](js-apis-app-ability-childProcessManager.md), you can transfer parameters to the child process through **ChildProcessArgs**.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## ChildProcessArgs

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Type                   | Mandatory| Description                                                        |
| ----------- | --------------------   | ---- | ------------------------------------------------------------ |
| entryParams | string                 |  No | Custom parameters to be transparently transmit to the child process. The parameters can be obtained through **args.entryParams** in [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart). The maximum data volume supported by **entryParams** is 150 KB.|
| fds         | Record<string, number> |  No | File Descriptor (FD) handles, which are used for communication between the main process and child process. They are passed to the child process in the form of key-value pairs, where **key** is a custom string and **value** is a DF handle. The FD handles can be obtained through **args.fds** in [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart).<br><b>NOTE</b><br>- **fds** supports a maximum of 16 groups. In each group, **key** contains a maximum of 20 characters.<br>- The ID of a handle passed to the child process may change, but the handle always points to the same file.|

**Example**

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
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
            let path = context.filesDir + "/test.txt";
            let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
            let args: ChildProcessArgs = {
              entryParams: "testParam",
              fds: {
                "key1": file.fd
              }
            };
            childProcessManager.startArkChildProcess("entry/./ets/process/DemoProcess.ets", args);
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```ts
// In the child process:
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ..
  }
}
```
