# KvStoreResultSet

Provides APIs to obtain the KV store result sets, and query and move the data read position. Before calling any method in **KvStoreResultSet**, you must use getKVStore to obtain a **KVStore** object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
```

## getCount

```TypeScript
getCount(): number
```

Obtains the total number of rows in the result set.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getCount

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of rows obtained. |

**Examples**

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

Obtains the KV pair from the current position.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getEntry

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Entry](arkts-arkdata-distributeddata-entry-i.md) | KV pair obtained. |

**Examples**

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

Obtains the current data read position (position from which data is read) in the result set.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getPosition

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Current data read position obtained. |

**Examples**

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

Checks whether the data read position is after the last row.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isAfterLast

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the data read position is after the last row; returns **false** otherwise. |

**Examples**

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

Checks whether the data read position is before the first row.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isBeforeFirst

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the data read position is before the first row; returns **false** otherwise. |

**Examples**

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

Checks whether the data read position is the first row.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isFirst

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the first row is being read; returns **false** otherwise. |

**Examples**

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

Checks whether the data read position is the last row.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isLast

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the last row is being read; returns **false** otherwise. |

**Examples**

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

Moves the data read position with the specified offset from the current position.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** move

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset to move the data read position. A negative value means to move backward, and a positive value means to move forward. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

Moves the data read position to the first row. If the result set is empty, **false** will be returned.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** moveToFirst

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

Moves the data read position to the last row. If the result set is empty, **false** will be returned.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** moveToLast

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

Moves the data read position to the next row. If the result set is empty, **false** will be returned.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** moveToNext

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

Moves the data read position from 0 to an absolute position.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** moveToPosition

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Absolute position to move to. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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

Moves the data read position to the previous row. If the result set is empty, **false** will be returned.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** moveToPrevious

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

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
