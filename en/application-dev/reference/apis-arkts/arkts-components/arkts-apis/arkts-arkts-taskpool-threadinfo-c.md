# ThreadInfo

```TypeScript
class ThreadInfo
```

Describes the internal information about a worker thread.

**Since:** 10

<!--Device-taskpool-class ThreadInfo--><!--Device-taskpool-class ThreadInfo-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## priority

```TypeScript
priority?: Priority
```

Priority of the calling thread. If the return value is empty, no task is running. You are advised not to change the value.

**Type:** [Priority](arkts-arkts-taskpool-priority-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ThreadInfo-priority?: Priority--><!--Device-ThreadInfo-priority?: Priority-End-->

**System capability:** SystemCapability.Utils.Lang

## taskIds

```TypeScript
taskIds?: number[]
```

IDs of tasks running on the calling thread. If the return value is empty, no task is running. You are advised not to change the value.

**Type:** number[]

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ThreadInfo-taskIds?: number[]--><!--Device-ThreadInfo-taskIds?: number[]-End-->

**System capability:** SystemCapability.Utils.Lang

## tid

```TypeScript
tid: number
```

ID of the worker thread. If the return value is empty, no task is running. You are advised not to change the value.

**Type:** number

**Default:** 0

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ThreadInfo-tid: number--><!--Device-ThreadInfo-tid: number-End-->

**System capability:** SystemCapability.Utils.Lang
