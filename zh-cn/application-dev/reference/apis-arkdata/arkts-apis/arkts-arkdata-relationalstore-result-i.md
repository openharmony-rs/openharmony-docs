# Result

记录受影响的数据行数量和结果集。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-relationalStore-interface Result--><!--Device-relationalStore-interface Result-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## changed

```TypeScript
readonly changed: long
```

表示受影响的行数量。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Result-readonly changed: long--><!--Device-Result-readonly changed: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## resultSet

```TypeScript
readonly resultSet: LiteResultSet
```

表示受影响数据的结果集。默认返回1024行，最大支持32766行，超出部分将被丢弃。

**类型：** LiteResultSet

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Result-readonly resultSet: LiteResultSet--><!--Device-Result-readonly resultSet: LiteResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

