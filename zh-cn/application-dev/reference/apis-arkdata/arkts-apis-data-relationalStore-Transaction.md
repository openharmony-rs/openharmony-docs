# Interface (Transaction)

> **说明：**
> 
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Interface首批接口从API version 14开始支持。

提供以事务方式管理数据库的方法。事务对象是通过[createTransaction](arkts-apis-data-relationalStore-RdbStore.md#createtransaction14)接口创建的，不同事务对象之间的操作是隔离的，不同类型事务的区别见[TransactionType](arkts-apis-data-relationalStore-e.md#transactiontype14) 。

当前关系型数据库同一时刻仅支持一个写事务，所以如果当前[RdbStore](arkts-apis-data-relationalStore-RdbStore.md)存在写事务未释放，创建IMMEDIATE或EXCLUSIVE事务会返回14800024错误码。如果是创建的DEFERRED事务，则可能在首次使用DEFERRED事务调用写操作时返回14800024错误码。通过IMMEDIATE或EXCLUSIVE创建写事务或者DEFERRED事务升级到写事务之后，[RdbStore](arkts-apis-data-relationalStore-RdbStore.md)的写操作也会返回14800024错误码。

当事务并发量较高且写事务持续时间较长时，返回14800024错误码的次数可能会变多，开发者可以通过减少事务占用时长减少14800024出现的次数，也可以通过重试的方式处理14800024错误码。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let store: relationalStore.RdbStore | undefined = undefined;

class EntryAbility extends UIAbility {
  async onWindowStageCreate(windowStage: window.WindowStage) {
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: "RdbTest.db",
      securityLevel: relationalStore.SecurityLevel.S3
    };

    await relationalStore.getRdbStore(this.context, STORE_CONFIG).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');
    }).catch((err: BusinessError) => {
      console.error(`Get RdbStore failed, code is ${err.code},message is ${err.message}`);
    });

    if (store != undefined) {
      (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
        console.info(`createTransaction success`);
        // 成功获取到事务对象后执行后续操作
      }).catch((err: BusinessError) => {
        console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
      });
    }
  }
}
```

## 导入模块

```ts
import { relationalStore } from '@kit.ArkData';
```

## commit<sup>14+</sup>

commit(): Promise&lt;void&gt;

提交已执行的SQL语句。如果是使用异步接口执行sql语句，请确保异步接口执行完成之后再调用commit接口，否则可能会丢失SQL操作。调用commit接口之后，该Transaction对象及创建的ResultSet对象都将被关闭。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |

**示例：**

```ts
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  const valueBucket: relationalStore.ValuesBucket = {
    'NAME': value1,
    'AGE': value2,
    'SALARY': value3,
    'CODES': value4
  };
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.execute("DELETE FROM TEST WHERE age = ? OR age = ?", ["18", "20"]).then(() => {
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`execute sql failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## rollback<sup>14+</sup>

rollback(): Promise&lt;void&gt;

回滚已经执行的SQL语句。调用rollback接口之后，该Transaction对象及创建的ResultSet对象都会被关闭。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |

**示例：**

```ts
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.execute("DELETE FROM TEST WHERE age = ? OR age = ?", ["18", "20"]).then(() => {
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`execute sql failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## insert<sup>14+</sup>

insert(table: string, values: ValuesBucket, conflict?: ConflictResolution): Promise&lt;number&gt;

向目标表中插入一行数据，使用Promise异步回调。由于共享内存大小限制为2Mb，因此单条数据的大小需小于2Mb，否则会查询失败。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                       |
| -------- | ------------------------------------------- | ---- | -------------------------- |
| table    | string                                      | 是   | 指定的目标表名。           |
| values   | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | 是   | 表示要插入到表中的数据行。 |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 否   | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。         |

**返回值**：

| 类型                  | 说明                                              |
| --------------------- | ------------------------------------------------- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回行ID；否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.insert("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((rowId: number) => {
      transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`Insert is failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## insertSync<sup>14+</sup>

insertSync(table: string, values: ValuesBucket | sendableRelationalStore.ValuesBucket, conflict?: ConflictResolution): number

向目标表中插入一行数据。由于共享内存大小限制为2Mb，因此单条数据的大小需小于2Mb，否则会查询失败。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| table    | string                                      | 是   | 指定的目标表名。                                             |
| values   | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket) \| [sendableRelationalStore.ValuesBucket](./js-apis-data-sendableRelationalStore.md#valuesbucket)   | 是   | 表示要插入到表中的数据行。                                   |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 否   | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值**：

| 类型   | 说明                                 |
| ------ | ------------------------------------ |
| number | 如果操作成功，返回行ID；否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | Failed to open the database because it is corrupted.                                          |
| 14800014     | The RdbStore or ResultSet is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**示例：**

```ts
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    try {
      let rowId: number = (transaction as relationalStore.Transaction).insertSync("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    } catch (e) {
      transaction.rollback();
      console.error(`Insert is failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsert<sup>14+</sup>

batchInsert(table: string, values: Array&lt;ValuesBucket&gt;): Promise&lt;number&gt;

向目标表中插入一组数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | 是   | 指定的目标表名。             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | 是   | 表示要插入到表中的一组数据。|

**返回值**：

| 类型                  | 说明                                                        |
| --------------------- | ----------------------------------------------------------- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回插入的数据个数，否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
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

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.batchInsert("EMPLOYEE", valueBuckets).then((insertNum: number) => {
      transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`batchInsert is failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsertSync<sup>14+</sup>

batchInsertSync(table: string, values: Array&lt;ValuesBucket&gt;): number

向目标表中插入一组数据。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | 是   | 指定的目标表名。             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | 是   | 表示要插入到表中的一组数据。 |

**返回值**：

| 类型   | 说明                                           |
| ------ | ---------------------------------------------- |
| number | 如果操作成功，返回插入的数据个数，否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | Failed to open the database because it is corrupted.                                          |
| 14800014     | The RdbStore or ResultSet is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**示例：**

```ts
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

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    try {
      let insertNum: number = (transaction as relationalStore.Transaction).batchInsertSync("EMPLOYEE", valueBuckets);
      transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (e) {
      transaction.rollback();
      console.error(`batchInsert is failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsertWithConflictResolution<sup>18+</sup>

batchInsertWithConflictResolution(table: string, values: Array&lt;ValuesBucket&gt;, conflict: ConflictResolution): Promise&lt;number&gt;

向目标表中插入一组数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | 是   | 指定的目标表名。             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | 是   | 表示要插入到表中的一组数据。|
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 是   | 指定冲突解决模式。如果是ON_CONFLICT_ROLLBACK模式，当发生冲突时会回滚整个事务。 |

**返回值**：

| 类型                  | 说明                                                        |
| --------------------- | ----------------------------------------------------------- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回插入的数据个数，否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
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

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.batchInsertWithConflictResolution("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((insertNum: number) => {
      transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`batchInsert is failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsertWithConflictResolutionSync<sup>18+</sup>

batchInsertWithConflictResolutionSync(table: string, values: Array&lt;ValuesBucket&gt;, conflict: ConflictResolution): number

向目标表中插入一组数据。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型                                       | 必填 | 说明                         |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | 是   | 指定的目标表名。             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | 是   | 表示要插入到表中的一组数据。 |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 是   | 指定冲突解决模式。如果是ON_CONFLICT_ROLLBACK模式，当发生冲突时会回滚整个事务。 |

**返回值**：

| 类型   | 说明                                           |
| ------ | ---------------------------------------------- |
| number | 如果操作成功，返回插入的数据个数，否则返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
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

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    try {
      let insertNum: number = (transaction as relationalStore.Transaction).batchInsertWithConflictResolutionSync("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (e) {
      transaction.rollback();
      console.error(`batchInsert is failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## update<sup>14+</sup>

update(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): Promise&lt;number&gt;

根据RdbPredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。由于共享内存大小限制为2Mb，因此单条数据的大小需小于2Mb，否则会查询失败。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                                        | 必填 | 说明                                                         |
| ---------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | 是   | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)            | 是   | RdbPredicates的实例对象指定的更新条件。                      |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 否   | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。                                          |

**返回值**：

| 类型                  | 说明                                      |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | 指定的Promise回调方法。返回受影响的行数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.equalTo("NAME", "Lisa");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.update(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then(async (rows: Number) => {
      transaction.commit();
      console.info(`Updated row count: ${rows}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`Updated failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## updateSync<sup>14+</sup>

updateSync(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): number

根据RdbPredicates的指定实例对象更新数据库中的数据。由于共享内存大小限制为2Mb，因此单条数据的大小需小于2Mb，否则会查询失败。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                                        | 必填 | 说明                                                         |
| ---------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | 是   | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)             | 是   | RdbPredicates的实例对象指定的更新条件。                      |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| 否   | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值**：

| 类型   | 说明               |
| ------ | ------------------ |
| number | 返回受影响的行数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | Failed to open the database because it is corrupted.                                          |
| 14800014     | The RdbStore or ResultSet is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**示例：**

```ts
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    try {
      let rows: Number = (transaction as relationalStore.Transaction).updateSync(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (e) {
      transaction.rollback();
      console.error(`Updated failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## delete<sup>14+</sup>

delete(predicates: RdbPredicates):Promise&lt;number&gt;

根据RdbPredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                                 | 必填 | 说明                                      |
| ---------- | ------------------------------------ | ---- | ----------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | 是   | RdbPredicates的实例对象指定的删除条件。 |

**返回值**：

| 类型                  | 说明                            |
| --------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise对象。返回受影响的行数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.delete(predicates).then((rows: Number) => {
      transaction.commit();
      console.info(`Delete rows: ${rows}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`Delete failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## deleteSync<sup>14+</sup>

deleteSync(predicates: RdbPredicates): number

根据RdbPredicates的指定实例对象从数据库中删除数据。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                            | 必填 | 说明                                    |
| ---------- | ------------------------------- | ---- | --------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | 是   | RdbPredicates的实例对象指定的删除条件。 |

**返回值**：

| 类型   | 说明               |
| ------ | ------------------ |
| number | 返回受影响的行数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    try {
      let rows: Number = (transaction as relationalStore.Transaction).deleteSync(predicates);
      transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (e) {
      transaction.rollback();
      console.error(`Delete failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## query<sup>14+</sup>

query(predicates: RdbPredicates, columns?: Array&lt;string&gt;): Promise&lt;ResultSet&gt;

根据指定条件查询数据库中的数据，使用Promise异步回调。由于共享内存大小限制为2Mb，因此单条数据的大小需小于2Mb，否则会查询失败。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                                 | 必填 | 说明                                             |
| ---------- | ------------------------------------ | ---- | ------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | 是   | RdbPredicates的实例对象指定的查询条件。        |
| columns    | Array&lt;string&gt;                  | 否   | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值**：

| 类型                                                    | 说明                                               |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |


**示例：**

```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄露与内存泄露
      resultSet.close();
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`Query failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## querySync<sup>14+</sup>

querySync(predicates: RdbPredicates, columns?: Array&lt;string&gt;): ResultSet

根据指定条件查询数据库中的数据。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到[taskpool](../apis-arkts/js-apis-taskpool.md)线程中执行。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名     | 类型                            | 必填 | 说明                                                         |
| ---------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | 是   | RdbPredicates的实例对象指定的查询条件。                      |
| columns    | Array&lt;string&gt;             | 否   | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值**：

| 类型                    | 说明                                |
| ----------------------- | ----------------------------------- |
| [ResultSet](arkts-apis-data-relationalStore-ResultSet.md) | 如果操作成功，则返回ResultSet对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then(async (transaction: relationalStore.Transaction) => {
    try {
      let resultSet: relationalStore.ResultSet = (transaction as relationalStore.Transaction).querySync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄露与内存泄露
      resultSet.close();
      transaction.commit();
    } catch (e) {
      transaction.rollback();
      console.error(`Query failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## querySql<sup>14+</sup>

querySql(sql: string, args?: Array&lt;ValueType&gt;): Promise&lt;ResultSet&gt;

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | 是   | 指定要执行的SQL语句。                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | 否   | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值**：

| 类型                                                    | 说明                                               |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'").then(async (resultSet: relationalStore.ResultSet) => {
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄露与内存泄露
      resultSet.close();
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`Query failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## querySqlSync<sup>14+</sup>

querySqlSync(sql: string, args?: Array&lt;ValueType&gt;): ResultSet

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到[taskpool](../apis-arkts/js-apis-taskpool.md)线程中执行。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | 是   | 指定要执行的SQL语句。                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | 否   | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空。 |

**返回值**：

| 类型                    | 说明                                |
| ----------------------- | ----------------------------------- |
| [ResultSet](arkts-apis-data-relationalStore-ResultSet.md) | 如果操作成功，则返回ResultSet对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then(async (transaction: relationalStore.Transaction) => {
    try {
      let resultSet: relationalStore.ResultSet = (transaction as relationalStore.Transaction).querySqlSync("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄露与内存泄露
      resultSet.close();
      transaction.commit();
    } catch (e) {
      transaction.rollback();
      console.error(`Query failed, code is ${e.code},message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## execute<sup>14+</sup>

execute(sql: string, args?: Array&lt;ValueType&gt;): Promise&lt;ValueType&gt;

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType，使用Promise异步回调。

该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。

此接口不支持执行查询、附加数据库和事务操作，查询可以使用[querySql](#querysql14)、[query](#query14)接口代替、附加数据库可以使用[attach](arkts-apis-data-relationalStore-RdbStore.md#attach12)接口代替。

不支持分号分隔的多条语句。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | 是   | 指定要执行的SQL语句。                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | 否   | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值**：

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | Promise对象，返回sql执行后的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| 14800000  | Inner error. |
| 14800011  | Failed to open the database because it is corrupted. |
| 14800014  | The RdbStore or ResultSet is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**示例：**

```ts
// 删除表中所有数据
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    transaction.execute(SQL_DELETE_TABLE).then((data) => {
      transaction.commit();
      console.info(`delete result: ${data}`);
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`delete failed, code is ${e.code}, message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## executeSync<sup>14+</sup>

executeSync(sql: string, args?: Array&lt;ValueType&gt;): ValueType

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType。

该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。

此接口不支持执行查询、附加数据库和事务操作，查询可以使用[querySql](#querysql14)、[query](#query14)接口代替、附加数据库可以使用[attach](arkts-apis-data-relationalStore-RdbStore.md#attach12)接口代替。

不支持分号分隔的多条语句。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型                                 | 必填 | 说明                                                         |
| ------ | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql    | string                               | 是   | 指定要执行的SQL语句。                                        |
| args   | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | 否   | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。该参数不填，或者填null或undefined，都认为是sql参数语句完整。默认值为空。 |

**返回值**：

| 类型                    | 说明                |
| ----------------------- | ------------------- |
| [ValueType](arkts-apis-data-relationalStore-t.md#valuetype) | 返回sql执行后的结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[关系型数据库错误码](errorcode-data-rdb.md)。其中，14800011错误码处理可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

| **错误码ID** | **错误信息**                                                 |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| 14800000     | Inner error.                                                 |
| 14800011     | Failed to open the database because it is corrupted.                                          |
| 14800014     | The RdbStore or ResultSet is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**示例：**

```ts
// 删除表中所有数据
if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then((transaction: relationalStore.Transaction) => {
    const SQL_DELETE_TABLE = 'DELETE FROM test';
    try {
      let data = (transaction as relationalStore.Transaction).executeSync(SQL_DELETE_TABLE);
      transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (e) {
      transaction.rollback();
      console.error(`delete failed, code is ${e.code}, message is ${e.message}`);
    };
  }).catch((err: BusinessError) => {
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```