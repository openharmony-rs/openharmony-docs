# DataSharePredicates（系统接口）

提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-dataSharePredicates-class DataSharePredicates--><!--Device-dataSharePredicates-class DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## and

```TypeScript
and(): DataSharePredicates
```

该接口用于将和条件添加到谓词中。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-and(): DataSharePredicates--><!--Device-DataSharePredicates-and(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回带有和条件的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .and()
    .equalTo("SALARY", 200.5);
```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值等于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | 是 | 指示要与谓词匹配的值。value为undefined或者null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataSharePredicates
```

该接口用于配置谓词以匹配值在指定范围内的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |
| value | Array&lt;[ValueType](arkts-arkdata-valuetype-t.md)&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.in("AGE", [18, 20]);
```

## inValues

```TypeScript
inValues(field: string, value: Array<ValueType>): DataSharePredicates
```

Configure {@code DataSharePredicates} to match the specified field whose data type is ValueType array and values are within a given range. Currently only used for RDB and KVDB(schema).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-inValues(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-inValues(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | Indicates the column name in the database table. |
| value | Array&lt;[ValueType](arkts-arkdata-valuetype-t.md)&gt; | 是 | Indicates the values to match with DataSharePredicates. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Returns DataSharePredicates that matches the specified field. |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inValues("AGE", [18, 20]);
```

## limit

```TypeScript
limit(total: int, offset: int): DataSharePredicates
```

该接口用于配置谓词以指定结果数和起始位置。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates--><!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | int | 是 | 最大数据记录数。当使用键值型数据库且total为undefined或null时，会限制最大记录数为0。当使用关系型数据库且total为undefined或 null时，不会限制最大记录数。当使用键值型数据库时，取值范围参考 [键值型数据库limit接口](arkts-arkdata-distributedkvstore-query-c.md#limit)中的total参数说明。当使用关系型数据库 时，取值范围参考[关系型数据库limitAs接口](arkts-arkdata-relationalstore-rdbpredicates-c.md#limitAs)中的value参数说明。 |
| offset | int | 是 | 指定查询结果的起始位置。当offset为undefined或null时，起始位置为结果集的最前端。当使用键值型数据库时，取值范围参考 [键值型数据库limit接口](arkts-arkdata-distributedkvstore-query-c.md#limit)中的offset参数说明。当使用关系型数据 库时，取值范围参考[关系型数据库offsetAs接口](arkts-arkdata-relationalstore-rdbpredicates-c.md#offsetAs)中的 rowOffset参数说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").limit(10, 3);
```

## notInValues

```TypeScript
notInValues(field: string, value: Array<ValueType>): DataSharePredicates
```

Configure {@code DataSharePredicates} to match the specified field whose data type is String array and values are out of a given range. Currently only used for RDB and KVDB(schema).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-notInValues(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-notInValues(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | Indicates the column name in the database table. |
| value | Array&lt;[ValueType](arkts-arkdata-valuetype-t.md)&gt; | 是 | Indicates the values to match with DataSharePredicates. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | Returns DataSharePredicates that matches the specified field. |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notInValues("NAME", ["Lisa", "Rose"]);
```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按升序排序的列。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-orderByAsc(field: string): DataSharePredicates--><!--Device-DataSharePredicates-orderByAsc(field: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 field为undefined或者null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByAsc("AGE");
```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按降序排序的列。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-orderByDesc(field: string): DataSharePredicates--><!--Device-DataSharePredicates-orderByDesc(field: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

## 示例

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByDesc("AGE");
```

