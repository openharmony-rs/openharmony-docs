# ProgressCode

Describes the status of `Progress`.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

The device-cloud sync is successful.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 1
```

An unknown error occurs during the device-cloud sync.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 2
```

A network error occurs during the device-cloud sync.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## CLOUD_DISABLED

```TypeScript
CLOUD_DISABLED = 3
```

The cloud is unavailable.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## LOCKED_BY_OTHERS

```TypeScript
LOCKED_BY_OTHERS = 4
```

The device-cloud sync of another device is being performed.

The sync of the local device can be performed only when the cloud resources are available.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## RECORD_LIMIT_EXCEEDED

```TypeScript
RECORD_LIMIT_EXCEEDED = 5
```

The number of records or size of the data to be synced exceeds the maximum. The maximum value is configured on the cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NO_SPACE_FOR_ASSET

```TypeScript
NO_SPACE_FOR_ASSET = 6
```

The remaining cloud space is less than the size of the data to be synced.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## BLOCKED_BY_NETWORK_STRATEGY

```TypeScript
BLOCKED_BY_NETWORK_STRATEGY = 7
```

The device-cloud sync is blocked due to the network strategy.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## STOP_CLOUD_SYNC

```TypeScript
STOP_CLOUD_SYNC = 8
```

STOP_CLOUD_SYNC: means cloud synchronization has been stopped.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
