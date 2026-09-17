# ThreadInfo

Describes the internal information about a worker thread.

**Since:** 10

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

**System capability:** SystemCapability.Utils.Lang

## taskIds

```TypeScript
taskIds?: number[]
```

IDs of tasks running on the calling thread. If the return value is empty, no task is running. You are advised not to change the value.

**Type:** number[]

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.Utils.Lang
