# @ohos.app.ability.ChildProcess (Child Process Base Class)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T10:03:05.121Z pushedAt=2026-09-05T10:47:30.342Z -->

ChildProcess is the base class for you to customize child processes. When starting a child process through [childProcessManager](js-apis-app-ability-childProcessManager.md), you must inherit this class and override the entrypoint method.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> 
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { ChildProcess } from '@kit.AbilityKit';
```

## ChildProcess.onStart

onStart(args?: ChildProcessArgs): void

Entrypoint method of the child process. This callback is triggered when the child process is started through [childProcessManager](js-apis-app-ability-childProcessManager.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | args<sup>12+</sup> | [ChildProcessArgs](js-apis-app-ability-childProcessArgs.md) | No | Parameters passed to the child process. This parameter is optional. If it is not passed or null is passed, the default configuration is used for startup. |

**Example**
```ts
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ...
  }
}
```