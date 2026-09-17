# RdbStore

Provides APIs for managing data in an RDB store.

Before using the APIs of this class, use [executeSql](#executesql) to initialize the database table structure and related data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

Inserts a batch of data into a table. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Name of the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md)&gt; | Yes | An array of data to insert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, the number of inserted data records is returned. Otherwise, **-1** is returned. |

**Examples**

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);
const valueBucket1: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
const valueBucket2: ValuesBucket = {
  key1: value5,
  key2: value6,
  key3: value7,
  key4: value8,
};
const valueBucket3: ValuesBucket = {
  key1: value9,
  key2: value10,
  key3: value11,
  key4: value12,
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
rdbStore.batchInsert("EMPLOYEE", valueBuckets, (status: number, insertNum: number) => {
  if (status) {
    console.error("batchInsert failed, status = " + status);
    return;
  }
  console.info("batchInsert is successful, the number of values that were inserted = " + insertNum);
})
```

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);
const valueBucket1: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
const valueBucket2: ValuesBucket = {
  key1: value5,
  key2: value6,
  key3: value7,
  key4: value8,
};
const valueBucket3: ValuesBucket = {
  key1: value9,
  key2: value10,
  key3: value11,
  key4: value12,
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
let promise: void = rdbStore.batchInsert("EMPLOYEE", valueBuckets);
promise.then((insertNum: number) => {
  console.info("batchInsert is successful, the number of values that were inserted = " + insertNum);
}).catch((status: number) => {
  console.error("batchInsert failed, status = " + status);
})
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>
```

Inserts a batch of data into a table. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Name of the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md)&gt; | Yes | An array of data to insert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. If the operation is successful, the number of inserted data records is returned. Otherwise, **-1** is returned. |

**Examples**

See [batchInsert](#batchinsert)

## beginTransaction

```TypeScript
beginTransaction(): void
```

Starts the transaction before executing an SQL statement.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [beginTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#begintransaction)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

data_rdb.getRdbStore(this.context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
  rdbStore.beginTransaction()
  await rdbStore.insert("test", valueBucket)
  rdbStore.commit()
})
```

## commit

```TypeScript
commit(): void
```

Commits the executed SQL statements.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [commit](arkts-arkdata-relationalstore-rdbstore-i.md#commit)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';
import featureAbility from '@ohos.ability.featureAbility';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

data_rdb.getRdbStore(this.context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
  rdbStore.beginTransaction()
  await rdbStore.insert("test", valueBucket)
  rdbStore.commit()
})
```

## delete

```TypeScript
delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Deletes data from the RDB store based on the specified **RdbPredicates** object. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [delete](arkts-arkdata-relationalstore-rdbstore-i.md#delete)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Deletion conditions specified by the **RdbPredicates** object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the number of rows deleted. |

**Examples**

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
rdbStore.delete(predicates, (err: BusinessError, rows: number) => {
  if (err) {
    console.error("Delete failed, err: " + err)
    return
  }
  console.info("Delete rows: " + rows)
})
```

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
let promise: void = rdbStore.delete(predicates)
promise.then((rows: number) => {
  console.info("Delete rows: " + rows)
}).catch((err: BusinessError) => {
  console.error("Delete failed, err: " + err)
})
```

## delete

```TypeScript
delete(predicates: RdbPredicates): Promise<number>
```

Deletes data from the RDB store based on the specified **RdbPredicates** object. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [delete](arkts-arkdata-relationalstore-rdbstore-i.md#delete)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Deletion conditions specified by the **RdbPredicates** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of rows deleted. |

**Examples**

See [delete](#delete)

## executeSql

```TypeScript
executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void
```

Executes an SQL statement that contains specified arguments but returns no value. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [executeSql](arkts-arkdata-relationalstore-rdbstore-i.md#executesql)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-rdb-valuetype-t.md)&gt; | Yes | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, the value of this parameter must be an empty array. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = ?"
rdbStore.executeSql(SQL_DELETE_TABLE, ['zhangsan'], (err: BusinessError) => {
  if (err) {
    console.error("ExecuteSql failed, err: " + err)
    return
  }
  console.info('Delete table done.')
})
```

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'"
let promise = rdbStore.executeSql(SQL_DELETE_TABLE)
promise.then(() => {
  console.info('Delete table done.')
}).catch((err: BusinessError) => {
  console.error("ExecuteSql failed, err: " + err)
})
```

## executeSql

```TypeScript
executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>
```

Executes an SQL statement that contains specified arguments but returns no value. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [executeSql](arkts-arkdata-relationalstore-rdbstore-i.md#executesql)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-rdb-valuetype-t.md)&gt; | No | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [executeSql](#executesql)

## insert

```TypeScript
insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void
```

Inserts a row of data into a table. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [insert](arkts-arkdata-relationalstore-rdbstore-i.md#insert)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Name of the target table. |
| values | [ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md) | Yes | Row of data to insert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, the row ID will be returned. Otherwise, **-1** will be returned. |

**Examples**

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisi";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

rdbStore.insert("EMPLOYEE", valueBucket, (status: number, rowId: number) => {
  if (status) {
    console.error("Insert failed");
    return;
  }
  console.info("Insert is successful, rowId = " + rowId);
})
```

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisi";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

let promise: void = rdbStore.insert("EMPLOYEE", valueBucket)
promise.then((rowId: BusinessError) => {
  console.info("Insert is successful, rowId = " + rowId);
}).catch((status: number) => {
  console.error("Insert failed");
})
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket): Promise<number>
```

Inserts a row of data into a table. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [insert](arkts-arkdata-relationalstore-rdbstore-i.md#insert)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Name of the target table. |
| values | [ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md) | Yes | Row of data to insert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. If the operation is successful, the row ID will be returned. Otherwise, **-1** will be returned. |

**Examples**

See [insert](#insert)

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void
```

Obtains the distributed table name of a remote device based on the local table name of the device. The distributed table name is required when the RDB store of a remote device is queried. This API uses an asynchronous callback to return the result.

> **NOTE:** 

> The value of **device** can be obtained by &lt;!--RP1--&gt;
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync)
> . &lt;!--RP1End--&gt;The APIs of the **deviceManager** module are system interfaces and available only to system
> applications.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [obtainDistributedTableName](arkts-arkdata-relationalstore-rdbstore-i.md#obtaindistributedtablename)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | ID of the remote device. |
| table | string | Yes | Local table name of the remote device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation succeeds, the distributed table name of the remote device is returned. |

**Examples**

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.error("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  let deviceId: Array<string> = devices[0].deviceId;
})

rdbStore.obtainDistributedTableName(deviceId, "EMPLOYEE", (err: BusinessError, tableName: String) {
  if (err) {
    console.error('ObtainDistributedTableName failed, err: ' + err)
    return
  }
  console.info('ObtainDistributedTableName successfully, tableName=.' + tableName)
})
```

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.error("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  let deviceId: Array<string> = devices[0].deviceId;
})

let promise: void = rdbStore.obtainDistributedTableName(deviceId, "EMPLOYEE")
promise.then((tableName: String) => {
  console.info('ObtainDistributedTableName successfully, tableName= ' + tableName)
}).catch((err: BusinessError) => {
  console.error('ObtainDistributedTableName failed, err: ' + err)
})
```

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string): Promise<string>
```

Obtains the distributed table name of a remote device based on the local table name of the device. The distributed table name is required when the RDB store of a remote device is queried. This API uses a promise to return the result.

> **NOTE:** 

> The value of **device** can be obtained by &lt;!--RP1--&gt;
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync)
> . &lt;!--RP1End--&gt;The APIs of the **deviceManager** module are system interfaces and available only to system
> applications.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [obtainDistributedTableName](arkts-arkdata-relationalstore-rdbstore-i.md#obtaindistributedtablename)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | ID of the remote device. |
| table | string | Yes | Local table name of the remote device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. If the operation succeeds, the distributed table name of the remote device is returned. |

**Examples**

See [obtainDistributedTableName](#obtaindistributedtablename)

## off

```TypeScript
off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

Unregisters the observer of the specified type from the RDB store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [off](arkts-arkdata-relationalstore-rdbstore-i.md#off)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event to observe. The value is **dataChange**, which indicates a data change event. |
| type | [SubscribeType](arkts-arkdata-rdb-subscribetype-e.md) | Yes | Subscription type to register. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Data change observer registered. **Array&lt;string&gt;** indicates the ID of the peer device whose data in the database is changed. |

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

Registers an observer for this RDB store. When the data in the RDB store changes, a callback is invoked to return the data changes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-arkdata-relationalstore-rdbstore-i.md#on)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event to observe. The value is **dataChange**, which indicates a data change event. |
| type | [SubscribeType](arkts-arkdata-rdb-subscribetype-e.md) | Yes | Subscription type to register. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Observer that listens for the data changes in the RDB store. **Array&lt;string&gt;** indicates the ID of the peer device whose data in the database is changed. |

## query

```TypeScript
query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

Queries data from the RDB store based on specified conditions. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [query](arkts-arkdata-relationalstore-rdbstore-i.md#query)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Query conditions specified by the **RdbPredicates** object. |
| columns | Array&lt;string&gt; | Yes | Columns to query. If this parameter is not specified, the query applies to all columns. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-rdb-resultset-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, a **ResultSet** object will be returned. |

**Examples**

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose")
rdbStore.query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], (err: BusinessError, resultSet: void) => {
  if (err) {
    console.error("Query failed, err: " + err)
    return
  }
  console.info("ResultSet column names: " + resultSet.columnNames)
  console.info("ResultSet column count: " + resultSet.columnCount)
})
```

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose")
let promise: void = rdbStore.query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"])
promise.then((resultSet: void) => {
  console.info("ResultSet column names: " + resultSet.columnNames)
  console.info("ResultSet column count: " + resultSet.columnCount)
}).catch((err: BusinessError) => {
  console.error("Query failed, err: " + err)
})
```

## query

```TypeScript
query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

Queries data from the RDB store based on specified conditions. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [query](arkts-arkdata-relationalstore-rdbstore-i.md#query)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Query conditions specified by the **RdbPredicates** object. |
| columns | Array&lt;string&gt; | No | Columns to query. If this parameter is not specified, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-rdb-resultset-t.md)&gt; | Promise used to return the result. If the operation is successful, a **ResultSet** object will be returned. |

**Examples**

See [query](#query)

## querySql

```TypeScript
querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void
```

Queries data using the specified SQL statement. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-rdb-valuetype-t.md)&gt; | Yes | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, the value of this parameter must be an empty array. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-rdb-resultset-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, a **ResultSet** object will be returned. |

**Examples**

```TypeScript
rdbStore.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = ?", ['sanguo'], (err: BusinessError, resultSet: void) => {
  if (err) {
    console.error("Query failed, err: " + err)
    return
  }
  console.info("ResultSet column names: " + resultSet.columnNames)
  console.info("ResultSet column count: " + resultSet.columnCount)
})
```

```TypeScript
let promise: void = rdbStore.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'")
promise.then((resultSet: void) => {
  console.info("ResultSet column names: " + resultSet.columnNames)
  console.info("ResultSet column count: " + resultSet.columnCount)
}).catch((err: BusinessError) => {
  console.error("Query failed, err: " + err)
})
```

## querySql

```TypeScript
querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

Queries data using the specified SQL statement. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-rdb-valuetype-t.md)&gt; | No | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-rdb-resultset-t.md)&gt; | Promise used to return the result. If the operation is successful, a **ResultSet** object will be returned. |

**Examples**

See [querySql](#querysql)

## rollBack

```TypeScript
rollBack(): void
```

Rolls back the SQL statements that have been executed.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [rollBack](arkts-arkdata-relationalstore-rdbstore-i.md#rollback)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';
import featureAbility from '@ohos.ability.featureAbility';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

const STORE_CONFIG = { name: "RdbTest.db"}
data_rdb.getRdbStore(this,context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
  try {
    rdbStore.beginTransaction()
    await rdbStore.insert("test", valueBucket)
    rdbStore.commit()
  } catch (e) {
    rdbStore.rollBack()
  }
})
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, callback: AsyncCallback<void>): void
```

Sets distributed tables. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedTables](arkts-arkdata-relationalstore-rdbstore-i.md#setdistributedtables)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Names of the distributed tables to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
rdbStore.setDistributedTables(["EMPLOYEE"], (err: BusinessError) => {
  if (err) {
    console.error('SetDistributedTables failed, err: ' + err)
    return
  }
  console.info('SetDistributedTables successfully.')
})
```

```TypeScript
let promise: void = rdbStore.setDistributedTables(["EMPLOYEE"])
promise.then(() => {
  console.info("SetDistributedTables successfully.")
}).catch((err: BusinessError) => {
  console.error("SetDistributedTables failed, err: " + err)
})
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>): Promise<void>
```

Sets distributed tables. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedTables](arkts-arkdata-relationalstore-rdbstore-i.md#setdistributedtables)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Names of the distributed tables to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setDistributedTables](#setdistributedtables)

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void
```

Synchronizes data across devices. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sync](arkts-arkdata-relationalstore-rdbstore-i.md#sync)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-rdb-syncmode-e.md) | Yes | Data sync mode. The value can be **push** or **pull**. |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | **RdbPredicates** object that specifies the data and devices to synchronize. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | Callback invoked to send the sync result to the caller.<br>**string** indicates the device ID. <br>**number** indicates the sync status of that device. The value **0** indicates a successful sync. Other values indicate a sync failure. |

**Examples**

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.error("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    let deviceIds: Array<string> = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates('EMPLOYEE')
predicates.inDevices(deviceIds)
rdbStore.sync(data_rdb.SyncMode.SYNC_MODE_PUSH, predicates, (err: BusinessError, result: void) {
  if (err) {
    console.error('Sync failed, err: ' + err)
    return
  }
  console.info('Sync done.')
  for (let i = 0; i < result.length; i++) {
    console.info('device=' + result[i][0] + ' status=' + result[i][1])
  }
})
```

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.error("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    let deviceIds: Array<string> = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates('EMPLOYEE')
predicates.inDevices(deviceIds)
let promise: void = rdbStore.sync(data_rdb.SyncMode.SYNC_MODE_PUSH, predicates)
promise.then((result: void) =>{
  console.info('Sync done.')
  for (let i = 0; i < result.length; i++) {
    console.info('device=' + result[i][0] + ' status=' + result[i][1])
  }
}).catch((err: BusinessError) => {
  console.error('Sync failed')
})
```

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>
```

Synchronizes data across devices. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sync](arkts-arkdata-relationalstore-rdbstore-i.md#sync)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-rdb-syncmode-e.md) | Yes | Data sync mode. The value can be **push** or **pull**. |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | **RdbPredicates** object that specifies the data and devices to synchronize. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise used to send the sync result.<br>**string** indicates the device ID. <br>**number** indicates the sync status of that device. The value **0** indicates a successful sync. Other values indicate a sync failure. |

**Examples**

See [sync](#sync)

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Updates data in the RDB store based on the specified **RdbPredicates** object. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [update](arkts-arkdata-relationalstore-rdbstore-i.md#update)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md) | Yes | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table. |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Update conditions specified by the **RdbPredicates** object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback invoked to return the number of rows updated. |

**Examples**

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
rdbStore.update(valueBucket, predicates, (err: BusinessError, rows: number) => {
  if (err) {
    console.error("Update failed, err: " + err)
    return
  }
  console.info("Updated row count: " + rows)
})
```

```TypeScript
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
let promise: void = rdbStore.update(valueBucket, predicates)
promise.then(async (rows: number) => {
  console.info("Updated row count: " + rows)
}).catch((err: BusinessError) => {
  console.error("Update failed, err: " + err)
})
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>
```

Updates data based on the specified **RdbPredicates** object. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [update](arkts-arkdata-relationalstore-rdbstore-i.md#update)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-rdb-valuesbucket-t.md) | Yes | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table. |
| predicates | [RdbPredicates](arkts-arkdata-rdb-rdbpredicates-c.md) | Yes | Update conditions specified by the **RdbPredicates** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of rows updated. |

**Examples**

See [update](#update)
