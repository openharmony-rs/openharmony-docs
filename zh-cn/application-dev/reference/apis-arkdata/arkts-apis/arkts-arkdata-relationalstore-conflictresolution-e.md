# ConflictResolution

插入和修改接口的冲突解决模式。请使用枚举名称而非枚举值。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-enum ConflictResolution--><!--Device-relationalStore-enum ConflictResolution-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_NONE

```TypeScript
ON_CONFLICT_NONE = 0
```

表示当冲突发生时，不做任何处理。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_NONE = 0--><!--Device-ConflictResolution-ON_CONFLICT_NONE = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_ROLLBACK

```TypeScript
ON_CONFLICT_ROLLBACK = 1
```

表示当冲突发生时，中止SQL语句并回滚当前事务。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_ROLLBACK = 1--><!--Device-ConflictResolution-ON_CONFLICT_ROLLBACK = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_ABORT

```TypeScript
ON_CONFLICT_ABORT = 2
```

表示当冲突发生时，中止当前SQL语句，并撤销当前 SQL 语句所做的任何更改，但是由同一事务中先前的 SQL 语句引起的更改被保留并且事务保持活动状态。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_ABORT = 2--><!--Device-ConflictResolution-ON_CONFLICT_ABORT = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_FAIL

```TypeScript
ON_CONFLICT_FAIL = 3
```

表示当冲突发生时，中止当前 SQL 语句。但它不会撤销失败的 SQL 语句的先前更改，也不会结束事务。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_FAIL = 3--><!--Device-ConflictResolution-ON_CONFLICT_FAIL = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_IGNORE

```TypeScript
ON_CONFLICT_IGNORE = 4
```

表示当冲突发生时，跳过包含违反约束的行并继续处理 SQL 语句的后续行。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_IGNORE = 4--><!--Device-ConflictResolution-ON_CONFLICT_IGNORE = 4-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ON_CONFLICT_REPLACE

```TypeScript
ON_CONFLICT_REPLACE = 5
```

表示当冲突发生时，在插入或更新当前行之前删除导致约束违例的预先存在的行，并且命令会继续正常执行。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ConflictResolution-ON_CONFLICT_REPLACE = 5--><!--Device-ConflictResolution-ON_CONFLICT_REPLACE = 5-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

