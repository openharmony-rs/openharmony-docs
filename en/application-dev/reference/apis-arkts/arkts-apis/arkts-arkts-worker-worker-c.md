# Worker

```TypeScript
class Worker implements EventTarget
```

The Worker class contains all Worker functions.

**Inheritance/Implementation:** Worker implements [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ThreadWorker](arkts-arkts-worker-threadworker-c.md)

<!--Device-worker-class Worker implements EventTarget--><!--Device-worker-class Worker implements EventTarget-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

Creates a worker instance

**Since:** 7

**Deprecated since:** 9

**Substitutes:** constructor

<!--Device-Worker-constructor(scriptURL: string, options?: WorkerOptions)--><!--Device-Worker-constructor(scriptURL: string, options?: WorkerOptions)-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scriptURL | string | Yes | scriptURL URL of the script to be executed by the worker |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | No | Options that can be set for the worker |

**Examples**

The following uses the Index.ets file in the entry module of the stage model as an example to describe how to load the worker file. For details about how to use the library to load the Worker thread file, see [Precautions for File URLs](../../../arkts-utils/worker-introduction.md#precautions-for-file-urls).

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// URL of the Worker file: "entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.Worker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

## off

```TypeScript
off(type: string, listener?: EventListener): void
```

Removes an event listener to the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** off

<!--Device-Worker-off(type: string, listener?: EventListener): void--><!--Device-Worker-off(type: string, listener?: EventListener): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event for which the event listener is removed. |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | No | listener Callback of the event listener to remove. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
// Use on, once, or addEventListener to add a listener for the "alert" event, and use off to remove the listener.
workerInstance.off("alert");
```

## on

```TypeScript
on(type: string, listener: EventListener): void
```

Adds an event listener to the worker.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** on

<!--Device-Worker-on(type: string, listener: EventListener): void--><!--Device-Worker-on(type: string, listener: EventListener): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | type Adds an event listener to the worker. |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | Yes | listener Callback to invoke when an event of the specified type occurs. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.on("alert", () => {
    console.info("alert listener callback");
})
```

## once

```TypeScript
once(type: string, listener: EventListener): void
```

Adds an event listener to the worker and removes the event listener automatically after it is invoked once.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** once

<!--Device-Worker-once(type: string, listener: EventListener): void--><!--Device-Worker-once(type: string, listener: EventListener): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event to listen for |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | Yes | listener Callback to invoke when an event of the specified type occurs |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.once("alert", () => {
    console.info("alert listener callback");
})
```

## onerror

```TypeScript
onerror?: (err: ErrorEvent) => void
```

The onerror attribute of the worker specifies the event handler to be called when an exception occurs during worker execution. The event handler is executed in the host thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onerror

<!--Device-Worker-onerror?: (err: ErrorEvent) => void--><!--Device-Worker-onerror?: (err: ErrorEvent) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| err | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Yes |  |

## onexit

```TypeScript
onexit?: (code: number) => void
```

Called when the Worker thread exits. The event handler is executed in the host thread. In the callback function, the code value is of the number type, where the value 1 indicates abnormal exit and 0 indicates normal exit.The default value is undefined.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onexit

<!--Device-Worker-onexit?: (code: number) => void--><!--Device-Worker-onexit?: (code: number) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes |  |

## onmessage

```TypeScript
onmessage?: (event: MessageEvent) => void
```

The onmessage attribute of the worker specifies the event handler to be called then the host thread receives a message created by itself and sent by the worker through the parentPort.postMessage. The event handler is executed in the host thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onmessage

<!--Device-Worker-onmessage?: (event: MessageEvent) => void--><!--Device-Worker-onmessage?: (event: MessageEvent) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | Yes |  |

## onmessageerror

```TypeScript
onmessageerror?: (event: MessageEvent) => void
```

The onmessage attribute of the worker specifies the event handler when the worker receives a message that cannot be serialized. The event handler is executed in the host thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onmessageerror

<!--Device-Worker-onmessageerror?: (event: MessageEvent) => void--><!--Device-Worker-onmessageerror?: (event: MessageEvent) => void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | Yes |  |

## postMessage

```TypeScript
postMessage(message: Object, transfer: ArrayBuffer[]): void
```

Sends a message to the worker thread. The data is transferred using the structured clone algorithm.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** postMessage

<!--Device-Worker-postMessage(message: Object, transfer: ArrayBuffer[]): void--><!--Device-Worker-postMessage(message: Object, transfer: ArrayBuffer[]): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Object | Yes | Data to be sent to the worker |
| transfer | ArrayBuffer[] | Yes | transfer ArrayBuffer instance that can be transferred. The transferList array cannot contain null. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

<a id="postmessage-1"></a>

## postMessage

```TypeScript
postMessage(message: Object, options?: PostMessageOptions): void
```

Sends a message to the worker thread. The data is transferred using the structured clone algorithm.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** postMessage

<!--Device-Worker-postMessage(message: Object, options?: PostMessageOptions): void--><!--Device-Worker-postMessage(message: Object, options?: PostMessageOptions): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Object | Yes | Data to be sent to the worker |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | No | Option can be set for postmessage. The transferList array cannot contain null. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

## terminate

```TypeScript
terminate(): void
```

Terminates the worker thread to stop the worker from receiving messages

**Since:** 7

**Deprecated since:** 9

**Substitutes:** terminate

<!--Device-Worker-terminate(): void--><!--Device-Worker-terminate(): void-End-->

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```
