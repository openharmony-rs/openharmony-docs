# WaitingReason

```TypeScript
enum WaitingReason
```

Enumerates the reasons why a task is waiting.

**Since:** 20

<!--Device-agent-enum WaitingReason--><!--Device-agent-enum WaitingReason-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## APP_BACKGROUND

```TypeScript
APP_BACKGROUND = 0x02
```

The application has been running in the background for a long time.

**Since:** 20

<!--Device-WaitingReason-APP_BACKGROUND = 0x02--><!--Device-WaitingReason-APP_BACKGROUND = 0x02-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## NETWORK_NOT_MATCH

```TypeScript
NETWORK_NOT_MATCH = 0x01
```

The required network conditions are not met.

**Since:** 20

<!--Device-WaitingReason-NETWORK_NOT_MATCH = 0x01--><!--Device-WaitingReason-NETWORK_NOT_MATCH = 0x01-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## TASK_QUEUE_FULL

```TypeScript
TASK_QUEUE_FULL = 0x00
```

The task queue is full.

**Since:** 20

<!--Device-WaitingReason-TASK_QUEUE_FULL = 0x00--><!--Device-WaitingReason-TASK_QUEUE_FULL = 0x00-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## USER_INACTIVATED

```TypeScript
USER_INACTIVATED = 0x03
```

The user is inactive.

**Since:** 20

<!--Device-WaitingReason-USER_INACTIVATED = 0x03--><!--Device-WaitingReason-USER_INACTIVATED = 0x03-End-->

**System capability:** SystemCapability.Request.FileTransferAgent
