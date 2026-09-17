# LoopObserver

The module defines an observer to listen for event processing timeout. It can be used as an input parameter in [ErrorManager.on](arkts-ability-errormanager-on-f.md#onloopobserver) to listen for the event processing timeout of the current application's main thread.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onLoopTimeOut

```TypeScript
onLoopTimeOut?(timeout: number): void
```

Called when a timeout occurs for the main thread to process an event in the JS runtime.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Actual execution time of the main thread. The value must be greater than **0**. The unit is milliseconds (ms). The value should be an integer. |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

errorManager.on('loopObserver', 1, observer);
```
