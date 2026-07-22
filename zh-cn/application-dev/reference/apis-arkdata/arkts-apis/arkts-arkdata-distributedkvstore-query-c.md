# Query

使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。Query对象的谓词方法均返回自身，支持链式调用。一个Query对象中谓词数量上限为256个。

**起始版本：** 9

<!--Device-distributedKVStore-class Query--><!--Device-distributedKVStore-class Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## and

```TypeScript
and(): Query
```

构造一个带有与条件的查询对象。需先通过equalTo、notEqualTo等谓词方法添加查询条件后，再调用and()连接多个条件，无前置谓词时调用and()无效。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-and(): Query--><!--Device-Query-and(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回查询对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value1');
      query.and();
      query.notEqualTo('field', 'value2');
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## beginGroup

```TypeScript
beginGroup(): Query
```

创建一个带有左括号的查询条件组。必须与[endGroup()](arkts-arkdata-distributedkvstore-query-c.md#endgroup)成对使用，以形成完整的查询条件分组。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-beginGroup(): Query--><!--Device-Query-beginGroup(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.beginGroup();
      query.isNotNull('field');
      query.endGroup();
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## constructor

```TypeScript
constructor()
```

用于创建Query实例的构造函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-constructor()--><!--Device-Query-constructor()-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId(deviceId: string): Query
```

添加设备ID作为Key的前缀。
> **说明：**  
>  
> 其中deviceId为[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md)中的  
> networkId，通过调用  
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)  
> 方法得到。  
>  
> deviceId具体获取方式请参考  
> [sync接口示例](arkts-arkdata-distributedkvstore-singlekvstore-i.md#sync)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-deviceId(deviceId: string): Query--><!--Device-Query-deviceId(deviceId: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要查询其数据的设备，不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.deviceId('deviceId');
      console.info(`query is ${query.getSqlLike()}`);
    }
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## endGroup

```TypeScript
endGroup(): Query
```

创建一个带有右括号的查询条件组。必须与[beginGroup()](arkts-arkdata-distributedkvstore-query-c.md#begingroup)成对使用，以形成完整的查询条件分组。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-endGroup(): Query--><!--Device-Query-endGroup(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.beginGroup();
      query.isNotNull('field');
      query.endGroup();
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## equalTo

```TypeScript
equalTo(field: string, value: number | number | string | boolean): Query
```

构造一个Query对象来查询具有指定字段的条目，其值等于指定的值。
> **说明：**  
>  
> 使用equalTo时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-equalTo(field: string, value: long | double | string | boolean): Query--><!--Device-Query-equalTo(field: string, value: long | double | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | number \| number \| string \| boolean | 是 | 表示指定字段要匹配的值，值的类型应与Schema中定义的字段类型一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## getSqlLike

```TypeScript
getSqlLike(): string
```

获取Query对象的查询语句。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-getSqlLike(): string--><!--Device-Query-getSqlLike(): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回Query对象构建的查询语句字符串，可用于查看和调试当前的查询条件。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      let sql1 = query.getSqlLike();
      console.info(`GetSqlLike sql= ${sql1}`);
    }
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## greaterThan

```TypeScript
greaterThan(field: string, value: number | number | string | boolean): Query
```

构造一个Query对象以查询具有大于指定值的指定字段的条目。
> **说明：**  
>  
> 使用greaterThan时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-greaterThan(field: string, value: long | double | string | boolean): Query--><!--Device-Query-greaterThan(field: string, value: long | double | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | Indicates the field, which cannot contain ^. |
| value | number \| number \| string \| boolean | 是 | Indicates the value to be compared. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: number | number | string): Query
```

构造一个Query对象以查询具有指定字段且值大于或等于指定值的条目。
> **说明：**  
>  
> 使用greaterThanOrEqualTo时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-greaterThanOrEqualTo(field: string, value: long | double | string): Query--><!--Device-Query-greaterThanOrEqualTo(field: string, value: long | double | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | number \| number \| string | 是 | 表示指定字段要匹配的值，值的类型应与Schema中定义的字段类型一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## inNumber

```TypeScript
inNumber(field: string, valueList: number[] | number[]): Query
```

构造一个Query对象以查询具有指定字段的条目，其值在指定的值列表中。
> **说明：**  
>  
> 使用inNumber时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-inNumber(field: string, valueList: long[] | double[]): Query--><!--Device-Query-inNumber(field: string, valueList: long[] | double[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| valueList | number[] \| number[] | 是 | 是 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## inString

```TypeScript
inString(field: string, valueList: string[]): Query
```

构造一个Query对象以查询具有指定字段的条目，其值在指定的字符串值列表中。
> **说明：**  
>  
> 使用inString时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-inString(field: string, valueList: string[]): Query--><!--Device-Query-inString(field: string, valueList: string[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| valueList | string[] | 是 | 表示指定的字符串值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.inString('field', ['test1', 'test2']);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## isNotNull

```TypeScript
isNotNull(field: string): Query
```

构造一个Query对象以查询具有值不为null的指定字段的条目。
> **说明：**  
>  
> 使用isNotNull时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-isNotNull(field: string): Query--><!--Device-Query-isNotNull(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.isNotNull('field');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## isNull

```TypeScript
isNull(field: string): Query
```

构造一个Query对象以查询具有值为null的指定字段的条目。
> **说明：**  
>  
> 使用isNull时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-isNull(field: string): Query--><!--Device-Query-isNull(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.isNull('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## lessThan

```TypeScript
lessThan(field: string, value: number | number | string): Query
```

构造一个Query对象以查询具有小于指定值的指定字段的条目。
> **说明：**  
>  
> 使用lessThan时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-lessThan(field: string, value: long | double | string): Query--><!--Device-Query-lessThan(field: string, value: long | double | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | number \| number \| string | 是 | 表示指定字段要匹配的值，值的类型应与Schema中定义的字段类型一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: number | number | string): Query
```

构造一个Query对象以查询具有指定字段且值小于或等于指定值的条目。
> **说明：**  
>  
> 使用lessThanOrEqualTo时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-lessThanOrEqualTo(field: string, value: long | double | string): Query--><!--Device-Query-lessThanOrEqualTo(field: string, value: long | double | string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | number \| number \| string | 是 | 表示指定字段要匹配的值，值的类型应与Schema中定义的字段类型一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## like

```TypeScript
like(field: string, value: string): Query
```

构造一个Query对象以查询具有与指定字符串值相似的指定字段的条目。
> **说明：**  
>  
> 使用like时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-like(field: string, value: string): Query--><!--Device-Query-like(field: string, value: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | string | 是 | 表示指定字段要匹配的字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.like('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## limit

```TypeScript
limit(total: number, offset: number): Query
```

构造一个Query对象来指定结果的数量和开始位置。该接口必须要在Query对象查询和升降序等操作之后调用，调用limit接口后，不可再对Query对象进行查询和升降序等操作。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-limit(total: int, offset: int): Query--><!--Device-Query-limit(total: int, offset: int): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| total | number | 是 | 表示最大数据记录数。<br/>取值为非负整数时表示指定的最大记录数。<br/>取值为负数时，表示查询整个结果集。 |
| offset | number | 是 | 指定查询结果的起始位置。取值为非负整数时表示指定的起始位置；取值为负数时，表示查询整个结果集。当offset超出结果集最后位置时，查询结果为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let total = 10;
let offset = 1;
try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.notEqualTo('field', 'value');
    query.limit(total, offset);
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: number | number | string | boolean): Query
```

构造一个Query对象以查询具有指定字段且值不等于指定值的条目。
> **说明：**  
>  
> 使用notEqualTo时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-notEqualTo(field: string, value: long | double | string | boolean): Query--><!--Device-Query-notEqualTo(field: string, value: long | double | string | boolean): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | number \| number \| string \| boolean | 是 | 表示指定字段要匹配的值，值的类型应与Schema中定义的字段类型一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## notInNumber

```TypeScript
notInNumber(field: string, valueList: number[] | number[]): Query
```

构造一个Query对象以查询具有指定字段的条目，该字段的值不在指定的值列表中。
> **说明：**  
>  
> 使用notInNumber时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-notInNumber(field: string, valueList: long[] | double[]): Query--><!--Device-Query-notInNumber(field: string, valueList: long[] | double[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| valueList | number[] \| number[] | 是 | 是 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

## notInString

```TypeScript
notInString(field: string, valueList: string[]): Query
```

构造一个Query对象以查询具有指定字段且值不在指定字符串值列表中的条目。
> **说明：**  
>  
> 使用notInString时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-notInString(field: string, valueList: string[]): Query--><!--Device-Query-notInString(field: string, valueList: string[]): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| valueList | string[] | 是 | 表示指定的字符串值列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notInString('field', ['test1', 'test2']);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## or

```TypeScript
or(): Query
```

构造一个带有或条件的Query对象。需先通过equalTo、notEqualTo等谓词方法添加查询条件后，再调用or()连接多个条件，无前置谓词时调用or()无效。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-or(): Query--><!--Device-Query-or(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回查询对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value1');
      query.or();
      query.notEqualTo('field', 'value2');
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## orderByAsc

```TypeScript
orderByAsc(field: string): Query
```

构造一个Query对象，将查询结果按升序排序。
> **说明：**  
>  
> 使用orderByAsc时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-orderByAsc(field: string): Query--><!--Device-Query-orderByAsc(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value');
      query.orderByAsc('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## orderByDesc

```TypeScript
orderByDesc(field: string): Query
```

构造一个Query对象，将查询结果按降序排序。
> **说明：**  
>  
> 使用orderByDesc时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-orderByDesc(field: string): Query--><!--Device-Query-orderByDesc(field: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value');
      query.orderByDesc('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## prefixKey

```TypeScript
prefixKey(prefix: string): Query
```

创建具有指定键前缀的查询条件。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-prefixKey(prefix: string): Query--><!--Device-Query-prefixKey(prefix: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 表示指定的键前缀，长度范围为0-[MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.prefixKey('$.name');
      query.prefixKey('0');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## reset

```TypeScript
reset(): Query
```

重置Query对象。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-reset(): Query--><!--Device-Query-reset(): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回重置后的Query对象，所有已添加的谓词条件被清空，可用于重新构建查询条件。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.equalTo('key', 'value');
    console.info('query is ' + query.getSqlLike());
    query.reset();
    console.info('query is ' + query.getSqlLike());
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## setSuggestIndex

```TypeScript
setSuggestIndex(index: string): Query
```

设置一个指定的索引，将优先用于查询。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-setSuggestIndex(index: string): Query--><!--Device-Query-setSuggestIndex(index: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | string | 是 | 表示要设置的索引，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.setSuggestIndex('$.name');
      query.setSuggestIndex('0');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## unlike

```TypeScript
unlike(field: string, value: string): Query
```

构造一个Query对象以查询具有与指定字符串值不相似的指定字段的条目。
> **说明：**  
>  
> 使用unlike时需要结合[Schema](arkts-arkdata-distributedkvstore-schema-c.md)使用。  
>  
> 使用Schema创建数据库请参见[通过键值型数据库实现数据持久化](../../../database/data-persistence-by-kv-store.md#开发步骤)中使用getKVStore()方法创建并获  
> 取键值数据库示例。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Query-unlike(field: string, value: string): Query--><!--Device-Query-unlike(field: string, value: string): Query-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 表示指定字段，不能包含'^'。包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| value | string | 是 | 表示指定字段要不匹配的字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 返回Query对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.unlike('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

