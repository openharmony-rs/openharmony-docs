# RebuildType

描述数据库重建类型的枚举。请使用枚举名称而非枚举值。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE

```TypeScript
NONE = 0
```

表示数据库未进行重建。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## REBUILT

```TypeScript
REBUILT = 1
```

表示数据库进行了重建并且生成了空数据库，需要应用重新建表和恢复数据。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## REPAIRED

```TypeScript
REPAIRED = 2
```

表示数据库进行了修复，恢复了未损坏的数据，当前只有向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）具备该能力。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
