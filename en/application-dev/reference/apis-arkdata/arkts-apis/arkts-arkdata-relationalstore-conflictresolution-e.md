# ConflictResolution

Enumerates the resolutions used when a conflict occurs during data insertion or modification. Use the enum name rather than the enum value.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_NONE

```TypeScript
ON_CONFLICT_NONE = 0
```

No operation is performed.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_ROLLBACK

```TypeScript
ON_CONFLICT_ROLLBACK = 1
```

Abort the SQL statement and roll back the current transaction.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_ABORT

```TypeScript
ON_CONFLICT_ABORT = 2
```

Abort the current SQL statement and revert any changes made by the current SQL statement. However, the changes made by the previous SQL statement in the same transaction are retained and the transaction remains active.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_FAIL

```TypeScript
ON_CONFLICT_FAIL = 3
```

Abort the current SQL statement. The **FAIL** resolution does not revert previous changes made by the failed SQL statement or end the transaction.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_IGNORE

```TypeScript
ON_CONFLICT_IGNORE = 4
```

Skip the rows that contain constraint violations and continue to process the subsequent rows of the SQL statement.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_REPLACE

```TypeScript
ON_CONFLICT_REPLACE = 5
```

Delete pre-existing rows that cause the constraint violation before inserting or updating the current row, and continue to execute the command normally.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
