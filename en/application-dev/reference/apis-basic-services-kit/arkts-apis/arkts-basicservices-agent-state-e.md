# State

Defines the current task status.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## INITIALIZED

```TypeScript
INITIALIZED = 0x00
```

The task is initialized based on the configuration specified in [Config](arkts-basicservices-agent-config-i.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## WAITING

```TypeScript
WAITING = 0x10
```

The task lacks resources for running or the resources for retries, or does not match the network status.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## RUNNING

```TypeScript
RUNNING = 0x20
```

The task is being executed.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## RETRYING

```TypeScript
RETRYING = 0x21
```

The task has failed at least once and is being executed again.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## PAUSED

```TypeScript
PAUSED = 0x30
```

The task is suspended and will be resumed later.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## STOPPED

```TypeScript
STOPPED = 0x31
```

The task is stopped.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## COMPLETED

```TypeScript
COMPLETED = 0x40
```

The task is complete.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## FAILED

```TypeScript
FAILED = 0x41
```

The task fails.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## REMOVED

```TypeScript
REMOVED = 0x50
```

The task is removed.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent
