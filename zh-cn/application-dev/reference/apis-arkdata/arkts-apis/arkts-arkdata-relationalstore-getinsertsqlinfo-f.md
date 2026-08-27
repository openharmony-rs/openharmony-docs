# getInsertSqlInfo

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## getInsertSqlInfo

```TypeScript
function getInsertSqlInfo(table: string, values: ValuesBucket, conflict?: ConflictResolution):SqlInfo
```

获取用于插入数据的SQL语句，此为同步接口。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 要写入数据的数据库表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 要写入数据库中数据的字段信息以及对应的值信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

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
const bucket: relationalStore.ValuesBucket = {
  name: "Logitech",
  age: 18,
  sex: "man",
  desc: "asserter"
};
const sqlInfo: relationalStore.SqlInfo = relationalStore.getInsertSqlInfo(
  "USER",
  bucket,
  relationalStore.ConflictResolution.ON_CONFLICT_NONE
);
```
