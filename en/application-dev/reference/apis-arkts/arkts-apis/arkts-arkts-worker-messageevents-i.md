# MessageEvents

Holds the data transferred between Worker threads.

**Inheritance/Implementation:** MessageEvents extends [Event](arkts-arkts-worker-event-i.md)

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## data

```TypeScript
readonly data: any
```

Data transferred when an exception occurs.

**Type:** any

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
