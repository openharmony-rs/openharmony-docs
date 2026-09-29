# State

```TypeScript
enum State
```

Defines the current task status.

**Since:** 10

<!--Device-agent-enum State--><!--Device-agent-enum State-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## INITIALIZED

```TypeScript
INITIALIZED = 0x00
```

The task is initialized based on the configuration specified in [Config](arkts-basicservices-agent-config-i.md).

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-INITIALIZED = 0x00--><!--Device-State-INITIALIZED = 0x00-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## WAITING

```TypeScript
WAITING = 0x10
```

The task lacks resources for running or the resources for retries, or does not match the network status.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-WAITING = 0x10--><!--Device-State-WAITING = 0x10-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## RUNNING

```TypeScript
RUNNING = 0x20
```

The task is being executed.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-RUNNING = 0x20--><!--Device-State-RUNNING = 0x20-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## RETRYING

```TypeScript
RETRYING = 0x21
```

The task has failed at least once and is being executed again.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-RETRYING = 0x21--><!--Device-State-RETRYING = 0x21-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## PAUSED

```TypeScript
PAUSED = 0x30
```

The task is suspended and will be resumed later.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-PAUSED = 0x30--><!--Device-State-PAUSED = 0x30-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## STOPPED

```TypeScript
STOPPED = 0x31
```

The task is stopped.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-STOPPED = 0x31--><!--Device-State-STOPPED = 0x31-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## COMPLETED

```TypeScript
COMPLETED = 0x40
```

The task is complete.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-COMPLETED = 0x40--><!--Device-State-COMPLETED = 0x40-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## FAILED

```TypeScript
FAILED = 0x41
```

The task fails.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-FAILED = 0x41--><!--Device-State-FAILED = 0x41-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## REMOVED

```TypeScript
REMOVED = 0x50
```

The task is removed.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-State-REMOVED = 0x50--><!--Device-State-REMOVED = 0x50-End-->

**System capability:** SystemCapability.Request.FileTransferAgent
