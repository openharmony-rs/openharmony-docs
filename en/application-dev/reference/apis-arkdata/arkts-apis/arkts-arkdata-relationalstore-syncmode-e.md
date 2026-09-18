# SyncMode

Defines the database synchronization mode. Use the enum name rather than the enum value.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_PUSH

```TypeScript
SYNC_MODE_PUSH = 0
```

Data is pushed from a local device to a remote device.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_PULL

```TypeScript
SYNC_MODE_PULL = 1
```

Data is pulled from a remote device to a local device.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SYNC_MODE_TIME_FIRST

```TypeScript
SYNC_MODE_TIME_FIRST
```

Synchronize with the data with the latest modification time.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## SYNC_MODE_NATIVE_FIRST

```TypeScript
SYNC_MODE_NATIVE_FIRST
```

Synchronize data from a local device to the cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## SYNC_MODE_CLOUD_FIRST

```TypeScript
SYNC_MODE_CLOUD_FIRST
```

Synchronize data from the cloud to a local device.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client
