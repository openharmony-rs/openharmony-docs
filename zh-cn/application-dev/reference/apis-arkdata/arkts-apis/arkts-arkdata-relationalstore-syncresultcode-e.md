# SyncResultCode

描述设备同步状态的枚举。请使用枚举名称而非枚举值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-relationalStore-enum SyncResultCode--><!--Device-relationalStore-enum SyncResultCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

表示同步成功。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-SUCCESS = 0--><!--Device-SyncResultCode-SUCCESS = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## FAIL

```TypeScript
FAIL = 1
```

表示同步失败。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-FAIL = 1--><!--Device-SyncResultCode-FAIL = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## OFFLINE

```TypeScript
OFFLINE = 2
```

表示远端设备离线。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-OFFLINE = 2--><!--Device-SyncResultCode-OFFLINE = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## INVALID_ARGS

```TypeScript
INVALID_ARGS = 3
```

表示参数无效。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-INVALID_ARGS = 3--><!--Device-SyncResultCode-INVALID_ARGS = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## DISTRIBUTED_TABLE_NOT_SET

```TypeScript
DISTRIBUTED_TABLE_NOT_SET = 4
```

表示本端设备或远端设备未设置分布式表。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-DISTRIBUTED_TABLE_NOT_SET = 4--><!--Device-SyncResultCode-DISTRIBUTED_TABLE_NOT_SET = 4-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## TABLE_FIELD_MISMATCH

```TypeScript
TABLE_FIELD_MISMATCH = 5
```

表示对端设备与本端设备本地表的同步字段不一致。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-TABLE_FIELD_MISMATCH = 5--><!--Device-SyncResultCode-TABLE_FIELD_MISMATCH = 5-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## DISTRIBUTED_SCHEMA_MISMATCH

```TypeScript
DISTRIBUTED_SCHEMA_MISMATCH = 6
```

表示对端设备与本端设备分布式表的Schema字段不一致，或者存在一个分布式表没有配置Schema。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-DISTRIBUTED_SCHEMA_MISMATCH = 6--><!--Device-SyncResultCode-DISTRIBUTED_SCHEMA_MISMATCH = 6-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## BUSY

```TypeScript
BUSY = 7
```

表示数据库繁忙。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-BUSY = 7--><!--Device-SyncResultCode-BUSY = 7-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CORRUPTED

```TypeScript
CORRUPTED = 8
```

表示数据库损坏。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-CORRUPTED = 8--><!--Device-SyncResultCode-CORRUPTED = 8-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## TIMEOUT

```TypeScript
TIMEOUT = 9
```

表示同步操作因超时失败。常见原因包括：对端设备数据库未创建、连接中断或网络抖动导致丢包。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-TIMEOUT = 9--><!--Device-SyncResultCode-TIMEOUT = 9-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## SCHEMA_CHANGED

```TypeScript
SCHEMA_CHANGED = 10
```

表示在同步过程中表结构已更改。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-SCHEMA_CHANGED = 10--><!--Device-SyncResultCode-SCHEMA_CHANGED = 10-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CONSTRAINT_VIOLATION

```TypeScript
CONSTRAINT_VIOLATION = 11
```

表示同步数据时违反约束条件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResultCode-CONSTRAINT_VIOLATION = 11--><!--Device-SyncResultCode-CONSTRAINT_VIOLATION = 11-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

