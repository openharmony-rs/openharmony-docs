# Query

使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** Query

<!--Device-distributedData-class Query--><!--Device-distributedData-class Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## and

```TypeScript
and(): Query
```

构造一个带有与条件的查询对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** and

<!--Device-Query-and(): Query--><!--Device-Query-and(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回查询对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value1");
    query.and();
    query.notEqualTo("field", "value2");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## beginGroup

```TypeScript
beginGroup(): Query
```

创建一个带有左括号的查询条件组。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** beginGroup

<!--Device-Query-beginGroup(): Query--><!--Device-Query-beginGroup(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.beginGroup();
    query.isNotNull("field");
    query.endGroup();
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## constructor

```TypeScript
constructor()
```

用于创建Query实例的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-Query-constructor()--><!--Device-Query-constructor()-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId(deviceId: string): Query
```

添加设备ID作为key的前缀。
> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deviceId

<!--Device-Query-deviceId(deviceId: string): Query--><!--Device-Query-deviceId(deviceId: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 指示查询的设备ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.deviceId("deviceId");
    console.log("query is " + query.getSqlLike());
} catch (e) {
    console.log("should be ok on Method Chaining : " + e);
}

```

## endGroup

```TypeScript
endGroup(): Query
```

创建一个带有右括号的查询条件组。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** endGroup

<!--Device-Query-endGroup(): Query--><!--Device-Query-endGroup(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.beginGroup();
    query.isNotNull("field");
    query.endGroup();
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## equalTo

```TypeScript
equalTo(field: string, value: number | string | boolean): Query
```

构造一个Query对象来查询具有指定字段的条目，其值等于指定的值。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** equalTo

<!--Device-Query-equalTo(field: string, value: number | string | boolean): Query--><!--Device-Query-equalTo(field: string, value: number | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string \| boolean | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.equalTo("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## getSqlLike

```TypeScript
getSqlLike(): string
```

获取Query对象的查询语句。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getSqlLike

<!--Device-Query-getSqlLike(): string--><!--Device-Query-getSqlLike(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回一个字段列中包含对应子串的结果。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    let sql1 = query.getSqlLike();
    console.log("GetSqlLike sql=" + sql1);
} catch (e) {
    console.log("duplicated calls should be ok : " + e);
}

```

## greaterThan

```TypeScript
greaterThan(field: string, value: number | string | boolean): Query
```

构造一个Query对象以查询具有大于指定值的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** greaterThan

<!--Device-Query-greaterThan(field: string, value: number | string | boolean): Query--><!--Device-Query-greaterThan(field: string, value: number | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string \| boolean | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.greaterThan("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: number | string): Query
```

构造一个Query对象以查询具有指定字段且值大于或等于指定值的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** greaterThanOrEqualTo

<!--Device-Query-greaterThanOrEqualTo(field: string, value: number | string): Query--><!--Device-Query-greaterThanOrEqualTo(field: string, value: number | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.greaterThanOrEqualTo("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## inNumber

```TypeScript
inNumber(field: string, valueList: number[]): Query
```

构造一个Query对象以查询具有指定字段的条目，其值在指定的值列表中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** inNumber

<!--Device-Query-inNumber(field: string, valueList: number[]): Query--><!--Device-Query-inNumber(field: string, valueList: number[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| valueList | number[] | 是 | 表示指定的值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.inNumber("field", [0, 1]);
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## inString

```TypeScript
inString(field: string, valueList: string[]): Query
```

构造一个Query对象以查询具有指定字段的条目，其值在指定的字符串值列表中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** inString

<!--Device-Query-inString(field: string, valueList: string[]): Query--><!--Device-Query-inString(field: string, valueList: string[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| valueList | string[] | 是 | 表示指定的字符串值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.inString("field", ['test1', 'test2']);
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## isNotNull

```TypeScript
isNotNull(field: string): Query
```

构造一个Query对象以查询具有值不为null的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isNotNull

<!--Device-Query-isNotNull(field: string): Query--><!--Device-Query-isNotNull(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.isNotNull("field");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## isNull

```TypeScript
isNull(field: string): Query
```

构造一个Query对象以查询具有值为null的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isNull

<!--Device-Query-isNull(field: string): Query--><!--Device-Query-isNull(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.isNull("field");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## lessThan

```TypeScript
lessThan(field: string, value: number | string): Query
```

构造一个Query对象以查询具有小于指定值的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** lessThan

<!--Device-Query-lessThan(field: string, value: number | string): Query--><!--Device-Query-lessThan(field: string, value: number | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.lessThan("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: number | string): Query
```

构造一个Query对象以查询具有指定字段且值小于或等于指定值的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** lessThanOrEqualTo

<!--Device-Query-lessThanOrEqualTo(field: string, value: number | string): Query--><!--Device-Query-lessThanOrEqualTo(field: string, value: number | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.lessThanOrEqualTo("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## like

```TypeScript
like(field: string, value: string): Query
```

构造一个Query对象以查询具有与指定字符串值相似的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** like

<!--Device-Query-like(field: string, value: string): Query--><!--Device-Query-like(field: string, value: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | string | 是 | 表示指定的字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.like("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## limit

```TypeScript
limit(total: number, offset: number): Query
```

构造一个Query对象来指定结果的数量和开始位置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** limit

<!--Device-Query-limit(total: number, offset: number): Query--><!--Device-Query-limit(total: number, offset: number): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | number | 是 | 表示指定的结果数。 |
| offset | number | 是 | 表示起始位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
let total = 10;
let offset = 1;
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.limit(total, offset);
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: number | string | boolean): Query
```

构造一个Query对象以查询具有指定字段且值不等于指定值的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** notEqualTo

<!--Device-Query-notEqualTo(field: string, value: number | string | boolean): Query--><!--Device-Query-notEqualTo(field: string, value: number | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | number \| string \| boolean | 是 | 表示指定的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## notInNumber

```TypeScript
notInNumber(field: string, valueList: number[]): Query
```

构造一个Query对象以查询具有指定字段的条目，该字段的值不在指定的值列表中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** notInNumber

<!--Device-Query-notInNumber(field: string, valueList: number[]): Query--><!--Device-Query-notInNumber(field: string, valueList: number[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| valueList | number[] | 是 | 表示指定的值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notInNumber("field", [0, 1]);
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## notInString

```TypeScript
notInString(field: string, valueList: string[]): Query
```

构造一个Query对象以查询具有指定字段且值不在指定字符串值列表中的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** notInString

<!--Device-Query-notInString(field: string, valueList: string[]): Query--><!--Device-Query-notInString(field: string, valueList: string[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| valueList | string[] | 是 | 表示指定的字符串值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notInString("field", ['test1', 'test2']);
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## or

```TypeScript
or(): Query
```

构造一个带有或条件的Query对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** or

<!--Device-Query-or(): Query--><!--Device-Query-or(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回查询对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value1");
    query.or();
    query.notEqualTo("field", "value2");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## orderByAsc

```TypeScript
orderByAsc(field: string): Query
```

构造一个Query对象，将查询结果按升序排序。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** orderByAsc

<!--Device-Query-orderByAsc(field: string): Query--><!--Device-Query-orderByAsc(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.orderByAsc("field");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## orderByDesc

```TypeScript
orderByDesc(field: string): Query
```

构造一个Query对象，将查询结果按降序排序。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** orderByDesc

<!--Device-Query-orderByDesc(field: string): Query--><!--Device-Query-orderByDesc(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.orderByDesc("field");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## prefixKey

```TypeScript
prefixKey(prefix: string): Query
```

创建具有指定键前缀的查询条件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** prefixKey

<!--Device-Query-prefixKey(prefix: string): Query--><!--Device-Query-prefixKey(prefix: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 表示指定的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.prefixKey("$.name");
    query.prefixKey("0");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

## reset

```TypeScript
reset(): Query
```

重置Query对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** reset

<!--Device-Query-reset(): Query--><!--Device-Query-reset(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回重置的Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.equalTo("key", "value");
    console.log("query is " + query.getSqlLike());
    query.reset();
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("simply calls should be ok :" + e);
}

```

## setSuggestIndex

```TypeScript
setSuggestIndex(index: string): Query
```

设置一个指定的索引，将优先用于查询。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSuggestIndex

<!--Device-Query-setSuggestIndex(index: string): Query--><!--Device-Query-setSuggestIndex(index: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | string | 是 | 指示要设置的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.setSuggestIndex("$.name");
    query.setSuggestIndex("0");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
   console.log("duplicated calls should be ok :" + e);
}

```

## unlike

```TypeScript
unlike(field: string, value: string): Query
```

构造一个Query对象以查询具有与指定字符串值不相似的指定字段的条目。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** unlike

<!--Device-Query-unlike(field: string, value: string): Query--><!--Device-Query-unlike(field: string, value: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含' ^ '。 |
| value | string | 是 | 表示指定的字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
try {
    let query = new distributedData.Query();
    query.unlike("field", "value");
    console.log("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.log("duplicated calls should be ok :" + e);
}

```

