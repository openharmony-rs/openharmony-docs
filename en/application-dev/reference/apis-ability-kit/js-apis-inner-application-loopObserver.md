# LoopObserver

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe--> 
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d7833d54288ec20034339cf7164e5aaef52722e9 translatedAt=2026-09-03T11:58:23.192Z pushedAt=2026-09-05T10:47:30.823Z -->

Defines a listener for exceptions on the main thread of an application. It can be used as an input parameter of [ErrorManager.on](./js-apis-app-ability-error-manager.md#errormanageronloopobserver12) to listen for timeouts in main thread event processing. Through the callback mechanism, the actual execution time of main thread messages is obtained in real time, helping developers detect and locate faults in a timely manner.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { errorManager } from '@kit.AbilityKit';
```

## LoopObserver.onLoopTimeOut

onLoopTimeOut?(timeout: number): void

Callback function triggered when a timeout occurs for the main thread to process an event in the JS runtime.

Usage scenario: used to monitor the execution of events processed by the main thread of an application. This callback is triggered when a timeout occurs for the main thread to process an event. Developers can record logs and optimize code logic based on the timeout condition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| timeout | number | Yes | Actual execution time of the application main thread message, in milliseconds. The value must be a positive integer greater than 0. |

**Example**

```ts
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

errorManager.on('loopObserver', 1, observer);
```
