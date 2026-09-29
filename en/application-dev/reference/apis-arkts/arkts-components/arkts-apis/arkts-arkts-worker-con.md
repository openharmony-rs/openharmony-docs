# Constants

## workerPort

```TypeScript
const workerPort: ThreadWorkerGlobalScope
```

The object used by the worker thread to communicate with the host thread.

**Type:** [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-worker-const workerPort: ThreadWorkerGlobalScope--><!--Device-worker-const workerPort: ThreadWorkerGlobalScope-End-->

**System capability:** SystemCapability.Utils.Lang

## parentPort

```TypeScript
const parentPort: DedicatedWorkerGlobalScope
```

The object used by the worker thread to communicate with the host thread.

**Type:** [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [workerPort](#workerport)

<!--Device-worker-const parentPort: DedicatedWorkerGlobalScope--><!--Device-worker-const parentPort: DedicatedWorkerGlobalScope-End-->

**System capability:** SystemCapability.Utils.Lang
