# StoreConfig（系统接口）

```TypeScript
interface StoreConfig
```

管理关系数据库配置。

**起始版本：** 9

<!--Device-relationalStore-interface StoreConfig--><!--Device-relationalStore-interface StoreConfig-End-->

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

<!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean--><!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## dumpStackOnFileDel

```TypeScript
dumpStackOnFileDel?: boolean
```

RDB存储是否开启dump-stack on文件删除开关，用于定位数据库文件被意外删除问题。

**true**：启用文件删除时转储堆栈功能。打开RDB存储后，文件系统输出直接删除数据库文件（**db**、**wal**、**shm**）时删除操作堆栈（通过文件接口）。

**false**（默认）：删除文件时禁用dump-stack。

该参数只对主备数据库的**db**、**wal**、**shm**文件生效，不包括数据库辅助文件（如日志文件和binlog文件）。

该参数依赖于设备文件系统的dump-stack能力。如果文件系统不支持该能力，则该参数不生效，不影响打开RDB存储。

默认值：false。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StoreConfig-dumpStackOnFileDel?: boolean--><!--Device-StoreConfig-dumpStackOnFileDel?: boolean-End-->

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

<!--Device-StoreConfig-haMode?: HAMode--><!--Device-StoreConfig-haMode?: HAMode-End-->

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

<!--Device-StoreConfig-isSearchable?: boolean--><!--Device-StoreConfig-isSearchable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。
