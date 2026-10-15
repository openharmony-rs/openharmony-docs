# KvStoreResultSet

```TypeScript
interface KvStoreResultSet
```

提供获取KVStore数据库结果集的相关方法，包括查询和移动数据读取位置等。在调用KvStoreResultSet的方法前，需要先通过getKVStore构建一个KVStore实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)

<!--Device-distributedData-interface KvStoreResultSet--><!--Device-distributedData-interface KvStoreResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
```

## getCount

```TypeScript
getCount(): number
```

获取结果集中的总行数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getCount](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#getcount)

<!--Device-KvStoreResultSet-getCount(): number--><!--Device-KvStoreResultSet-getCount(): number-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回数据的总行数。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const count = resultSet.getCount();
    console.info("getCount succeed:" + count);
} catch (e) {
    console.error("getCount failed: " + e);
}
```

## getEntry

```TypeScript
getEntry(): Entry
```

从当前位置获取对应的键值对。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getEntry](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#getentry)

<!--Device-KvStoreResultSet-getEntry(): Entry--><!--Device-KvStoreResultSet-getEntry(): Entry-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Entry](arkts-arkdata-distributeddata-entry-i.md) | 返回键值对。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const entry  = resultSet.getEntry();
    console.info("getEntry succeed:" + JSON.stringify(entry));
} catch (e) {
    console.error("getEntry failed: " + e);
}
```

## getPosition

```TypeScript
getPosition(): number
```

获取结果集中当前的读取位置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getPosition](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#getposition)

<!--Device-KvStoreResultSet-getPosition(): number--><!--Device-KvStoreResultSet-getPosition(): number-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前读取位置。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeeded.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const position = resultSet.getPosition();
    console.info("getPosition succeed:" + position);
} catch (e) {
    console.error("getPosition failed: " + e);
}
```

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

检查读取位置是否在最后一行之后。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isAfterLast](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#isafterlast)

<!--Device-KvStoreResultSet-isAfterLast(): boolean--><!--Device-KvStoreResultSet-isAfterLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置在最后一行之后；返回false表示读取位置不在最后一行之后。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const isafterlast = resultSet.isAfterLast();
    console.info("Check isAfterLast succeed:" + isafterlast);
} catch (e) {
    console.error("Check isAfterLast failed: " + e);
}
```

## isBeforeFirst

```TypeScript
isBeforeFirst(): boolean
```

检查读取位置是否在第一行之前。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isBeforeFirst](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#isbeforefirst)

<!--Device-KvStoreResultSet-isBeforeFirst(): boolean--><!--Device-KvStoreResultSet-isBeforeFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置在第一行之前；返回false表示读取位置不在第一行之前。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const isbeforefirst = resultSet.isBeforeFirst();
    console.info("Check isBeforeFirst succeed: " + isbeforefirst);
} catch (e) {
    console.error("Check isBeforeFirst failed: " + e);
}
```

## isFirst

```TypeScript
isFirst(): boolean
```

检查读取位置是否为第一行。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isFirst](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#isfirst)

<!--Device-KvStoreResultSet-isFirst(): boolean--><!--Device-KvStoreResultSet-isFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置为第一行；返回false表示读取位置不是第一行。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const isfirst = resultSet.isFirst();
    console.info("Check isFirst succeed:" + isfirst);
} catch (e) {
    console.error("Check isFirst failed: " + e);
}
```

## isLast

```TypeScript
isLast(): boolean
```

检查读取位置是否为最后一行。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isLast](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#islast)

<!--Device-KvStoreResultSet-isLast(): boolean--><!--Device-KvStoreResultSet-isLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示读取位置为最后一行；返回false表示读取位置不是最后一行。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const islast = resultSet.isLast();
    console.info("Check isLast succeed: " + islast);
} catch (e) {
    console.error("Check isLast failed: " + e);
}
```

## move

```TypeScript
move(offset: number): boolean
```

将读取位置移动到当前位置的相对偏移量。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [move](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#move)

<!--Device-KvStoreResultSet-move(offset: number): boolean--><!--Device-KvStoreResultSet-move(offset: number): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 表示与当前位置的相对偏移量，负偏移表示向后移动，正偏移表示向前移动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved5 = resultSet.move(1);
    console.info("move succeed:" + moved5);
} catch (e) {
    console.error("move failed: " + e);
}
```

## moveToFirst

```TypeScript
moveToFirst(): boolean
```

将读取位置移动到第一行。如果结果集为空，则返回false。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moveToFirst](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetofirst)

<!--Device-KvStoreResultSet-moveToFirst(): boolean--><!--Device-KvStoreResultSet-moveToFirst(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved1 = resultSet.moveToFirst();
    console.info("moveToFirst succeed: " + moved1);
} catch (e) {
    console.error("moveToFirst failed " + e);
}
```

## moveToLast

```TypeScript
moveToLast(): boolean
```

将读取位置移动到最后一行。如果结果集为空，则返回false。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moveToLast](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetolast)

<!--Device-KvStoreResultSet-moveToLast(): boolean--><!--Device-KvStoreResultSet-moveToLast(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved2 = resultSet.moveToLast();
    console.info("moveToLast succeed:" + moved2);
} catch (e) {
    console.error("moveToLast failed: " + e);
}
```

## moveToNext

```TypeScript
moveToNext(): boolean
```

将读取位置移动到下一行。如果结果集为空，则返回false。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moveToNext](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetonext)

<!--Device-KvStoreResultSet-moveToNext(): boolean--><!--Device-KvStoreResultSet-moveToNext(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved3 = resultSet.moveToNext();
    console.info("moveToNext succeed: " + moved3);
} catch (e) {
    console.error("moveToNext failed: " + e);
}
```

## moveToPosition

```TypeScript
moveToPosition(position: number): boolean
```

将读取位置从 0 移动到绝对位置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moveToPosition](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetoposition)

<!--Device-KvStoreResultSet-moveToPosition(position: number): boolean--><!--Device-KvStoreResultSet-moveToPosition(position: number): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 表示绝对位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved6 = resultSet.moveToPosition(1);
    console.info("moveToPosition succeed: " + moved6);
} catch (e) {
    console.error("moveToPosition failed: " + e);
}
```

## moveToPrevious

```TypeScript
moveToPrevious(): boolean
```

将读取位置移动到上一行。如果结果集为空，则返回false。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moveToPrevious](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md#movetoprevious)

<!--Device-KvStoreResultSet-moveToPrevious(): boolean--><!--Device-KvStoreResultSet-moveToPrevious(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示操作成功；返回false则表示操作失败。 |

**示例**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + err);
    });
    const moved4 = resultSet.moveToPrevious();
    console.info("moveToPrevious succeed:" + moved4);
} catch (e) {
    console.error("moveToPrevious failed: " + e);
}
```
