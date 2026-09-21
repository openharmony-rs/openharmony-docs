# SecurityLevel

```TypeScript
enum SecurityLevel
```

Enumerates the KV store security levels.

> **NOTE:** 
> 
> For the scenarios involving a single device, you can upgrade the security level of a KV store by modifying the
> **securityLevel** parameter. When upgrading the database security level, observe the following:
> 
> * This operation does not apply to the databases that require cross-device sync. Data cannot be synced between databases of different security levels. If you want to upgrade the security level of a database, you are advised to create a database of a higher security level.
> 
> * You need to close the database before modifying the **securityLevel** parameter, and open it after the security level is upgraded.
> 
> * You cannot downgrade the database security level. For example, you can change the database security level from S2 to S3, but cannot change it from S3 to S2.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S1

```TypeScript
S1
```

S1: means the db is in the low security level There are some low impact when the data is leaked.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S2

```TypeScript
S2
```

S2: means the db is in the middle security level There are some major impact when the data is leaked.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S3

```TypeScript
S3
```

S3: means the db is in the high security level There are some severity impact when the data is leaked.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S4

```TypeScript
S4
```

S4: means the db is in the critical security level There are some critical impact when the data is leaked.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
