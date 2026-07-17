# DataAbilityPredicates

提供用于实现不同查询方法的谓词。

**起始版本：** 7

<!--Device-dataAbility-class DataAbilityPredicates--><!--Device-dataAbility-class DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

## 导入模块

```TypeScript
import { dataAbility } from '@kit.ArkData';
```

## and

```TypeScript
and(): DataAbilityPredicates
```

将和条件添加到谓词中。

**起始版本：** 7

<!--Device-DataAbilityPredicates-and(): DataAbilityPredicates--><!--Device-DataAbilityPredicates-and(): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回带有和条件的DataAbility谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Lisa")
    .and()
    .equalTo("SALARY", 200.5)

```

## beginWrap

```TypeScript
beginWrap(): DataAbilityPredicates
```

在谓词中添加左括号。此方法类似于SQL语句的“(”，需要与[endWrap](arkts-arkdata-dataability-dataabilitypredicates-c.md#endwrap-1)一起使用。

**起始版本：** 7

<!--Device-DataAbilityPredicates-beginWrap(): DataAbilityPredicates--><!--Device-DataAbilityPredicates-beginWrap(): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回带有左括号的DataAbility谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()

```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): DataAbilityPredicates
```

配置谓词以匹配数据类型为string且值以指定字符串开头的字段。

此方法类似于SQL语句的“value%”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-beginsWith(field: string, value: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-beginsWith(field: string, value: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.beginsWith("NAME", "os")

```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且value在指定范围内的指定字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| low | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示与谓词匹配的最小值。 |
| high | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示与谓词匹配的最大值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.between("AGE", 10, 50)

```

## contains

```TypeScript
contains(field: string, value: string): DataAbilityPredicates
```

配置谓词以匹配数据类型为string且value包含指定值的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-contains(field: string, value: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-contains(field: string, value: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.contains("NAME", "os")

```

## distinct

```TypeScript
distinct(): DataAbilityPredicates
```

配置谓词以过滤重复记录并仅保留其中一个。

**起始版本：** 7

<!--Device-DataAbilityPredicates-distinct(): DataAbilityPredicates--><!--Device-DataAbilityPredicates-distinct(): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回可用于过滤重复记录的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Rose").distinct()

```

## endWrap

```TypeScript
endWrap(): DataAbilityPredicates
```

在谓词中添加右括号。此方法类似于SQL语句的“)”，需要和[beginWrap](arkts-arkdata-dataability-dataabilitypredicates-c.md#beginwrap-1)一起使用。

**起始版本：** 7

<!--Device-DataAbilityPredicates-endWrap(): DataAbilityPredicates--><!--Device-DataAbilityPredicates-endWrap(): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回带有右括号的DataAbility谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()

```

## endsWith

```TypeScript
endsWith(field: string, value: string): DataAbilityPredicates
```

配置谓词以匹配数据类型为string且值以指定字符串结尾的字段。

此方法类似于SQL语句的“%value”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-endsWith(field: string, value: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-endsWith(field: string, value: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.endsWith("NAME", "se")

```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据，数据的指定字段数据类型为ValueType且值等于指定值。

此方法类似于SQL语句的“=”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-equalTo(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-equalTo(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi")

```

## glob

```TypeScript
glob(field: string, value: string): DataAbilityPredicates
```

配置谓词以匹配数据类型为string的指定字段。与like方法不同，该方法的输入参数区分大小写。

**起始版本：** 7

<!--Device-DataAbilityPredicates-glob(field: string, value: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-glob(field: string, value: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.glob("NAME", "?h*g")

// 仅可匹配到"NAME"字段值为"Lisa"
dataAbilityPredicates.glob("NAME", "Lisa")

// 仅可以匹配到"NAME"字段值为"lisa"
dataAbilityPredicates.glob("NAME", "lisa")

```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且值大于指定值的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-greaterThan(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-greaterThan(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.greaterThan("AGE", 18)

```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且value大于或等于指定值的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.greaterThanOrEqualTo("AGE", 18)

```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataAbilityPredicates
```

配置谓词按指定列分组查询结果。

**起始版本：** 7

<!--Device-DataAbilityPredicates-groupBy(fields: Array<string>): DataAbilityPredicates--><!--Device-DataAbilityPredicates-groupBy(fields: Array<string>): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 指定分组依赖的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回分组查询列的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.groupBy(["AGE", "NAME"])

```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType数组且值在给定范围内的指定字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-in(field: string, value: Array<ValueType>): DataAbilityPredicates--><!--Device-DataAbilityPredicates-in(field: string, value: Array<ValueType>): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ValueType> | 是 | 以ValueType类型数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.in("AGE", [18, 20])

```

## indexedBy

```TypeScript
indexedBy(field: string): DataAbilityPredicates
```

配置谓词以指定索引列。在使用此方法之前，您需要创建一个索引列。

**起始版本：** 7

<!--Device-DataAbilityPredicates-indexedBy(field: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-indexedBy(field: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 创建的索引列名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回具有指定索引列的谓词。 |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { dataAbility, relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  async onCreate(): Promise<void> {
    let store: relationalStore.RdbStore | undefined = undefined;
    let context = this.context;

    try {
      const STORE_CONFIG: relationalStore.StoreConfig = {
        name: 'RdbTest.db', // 数据库文件名
        securityLevel: relationalStore.SecurityLevel.S3,
      };
      // 表结构：EMPLOYEE (NAME, AGE, SALARY, CODES)
      const SQL_CREATE_TABLE =
        'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)'; // 建表Sql语句
      store = await relationalStore.getRdbStore(context, STORE_CONFIG);
      console.info('Succeeded in getting RdbStore.');
      await store.executeSql(SQL_CREATE_TABLE); // 创建数据表
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to get RdbStore. Code:${err.code}, message:${err.message}`);
    }

    if (!store) {
      return;
    }

    // 创建索引
    const SQL_CREATE_INDEX = 'CREATE INDEX SALARY_INDEX ON EMPLOYEE(SALARY)'
    await store.executeSql(SQL_CREATE_INDEX);
    // ...

    let dataAbilityPredicates = new dataAbility.DataAbilityPredicates()
    dataAbilityPredicates.indexedBy("SALARY_INDEX")

    // ...
  }
}

```

## isNotNull

```TypeScript
isNotNull(field: string): DataAbilityPredicates
```

配置谓词以匹配值不为null的指定字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-isNotNull(field: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-isNotNull(field: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.isNotNull("NAME")

```

## isNull

```TypeScript
isNull(field: string): DataAbilityPredicates
```

配置谓词以匹配值为null的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-isNull(field: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-isNull(field: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.isNull("NAME")

```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且value小于指定值的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-lessThan(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-lessThan(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.lessThan("AGE", 20)

```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且value小于或等于指定值的字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.lessThanOrEqualTo("AGE", 20)

```

## like

```TypeScript
like(field: string, value: string): DataAbilityPredicates
```

配置谓词以匹配数据类型为string且值类似于指定字符串的字段。

此方法类似于SQL语句“like”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-like(field: string, value: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-like(field: string, value: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.like("NAME", "%os%")

```

## limitAs

```TypeScript
limitAs(value: number): DataAbilityPredicates
```

设置谓词的最大数据记录数量。

**起始版本：** 7

<!--Device-DataAbilityPredicates-limitAs(value: number): DataAbilityPredicates--><!--Device-DataAbilityPredicates-limitAs(value: number): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 最大数据记录数，取值为正整数。传入值小于等于0时，不会限制记录数量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回可用于设置最大数据记录数的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Rose").limitAs(3)

```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType且value超出给定范围的指定字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| low | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示与谓词匹配的最小值。 |
| high | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示与谓词匹配的最大值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.notBetween("AGE", 10, 50)

```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

配置谓词以匹配数据，数据的指定字段数据类型为ValueType且不等于指定值。

此方法类似于SQL语句的“!=”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-notEqualTo(field: string, value: ValueType): DataAbilityPredicates--><!--Device-DataAbilityPredicates-notEqualTo(field: string, value: ValueType): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.notEqualTo("NAME", "lisi")

```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): DataAbilityPredicates
```

配置谓词以匹配数据类型为ValueType数组且值不在给定范围内的指定字段。

**起始版本：** 7

<!--Device-DataAbilityPredicates-notIn(field: string, value: Array<ValueType>): DataAbilityPredicates--><!--Device-DataAbilityPredicates-notIn(field: string, value: Array<ValueType>): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ValueType> | 是 | 以ValueType类型数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.notIn("NAME", ["Lisa", "Rose"])

```

## offsetAs

```TypeScript
offsetAs(rowOffset: number): DataAbilityPredicates
```

设置谓词查询结果的起始位置。需要同步调用[limitAs](arkts-arkdata-dataability-dataabilitypredicates-c.md#limitas-1)接口指定查询数量，否则无查询结果。查询指定偏移位置后的所有行时，[limitAs](arkts-arkdata-dataability-dataabilitypredicates-c.md#limitas-1)接口需传入参数-1。

**起始版本：** 7

<!--Device-DataAbilityPredicates-offsetAs(rowOffset: number): DataAbilityPredicates--><!--Device-DataAbilityPredicates-offsetAs(rowOffset: number): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rowOffset | number | 是 | 返回结果的起始位置，取值为正整数。传入值小于等于0时，查询结果将从第一个元素位置返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回具有指定返回结果起始位置的谓词。 |

**示例：**

```TypeScript
// 跳过前三条数据，显示后续三条数据
dataAbilityPredicates.equalTo("NAME", "Rose").offsetAs(3).limitAs(3)

```

## or

```TypeScript
or(): DataAbilityPredicates
```

将或条件添加到谓词中。

此方法类似于SQL语句“or”。

**起始版本：** 7

<!--Device-DataAbilityPredicates-or(): DataAbilityPredicates--><!--Device-DataAbilityPredicates-or(): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回带有或条件的DataAbility谓词。 |

**示例：**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Lisa")
    .or()
    .equalTo("NAME", "Rose")

```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataAbilityPredicates
```

配置谓词以匹配其值按升序排序的列。当有多个orderByAsc使用时，最先使用的具有最高优先级。

**起始版本：** 7

<!--Device-DataAbilityPredicates-orderByAsc(field: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-orderByAsc(field: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
// 先按"NAME"字段排序，相同时按"AGE"字段排序，其次按"SALARY"排序
dataAbilityPredicates.orderByAsc("NAME").orderByAsc("AGE").orderByAsc("SALARY")

```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataAbilityPredicates
```

配置谓词以匹配其值按降序排序的列。当有多个orderByDesc使用时，最先使用的具有最高优先级。

**起始版本：** 7

<!--Device-DataAbilityPredicates-orderByDesc(field: string): DataAbilityPredicates--><!--Device-DataAbilityPredicates-orderByDesc(field: string): DataAbilityPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例：**

```TypeScript
// 优先按"AGE"排序，相同时按"SALARY"排序
dataAbilityPredicates.orderByDesc("AGE").orderByDesc("SALARY")

```

