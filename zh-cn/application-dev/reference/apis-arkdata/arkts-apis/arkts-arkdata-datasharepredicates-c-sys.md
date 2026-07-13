# DataSharePredicates（系统接口）

提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## beginWrap

```TypeScript
beginWrap(): DataSharePredicates
```

该接口用于向谓词添加左括号，相当于sql语句的“(”，必须和右括号一起使用。

目前仅关系型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回带有左括号的谓词。 |

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

该接口用于配置谓词以匹配值以指定字符串起始的字段。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值以该字符串起始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.beginsWith("NAME", "os");

```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值在指定范围内的字段。包含两端边界值，为左闭右闭区间。

目前仅关系型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| low | ValueType | 是 | 指示与谓词匹配的最小值。low为number时，按数值排序指定匹配范围。low为string时，按字典序排序指定匹配范围。low为boolean时，按数值排序指定匹配范围。 |
| high | ValueType | 是 | 指示与谓词匹配的最大值。high为number时，按数值排序指定匹配范围。high为string时，按字典序排序指定匹配范围。high为boolean时，按数值排序指定匹配范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.between("AGE", 10, 50);

```

## contains

```TypeScript
contains(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值包含指定字段的字段。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值中包含该字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.contains("NAME", "os");

```

## distinct

```TypeScript
distinct(): DataSharePredicates
```

该接口用于配置谓词以过滤重复记录并仅保留其中一个。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").distinct();

```

## endWrap

```TypeScript
endWrap(): DataSharePredicates
```

该接口用于向谓词添加右括号，相当于sql语句的“)”，必须和左括号一起使用。

目前仅关系型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回带有右括号的谓词。 |

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

该接口用于配置谓词以匹配值以指定字符串结尾的字段。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示值以该字符串结尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.endsWith("NAME", "os");

```

## glob

```TypeScript
glob(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配指定通配符表达式的字段。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。表达式中'*'代表零个、一个或多个数字或字符，'?'代表一个单一的数字或字符，区分大小写。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.glob("NAME", "?h*g");

```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值大于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThan("AGE", 10);

```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值大于或等于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，此次调用接口配置的谓词匹配结果非预期或抛出异常。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThanOrEqualTo("AGE", 10);

```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataSharePredicates
```

该接口用于配置谓词按指定列分组查询结果。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;string&gt; | 是 | 指定分组依赖的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.groupBy(["AGE", "NAME"]);

```

## inKeys

```TypeScript
inKeys(keys: Array<string>): DataSharePredicates
```

该接口用于配置谓词以匹配键在指定范围内的字段。

目前仅KVDB支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 是 | 指定范围的键数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inKeys(["Lisa", "Rose"]);

```

## indexedBy

```TypeScript
indexedBy(field: string): DataSharePredicates
```

该接口用于配置谓词按指定索引列查询结果。使用该方法前，需要设置索引列。

目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 索引列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.indexedBy("SALARY_INDEX");

```

## isNotNull

```TypeScript
isNotNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值不为null的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNotNull("NAME");

```

## isNull

```TypeScript
isNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值为null的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | **DataSharePredicates** object created. |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNull("NAME");

```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值小于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。当field为null或undefined时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThan("AGE", 50);

```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值小于或等于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThanOrEqualTo("AGE", 50);

```

## like

```TypeScript
like(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配指定通配符表达式的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。 表达式中'%'代表零个、一个或多个数字或字符，'_'代表一个单一的数字或字符，不区分大小写。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.like("NAME", "%os%");

```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值超出指定范围的字段。不包含两端边界值，为左开右开区间。

目前仅关系型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| low | ValueType | 是 | 指示与谓词匹配的最小值。low为number时，按数值排序指定匹配范围。low为string时，按字典序排序指定匹配范围。low为boolean时，按数值排序指定匹配范围。 |
| high | ValueType | 是 | 指示与谓词匹配的最大值。high为number时，按数值排序指定匹配范围。high为string时，按字典序排序指定匹配范围。high为boolean时，按数值排序指定匹配范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notBetween("AGE", 10, 50);

```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): DataSharePredicates
```

该接口用于配置谓词以匹配值不等于指定值的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。当field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notEqualTo("NAME", "Rose");

```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): DataSharePredicates
```

该接口用于配置谓词以匹配值不在指定范围内的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。field为undefined或null时，此次调用接口配置的谓词无效。当field为字符串'null'或'undefined'时，键值型数据库和关系型数据库接口使用该谓词时，可能匹配结果非预期或抛出异常。 |
| value | Array&lt;ValueType&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。value为undefined或null时，此次调用接口配置的谓词无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notIn("NAME", ["Lisa", "Rose"]);

```

## or

```TypeScript
or(): DataSharePredicates
```

该接口用于将或条件添加到谓词中。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回带有或条件的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates()
predicates.equalTo("NAME", "lisi")
    .or()
    .equalTo("NAME", "Rose");

```

## prefixKey

```TypeScript
prefixKey(prefix: string): DataSharePredicates
```

该接口用于配置谓词以匹配键前缀的指定字段。

目前仅KVDB支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 指定的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.prefixKey("NAME");

```

## unlike

```TypeScript
unlike(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配不类似指定通配符表达式的字段。

目前仅关系型数据库及键值型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的通配符表达式。表达式中'%'代表零个、一个或多个数字或字符，'_'代表一个单一的数字或字符，不区分大小写。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataSharePredicates | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.unlike("NAME", "%os%");

```

