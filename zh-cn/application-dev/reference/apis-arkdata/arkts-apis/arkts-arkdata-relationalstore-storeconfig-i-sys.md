# StoreConfig

管理关系数据库配置。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface StoreConfig--><!--Device-relationalStore-interface StoreConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoCleanDeviceDirtyData

```TypeScript
autoCleanDeviceDirtyData?: boolean
```

指定本地设备是否自动清理远端设备删除后同步过来的数据，true表示自动清理，false表示手动清理，默认自动清理。若设置为false，需要主动调用 [cleanDeviceDirtyData]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_进行脏数据清理。 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_分布式数据表配置不生效。 **系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean--><!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## haMode

```TypeScript
haMode?: HAMode
```

指定关系型数据库存储的高可用性模式，SINGLE表示将数据写入单个关系型数据库存储，MAIN\_REPLICA表示将数据写入主关系型数据库存储和副本关系型数据库存储，但不支持加密场景和attach场景。MAIN\_REPLICA会 导致数据库写入性能的劣化，默认为SINGLE。 **系统接口：** 此接口为系统接口。 从API version 12开始，支持此可选参数。

**类型：** HAMode

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-StoreConfig-haMode?: HAMode--><!--Device-StoreConfig-haMode?: HAMode-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## isSearchable

```TypeScript
isSearchable?: boolean
```

指定数据库是否支持搜索，true表示支持搜索，false表示不支持搜索，默认不支持搜索。 **系统接口：** 此接口为系统接口。 从API version 11开始，支持此可选参数。

**类型：** boolean

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-StoreConfig-isSearchable?: boolean--><!--Device-StoreConfig-isSearchable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

