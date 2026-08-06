# CloudSyncConfig

云同步配置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-relationalStore-interface CloudSyncConfig--><!--Device-relationalStore-interface CloudSyncConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## downloadOnly

```TypeScript
downloadOnly?: boolean
```

是否仅下行云端数据到本地。true表示仅下行云端数据到本地，false表示先下行云端数据到本地，再上行本地数据到云侧的同步流程。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudSyncConfig-downloadOnly?: boolean--><!--Device-CloudSyncConfig-downloadOnly?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

