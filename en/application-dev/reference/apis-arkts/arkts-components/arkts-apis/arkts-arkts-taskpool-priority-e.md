# Priority

Enumerates the priorities available for created tasks. The task priority applies during task execution. The worker thread priority is updated with the task priority. For details about the mappings, see [QoS Level](../../../napi/qos-guidelines.md#qos-level).

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

The task has a high priority.

This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

The task has a medium priority.

This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

The task has a low priority.

This API can be used in atomic services since API version 11.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

The task is a background task.

This API can be used in atomic services since API version 12.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
