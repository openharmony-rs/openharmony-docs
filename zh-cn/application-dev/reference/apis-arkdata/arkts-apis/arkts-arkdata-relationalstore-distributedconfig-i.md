# DistributedConfig

记录表的分布式配置信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface DistributedConfig--><!--Device-relationalStore-interface DistributedConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## assetConflictPolicy

```TypeScript
assetConflictPolicy?: AssetConflictPolicy
```

资产冲突策略。默认值为CONFLICT\_POLICY\_DEFAULT。

**类型：** AssetConflictPolicy

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedConfig-assetConflictPolicy?: AssetConflictPolicy--><!--Device-DistributedConfig-assetConflictPolicy?: AssetConflictPolicy-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## assetDownloadOnDemand

```TypeScript
assetDownloadOnDemand?: boolean
```

是否按需下载资产。true表示仅下行数据到本地，当需要下载资产时，调用[cloudSyncEx]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口触发资产下载；false表示数据与资产 都下行到本地。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedConfig-assetDownloadOnDemand?: boolean--><!--Device-DistributedConfig-assetDownloadOnDemand?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## assetTempPath

```TypeScript
assetTempPath?: string
```

资产临时路径。仅当assetConflictPolicy值为CONFLICT\_POLICY\_TEMP\_PATH时生效，需指定为 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_下的临时路径，格式示例：tmp/，若未填写或路径不合规，将 抛出 401 错误码。默认值为空。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedConfig-assetTempPath?: string--><!--Device-DistributedConfig-assetTempPath?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## asyncDownloadAsset

```TypeScript
asyncDownloadAsset?: boolean
```

表示当前数据库在端云同步时，同步或异步下载资产。true表示优先下载完所有数据后，使用异步任务下载资产；false表示同步下载资产；默认值为false。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-DistributedConfig-asyncDownloadAsset?: boolean--><!--Device-DistributedConfig-asyncDownloadAsset?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoSync

```TypeScript
autoSync: boolean
```

表示该表是否支持端云自动同步。为true时，支持系统自动触发端云同步；为false时不支持系统自动触发端云同步，需要调用 [cloudSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口触发端云同步。

**类型：** boolean

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-DistributedConfig-autoSync: boolean--><!--Device-DistributedConfig-autoSync: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoSyncSwitch

```TypeScript
autoSyncSwitch?: boolean
```

是否启用自动同步开关。true表示启用自动同步，false表示不启用。默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedConfig-autoSyncSwitch?: boolean--><!--Device-DistributedConfig-autoSyncSwitch?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## enableCloud

```TypeScript
enableCloud?: boolean
```

表示当前数据库是否允许端云同步。true表示允许端云同步；false表示不允许端云同步。默认值为true。

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-DistributedConfig-enableCloud?: boolean--><!--Device-DistributedConfig-enableCloud?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## tableType

```TypeScript
tableType?: DistributedTableType
```

分布式表类型。DEVICE\_COLLABORATION表示设备协作表；SINGLE\_VERSION表示单版本表。跨设备数据同步时，默认值为DEVICE\_COLLABORATION；端云数据同步时，默认值为 SINGLE\_VERSION，不支持DEVICE\_COLLABORATION。

**类型：** DistributedTableType

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-DistributedConfig-tableType?: DistributedTableType--><!--Device-DistributedConfig-tableType?: DistributedTableType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

