# getUpdateSqlInfo

## getUpdateSqlInfo

```TypeScript
function getUpdateSqlInfo(predicates: RdbPredicates, values: ValuesBucket, conflict?: ConflictResolution):SqlInfo
```

获取用于更新数据的SQL语句，此为同步接口。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-function getUpdateSqlInfo(predicates: RdbPredicates, values: ValuesBucket, conflict?: ConflictResolution):SqlInfo--><!--Device-relationalStore-function getUpdateSqlInfo(predicates: RdbPredicates, values: ValuesBucket, conflict?: ConflictResolution):SqlInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 与指定字段匹配的谓词。 |
| values | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要写入数据库中数据的字段信息以及对应的值信息。 |
| conflict | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 指定冲突解决模式。 默认值是relationalStore.ConflictResolution.ON\_\_\_ESCAPED\_UNDERSCORE\_\_\_CONFLICT\_\_\_ESCAPED\_UNDERSCORE\_\_\_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | SqlInfo对象，其中sql为返回的SQL语句，args为执行SQL中的参数信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
const bucket: relationalStore.ValuesBucket = {
  name: "Logitech",
  age: 18,
  sex: "man",
  desc: "asserter"
};
const predicates = new relationalStore.RdbPredicates("users");
const sqlInfo: relationalStore.SqlInfo = relationalStore.getUpdateSqlInfo(
  predicates,
  bucket,
  relationalStore.ConflictResolution.ON_CONFLICT_NONE
);
```

ArkTS-Sta示例：

```TypeScript
const bucket: relationalStore.ValuesBucket = {
  'name': "Logitech",
  'age': 18 as long,
  'sex': "man",
  'desc': "asserter"
};
const predicates = new relationalStore.RdbPredicates("users");
const sqlInfo: relationalStore.SqlInfo = relationalStore.getUpdateSqlInfo(
  predicates,
  bucket,
  relationalStore.ConflictResolution.ON_CONFLICT_NONE
);
```

