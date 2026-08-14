# SqlExecutionInfo

描述数据库执行的SQL语句的统计信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface SqlExecutionInfo--><!--Device-relationalStore-interface SqlExecutionInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## executeTime

```TypeScript
executeTime: long
```

表示执行SQL语句的时间，单位为μs。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SqlExecutionInfo-executeTime: long--><!--Device-SqlExecutionInfo-executeTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## prepareTime

```TypeScript
prepareTime: long
```

表示准备SQL和绑定参数的时间，单位为μs。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SqlExecutionInfo-prepareTime: long--><!--Device-SqlExecutionInfo-prepareTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: Array<string>
```

表示执行的SQL语句的数组。当 [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchInsert) 的参数太大时，可能有多个SQL。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SqlExecutionInfo-sql: Array<string>--><!--Device-SqlExecutionInfo-sql: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## totalTime

```TypeScript
totalTime: long
```

表示执行SQL语句的总时间，单位为μs。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SqlExecutionInfo-totalTime: long--><!--Device-SqlExecutionInfo-totalTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## waitTime

```TypeScript
waitTime: long
```

表示获取句柄的时间，单位为μs。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SqlExecutionInfo-waitTime: long--><!--Device-SqlExecutionInfo-waitTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

