# ThreadWorkerPriority

```TypeScript
export enum ThreadWorkerPriority
```

Enumerates the priorities available for Worker threads. For details about the mappings between priorities and QoS levels, see QoS Level.

**Since:** 18

<!--Device-unnamed-export enum ThreadWorkerPriority--><!--Device-unnamed-export enum ThreadWorkerPriority-End-->

**System capability:** SystemCapability.Utils.Lang

## DEADLINE

```TypeScript
DEADLINE = 4
```

Deadline priority, corresponding to QOS_DEADLINE_REQUEST.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ThreadWorkerPriority-DEADLINE = 4--><!--Device-ThreadWorkerPriority-DEADLINE = 4-End-->

**System capability:** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

High priority, corresponding to QOS_USER_INITIATED.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ThreadWorkerPriority-HIGH = 0--><!--Device-ThreadWorkerPriority-HIGH = 0-End-->

**System capability:** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

Background priority, corresponding to QOS_BACKGROUND.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ThreadWorkerPriority-IDLE = 3--><!--Device-ThreadWorkerPriority-IDLE = 3-End-->

**System capability:** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

Low priority, corresponding to QOS_UTILITY.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ThreadWorkerPriority-LOW = 2--><!--Device-ThreadWorkerPriority-LOW = 2-End-->

**System capability:** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

Medium priority, corresponding to QOS_DEFAULT.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ThreadWorkerPriority-MEDIUM = 1--><!--Device-ThreadWorkerPriority-MEDIUM = 1-End-->

**System capability:** SystemCapability.Utils.Lang

## VIP

```TypeScript
VIP = 5
```

Vip priority, corresponding to QOS_USER_INTERACTIVE.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ThreadWorkerPriority-VIP = 5--><!--Device-ThreadWorkerPriority-VIP = 5-End-->

**System capability:** SystemCapability.Utils.Lang
