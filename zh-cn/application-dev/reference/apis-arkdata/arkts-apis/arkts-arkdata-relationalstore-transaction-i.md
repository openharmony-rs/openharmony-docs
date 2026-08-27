# Transaction

提供以事务方式管理数据库的方法。事务对象是通过[createTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#createtransaction)接口创建的，不同事务对象之间的操作是隔离的，不 同类型事务的区别见[TransactionType](arkts-arkdata-relationalstore-transactiontype-e.md) 。当前关系型数据库同一时刻仅支持一个写事务，所以如果当前[RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)存在写事务未释放，创建IMMEDIATE或EXCLUSIVE事务会返回14800024错误 码。如果是创建的DEFERRED事务，则可能在首次使用DEFERRED事务调用写操作时返回14800024错误码。通过IMMEDIATE或EXCLUSIVE创建写事务或者DEFERRED事务升级到写事务之后， [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)的写操作也会返回14800024错误码。当事务并发量较高且写事务持续时间较长时，返回14800024错误码的次数可能会变多，开发者可以通过减少事务占用时长减少14800024出现的次数，也可以通过重试的方式处理14800024错误码。在使用以下API前，请先通过[createTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#createtransaction)方法获取Transaction实例，再通过此实例调用对应方法。

> **说明：**
> 
> - 本Interface首批接口从API version 14开始支持。
**示例：**示例代码中this.context定义见Stage模型的应用Context。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>
```

向目标表中插入一组数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。按每批32766个参数，分批以[ConflictResolution.ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md)策略写入，参数数量计算方式为插入 数据条数乘以插入数据的所有字段的并集大小，中途失败则立即返回。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

关系型数据库：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
  (store as relationalStore.RdbStore).batchInsert("EMPLOYEE", valueBuckets).then((insertNum: number) => {
    if (insertNum == -1) {
      console.error(`batchInsert is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  })
}
```

向量数据库：

```TypeScript
let createSql = "CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY AUTOINCREMENT, data1 floatvector(2));";
await store!.execute(createSql, 0, undefined); // 创建关系表，第二个参数0表示不开启显式事务，第三个参数undefined表示sql未使用绑定参数化
let floatVector = Float32Array.from([1.2, 2.3]);
let valueBucketArray = new Array<relationalStore.ValuesBucket>();
for (let i = 0; i < 100; i++) { // 构造一个BucketArray用于写入
  const row : relationalStore.ValuesBucket = {
    "id" : i,
    "data1" : floatVector,
  }
  valueBucketArray.push(row);
}
await store!.batchInsert("test", valueBucketArray); // 执行批量写入
```

```TypeScript
const valueBucket3: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket4: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket5: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets = new Array(valueBucket3, valueBucket4, valueBucket5);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsert('EMPLOYEE', valueBuckets);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertSync

```TypeScript
batchInsertSync(table: string, values: Array<ValuesBucket>): number
```

向目标表中插入一组数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。按每批32766个参数，分批以[ConflictResolution.ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md)策略写入，参数数量计算方式为插入 数据条数乘以插入数据的所有字段的并集大小，中途失败则立即返回。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
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
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertSync("EMPLOYEE", valueBuckets);
    if (insertNum == -1) {
      console.error(`batchInsertSync is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucket6: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket7: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket8: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets2 = new Array(valueBucket6, valueBucket7, valueBucket8);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let insertNum: number = (transaction as relationalStore.Transaction).batchInsertSync('EMPLOYEE', valueBuckets2);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolution

```TypeScript
batchInsertWithConflictResolution(
        table: string,
        values: Array<ValuesBucket>,
        conflict: ConflictResolution
    ): Promise<number>
```

向目标表中插入一组数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。单次插入参数的最大数量限制为32766，超出上限会返回14800000错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。如果是ON_CONFLICT_ROLLBACK模式，当发生冲突时会回滚整个事务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
  (store as relationalStore.RdbStore).batchInsertWithConflictResolution("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((insertNum: number) => {
    console.info(`batchInsert is successful, insertNum = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
const valueBucket9: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketA: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketB: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets3 = new Array(valueBucket9, valueBucketA, valueBucketB);

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsertWithConflictResolution(
        'EMPLOYEE',
        valueBuckets3,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolutionSync

```TypeScript
batchInsertWithConflictResolutionSync(table: string, values: Array<ValuesBucket>,
      conflict: ConflictResolution): number
```

向目标表中插入一组数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。单次插入参数的最大数量限制为32766，超出上限会返回14800000错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。如果是ON_CONFLICT_ROLLBACK模式，当发生冲突时会回滚整个事务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
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
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertWithConflictResolutionSync("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucketC: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketD: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketE: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets4 = new Array(valueBucketC, valueBucketD, valueBucketE);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = transaction.batchInsertWithConflictResolutionSync(
        'EMPLOYEE',
        valueBuckets4,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithReturning

```TypeScript
batchInsertWithReturning(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

向目标表中插入一组数据，可以通过conflict参数指定当发生数据冲突时的解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回 [Result](arkts-arkdata-relationalstore-result-i.md)。使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。单次插入参数的最大数量限制为32766，超出上限会返回14800001错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 要插入的目标表名。注意：正确的表名不应包含空格、逗号和星号，不能以点开头和结尾等，否则会抛出参数错误。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。注意：空数组、含有重复资产数据会抛出参数错误。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Result & gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function batchInsertWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await rdbStore.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transBatchInsertWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await trans.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## batchInsertWithReturningSync

```TypeScript
batchInsertWithReturningSync(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

向目标表中插入一组数据，可以通过conflict参数指定当发生数据冲突时的解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回 [Result](arkts-arkdata-relationalstore-result-i.md)。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。单次插入参数的最大数量限制为32766，超出上限会返回14800001错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 要插入的目标表名。注意：正确的表名不应包含空格、逗号和星号，不能以点开头和结尾等，否则会抛出参数错误。 |
| values | Array & lt;ValuesBucket & gt; | 是 | 表示要插入到表中的一组数据。注意：空数组、含有重复资产数据会抛出参数错误。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function batchInsertWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = rdbStore.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transBatchInsertWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = trans.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## commit

```TypeScript
commit(): Promise<void>
```

提交已执行的SQL语句，使用Promise异步回调。如果是使用异步接口执行SQL语句，请确保异步接口执行完成之后再调用commit接口，否则可能会丢失SQL操作。调用commit接口之后，该Transaction对象及创建的 ResultSet对象都将被关闭。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |

**示例**

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      await transaction.execute('CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT NOT NULL, age INTEGER, salary REAL)');
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## delete

```TypeScript
delete(predicates: RdbPredicates): Promise<number>
```

根据RdbPredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete(predicates).then((rows: number) => {
    console.info(`Delete rows: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
let predicates2 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates2.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rows = await transaction.delete(predicates2);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteSync

```TypeScript
deleteSync(predicates: RdbPredicates): number
```

根据RdbPredicates的指定实例对象从数据库中删除数据。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  try {
    let rows: number = (store as relationalStore.RdbStore).deleteSync(predicates);
    console.info(`Delete rows: ${rows}`);
  } catch (err) {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
let predicates3 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates3.equalTo('NAME', 'Lisa');
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.deleteSync(predicates3);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteWithReturning

```TypeScript
deleteWithReturning(predicates: RdbPredicates, config: ReturningConfig): Promise<Result>
```

根据RdbPredicates的实例对象从数据库中删除数据，返回[Result](arkts-arkdata-relationalstore-result-i.md)，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Result & gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function deleteWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await rdbStore.deleteWithReturning(predicates, config);
    console.info(`deleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transDeleteWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await trans.deleteWithReturning(predicates, config);
    console.info(`transDeleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## deleteWithReturningSync

```TypeScript
deleteWithReturningSync(predicates: RdbPredicates, config: ReturningConfig): Result
```

根据RdbPredicates的实例对象从数据库中删除数据，返回[Result](arkts-arkdata-relationalstore-result-i.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function deleteWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = rdbStore.deleteWithReturningSync(predicates, config);
    console.info(`deleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transDeleteWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = trans.deleteWithReturningSync(predicates, config);
    console.info(`transDeleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## execute

```TypeScript
execute(sql: string, args?: Array<ValueType>): Promise<ValueType>
```

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType，使用Promise异步回调。该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。此接口不支持执行查询、附加数据库和事务操作，查询可以使用[querySql](#querysql)、 [query](#query)接口代替、附加数据库可以使用 [attach](arkts-arkdata-relationalstore-rdbstore-i.md#attach)接口代替。不支持分号分隔的多条语句。不支持开头包含注释的语句。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。<br>**起始版本：** 20 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;ValueType & gt; | Promise对象，返回sql执行后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

关系型数据库：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 校验数据库完整性
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  (store as relationalStore.RdbStore).execute(SQL_CHECK_INTEGRITY).then((data) => {
    console.info(`check result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  });
}

// 删除表中所有数据
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  (store as relationalStore.RdbStore).execute(SQL_DELETE_TABLE).then((data) => {
    console.info(`delete result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  });
}

// 删表
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  (store as relationalStore.RdbStore).execute(SQL_DROP_TABLE).then((data) => {
    console.info(`drop result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

向量数据库：

```TypeScript
// FLOATVECTOR(2)是维度为2的向量属性，后续操作repr需依照该维度进行。
let createSql = "CREATE TABLE test (ID INTEGER PRIMARY KEY,REPR FLOATVECTOR(2));";
// 建表
await store!.execute(createSql);
// 使用参数绑定插入数据
let insertSql = "insert into test VALUES(?, ?);";
const vectorValue: Float32Array = Float32Array.from([1.5, 6.6]);
await store!.execute(insertSql, [0, vectorValue]);
// 不使用绑定参数直接执行
await store!.execute("insert into test values(1, '[3.5, 1.8]');");
```

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      // 删除表中所有数据
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      const data = await transaction.execute(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## executeSync

```TypeScript
executeSync(sql: string, args?: Array<ValueType>): ValueType
```

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType。该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。此接口不支持执行查询、附加数据库和事务操作，查询可以使用[querySql](#querysql)、 [query](#query)接口代替、附加数据库可以使用 [attach](arkts-arkdata-relationalstore-rdbstore-i.md#attach)接口代替。不支持分号分隔的多条语句。不支持开头包含注释的语句。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。该参数不填，或者填null或undefined，都认为是sql参数语句完整。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 返回sql执行后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
// 校验数据库完整性
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_CHECK_INTEGRITY);
    console.info(`check result: ${data}`);
  } catch (err) {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  }
}

// 删除表中所有数据
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DELETE_TABLE);
    console.info(`delete result: ${data}`);
  } catch (err) {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  }
}

// 删表
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DROP_TABLE);
    console.info(`drop result: ${data}`);
  } catch (err) {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

```TypeScript
// 删除表中所有数据
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      let data = transaction.executeSync(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict?: ConflictResolution): Promise<number>
```

向目标表中插入一行数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串，不应包含空格、逗号和星号，不能以点开头和结尾等，否则会抛出401错误码。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
const valueBucket1: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rowId = await transaction.insert('EMPLOYEE', valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## insertSync

```TypeScript
insertSync(table: string, values: ValuesBucket | sendableRelationalStore.ValuesBucket,
      conflict?: ConflictResolution): number
```

向目标表中插入一行数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket \| sendableRelationalStore.ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let value5 = 'Lisa';
let value6 = 18;
let value7 = 100.5;
let value8 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value5,
  AGE: value6,
  SALARY: value7,
  CODES: value8
};
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rowId: number = transaction.insertSync(
        'EMPLOYEE',
        valueBucket2,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    } catch (e) {
      await transaction.rollback();
      console.error(`Insert is failed, code is ${e.code},message is ${e.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## query

```TypeScript
query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据指定条件查询数据库中的数据，使用Promise异步回调。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array & lt;string & gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;ResultSet & gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
let predicates4 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates4.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const resultSet = await transaction.query(predicates4, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySql

```TypeScript
querySql(sql: string, args?: Array<ValueType>): Promise<ResultSet>
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用Promise异步回调。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;ResultSet & gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const resultSet = await transaction.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySqlSync

```TypeScript
querySqlSync(sql: string, args?: Array<ValueType>): ResultSet
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤 放到[taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResultSet | 返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let resultSet = transaction.querySqlSync("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySqlWithoutRowCount

```TypeScript
querySqlWithoutRowCount(sql: string, bindArgs?: Array<ValueType>): Promise<LiteResultSet>
```

根据指定条件查询数据库中的数据，查询时不计算行数。使用Promise异步回调。性能优于[querySql](#querysql)接口。SQL语句中的各种表达式和 操作符之间的关系操作符号不超过1000个。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | Promise对象。返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
async function querySqlWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
      if (resultSet != undefined) {
        // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

```TypeScript
async function querySqlWithoutRowCountExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySqlWithoutRowCountSync

```TypeScript
querySqlWithoutRowCountSync(sql: string, bindArgs?: Array<ValueType>): LiteResultSet
```

根据指定SQL语句查询数据库中的数据，查询时不计算行数。SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个。对querySqlWithoutRowCountSync同步接口获得的LiteResultSet进行操 作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到[taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array & lt;ValueType & gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

```TypeScript
async function querySqlWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySync

```TypeScript
querySync(predicates: RdbPredicates, columns?: Array<string>): ResultSet
```

根据指定条件查询数据库中的数据。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到 [taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array & lt;string & gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResultSet | 返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.ResultSet | undefined;
  try {
    resultSet = store.querySync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet) {
      resultSet.close();
    }
  }
}
```

```TypeScript
let predicates5 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates5.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let resultSet = transaction.querySync(predicates5, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## queryWithoutRowCount

```TypeScript
queryWithoutRowCount(predicates: RdbPredicates, columns?: Array<string>): Promise<LiteResultSet>
```

根据指定条件查询数据库中的数据，查询时不计算行数，性能优于[query](#query)接口。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array & lt;string & gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
async function queryWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
      if (resultSet != undefined) {
        // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

```TypeScript
async function queryWithoutRowCountExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## queryWithoutRowCountSync

```TypeScript
queryWithoutRowCountSync(predicates: RdbPredicates, columns?: Array<string>): LiteResultSet
```

根据指定条件查询数据库中的数据，查询时不计算行数。对queryWithoutRowCountSync同步接口获得的LiteResultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到 [taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array & lt;string & gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    if (resultSet != undefined) {
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

```TypeScript
async function queryWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## rollback

```TypeScript
rollback(): Promise<void>
```

回滚已经执行的SQL语句，使用Promise异步回调。调用rollback接口之后，该Transaction对象及创建的ResultSet对象都会被关闭。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |

**示例**

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      await transaction.execute('DELETE FROM TEST WHERE age = ? OR age = ?', ['18', '20']);
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): Promise<number>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
const valueBucketF: relationalStore.ValuesBucket = {
  NAME: 'Rose',
  AGE: 22,
  SALARY: 200.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rows = await transaction.update(valueBucketF, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateSync

```TypeScript
updateSync(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): number
```

根据RdbPredicates的指定实例对象更新数据库中的数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
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
  try {
    let rows: number = (store as relationalStore.RdbStore).updateSync(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Updated row count: ${rows}`);
  } catch (err) {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucketG: relationalStore.ValuesBucket = {
  NAME: 'Rose',
  AGE: 22,
  SALARY: 200.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
let predicates1 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates1.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.updateSync(valueBucketG, predicates1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateWithReturning

```TypeScript
updateWithReturning(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定当发生数据冲突时的解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回[Result](arkts-arkdata-relationalstore-result-i.md)，使用Promise 异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Result & gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function updateWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await rdbStore.updateWithReturning(valueBucket1, predicates, config);
    console.info(`updateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transUpdateWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await trans.updateWithReturning(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## updateWithReturningSync

```TypeScript
updateWithReturningSync(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定当发生数据冲突时的解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回[Result](arkts-arkdata-relationalstore-result-i.md)。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](arkts-arkdata-relationalstore-rdbstore-i.md#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function updateWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = rdbStore.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`updateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transUpdateWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = trans.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```
