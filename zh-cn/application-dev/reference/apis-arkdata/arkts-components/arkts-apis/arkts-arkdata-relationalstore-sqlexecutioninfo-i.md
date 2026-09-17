# SqlExecutionInfo

描述数据库执行的SQL语句的统计信息。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## executeTime

```TypeScript
executeTime: number
```

表示执行SQL语句的时间，单位为μs。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## prepareTime

```TypeScript
prepareTime: number
```

表示准备SQL和绑定参数的时间，单位为μs。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: Array<string>
```

表示执行的SQL语句的数组。当[batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert)的参数太大时，可能有多个SQL。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## totalTime

```TypeScript
totalTime: number
```

表示执行SQL语句的总时间，单位为μs。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## waitTime

```TypeScript
waitTime: number
```

表示获取句柄的时间，单位为μs。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
