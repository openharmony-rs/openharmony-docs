# 批量数据写数据库场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

对于需要频繁读写关系型数据库的场景，可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)将数据库操作调度到后台线程执行，避免数据库打开、建表、批量插入和查询过程阻塞宿主线程。

ArkTS-Sta中的TaskPool任务函数不需要使用@Concurrent装饰，taskpool不需要从@kit.ArkTS导入。关系型数据库relationalStore已提供ArkTS-Sta接口，ValuesBucket中的数字字段需要使用long或double类型。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 示例使用@kit.ArkData中的关系型数据库能力。数据库API涉及上下文、权限、数据库路径和错误码处理，实际工程中需要按业务要求补充异常处理。若项目使用的具体数据库接口未标注支持后台线程调用，应先确认接口约束后再放入TaskPool任务。

## 使用TaskPool进行频繁数据库操作

本场景按照以下步骤实现：

1. 使用UserRecord定义数据库记录的数据结构，并使用long和double类型表示数据库中的整数和浮点数字段。
2. 将建表、批量插入、查询和清理分别封装为独立的TaskPool任务函数。插入任务先把UserRecord数组转换为ValuesBucket数组，再通过batchInsert一次写入多条记录；查询任务将ResultSet逐行转换回UserRecord，并在读取完成后关闭ResultSet。
3. 宿主线程负责获取UIAbilityContext、构造待写入数据，并按照“创建数据库、批量插入、查询校验、清理数据库”的顺序调用taskpool.execute。数据库操作在TaskPool工作线程中执行，宿主线程只等待各阶段结果并处理日志或界面更新。
4. 数据量较大时，先将记录数组拆分为多个批次，再使用SequenceRunner按顺序提交写入任务，避免多个任务同时写入同一个数据库造成锁竞争。

```ts
// ArkTS-Sta示例
// UserRecord.ets
export class UserRecord {
  id: long = 0;
  name: string = "";
  age: long = 0;
  salary: double = 0.0;

  constructor(id: long, name: string, age: long, salary: double) {
    this.id = id;
    this.name = name;
    this.age = age;
    this.salary = salary;
  }
}
```

```ts
// ArkTS-Sta示例
// DatabaseTask.ets
import { relationalStore } from '@kit.ArkData';
import common from '@ohos.app.ability.common';
import { UserRecord } from './UserRecord';

const TABLE_NAME: string = "test";
const STORE_CONFIG: relationalStore.StoreConfig = {
  name: "Store.db",
  securityLevel: relationalStore.SecurityLevel.S1
};

const CREATE_TABLE_SQL: string = "CREATE TABLE IF NOT EXISTS test (" +
  "id INTEGER PRIMARY KEY, " +
  "name TEXT NOT NULL, " +
  "age INTEGER, " +
  "salary REAL)";

function toValuesBucket(record: UserRecord): relationalStore.ValuesBucket {
  return {
    "id": record.id,
    "name": record.name,
    "age": record.age,
    "salary": record.salary
  };
}

async function getStore(context: common.Context): Promise<relationalStore.RdbStore> {
  return await relationalStore.getRdbStore(context, STORE_CONFIG);
}

export async function createDatabase(context: common.Context): Promise<void> {
  let store: relationalStore.RdbStore = await getStore(context);
  await store.executeSql(CREATE_TABLE_SQL);
}

export async function insertRecords(context: common.Context, records: Array<UserRecord>): Promise<long> {
  let valueBuckets: Array<relationalStore.ValuesBucket> = [];
  for (let record of records) {
    valueBuckets.push(toValuesBucket(record));
  }

  let store: relationalStore.RdbStore = await getStore(context);
  return await store.batchInsert(TABLE_NAME, valueBuckets);
}

export async function queryRecords(context: common.Context): Promise<Array<UserRecord>> {
  let store: relationalStore.RdbStore = await getStore(context);
  let predicates: relationalStore.RdbPredicates = new relationalStore.RdbPredicates(TABLE_NAME);
  let resultSet: relationalStore.ResultSet = await store.query(predicates);
  let records: Array<UserRecord> = [];

  try {
    if (resultSet.rowCount <= 0) {
      return records;
    }

    resultSet.goToFirstRow();
    do {
      let id: long = resultSet.getLong(resultSet.getColumnIndex("id"));
      let name: string = resultSet.getString(resultSet.getColumnIndex("name"));
      let age: long = resultSet.getLong(resultSet.getColumnIndex("age"));
      let salary: double = resultSet.getDouble(resultSet.getColumnIndex("salary"));
      records.push(new UserRecord(id, name, age, salary));
    } while (resultSet.goToNextRow());
  } finally {
    resultSet.close();
  }

  return records;
}

export async function clearDatabase(context: common.Context): Promise<void> {
  await relationalStore.deleteRdbStore(context, STORE_CONFIG);
}
```

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import common from '@ohos.app.ability.common';
import { UserRecord } from './UserRecord';
import {
  clearDatabase,
  createDatabase,
  insertRecords,
  queryRecords
} from './DatabaseTask';

function buildRecords(count: int): Array<UserRecord> {
  let records: Array<UserRecord> = [];

  for (let index: int = 0; index < count; index++) {
    records.push(new UserRecord(
      Int.toLong(index),
      "zhangsan" + index,
      Int.toLong(20),
      5000.0 + Int.toDouble(index) * 50.0
    ));
  }

  return records;
}

async function runBatchDatabaseOperations(context: common.Context): Promise<void> {
  let records: Array<UserRecord> = buildRecords(5);

  await taskpool.execute(createDatabase, context);

  let insertCount: long =
    (await taskpool.execute(insertRecords, context, records)) as long;
  console.info("insert count: " + insertCount); // insert count: 5

  let result: Array<UserRecord> =
    (await taskpool.execute(queryRecords, context)) as Array<UserRecord>;
  for (let record of result) {
    console.info("id: " + record.id + ", name: " + record.name); // id: 0, name: zhangsan0（首次输出，后续依次递增）
  }

  await taskpool.execute(clearDatabase, context);
}

@Entry
@Component
struct Index {
  build() {
    Column(undefined) {
      Button("Batch insert")
        .onClick((e: ClickEvent) => {
          let context: common.UIAbilityContext =
            this.getUIContext().getHostContext() as common.UIAbilityContext;
          runBatchDatabaseOperations(context);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 大容量数据写入

动态ArkTS文档中通常使用Sendable封装数据库数据，以减少跨线程拷贝。ArkTS-Sta采用共享内存模型，不需要通过@Sendable声明共享对象；但这也意味着任务提交后，宿主线程和TaskPool任务可能看到同一份可变数据。大容量数据写入时建议遵循以下策略：

1. 任务提交前生成只读业务数据，提交后不要继续修改该数组。
2. 如需避免任务与宿主线程共享同一份数组结构，提交前显式拷贝数组。
3. 多个批量写入任务访问同一数据库时，优先使用SequenceRunner串行执行，减少数据库锁竞争。

以下示例将大数组拆分为多个批次，并通过SequenceRunner保证写入任务按顺序执行。

```ts
// ArkTS-Sta示例
// BatchWriter.ets
import common from '@ohos.app.ability.common';
import { UserRecord } from './UserRecord';
import { insertRecords } from './DatabaseTask';

function splitRecords(records: Array<UserRecord>, chunkSize: int): Array<Array<UserRecord>> {
  let chunks: Array<Array<UserRecord>> = [];
  let current: Array<UserRecord> = [];

  for (let record of records) {
    current.push(record);
    if (current.length >= chunkSize) {
      chunks.push(current);
      current = [];
    }
  }

  if (current.length > 0) {
    chunks.push(current);
  }

  return chunks;
}

export async function insertRecordsByChunks(
  context: common.Context,
  records: Array<UserRecord>,
  chunkSize: int
): Promise<long> {
  let chunks: Array<Array<UserRecord>> = splitRecords(Array.from(records), chunkSize);
  let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner("database-writer");
  let total: long = 0;

  for (let chunk of chunks) {
    let task: taskpool.Task = new taskpool.Task(insertRecords, context, chunk);
    let count: long = (await runner.execute(task)) as long;
    total += count;
  }

  return total;
}
```

在Index.ets中调用时，先引入insertRecordsByChunks，再复用前文的buildRecords生成数据。以下示例在按钮点击后创建数据库，按20条一批写入100条数据，写入完成后查询结果并清理数据库。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import common from '@ohos.app.ability.common';
import { UserRecord } from './UserRecord';
import {
  clearDatabase,
  createDatabase,
  queryRecords
} from './DatabaseTask';
import { insertRecordsByChunks } from './BatchWriter';

function buildRecords(count: int): Array<UserRecord> {
  let records: Array<UserRecord> = [];

  for (let index: int = 0; index < count; index++) {
    records.push(new UserRecord(
      Int.toLong(index),
      "zhangsan" + index,
      Int.toLong(20),
      5000.0 + Int.toDouble(index) * 50.0
    ));
  }

  return records;
}

async function runBatchInsertByChunks(context: common.Context): Promise<void> {
  let records: Array<UserRecord> = buildRecords(100);

  await taskpool.execute(createDatabase, context);

  let insertCount: long = await insertRecordsByChunks(context, records, 20);
  console.info("insert count: " + insertCount); // insert count: 100

  let result: Array<UserRecord> =
    (await taskpool.execute(queryRecords, context)) as Array<UserRecord>;
  console.info("query count: " + result.length); // query count: 100

  await taskpool.execute(clearDatabase, context);
}

@Entry
@Component
struct Index {
  build() {
    Column(undefined) {
      Button("Batch insert by chunks")
        .onClick((e: ClickEvent) => {
          let context: common.UIAbilityContext =
            this.getUIContext().getHostContext() as common.UIAbilityContext;
          runBatchInsertByChunks(context);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- ValuesBucket是数据库接口使用的键值对类型。ArkTS-Sta中数字字段应使用long或double，避免沿用动态ArkTS中的number写法。
- 不建议将同一个可变Array\<UserRecord>在多个TaskPool任务中并发修改。需要并发读写时，应使用锁或并发容器保护。
- 对同一个数据库进行大量写操作时，盲目并发提交多个写入任务可能触发数据库锁竞争。可使用SequenceRunner串行写入，或在一个任务内完成分批写入。
- RdbStore和ResultSet等数据库对象建议在任务内部获取和关闭，避免跨任务长期共享。
- 单条数据过大时，需要遵守关系型数据库接口文档中的大小限制；大批量查询时建议分批查询，避免一次性返回过多数据。
