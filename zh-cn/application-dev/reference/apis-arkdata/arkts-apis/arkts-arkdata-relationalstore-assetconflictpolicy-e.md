# AssetConflictPolicy

资产冲突策略枚举。请使用枚举名称而非枚举值。

**起始版本：** 26.0.0

<!--Device-relationalStore-enum AssetConflictPolicy--><!--Device-relationalStore-enum AssetConflictPolicy-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CONFLICT_POLICY_DEFAULT

```TypeScript
CONFLICT_POLICY_DEFAULT = 0
```

默认冲突策略，按照端云同步模式[SyncMode](arkts-arkdata-relationalstore-syncmode-e.md)执行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetConflictPolicy-CONFLICT_POLICY_DEFAULT = 0--><!--Device-AssetConflictPolicy-CONFLICT_POLICY_DEFAULT = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CONFLICT_POLICY_TIME_FIRST

```TypeScript
CONFLICT_POLICY_TIME_FIRST = 1
```

基于时间优先的冲突策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetConflictPolicy-CONFLICT_POLICY_TIME_FIRST = 1--><!--Device-AssetConflictPolicy-CONFLICT_POLICY_TIME_FIRST = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CONFLICT_POLICY_TEMP_PATH

```TypeScript
CONFLICT_POLICY_TEMP_PATH = 2
```

基于临时路径的冲突策略。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AssetConflictPolicy-CONFLICT_POLICY_TEMP_PATH = 2--><!--Device-AssetConflictPolicy-CONFLICT_POLICY_TEMP_PATH = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

