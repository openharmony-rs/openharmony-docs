# @ohos.app.ability.ChildProcessArgs (Child Process Arguments)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e7bd4b9be9a9e20b7a13185fe75e55f283c09e67 translatedAt=2026-09-03T10:07:11.526Z pushedAt=2026-09-05T10:47:30.344Z -->

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

| Name       | Type                   | Read-Only| Optional | Description                                                        |
| ----------- | --------------------   | ---- | ------|------------------------------------------------------ |
| entryParams | string                 |  No  | Yes |Developer-defined parameters passed through to the child process. They can be obtained through args.entryParams in the [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) method. If not passed in, the child process cannot obtain the developer-defined parameters. entryParams is transmitted over IPC. The maximum amount of data transmitted over IPC is 200 KB (for details, see [Constraints](../../ipc/ipc-rpc-overview.md#constraints)), part of which is occupied by the system. It is recommended that the data size of entryParams not exceed 150 KB; otherwise, the child process may fail to be created.|
| fds         | Record<string, number> |  No  | Yes |A collection of file descriptor handles used for communication between the main process and the child process. If not passed in, the child process cannot obtain the file handles passed by the main process. This parameter is passed to the child process in key-value pairs, where key is a custom string and value is a file descriptor handle. The fd handle can be obtained through args.fds in the [ChildProcess.onStart](js-apis-app-ability-childProcess.md#childprocessonstart) method.<br/><b>Note:</b> <br>- fds supports a maximum of 16 groups, and the maximum length of each key is 20 characters.<br>- The handle number passed to the child process may change, but the file it points to remains the same.|

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

```ts
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
