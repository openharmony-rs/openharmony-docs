# TaskInfo

Describes the internal information about a task.

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## duration

```TypeScript
duration?: number
```

Duration that the task has been executed, in ms. The default value is **0**. If the return value is **0**, the task is not running. If the return value is empty, no task is running. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

Task name. You are advised not to change the value.<br> This API can be used in atomic services since API version 12.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## state

```TypeScript
state: State
```

Task state. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** [State](arkts-arkts-taskpool-state-e.md)

**Default:** State::WAITING

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## taskId

```TypeScript
taskId: number
```

Task ID, which is globally unique by default. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** number

**Default:** 0

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
