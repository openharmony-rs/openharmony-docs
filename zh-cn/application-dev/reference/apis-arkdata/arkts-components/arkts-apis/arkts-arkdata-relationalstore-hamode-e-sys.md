# HAMode（系统接口）

描述关系型数据库存储的高可用性模式的枚举。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## SINGLE

```TypeScript
SINGLE = 0
```

表示将数据写入单个关系型数据库存储。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## MAIN_REPLICA

```TypeScript
MAIN_REPLICA = 1
```

表示将数据写入主关系型数据库存储和副本关系型数据库存储，不支持加密场景和attach场景，会导致数据库写入性能的劣化。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。
