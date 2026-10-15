# EventTarget

```TypeScript
export interface EventTarget
```

Specific event features.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

<!--Device-unnamed-export interface EventTarget--><!--Device-unnamed-export interface EventTarget-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## addEventListener

```TypeScript
addEventListener(type: string, listener: EventListener): void
```

Adds an event listener to the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addEventListener](arkts-arkts-worker-workereventtarget-i.md#addeventlistener)

<!--Device-EventTarget-addEventListener(type: string, listener: EventListener): void--><!--Device-EventTarget-addEventListener(type: string, listener: EventListener): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event to listen for. |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | Yes | listener Callback to invoke when an event of the specified type occurs. |

**Examples**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})
```

## dispatchEvent

```TypeScript
dispatchEvent(event: Event): boolean
```

Dispatches the event defined for the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [dispatchEvent](arkts-arkts-worker-workereventtarget-i.md#dispatchevent)

<!--Device-EventTarget-dispatchEvent(event: Event): boolean--><!--Device-EventTarget-dispatchEvent(event: Event): boolean-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-arkts-worker-event-i.md) | Yes | Event to dispatch. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean |  |

**Examples**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.dispatchEvent({type: 'alert_add', timeStamp: 0}); // timeStamp is not supported yet.
```

The dispatchEvent API can be used together with the addEventListener API. The sample code is as follows:

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (): void => {
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", ()=>{
  console.info("alert listener callback");
})

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.dispatchEvent({type:"alert", timeStamp:0}); // timeStamp is not supported yet.
}
```

## removeAllListener

```TypeScript
removeAllListener(): void
```

Removes all event listeners for the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeAllListener](arkts-arkts-worker-workereventtarget-i.md#removealllistener)

<!--Device-EventTarget-removeAllListener(): void--><!--Device-EventTarget-removeAllListener(): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.removeAllListener();
```

## removeEventListener

```TypeScript
removeEventListener(type: string, callback?: EventListener): void
```

Removes an event defined for the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeEventListener](arkts-arkts-worker-workereventtarget-i.md#removeeventlistener)

<!--Device-EventTarget-removeEventListener(type: string, callback?: EventListener): void--><!--Device-EventTarget-removeEventListener(type: string, callback?: EventListener): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event for which the event listener is removed. |
| callback | [EventListener](arkts-arkts-worker-eventlistener-i.md) | No | Callback of the event listener to remove. |

**Examples**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerPort.removeEventListener('alert');
```
