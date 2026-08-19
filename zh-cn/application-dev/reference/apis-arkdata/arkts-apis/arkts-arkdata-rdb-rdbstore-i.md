# RdbStore

提供管理关系数据库（RDB）方法的接口。 在使用以下相关接口前，请使用 [executeSql](#executesql) 接口初始化数据库表结构和相关数据。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)

<!--Device-rdb-interface RdbStore--><!--Device-rdb-interface RdbStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

向目标表中插入一组数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert)

<!--Device-RdbStore-batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void--><!--Device-RdbStore-batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array&lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当操作成功，err为undefined，data为插入的数据个数；否则为错误对象。 |

**示例**

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

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>
```

向目标表中插入一组数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [batchInsert](arkts-arkdata-relationalstore-rdbstore-i.md#batchinsert)

<!--Device-RdbStore-batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>--><!--Device-RdbStore-batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array&lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回插入的数据个数，否则返回-1。 |

**示例**

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

## beginTransaction

```TypeScript
beginTransaction(): void
```

在开始执行SQL语句之前，开始事务。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [beginTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#begintransaction)

<!--Device-RdbStore-beginTransaction(): void--><!--Device-RdbStore-beginTransaction(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例**

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

提交已执行的SQL语句。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [commit](arkts-arkdata-relationalstore-rdbstore-i.md#commit)

<!--Device-RdbStore-commit(): void--><!--Device-RdbStore-commit(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例**

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

根据RdbPredicates的指定实例对象从数据库中删除数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [delete](arkts-arkdata-relationalstore-rdbstore-i.md#delete)

<!--Device-RdbStore-delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void--><!--Device-RdbStore-delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当操作成功，err为undefined，data为受影响的行数；否则为错误对象。 |

**示例**

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

## delete

```TypeScript
delete(predicates: RdbPredicates): Promise<number>
```

根据RdbPredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [delete](arkts-arkdata-relationalstore-rdbstore-i.md#delete)

<!--Device-RdbStore-delete(predicates: RdbPredicates): Promise<number>--><!--Device-RdbStore-delete(predicates: RdbPredicates): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回受影响的行数。 |

**示例**

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

## executeSql

```TypeScript
executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void
```

执行包含指定参数但不返回值的SQL语句，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [executeSql](arkts-arkdata-relationalstore-rdbstore-i.md#executesql)

<!--Device-RdbStore-executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void--><!--Device-RdbStore-executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array&lt;ValueType&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数需为空数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当操作成功，err为undefined；否则为错误对象。 |

**示例**

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

## executeSql

```TypeScript
executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>
```

执行包含指定参数但不返回值的SQL语句，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [executeSql](arkts-arkdata-relationalstore-rdbstore-i.md#executesql)

<!--Device-RdbStore-executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>--><!--Device-RdbStore-executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array&lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'"
let promise = rdbStore.executeSql(SQL_DELETE_TABLE)
promise.then(() => {
  console.info('Delete table done.')
}).catch((err: BusinessError) => {
  console.error("ExecuteSql failed, err: " + err)
})
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void
```

向目标表中插入一行数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [insert](arkts-arkdata-relationalstore-rdbstore-i.md#insert)

<!--Device-RdbStore-insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void--><!--Device-RdbStore-insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当操作成功，err为undefined，data为行ID；否则为错误对象。 |

**示例**

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

## insert

```TypeScript
insert(table: string, values: ValuesBucket): Promise<number>
```

向目标表中插入一行数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [insert](arkts-arkdata-relationalstore-rdbstore-i.md#insert)

<!--Device-RdbStore-insert(table: string, values: ValuesBucket): Promise<number>--><!--Device-RdbStore-insert(table: string, values: ValuesBucket): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回行ID；否则返回-1。 |

**示例**

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

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void
```

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用callback异步回调。 > **说明：** > > 其中device通过调用<!--RP1--> > [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync) > 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [obtainDistributedTableName](arkts-arkdata-relationalstore-rdbstore-i.md#obtaindistributedtablename)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void--><!--Device-RdbStore-obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 远程设备ID 。 |
| table | string | 是 | 远程设备的本地表名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数。当操作成功，err为undefined，data为远程设备的分布式表名；否则为错误对象。 |

**示例**

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

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string): Promise<string>
```

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用Promise异步回调。 > **说明：** > > 其中device通过调用<!--RP1--> > [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync) > 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [obtainDistributedTableName](arkts-arkdata-relationalstore-rdbstore-i.md#obtaindistributedtablename)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-obtainDistributedTableName(device: string, table: string): Promise<string>--><!--Device-RdbStore-obtainDistributedTableName(device: string, table: string): Promise<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 远程设备ID。 |
| table | string | 是 | 远程设备的本地表名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。如果操作成功，返回远程设备的分布式表名。 |

**示例**

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

## off_dataChange

```TypeScript
off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

从数据库中删除指定类型的指定观察者，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](arkts-arkdata-relationalstore-rdbstore-i.md#off_datachange)

<!--Device-RdbStore-off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void--><!--Device-RdbStore-off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 指已注册的数据更改观察者。Array&lt;string&gt;为数据库中的数据发生改变的对端设备ID。 |

**示例**

```TypeScript
let devices: Array<string>;

try {
  rdbStore.off('dataChange', data_rdb.SubscribeType.SUBSCRIBE_TYPE_REMOTE, (storeObserver: Array<string>) => {
    for (let i = 0; i < devices.length; i++) {
      console.info('device=' + devices[i] + ' data changed')
    }
  })
} catch (err) {
  console.error('Unregister observer failed')
}
```

## on_dataChange

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

注册数据库的观察者。当分布式数据库中的数据发生更改时，将调用回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](arkts-arkdata-relationalstore-rdbstore-i.md#on_datachange)

<!--Device-RdbStore-on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void--><!--Device-RdbStore-on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 指分布式数据库中数据更改事件的观察者。Array&lt;string&gt;为数据库中的数据发生改变的对端设备ID。 |

**示例**

```TypeScript
let devices: Array<string>;

try {
  rdbStore.on('dataChange', data_rdb.SubscribeType.SUBSCRIBE_TYPE_REMOTE, (storeObserver: Array<string>) => {
    for (let i = 0; i < devices.length; i++) {
      console.info('device=' + devices[i] + ' data changed')
    }
  })
} catch (err) {
  console.error('Register observer failed')
}
```

## query

```TypeScript
query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

根据指定条件查询数据库中的数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [query](arkts-arkdata-relationalstore-rdbstore-i.md#query)

<!--Device-RdbStore-query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void--><!--Device-RdbStore-query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。当操作成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**示例**

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

## query

```TypeScript
query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据指定条件查询数据库中的数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [query](arkts-arkdata-relationalstore-rdbstore-i.md#query)

<!--Device-RdbStore-query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>--><!--Device-RdbStore-query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**示例**

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

## querySql

```TypeScript
querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void
```

根据指定SQL语句查询数据库中的数据，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql)

<!--Device-RdbStore-querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void--><!--Device-RdbStore-querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array&lt;ValueType&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数需为空数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。当操作成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**示例**

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

## querySql

```TypeScript
querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

根据指定SQL语句查询数据库中的数据，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querysql)

<!--Device-RdbStore-querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>--><!--Device-RdbStore-querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array&lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**示例**

```TypeScript
let promise: void = rdbStore.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'")
promise.then((resultSet: void) => {
  console.info("ResultSet column names: " + resultSet.columnNames)
  console.info("ResultSet column count: " + resultSet.columnCount)
}).catch((err: BusinessError) => {
  console.error("Query failed, err: " + err)
})
```

## rollBack

```TypeScript
rollBack(): void
```

回滚已经执行的SQL语句。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [rollBack](arkts-arkdata-relationalstore-rdbstore-i.md#rollback)

<!--Device-RdbStore-rollBack(): void--><!--Device-RdbStore-rollBack(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例**

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

设置分布式列表，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedTables](arkts-arkdata-relationalstore-rdbstore-i.md#setdistributedtables)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-setDistributedTables(tables: Array<string>, callback: AsyncCallback<void>): void--><!--Device-RdbStore-setDistributedTables(tables: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | 是 | 要设置的分布式列表表名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当操作成功，err为undefined；否则为错误对象。 |

**示例**

```TypeScript
rdbStore.setDistributedTables(["EMPLOYEE"], (err: BusinessError) => {
  if (err) {
    console.error('SetDistributedTables failed, err: ' + err)
    return
  }
  console.info('SetDistributedTables successfully.')
})
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>): Promise<void>
```

设置分布式列表，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedTables](arkts-arkdata-relationalstore-rdbstore-i.md#setdistributedtables)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-setDistributedTables(tables: Array<string>): Promise<void>--><!--Device-RdbStore-setDistributedTables(tables: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | 是 | 要设置的分布式列表表名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
let promise: void = rdbStore.setDistributedTables(["EMPLOYEE"])
promise.then(() => {
  console.info("SetDistributedTables successfully.")
}).catch((err: BusinessError) => {
  console.error("SetDistributedTables failed, err: " + err)
})
```

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void
```

在设备之间同步数据，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sync](arkts-arkdata-relationalstore-rdbstore-i.md#sync)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void--><!--Device-RdbStore-sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 指同步模式。该值可以是推、拉。 |
| predicates | RdbPredicates | 是 | 约束同步数据和设备。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数。当操作成功，err为undefined，data为同步结果，其中string为设备ID， number为每个设备同步状态，0表示成功，其他值表示失败；否则为错误对象。 |

**示例**

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

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>
```

在设备之间同步数据，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sync](arkts-arkdata-relationalstore-rdbstore-i.md#sync)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-RdbStore-sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>--><!--Device-RdbStore-sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 指同步模式。该值可以是推、拉。 |
| predicates | RdbPredicates | 是 | 约束同步数据和设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise对象，用于向调用者发送同步结果。string：设备ID；number：每个设备同步状态，0表示成功，其他值表示失败。 |

**示例**

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

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

根据RdbPredicates的指定实例对象更新数据库中的数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [update](arkts-arkdata-relationalstore-rdbstore-i.md#update)

<!--Device-RdbStore-update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void--><!--Device-RdbStore-update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当操作成功，err为undefined，data为受影响的行数；否则为错误对象。 |

**示例**

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

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [update](arkts-arkdata-relationalstore-rdbstore-i.md#update)

<!--Device-RdbStore-update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>--><!--Device-RdbStore-update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 指定的Promise回调方法。返回受影响的行数。 |

**示例**

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

