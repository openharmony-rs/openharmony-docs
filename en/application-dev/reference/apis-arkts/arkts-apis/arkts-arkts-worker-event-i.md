# Event

```TypeScript
export interface Event
```

Defines the event.

**Since:** 7

<!--Device-unnamed-export interface Event--><!--Device-unnamed-export interface Event-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## timeStamp

```TypeScript
readonly timeStamp: number
```

Timestamp (accurate to millisecond) when the event is created. This parameter is not supported yet.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Event-readonly timeStamp: number--><!--Device-Event-readonly timeStamp: number-End-->

**System capability:** SystemCapability.Utils.Lang

## type

```TypeScript
readonly type: string
```

Type of the Event.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Event-readonly type: string--><!--Device-Event-readonly type: string-End-->

**System capability:** SystemCapability.Utils.Lang
