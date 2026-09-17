# WorkerGlobalScope

Specifies the worker thread running environment, which is isolated from the host thread environment.

**Inheritance/Implementation:** WorkerGlobalScope extends [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [GlobalScope](arkts-arkts-worker-globalscope-i.md)

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

The onerror attribute of parentPort specifies the event handler to be called when an exception occurs during worker execution. The event handler is executed in the worker thread.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onerror

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ev | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Yes |  |

## name

```TypeScript
readonly name: string
```

Worker name specified when there is a new worker.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

**System capability:** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: WorkerGlobalScope & typeof globalThis
```

Specify the type attribute for self.

**Type:** [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md) & typeof globalThis

**Since:** 7

**Deprecated since:** 9

**Substitutes:** self

**System capability:** SystemCapability.Utils.Lang
