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
> * After closing the current database, modify the **securityLevel** parameter to reset the database security level,and then call the getKVStore API to open the database again.
> 
> * You cannot downgrade the database security level. For example, you can change the database security level from S2 to S3, but cannot change it from S3 to S2.

**Since:** 9

<!--Device-distributedKVStore-enum SecurityLevel--><!--Device-distributedKVStore-enum SecurityLevel-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S1

```TypeScript
S1
```

Low security level. Disclosure, tampering, corruption, or loss of the data may cause minor impact on an individual or group.<br>Examples: gender and nationality information, and user application records

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityLevel-S1--><!--Device-SecurityLevel-S1-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S2

```TypeScript
S2
```

Medium security level. Disclosure, tampering, corruption, or loss of the data may cause major impact on an individual or group.<br>Examples: individual mailing addresses and nicknames

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityLevel-S2--><!--Device-SecurityLevel-S2-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S3

```TypeScript
S3
```

High security level. Disclosure, tampering, corruption, or loss of the data may cause critical impact on an individual or group.<br>Examples: real-time precise positioning information and movement trajectory

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityLevel-S3--><!--Device-SecurityLevel-S3-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## S4

```TypeScript
S4
```

Critical security level for a KV store. Disclosure, tampering, corruption, or loss of the data may cause significant adverse impact on an individual or group.<br><br>Examples: political opinions, religion, philosophical belief, trade union membership, genetic data, biological information, health, sexual life status, sexual orientation, device authentication, and personal credit card information.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityLevel-S4--><!--Device-SecurityLevel-S4-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
