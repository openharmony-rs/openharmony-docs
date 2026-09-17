# StoreConfig

管理关系数据库配置。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## autoCleanDeviceDirtyData

```TypeScript
autoCleanDeviceDirtyData?: boolean
```

指定本地设备是否自动清理远端设备删除后同步过来的数据，true表示自动清理，false表示手动清理，默认自动清理。若设置为false，需要主动调用[cleanDeviceDirtyData](arkts-arkdata-relationalstore-rdbstore-i-sys.md#cleandevicedirtydata)进行脏数据清理。

[数据同步存储机制](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/database/data-sync-of-rdb-store.md#数据同步存储机制)分布式数据表配置不生效。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## haMode

```TypeScript
haMode?: HAMode
```

指定关系型数据库存储的高可用性模式，SINGLE表示将数据写入单个关系型数据库存储，MAIN_REPLICA表示将数据写入主关系型数据库存储和副本关系型数据库存储，但不支持加密场景和attach场景。MAIN_REPLICA会导致数据库写入性能的劣化，默认为SINGLE。

**系统接口：** 此接口为系统接口。

从API version 12开始，支持此可选参数。

**类型：** [HAMode](arkts-arkdata-relationalstore-hamode-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## isSearchable

```TypeScript
isSearchable?: boolean
```

指定数据库是否支持搜索，true表示支持搜索，false表示不支持搜索，默认不支持搜索。

**系统接口：** 此接口为系统接口。

从API version 11开始，支持此可选参数。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。
