# SyncMode

同步模式枚举。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SyncMode

<!--Device-distributedData-enum SyncMode--><!--Device-distributedData-enum SyncMode-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PULL_ONLY

```TypeScript
PULL_ONLY = 0
```

表示只能从远端拉取数据到本端。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** PULL_ONLY

<!--Device-SyncMode-PULL_ONLY = 0--><!--Device-SyncMode-PULL_ONLY = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_ONLY

```TypeScript
PUSH_ONLY = 1
```

表示只能从本端推送数据到远端。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** PUSH_ONLY

<!--Device-SyncMode-PUSH_ONLY = 1--><!--Device-SyncMode-PUSH_ONLY = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## PUSH_PULL

```TypeScript
PUSH_PULL = 2
```

表示从本端推送数据到远端，然后从远端拉取数据到本端。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** PUSH_PULL

<!--Device-SyncMode-PUSH_PULL = 2--><!--Device-SyncMode-PUSH_PULL = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

