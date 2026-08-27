# DataSharePredicates

提供用于不同实现不同查询方法的数据共享谓词。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

## 导入模块

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值以指定字符串起始的字段。目前仅关系型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.beginsWith("NAME", "os");
```

## contains

```TypeScript
contains(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值包含指定字段的字段。目前仅关系型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.contains("NAME", "os");
```

## distinct

```TypeScript
distinct(): DataSharePredicates
```

该接口用于配置谓词以过滤重复记录并仅保留其中一个。目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").distinct();
```

## endsWith

```TypeScript
endsWith(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配值以指定字符串结尾的字段。目前仅关系型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.endsWith("NAME", "os");
```

## glob

```TypeScript
glob(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配指定通配符表达式的字段。目前仅关系型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.glob("NAME", "?h*g");
```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataSharePredicates
```

该接口用于配置谓词按指定列分组查询结果。目前仅关系型数据库支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array & lt;string & gt; | 是 | 指定分组依赖的列名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.groupBy(["AGE", "NAME"]);
```

## indexedBy

```TypeScript
indexedBy(field: string): DataSharePredicates
```

该接口用于配置谓词按指定索引列查询结果。使用该方法前，需要设置索引列。目前仅关系型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.indexedBy("SALARY_INDEX");
```

## inKeys

```TypeScript
inKeys(keys: Array<string>): DataSharePredicates
```

该接口用于配置谓词以匹配键在指定范围内的字段。目前仅KVDB支持该谓词。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array & lt;string & gt; | 是 | 指定范围的键数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inKeys(["Lisa", "Rose"]);
```

## isNotNull

```TypeScript
isNotNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值不为null的字段。目前仅关系型数据库及键值型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNotNull("NAME");
```

## isNull

```TypeScript
isNull(field: string): DataSharePredicates
```

该接口用于配置谓词以匹配值为null的字段。目前仅关系型数据库及键值型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | DataSharePredicates** object created. |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNull("NAME");
```

## prefixKey

```TypeScript
prefixKey(prefix: string): DataSharePredicates
```

该接口用于配置谓词以匹配键前缀的指定字段。目前仅KVDB支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.prefixKey("NAME");
```

## unlike

```TypeScript
unlike(field: string, value: string): DataSharePredicates
```

该接口用于配置谓词以匹配不类似指定通配符表达式的字段。目前仅关系型数据库及键值型数据库支持该谓词。

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
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | 返回与指定字段匹配的谓词。 |

**示例**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.unlike("NAME", "%os%");
```
