# DataSharePredicates（系统接口）

提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 10

<!--Device-dataSharePredicates-class DataSharePredicates--><!--Device-dataSharePredicates-class DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## and

```TypeScript
and(): DataSharePredicates
```

该接口用于将和条件添加到谓词中。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-and(): DataSharePredicates--><!--Device-DataSharePredicates-and(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回带有和条件的谓词。 |

**示例：**

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

该接口用于配置谓词以匹配值等于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。value为undefined或者null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");

```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataSharePredicates
```

该接口用于配置谓词以匹配值在指定范围内的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |
| value | Array&lt;ValueType&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.in("AGE", [18, 20]);

```

## limit

```TypeScript
limit(total: number, offset: number): DataSharePredicates
```

该接口用于配置谓词以指定结果数和起始位置。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates--><!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | number | 是 | 最大数据记录数。当使用键值型数据库且total为undefined或null时，会限制最大记录数为0。当使用关系型数据库且total为undefined或null时，不会限制最大记录数。当使用键值型数据库时，取值范围参考[键值型数据库limit接口](arkts-arkdata-distributedkvstore-query-c.md#limit)中的total参数说明。当使用关系型数据库时，取值范围参考[关系型数据库limitAs接口](@ohos.data.relationalStore:relationalStore.RdbPredicates.limitAs)中的value参数说明。 |
| offset | number | 是 | 指定查询结果的起始位置。当offset为undefined或null时，起始位置为结果集的最前端。当使用键值型数据库时，取值范围参考[键值型数据库limit接口](arkts-arkdata-distributedkvstore-query-c.md#limit)中的offset参数说明。当使用关系型数据库时，取值范围参考[关系型数据库offsetAs接口](@ohos.data.relationalStore:relationalStore.RdbPredicates.offsetAs)中的rowOffset参数说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").limit(10, 3);

```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按升序排序的列。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

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

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByAsc("AGE");

```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按降序排序的列。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

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

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByDesc("AGE");

```

