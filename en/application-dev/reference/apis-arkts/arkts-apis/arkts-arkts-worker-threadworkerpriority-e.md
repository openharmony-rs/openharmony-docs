# ThreadWorkerPriority

Enumerates the priorities available for Worker threads. For details about the mappings between priorities and QoS levels, see QoS Level.

**Since:** 18

**System capability:** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

High priority, corresponding to QOS_USER_INITIATED.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

Medium priority, corresponding to QOS_DEFAULT.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

Low priority, corresponding to QOS_UTILITY.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

Background priority, corresponding to QOS_BACKGROUND.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## DEADLINE

```TypeScript
DEADLINE = 4
```

Deadline priority, corresponding to QOS_DEADLINE_REQUEST.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

## VIP

```TypeScript
VIP = 5
```

Vip priority, corresponding to QOS_USER_INTERACTIVE.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang
