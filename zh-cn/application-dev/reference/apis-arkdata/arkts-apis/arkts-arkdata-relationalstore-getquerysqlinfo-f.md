# getQuerySqlInfo

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## getQuerySqlInfo

```TypeScript
function getQuerySqlInfo(predicates: RdbPredicates, columns?: Array<string>):SqlInfo
```

获取用于查询数据的SQL语句，此为同步接口。

**起始版本：** 23

<!--Device-relationalStore-function getQuerySqlInfo(predicates: RdbPredicates, columns?: Array<string>):SqlInfo--><!--Device-relationalStore-function getQuerySqlInfo(predicates: RdbPredicates, columns?: Array<string>):SqlInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | 与指定字段匹配的谓词。 |
| columns | Array&lt;string&gt; | 否 | 要查询的列；如果不指定此参数，则查询所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SqlInfo](arkts-arkdata-relationalstore-sqlinfo-i.md) | SqlInfo对象，其中sql为返回的SQL语句，args为执行SQL中的参数信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |

**示例**

ArkTS-Dyn示例：

```TypeScript
const predicates = new relationalStore.RdbPredicates("users");
predicates.notEqualTo("age", 18);
predicates.equalTo("name", "zhangsan");
const sqlInfo: relationalStore.SqlInfo = relationalStore.getQuerySqlInfo(predicates);
```

ArkTS-Sta示例：

```TypeScript
const predicates = new relationalStore.RdbPredicates("users");
predicates.notEqualTo("age", 18 as long);
predicates.equalTo("name", "zhangsan");
const sqlInfo: relationalStore.SqlInfo = relationalStore.getQuerySqlInfo(predicates);
```

