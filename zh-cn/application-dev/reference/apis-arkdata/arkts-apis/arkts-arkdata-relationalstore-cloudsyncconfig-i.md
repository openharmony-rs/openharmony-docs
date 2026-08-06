# CloudSyncConfig

云同步配置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-relationalStore-interface CloudSyncConfig--><!--Device-relationalStore-interface CloudSyncConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## enablePredicate

```TypeScript
enablePredicate?: boolean
```

是否启用表级同步开关。true表示启用表级同步，false表示不启用。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudSyncConfig-enablePredicate?: boolean--><!--Device-CloudSyncConfig-enablePredicate?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## mode

```TypeScript
mode: SyncMode
```

数据库同步模式。

**类型：** SyncMode

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudSyncConfig-mode: SyncMode--><!--Device-CloudSyncConfig-mode: SyncMode-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## predicate

```TypeScript
predicate?: RdbPredicates
```

表级同步谓词。仅当enablePredicate为true时，此参数有效。

**类型：** RdbPredicates

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudSyncConfig-predicate?: RdbPredicates--><!--Device-CloudSyncConfig-predicate?: RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

