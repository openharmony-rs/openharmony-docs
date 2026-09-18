# EventListener

Implements event listening.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md)

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## [[Call]]

```TypeScript
(evt: Event): void | Promise<void>
```

Specifies the callback to invoke.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** ohos.worker.WorkerEventListener.(event: Event)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| evt | [Event](arkts-arkts-worker-event-i.md) | Yes | evt evt Event class for the callback to invoke. |
