# worker(Worker Thread Management)

```TypeScript
declare namespace worker
```

JS cross-thread communication tool

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ThreadWorker](arkts-arkts-worker-threadworker-c.md) | Before using the following APIs, you must create a ThreadWorker instance. The ThreadWorker class inherits from WorkerEventTarget. |
| [Worker](arkts-arkts-worker-worker-c.md) | The Worker class contains all Worker functions. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [RestrictedWorker](arkts-arkts-worker-restrictedworker-c-sys.md) | The RestrictedWorker class contains all Worker functions. |
<!--DelEnd-->

### Constants

| Name | Description |
| --- | --- |
| [parentPort](arkts-arkts-worker-con.md#parentport) | The object used by the worker thread to communicate with the host thread. |
| [workerPort](arkts-arkts-worker-con.md#workerport) | The object used by the worker thread to communicate with the host thread. |
