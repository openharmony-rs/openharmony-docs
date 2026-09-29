# SqlInfo

```TypeScript
interface SqlInfo
```

描述数据库执行的SQL语句的详细信息。

**起始版本：** 20

<!--Device-relationalStore-interface SqlInfo--><!--Device-relationalStore-interface SqlInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## args

```TypeScript
args: Array<ValueType>
```

表示执行SQL中的参数信息。

**类型：** Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt;

**起始版本：** 20

<!--Device-SqlInfo-args: Array<ValueType>--><!--Device-SqlInfo-args: Array<ValueType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: string
```

表示执行的SQL语句。

**类型：** string

**起始版本：** 20

<!--Device-SqlInfo-sql: string--><!--Device-SqlInfo-sql: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
