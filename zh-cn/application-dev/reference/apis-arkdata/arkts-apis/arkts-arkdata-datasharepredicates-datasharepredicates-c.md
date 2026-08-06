# DataSharePredicates

提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-dataSharePredicates-class DataSharePredicates--><!--Device-dataSharePredicates-class DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

## and

```TypeScript
and(): DataSharePredicates
```

该接口用于将和条件添加到谓词中。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-and(): DataSharePredicates--><!--Device-DataSharePredicates-and(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回带有和条件的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .and()
    .equalTo("SALARY", 200.5);
```

## beginWrap

```TypeScript
beginWrap(): DataSharePredicates
```

该接口用于向谓词添加左括号，相当于sql语句的“(”，必须和右括号一起使用。 目前仅关系型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-beginWrap(): DataSharePredicates--><!--Device-DataSharePredicates-beginWrap(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回带有左括号的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值以指定字符串起始的字段。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-beginsWith(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-beginsWith(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值以该字符串起始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.beginsWith("NAME", "os");
```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值在指定范围内的字段。包含两端边界值，为左闭右闭区间。 目前仅关系型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-between(field: string, low: ValueType, high: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-between(field: string, low: ValueType, high: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| low | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示与谓词匹配的最小值。low为number时，按数值排序指定匹配范围。low为string时，按字典序排序指定匹配范围。low为boolean时，按数值排序指定匹配范围。 |
| high | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示与谓词匹配的最大值。high为number时，按数值排序指定匹配范围。high为string时，按字典序排序指定匹配范围。high为boolean时，按数值排序指定匹配范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.between("AGE", 10, 50);
```

## contains

```TypeScript
contains(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值包含指定字段的字段。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-contains(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-contains(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值中包含该字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.contains("NAME", "os");
```

## distinct

```TypeScript
distinct(): DataSharePredicates
```

该接口用于配置谓词以过滤重复记录并仅保留其中一个。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-distinct(): DataSharePredicates--><!--Device-DataSharePredicates-distinct(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").distinct();
```

## endWrap

```TypeScript
endWrap(): DataSharePredicates
```

该接口用于向谓词添加右括号，相当于sql语句的“)”，必须和左括号一起使用。 目前仅关系型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-endWrap(): DataSharePredicates--><!--Device-DataSharePredicates-endWrap(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回带有右括号的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## endsWith

```TypeScript
endsWith(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值以指定字符串结尾的字段。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-endsWith(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-endsWith(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值以该字符串结尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.endsWith("NAME", "os");
```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值等于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或者null时，此次调用接口配置的谓词无效。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或者null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
```

## glob

```TypeScript
glob(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配指定通配符表达式的字段。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-glob(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-glob(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。表达式中'*'代表零个、一个或多个数字或字符，'?'代表一个单一的数字或字符，区分大小写。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.glob("NAME", "?h*g");
```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值大于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-greaterThan(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-greaterThan(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThan("AGE", 10);
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值大于或等于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，此次调用接口配置的谓词匹配结果非预期或抛出异常。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThanOrEqualTo("AGE", 10);
```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataSharePredicates
```

该接口用于配置谓词按指定列分组查询结果。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-groupBy(fields: Array<string>): DataSharePredicates--><!--Device-DataSharePredicates-groupBy(fields: Array<string>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;string&gt; | 是 | 指定分组依赖的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.groupBy(["AGE", "NAME"]);
```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataSharePredicates
```

该接口用于配置谓词以匹配值在指定范围内的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

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
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.in("AGE", [18, 20]);
```

## inKeys

```TypeScript
inKeys(keys: Array<string>): DataSharePredicates
```

该接口用于配置谓词以匹配键在指定范围内的字段。 目前仅KVDB支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-inKeys(keys: Array<string>): DataSharePredicates--><!--Device-DataSharePredicates-inKeys(keys: Array<string>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 是 | 指定范围的键数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inKeys(["Lisa", "Rose"]);
```

## inValues

```TypeScript
inValues(field: string, value: Array<ValueType>): DataSharePredicates
```

Configure {@code DataSharePredicates} to match the specified field whose data type is ValueType array and values are within a given range. Currently only used for RDB and KVDB(schema).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-inValues(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-inValues(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | Indicates the column name in the database table. |
| value | Array&lt;ValueType&gt; | 是 | Indicates the values to match with DataSharePredicates. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns DataSharePredicates that matches the specified field. |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inValues("AGE", [18, 20]);
```

## indexedBy

```TypeScript
indexedBy(field: string): DataSharePredicates
```

该接口用于配置谓词按指定索引列查询结果。使用该方法前，需要设置索引列。 目前仅关系型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-indexedBy(field: string): DataSharePredicates--><!--Device-DataSharePredicates-indexedBy(field: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 索引列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.indexedBy("SALARY_INDEX");
```

## isNotNull

```TypeScript
isNotNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值不为null的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-isNotNull(field: string): DataSharePredicates--><!--Device-DataSharePredicates-isNotNull(field: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNotNull("NAME");
```

## isNull

```TypeScript
isNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值为null的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-isNull(field: string): DataSharePredicates--><!--Device-DataSharePredicates-isNull(field: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | **DataSharePredicates** object created. |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNull("NAME");
```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值小于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-lessThan(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-lessThan(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。当field为null或undefined时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThan("AGE", 50);
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值小于或等于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThanOrEqualTo("AGE", 50);
```

## like

```TypeScript
like(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配指定通配符表达式的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-like(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-like(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。 表达式中'%'代表零个、一个或多个数字或字符，'\_\_\_ESCAPED\_UNDERSCORE\_\_\_'代表一个单一的数字或字符，不区分大小写。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.like("NAME", "%os%");
```

## limit

ArkTS-Dyn:
```TypeScript
limit(total: number, offset: number): DataSharePredicates
```

ArkTS-Sta:
```TypeScript
limit(total: int, offset: int): DataSharePredicates
```

该接口用于配置谓词以指定结果数和起始位置。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates--><!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 最大数据记录数。当使用键值型数据库且total为undefined或null时，会限制最大记录数为0。当使用关系型数据库且total为undefined或null时，不会限制最大记录数。当使用键值型数据库时，取值范围参考[键值型数据库limit接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的total参数说明。当使用关系型数据库时，取值范围参考[关系型数据库limitAs接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的value参数说明。 |
| offset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定查询结果的起始位置。当offset为undefined或null时，起始位置为结果集的最前端。当使用键值型数据库时，取值范围参考[键值型数据库limit接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的offset参数说明。当使用关系型数据库时，取值范围参考[关系型数据库offsetAs接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的rowOffset参数说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").limit(10, 3);
```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值超出指定范围的字段。不包含两端边界值，为左开右开区间。 目前仅关系型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| low | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示与谓词匹配的最小值。low为number时，按数值排序指定匹配范围。low为string时，按字典序排序指定匹配范围。low为boolean时，按数值排序指定匹配范围。 |
| high | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示与谓词匹配的最大值。high为number时，按数值排序指定匹配范围。high为string时，按字典序排序指定匹配范围。high为boolean时，按数值排序指定匹配范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notBetween("AGE", 10, 50);
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值不等于指定值的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-notEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-notEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。当field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notEqualTo("NAME", "Rose");
```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): DataSharePredicates
```

该接口用于配置谓词以匹配值不在指定范围内的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-notIn(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-notIn(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | Array&lt;ValueType&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notIn("NAME", ["Lisa", "Rose"]);
```

## notInValues

```TypeScript
notInValues(field: string, value: Array<ValueType>): DataSharePredicates
```

Configure {@code DataSharePredicates} to match the specified field whose data type is String array and values are out of a given range. Currently only used for RDB and KVDB(schema).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-notInValues(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-notInValues(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | Indicates the column name in the database table. |
| value | Array&lt;ValueType&gt; | 是 | Indicates the values to match with DataSharePredicates. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns DataSharePredicates that matches the specified field. |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notInValues("NAME", ["Lisa", "Rose"]);
```

## or

```TypeScript
or(): DataSharePredicates
```

该接口用于将或条件添加到谓词中。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-or(): DataSharePredicates--><!--Device-DataSharePredicates-or(): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回带有或条件的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates()
predicates.equalTo("NAME", "lisi")
    .or()
    .equalTo("NAME", "Rose");
```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按升序排序的列。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

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
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByAsc("AGE");
```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配其值按降序排序的列。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

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
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByDesc("AGE");
```

## prefixKey

```TypeScript
prefixKey(prefix: string): DataSharePredicates
```

该接口用于配置谓词以匹配键前缀的指定字段。 目前仅KVDB支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-prefixKey(prefix: string): DataSharePredicates--><!--Device-DataSharePredicates-prefixKey(prefix: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 指定的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.prefixKey("NAME");
```

## unlike

```TypeScript
unlike(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配不类似指定通配符表达式的字段。 目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataSharePredicates-unlike(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-unlike(field: string, value: string): DataSharePredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。表达式中'%'代表零个、一个或多个数字或字符，'\_\_\_ESCAPED\_UNDERSCORE\_\_\_'代表一个单一的数字或字符，不区分大小写。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.unlike("NAME", "%os%");
```

