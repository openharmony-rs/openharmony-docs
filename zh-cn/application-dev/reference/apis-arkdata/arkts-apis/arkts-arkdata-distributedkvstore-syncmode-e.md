# SyncMode

同步模式枚举。

**起始版本：** 9

<!--Device-distributedKVStore-enum SyncMode--><!--Device-distributedKVStore-enum SyncMode-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PULL_ONLY

```TypeScript
PULL_ONLY
```

表示只能从远端拉取数据到本端。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncMode-PULL_ONLY--><!--Device-SyncMode-PULL_ONLY-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_ONLY

```TypeScript
PUSH_ONLY
```

表示只能从本端推送数据到远端。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncMode-PUSH_ONLY--><!--Device-SyncMode-PUSH_ONLY-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_PULL

```TypeScript
PUSH_PULL
```

表示从本端推送数据到远端，然后从远端拉取数据到本端。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncMode-PUSH_PULL--><!--Device-SyncMode-PUSH_PULL-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

