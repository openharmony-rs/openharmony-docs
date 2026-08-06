# SqlExecutionInfo

描述数据库执行的SQL语句的统计信息。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface SqlExecutionInfo--><!--Device-relationalStore-interface SqlExecutionInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## executeTime

```TypeScript
executeTime: long
```

表示执行SQL语句的时间，单位为μs。

**类型：** long

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-SqlExecutionInfo-executeTime: long--><!--Device-SqlExecutionInfo-executeTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## prepareTime

```TypeScript
prepareTime: long
```

表示准备SQL和绑定参数的时间，单位为μs。

**类型：** long

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-SqlExecutionInfo-prepareTime: long--><!--Device-SqlExecutionInfo-prepareTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: Array<string>
```

表示执行的SQL语句的数组。当 [batchInsert]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 的参数太大时，可能有多个SQL。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-SqlExecutionInfo-sql: Array<string>--><!--Device-SqlExecutionInfo-sql: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## totalTime

```TypeScript
totalTime: long
```

表示执行SQL语句的总时间，单位为μs。

**类型：** long

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-SqlExecutionInfo-totalTime: long--><!--Device-SqlExecutionInfo-totalTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## waitTime

```TypeScript
waitTime: long
```

表示获取句柄的时间，单位为μs。

**类型：** long

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-SqlExecutionInfo-waitTime: long--><!--Device-SqlExecutionInfo-waitTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

