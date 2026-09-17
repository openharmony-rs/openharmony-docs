# MessageEvent

Holds the data transferred between worker threads.

**Inheritance/Implementation:** MessageEvent extends [Event](arkts-arkts-worker-event-i.md)

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## data

```TypeScript
readonly data: T
```

Data transferred when an exception occurs.

**Type:** T

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
