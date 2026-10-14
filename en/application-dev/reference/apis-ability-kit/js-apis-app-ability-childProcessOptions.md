# @ohos.app.ability.ChildProcessOptions (Child Process Startup Options)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e7bd4b9be9a9e20b7a13185fe75e55f283c09e67 translatedAt=2026-09-03T10:07:53.748Z pushedAt=2026-09-05T10:47:30.348Z -->

Defines the startup configuration options of a child process, including the sandbox isolation level, network access permission, and independent UID. When a child process is started through [childProcessManager](js-apis-app-ability-childProcessManager.md), you can use ChildProcessOptions to configure the startup options of the child process.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ChildProcessOptions } from '@kit.AbilityKit';
```

## ChildProcessOptions

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Type     | Read-Only| Optional| Description                                                              |
| ----------- | --------- | ---- | ----- | ----------------------------------------------- |
| isolationMode | boolean | No| Yes| Controls the sandbox isolation level and network access permissions of the child process. **true** if the child process runs in an independent sandbox environment and cannot access the network; **false** if the child process shares the sandbox and network environment with the main process. The default value is **false**.|
| isolationUid<sup>21+</sup> | boolean | No | Yes | Whether the child process uses an independent UID. The value true means the child process has an independent UID, and false means the child process shares the same UID as the main process. The default value is false. Only effective when isolationMode is true. |

**Example**

Sample code for the child process:

```ts
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

<!--code_no_check-->
```ts
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