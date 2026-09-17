# DistributedTableType

分布式表类型的枚举。请使用枚举名称而非枚举值。此配置项为数据库级配置，如果数据库中有多张分布式表，则所有表必须使用相同的分布式表类型，且不支持切换升级。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## DEVICE_COLLABORATION

```TypeScript
DEVICE_COLLABORATION = 0
```

多设备协同表，各设备的数据将被隔离存储在独立的分布式表中，而非写入本地表，分布式表名为在原来表名前拼接对端设备的DeviceID标识符。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SINGLE_VERSION

```TypeScript
SINGLE_VERSION = 1
```

单版本表，数据通过分布式数据管理框架直接写入对端设备的本地表中。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
