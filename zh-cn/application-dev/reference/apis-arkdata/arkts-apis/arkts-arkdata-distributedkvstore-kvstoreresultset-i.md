# KVStoreResultSet

提供获取数据库结果集的相关方法，包括查询和移动数据读取位置等。同时允许打开的结果集的最大数量为8个。

KVStoreResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。

在调用KVStoreResultSet的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个SingleKVStore或者DeviceKVStore实例。
> **说明：**  
>  
> KVStoreResultSet的游标起始位置为-1。

**起始版本：** 9

<!--Device-distributedKVStore-interface KVStoreResultSet--><!--Device-distributedKVStore-interface KVStoreResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## getCount

```TypeScript
getCount(): number
```

获取结果集中的总行数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-getCount(): int--><!--Device-KVStoreResultSet-getCount(): int-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回数据的总行数。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let count: number;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    count = resultSet.getCount();
    console.info('getCount succeed:' + count);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get count. Code: ${error.code}, message: ${error.message}`);
}

```

## getEntry

```TypeScript
getEntry(): Entry
```

从当前位置获取对应的键值对。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-getEntry(): Entry--><!--Device-KVStoreResultSet-getEntry(): Entry-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Entry](arkts-arkdata-distributeddata-entry-i.md) | 返回键值对。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    let entry = resultSet.getEntry();
    console.info('getEntry succeed:' + JSON.stringify(entry));
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get entry. Code: ${error.code}, message: ${error.message}`);
}

```

## getPosition

```TypeScript
getPosition(): number
```

获取结果集中当前的读取位置。读取位置会因[moveToFirst](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetofirst)、[moveToLast](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetolast)等操作而发生变化。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-getPosition(): int--><!--Device-KVStoreResultSet-getPosition(): int-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前读取位置。取值范围>= -1，值为 -1 时表示还未开始读取，值为 0 时表示第一行。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let position: number;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeeded.');
    resultSet = result;
    position = resultSet.getPosition();
    console.info('getPosition succeed:' + position);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get position. Code: ${error.code}, message: ${error.message}`);
}

```

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

检查读取位置是否在最后一行之后。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-isAfterLast(): boolean--><!--Device-KVStoreResultSet-isAfterLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置在最后一行之后；返回false表示读取位置不在最后一行之后。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    let isAfterLast = resultSet.isAfterLast();
    console.info('Check isAfterLast succeed:' + isAfterLast);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check isAfterLast. Code: ${error.code}, message: ${error.message}`);
}

```

## isBeforeFirst

```TypeScript
isBeforeFirst(): boolean
```

检查读取位置是否在第一行之前。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-isBeforeFirst(): boolean--><!--Device-KVStoreResultSet-isBeforeFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置在第一行之前；返回false表示读取位置不在第一行之前。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    let isBeforeFirst = resultSet.isBeforeFirst();
    console.info('Check isBeforeFirst succeed: ' + isBeforeFirst);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check isBeforeFirst. Code: ${error.code}, message: ${error.message}`);
}

```

## isFirst

```TypeScript
isFirst(): boolean
```

检查读取位置是否为第一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-isFirst(): boolean--><!--Device-KVStoreResultSet-isFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置为第一行；返回false表示读取位置不是第一行。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let isFirst: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    isFirst = resultSet.isFirst();
    console.info('Check isFirst succeed:' + isFirst);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check isFirst. Code: ${error.code}, message: ${error.message}`);
}

```

## isLast

```TypeScript
isLast(): boolean
```

检查读取位置是否为最后一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-isLast(): boolean--><!--Device-KVStoreResultSet-isLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置为最后一行；返回false表示读取位置不是最后一行。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let isLast: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    isLast = resultSet.isLast();
    console.info('Check isLast succeed: ' + isLast);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check isLast. Code: ${error.code}, message: ${error.message}`);
}

```

## move

```TypeScript
move(offset: number): boolean
```

将读取位置移动到当前位置的相对偏移量。即当前游标位置向下偏移 offset 行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-move(offset: int): boolean--><!--Device-KVStoreResultSet-move(offset: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 表示与当前位置的相对偏移量，正偏移表示向结果集末尾方向移动（行号增大），负偏移表示向结果集起始方向移动（行号减小）。当游标超出结果集最前或者最后的位置时，接口返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    moved = resultSet.move(2); // 若当前位置为0，将读取位置从绝对位置为0的位置移动2行，即移动到绝对位置为2，行数为3的位置
    console.info(`Succeeded in moving.moved = ${moved}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move. Code: ${error.code}, message: ${error.message}`);
}

```

## moveToFirst

```TypeScript
moveToFirst(): boolean
```

将读取位置移动到第一行。如果结果集为空，则返回false。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-moveToFirst(): boolean--><!--Device-KVStoreResultSet-moveToFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    moved = resultSet.moveToFirst();
    console.info('moveToFirst succeed: ' + moved);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move to first. Code: ${error.code}, message: ${error.message}`);
}

```

## moveToLast

```TypeScript
moveToLast(): boolean
```

将读取位置移动到最后一行。如果结果集为空，则返回false。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-moveToLast(): boolean--><!--Device-KVStoreResultSet-moveToLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    moved = resultSet.moveToLast();
    console.info('moveToLast succeed:' + moved);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move to last. Code: ${error.code}, message: ${error.message}`);
}

```

## moveToNext

```TypeScript
moveToNext(): boolean
```

将读取位置移动到下一行。如果结果集为空，则返回false。适用于全量获取数据库结果集的场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-moveToNext(): boolean--><!--Device-KVStoreResultSet-moveToNext(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    do {
      moved = resultSet.moveToNext();
      console.info('moveToNext succeed: ' + moved);
    } while (moved);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move to next. Code: ${error.code}, message: ${error.message}`);
}

```

## moveToPosition

```TypeScript
moveToPosition(position: number): boolean
```

将读取位置从 0 移动到绝对位置。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-moveToPosition(position: int): boolean--><!--Device-KVStoreResultSet-moveToPosition(position: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 表示绝对位置。当绝对位置超出结果集最前或者最后的位置时，接口返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    moved = resultSet.moveToPosition(1);
    console.info(`Succeeded in moving to position.moved=${moved}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move to position. Code: ${error.code}, message: ${error.message}`);
}

```

## moveToPrevious

```TypeScript
moveToPrevious(): boolean
```

将读取位置移动到上一行。如果结果集为空，则返回false。适用于全量获取数据库结果集的场景。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVStoreResultSet-moveToPrevious(): boolean--><!--Device-KVStoreResultSet-moveToPrevious(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('getResultSet succeed.');
    resultSet = result;
    moved = resultSet.moveToLast();
    moved = resultSet.moveToPrevious();
    console.info('moveToPrevious succeed:' + moved);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move to previous. Code: ${error.code}, message: ${error.message}`);
}

```

