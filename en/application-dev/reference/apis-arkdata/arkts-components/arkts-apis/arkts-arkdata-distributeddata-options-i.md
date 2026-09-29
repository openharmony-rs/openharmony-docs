# Options

```TypeScript
interface Options
```

Provides KV store configuration.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** Options

<!--Device-distributedData-interface Options--><!--Device-distributedData-interface Options-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
```

## autoSync

```TypeScript
autoSync?: boolean
```

Whether to automatically synchronize database files. The default value is **false**, which means the database files are manually synchronized.

ohos.permission.DISTRIBUTED_DATASYNC

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** autoSync

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-Options-autoSync?: boolean--><!--Device-Options-autoSync?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## backup

```TypeScript
backup?: boolean
```

Whether to back up the KV store. The default value is **true**, which means to back up the KV store.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** backup

<!--Device-Options-backup?: boolean--><!--Device-Options-backup?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## createIfMissing

```TypeScript
createIfMissing?: boolean
```

Whether to create a KV store if the database file does not exist. The default value is **true**, which means to create a KV store.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** createIfMissing

<!--Device-Options-createIfMissing?: boolean--><!--Device-Options-createIfMissing?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## encrypt

```TypeScript
encrypt?: boolean
```

Whether to encrypt the KV store. The default value is **false**, which means the KV store is not encrypted.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** encrypt

<!--Device-Options-encrypt?: boolean--><!--Device-Options-encrypt?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## kvStoreType

```TypeScript
kvStoreType?: KVStoreType
```

Type of the KV store to create. The default value is **DEVICE_COLLABORATION**, which indicates a device KV store.

**Type:** [KVStoreType](arkts-arkdata-distributeddata-kvstoretype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** kvStoreType

<!--Device-Options-kvStoreType?: KVStoreType--><!--Device-Options-kvStoreType?: KVStoreType-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## schema

```TypeScript
schema?: Schema
```

Schema that defines the values stored in the KV store. The default value is **undefined**, which means no schema is used.

**Type:** [Schema](arkts-arkdata-distributeddata-schema-c.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** schema

<!--Device-Options-schema?: Schema--><!--Device-Options-schema?: Schema-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## securityLevel

```TypeScript
securityLevel?: SecurityLevel
```

Security level (S1 to S4) of the KV store.

**Type:** [SecurityLevel](arkts-arkdata-distributeddata-securitylevel-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** securityLevel

<!--Device-Options-securityLevel?: SecurityLevel--><!--Device-Options-securityLevel?: SecurityLevel-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core
