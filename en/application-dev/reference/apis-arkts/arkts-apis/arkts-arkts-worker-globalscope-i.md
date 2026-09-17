# GlobalScope

Implements the running environment of the Worker thread. The GlobalScope class inherits from WorkerEventTarget.

**Inheritance/Implementation:** GlobalScope extends [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

Called when an exception occurs during worker execution. The event handler is executed in the Worker thread. In the callback function, the ev type is ErrorEvent, indicating the received abnormal data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ev | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Yes |  |

## name

```TypeScript
readonly name: string
```

Worker instance specified when there is a new Worker instance.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: GlobalScope & typeof globalThis
```

GlobalScope itself.

**Type:** [GlobalScope](arkts-arkts-worker-globalscope-i.md) & typeof globalThis

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
