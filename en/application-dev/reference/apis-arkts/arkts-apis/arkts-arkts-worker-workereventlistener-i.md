# WorkerEventListener

```TypeScript
export interface WorkerEventListener
```

Implements event listening.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## [[Call]]

```TypeScript
(event: Event): void | Promise<void>
```

Specifies the callback function to be invoked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-arkts-worker-event-i.md) | Yes | Event class for the callback to invoke. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

**Examples**

```TypeScript
// Index.ets
import { worker, Event } from "@kit.ArkTS"

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", (event: Event) => {
  console.info("event type is: ", JSON.stringify(event.type));
});

const eventToDispatch : Event = { type: "alert", timeStamp: 0 }; // timeStamp is not supported.
workerInstance.dispatchEvent(eventToDispatch);
```
