# TransactionType

Enumerates the types of transaction objects that can be created. Use the enum name rather than the enum value.

**Since:** 14

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## DEFERRED

```TypeScript
DEFERRED = 0
```

Deferred transaction object. When a deferred transaction object is created, automatic commit is disabled and no transaction will start. A read or write transaction starts only when the first read or write operation is performed.

**Since:** 14

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## IMMEDIATE

```TypeScript
IMMEDIATE = 1
```

Immediate transaction object. When an immediate transaction object is created, a write transaction starts. If there is any uncommitted write transaction, the transaction object cannot be created and error 14800024 is returned.

**Since:** 14

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## EXCLUSIVE

```TypeScript
EXCLUSIVE = 2
```

Exclusive transaction object. In WAL mode, the exclusive transaction object is the same as the immediate transaction object. In other log modes, this type of transaction can prevent the database from being read by other connections during the transaction.

**Since:** 14

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
