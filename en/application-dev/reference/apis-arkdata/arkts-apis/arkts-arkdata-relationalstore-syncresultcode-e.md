# SyncResultCode

Describes the status of device sync.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

Indicates sync success.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## FAIL

```TypeScript
FAIL = 1
```

Indicates sync fail, for detailed reasons, please refer to the message.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## OFFLINE

```TypeScript
OFFLINE = 2
```

Indicates that the device is offline.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## INVALID_ARGS

```TypeScript
INVALID_ARGS = 3
```

Indicates parameter is invalid.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## DISTRIBUTED_TABLE_NOT_SET

```TypeScript
DISTRIBUTED_TABLE_NOT_SET = 4
```

Indicates that a distributed table is not set.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## TABLE_FIELD_MISMATCH

```TypeScript
TABLE_FIELD_MISMATCH = 5
```

Indicates that the synchronization field of the peer device is inconsistent with that of the local device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## DISTRIBUTED_SCHEMA_MISMATCH

```TypeScript
DISTRIBUTED_SCHEMA_MISMATCH = 6
```

Indicates that the schema field of the peer device is inconsistent with that of the local device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## BUSY

```TypeScript
BUSY = 7
```

Indicates that the database is busy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## CORRUPTED

```TypeScript
CORRUPTED = 8
```

Indicates that the database is corrupted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## TIMEOUT

```TypeScript
TIMEOUT = 9
```

Indicates synchronization timeout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SCHEMA_CHANGED

```TypeScript
SCHEMA_CHANGED = 10
```

Indicates that the table structure changed during the synchronization process.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## CONSTRAINT_VIOLATION

```TypeScript
CONSTRAINT_VIOLATION = 11
```

Indicates a violation of constraints when synchronizing data.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
