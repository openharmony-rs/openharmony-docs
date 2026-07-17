# Options

用于提供创建数据库的配置信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** Options

<!--Device-distributedData-interface Options--><!--Device-distributedData-interface Options-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## autoSync

```TypeScript
autoSync?: boolean
```

设置数据库文件是否自动同步。默认为false，即手动同步。

ohos.permission.DISTRIBUTED_DATASYNC

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** autoSync

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-Options-autoSync?: boolean--><!--Device-Options-autoSync?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## backup

```TypeScript
backup?: boolean
```

设置数据库文件是否备份，默认为true，即备份。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** backup

<!--Device-Options-backup?: boolean--><!--Device-Options-backup?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## createIfMissing

```TypeScript
createIfMissing?: boolean
```

当数据库文件不存在时是否创建数据库，默认为true，即创建。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createIfMissing

<!--Device-Options-createIfMissing?: boolean--><!--Device-Options-createIfMissing?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## encrypt

```TypeScript
encrypt?: boolean
```

设置数据库文件是否加密，默认为false，即不加密。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** encrypt

<!--Device-Options-encrypt?: boolean--><!--Device-Options-encrypt?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## kvStoreType

```TypeScript
kvStoreType?: KVStoreType
```

设置要创建的数据库类型，默认为DEVICE_COLLABORATION，即多设备协同数据库。

**类型：** KVStoreType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** kvStoreType

<!--Device-Options-kvStoreType?: KVStoreType--><!--Device-Options-kvStoreType?: KVStoreType-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## schema

```TypeScript
schema?: Schema
```

设置定义存储在数据库中的值，默认为undefined，即不使用schema。

**类型：** Schema

**起始版本：** 8

**废弃版本：** 9

**替代接口：** schema

<!--Device-Options-schema?: Schema--><!--Device-Options-schema?: Schema-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## securityLevel

```TypeScript
securityLevel?: SecurityLevel
```

设置数据库安全级别(S1-S4)。

**类型：** SecurityLevel

**起始版本：** 7

**废弃版本：** 9

**替代接口：** securityLevel

<!--Device-Options-securityLevel?: SecurityLevel--><!--Device-Options-securityLevel?: SecurityLevel-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

