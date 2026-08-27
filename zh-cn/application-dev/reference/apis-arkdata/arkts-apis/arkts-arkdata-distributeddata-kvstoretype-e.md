# KVStoreType

KVStore数据库类型枚举。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** KVStoreType

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## DEVICE_COLLABORATION

```TypeScript
DEVICE_COLLABORATION = 0
```

表示多设备协同数据库。  
**数据库特点：** 数据以设备的维度管理，不存在冲突；支持按照设备的维度查询数据。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** DEVICE_COLLABORATION

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## SINGLE_VERSION

```TypeScript
SINGLE_VERSION = 1
```

表示单版本数据库。  
**数据库特点：** 数据不分设备，设备之间修改相同的key会覆盖。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SINGLE_VERSION

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## MULTI_VERSION

```TypeScript
MULTI_VERSION = 2
```

表示多版本数据库。当前暂不支持使用此接口。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
