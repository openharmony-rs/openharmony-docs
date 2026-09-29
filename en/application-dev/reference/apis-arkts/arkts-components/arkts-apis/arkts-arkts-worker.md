# @ohos.worker(Worker Thread Management)

JS cross-thread communication tool

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [worker](arkts-arkts-worker-n.md) | JS cross-thread communication tool |

### Interfaces

| Name | Description |
| --- | --- |
| [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | Specifies the worker thread running environment, which is isolated from the host thread environment |
| [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Provides detailed information about the exception that occurs during worker execution. The ErrorEvent class inherits from Event. |
| [Event](arkts-arkts-worker-event-i.md) | Defines the event. |
| [EventListener](arkts-arkts-worker-eventlistener-i.md) | Implements event listening. |
| [EventTarget](arkts-arkts-worker-eventtarget-i.md) | Specific event features. |
| [GlobalScope](arkts-arkts-worker-globalscope-i.md) | Implements the running environment of the Worker thread. The GlobalScope class inherits from WorkerEventTarget. |
| [MessageEvent](arkts-arkts-worker-messageevent-i.md) | Holds the data transferred between worker threads. |
| [MessageEvents](arkts-arkts-worker-messageevents-i.md) | Holds the data transferred between Worker threads. |
| [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | Defines the object for which the ownership is to be transferred during data transfer. The object must be an ArrayBuffer instance. After the ownership is transferred, the object becomes unavailable in the sender and can be used only in the receiver. |
| [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md) | Implements communication between the Worker thread and the host thread. The postMessage API is used to send messages to the host thread, and the close API is used to terminate the Worker thread. The ThreadWorkerGlobalScope class inherits from GlobalScope9+. |
| [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | Implements event listening. |
| [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md) | Processes worker listening events. |
| [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md) | Specifies the worker thread running environment, which is isolated from the host thread environment. |
| [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | Provides options that can be set for the Worker instance to create. |

### Types

| Name | Description |
| --- | --- |
| [ErrorCallback](arkts-arkts-errorcallback-t.md) | The event handler to be called when an exception occurs during worker execution. |
| [MessageType](arkts-arkts-messagetype-t.md) | Type of message, only "message" and "messageerror". |

### Enums

| Name | Description |
| --- | --- |
| [Priority](arkts-arkts-worker-priority-e.md) | Enumerates the priorities available for EventHandler. For details about the mappings between priorities and EventHandler levels, see EventHandler Level. |
| [ThreadWorkerPriority](arkts-arkts-worker-threadworkerpriority-e.md) | Enumerates the priorities available for Worker threads. For details about the mappings between priorities and QoS levels, see QoS Level. |
