# DedicatedWorkerGlobalScope

```TypeScript
export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope
```

Specifies the worker thread running environment, which is isolated from the host thread environment

**Inheritance/Implementation:** DedicatedWorkerGlobalScope extends [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md)

<!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope--><!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## close

```TypeScript
close(): void
```

Close the worker thread to stop the worker from receiving messages

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [close](arkts-arkts-worker-threadworkerglobalscope-i.md#close)

<!--Device-DedicatedWorkerGlobalScope-close(): void--><!--Device-DedicatedWorkerGlobalScope-close(): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
```

```TypeScript
// worker.ets
import { worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (): void => {
    parentPort.close()
}
```

## onmessage

```TypeScript
onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

The onmessage attribute of parentPort specifies the event handler to be called then the worker thread receives a message sent by the host thread through worker postMessage. The event handler is executed in the worker thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [onmessage](arkts-arkts-worker-threadworkerglobalscope-i.md#onmessage)

<!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | Yes |  |
| ev | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | Yes |  |

## onmessageerror

```TypeScript
onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

The onmessage attribute of parentPort specifies the event handler to be called then the worker receives a message that cannot be deserialized. The event handler is executed in the worker thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [onmessageerror](arkts-arkts-worker-threadworkerglobalscope-i.md#onmessageerror)

<!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | Yes |  |
| ev | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | Yes |  |

<a id="postmessage1"></a>

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: Transferable[]): void
```

Send a message to be host thread from the worker

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| messageObject | Object | Yes | messageObject Data to be sent to the worker |
| transfer | Transferable[] | Yes | transfer array cannot contain null. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    // let data = e.data;
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.onmessage = (): void => {
    // let data = e.data;
    let buffer = new ArrayBuffer(5)
    workerPort.postMessage(buffer, [buffer]);
}
```

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
import { ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (e: MessageEvents) => {
  parentPort.postMessage("receive data from main thread");
}
```

<a id="postmessage2"></a>

## postMessage

```TypeScript
postMessage(messageObject: Object, options?: PostMessageOptions): void
```

Send a message to be host thread from the worker

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| messageObject | Object | Yes | messageObject Data to be sent to the worker |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | No | Option can be set for postmessage. |

**Examples**

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
import { ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (e: MessageEvents) => {
  parentPort.postMessage("receive data from main thread");
}
```

<a id="postmessage3"></a>

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: ArrayBuffer[]): void
```

Send a message to host thread from the worker

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| messageObject | Object | Yes | messageObject Data to be sent to the worker |
| transfer | ArrayBuffer[] | Yes | transfer array cannot contain null. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    // let data = e.data;
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.onmessage = (): void => {
    // let data = e.data;
    let buffer = new ArrayBuffer(5)
    workerPort.postMessage(buffer, [buffer]);
}
```
