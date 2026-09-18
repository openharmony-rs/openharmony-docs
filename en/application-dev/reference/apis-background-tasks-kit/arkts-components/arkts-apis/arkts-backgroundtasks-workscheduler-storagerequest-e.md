# StorageRequest

Enumerates the storage status that triggers the deferred task callback.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## STORAGE_LEVEL_LOW

```TypeScript
STORAGE_LEVEL_LOW = 0
```

The storage space is insufficient.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## STORAGE_LEVEL_OKAY

```TypeScript
STORAGE_LEVEL_OKAY = 1
```

The storage space is restored from insufficient to normal.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## STORAGE_LEVEL_LOW_OR_OKAY

```TypeScript
STORAGE_LEVEL_LOW_OR_OKAY = 2
```

The storage space is insufficient, or the storage space is restored from insufficient to normal.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler
