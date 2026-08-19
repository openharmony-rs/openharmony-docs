# ExceptionMessage

描述数据库执行的SQL语句的错误信息。

**起始版本：** 23

<!--Device-relationalStore-interface ExceptionMessage--><!--Device-relationalStore-interface ExceptionMessage-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## code

```TypeScript
code: int
```

表示执行SQL返回的错误码，对应的取值和含义请见[SQLite错误码](https://www.sqlite.org/rescode.html)。

**类型：** int

**起始版本：** 23

<!--Device-ExceptionMessage-code: int--><!--Device-ExceptionMessage-code: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
message: string
```

表示执行SQL返回的错误信息，长度不超过1024字节。

**类型：** string

**起始版本：** 23

<!--Device-ExceptionMessage-message: string--><!--Device-ExceptionMessage-message: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## sql

```TypeScript
sql: string
```

表示报错执行的SQL语句，长度不超过1024字节。

**类型：** string

**起始版本：** 23

<!--Device-ExceptionMessage-sql: string--><!--Device-ExceptionMessage-sql: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

