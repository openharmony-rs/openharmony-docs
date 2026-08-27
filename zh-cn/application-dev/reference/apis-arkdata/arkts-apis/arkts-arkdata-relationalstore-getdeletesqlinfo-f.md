# getDeleteSqlInfo

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## getDeleteSqlInfo

```TypeScript
function getDeleteSqlInfo(predicates: RdbPredicates):SqlInfo
```

获取用于删除数据的SQL语句，此为同步接口。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | 与指定字段匹配的谓词。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SqlInfo](arkts-arkdata-relationalstore-sqlinfo-i.md) | SqlInfo对象，其中sql为返回的SQL语句，args为执行SQL中的参数信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |

**示例**

```TypeScript
const predicates = new relationalStore.RdbPredicates("users");
predicates.equalTo("tableName", "a");
predicates.notEqualTo("age", 18);
const sqlInfo: relationalStore.SqlInfo = relationalStore.getDeleteSqlInfo(predicates);
```
