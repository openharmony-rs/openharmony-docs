# Batch Database Operations
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=404e8f67bcb9eb1f1bc6bc4c58c9e48ab651c853 translatedAt=2026-11-04T09:08:58.704Z pushedAt=2026-11-04T09:40:59.095Z nl=1 -->

## Using TaskPool for Frequent Database Operations

When dealing with scenarios that require frequent database operations, the time-consuming nature of reading from and writing to the database can lead to UI thread blockages. To mitigate this, you are advised to offload these operations to background threads.

By leveraging the TaskPool capabilities provided by ArkTS, database operations can be efficiently moved to background threads. The implementation involves the following steps:

1. Create multiple tasks to support various database operations such as creation, insertion, querying, and clearing.

2. The UI main thread initiates a database operation request and performs operations such as adding, deleting, modifying, and querying the data in the child thread.

<!-- @[operate_child_thread_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/UsingTaskPool.ets) -->

``` TypeScript
import { relationalStore, ValuesBucket } from '@kit.ArkData';
import { taskpool } from '@kit.ArkTS';

@Concurrent
async function create(context: Context) {
  const CONFIG: relationalStore.StoreConfig = {
    name: 'Store.db',
    securityLevel: relationalStore.SecurityLevel.S1,
  };

  // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name
  let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
  console.info(`Get Store.db successfully!`);

  // Create the table.
  const CREATE_TABLE_SQL = 'CREATE TABLE IF NOT EXISTS test (' +
    'id INTEGER PRIMARY KEY AUTOINCREMENT, ' +
    'name TEXT NOT NULL, ' +
    'age INTEGER, ' +
    'salary REAL, ' +
    'blobType BLOB)';
  await store.executeSql(CREATE_TABLE_SQL);
  console.info(`Create table test successfully!`);
}

@Concurrent
async function insert(context: Context, valueBucketArray: Array<relationalStore.ValuesBucket>) {
  const CONFIG: relationalStore.StoreConfig = {
    name: 'Store.db',
    securityLevel: relationalStore.SecurityLevel.S1,
  };

  // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name
  let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
  console.info(`Get Store.db successfully!`);

  // Insert data.
  await store.batchInsert('test', valueBucketArray as Object as Array<relationalStore.ValuesBucket>);
}

@Concurrent
async function query(context: Context): Promise<Array<relationalStore.ValuesBucket>> {
  const CONFIG: relationalStore.StoreConfig = {
    name: 'Store.db',
    securityLevel: relationalStore.SecurityLevel.S1,
  };

  // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name
  let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
  console.info(`Get Store.db successfully!`);

  // Obtain the result set.
  let predicates: relationalStore.RdbPredicates = new relationalStore.RdbPredicates('test');
  let resultSet = await store.query(predicates); // Query all data.
  console.info(`Query data successfully! row count:${resultSet.rowCount}`);
  let index = 0;
  let result = new Array<relationalStore.ValuesBucket>(resultSet.rowCount);
  resultSet.goToFirstRow();
  do {
    result[index++] = resultSet.getRow();
  } while (resultSet.goToNextRow());
  resultSet.close();
  return result;
}

@Concurrent
async function clear(context: Context) {
  const CONFIG: relationalStore.StoreConfig = {
    name: 'Store.db',
    securityLevel: relationalStore.SecurityLevel.S1,
  };

  // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name
  await relationalStore.deleteRdbStore(context, CONFIG);
  console.info(`Delete Store.db successfully!`);
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(async () => {
          let context: Context = this.getUIContext().getHostContext() as Context;

          // Prepare data.
          const count = 5;
          let valueBucketArray = new Array<relationalStore.ValuesBucket>(count);
          for (let i = 0; i < count; i++) {
            let v: relationalStore.ValuesBucket = {
              id: i,
              name: 'zhangsan' + i,
              age: 20,
              salary: 5000 + 50 * i
            };
            valueBucketArray[i] = v;
          }
          await taskpool.execute(create, context);
          await taskpool.execute(insert, context, valueBucketArray);
          let index = 0;
          let ret = await taskpool.execute(query, context) as Array<relationalStore.ValuesBucket>;
          for (let v of ret) {
            console.info(`Row[${index}].id = ${v.id}`);
            console.info(`Row[${index}].name = ${v.name}`);
            console.info(`Row[${index}].age = ${v.age}`);
            console.info(`Row[${index}].salary = ${v.salary}`);
            index++;
          };
          await taskpool.execute(clear, context);
          this.message = 'success';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```


## Using Sendable for Large-Scale Database Operations

When handling large volumes of database data, cross-thread data transfer may still block the UI main thread due to its time-consuming nature. To address this, you are advised to use Sendable to encapsulate database data, thereby reducing cross-thread overhead.

1. Define the data format in the database. Sendable can be used to minimize cross-thread latency.

   <!-- @[define_data_format](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/SharedValuesBucket.ets) -->
   
   ``` TypeScript
   export interface IValueBucket {
     id: number;
     name: string;
     age: number;
     salary: number;
   }
   
   @Sendable
   export class SharedValuesBucket implements IValueBucket {
     public id: number = 0;
     public name: string = '';
     public age: number = 0;
     public salary: number = 0;
   
     constructor(v: IValueBucket) {
       this.id = v.id;
       this.name = v.name;
       this.age = v.age;
       this.salary = v.salary;
     }
   }
   ```

2. The UI main thread initiates a database operation request and performs operations such as adding, deleting, modifying, and querying the data in the child thread.

   <!-- @[taskpool_frequently_operate_database](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/UsingSendable.ets) -->
   
   ``` TypeScript
   import { relationalStore, ValuesBucket } from '@kit.ArkData';
   import { collections, taskpool } from '@kit.ArkTS';
   import { IValueBucket, SharedValuesBucket } from './SharedValuesBucket';
   
   @Concurrent
   async function create(context: Context) {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name
     let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
     console.info(`Get Store.db successfully!`);
   
     // Create the table.
     const CREATE_TABLE_SQL = 'CREATE TABLE IF NOT EXISTS test (' +
       'id INTEGER PRIMARY KEY AUTOINCREMENT, ' +
       'name TEXT NOT NULL, ' +
       'age INTEGER, ' +
       'salary REAL, ' +
       'blobType BLOB)';
     await store.executeSql(CREATE_TABLE_SQL);
     console.info(`Create table test successfully!`);
   }
   
   @Concurrent
   async function insert(context: Context, valueBucketArray: Array<relationalStore.ValuesBucket>) {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
     console.info(`Get Store.db successfully!`);
   
     // Insert data.
     await store.batchInsert('test', valueBucketArray as Object as Array<relationalStore.ValuesBucket>);
   }
   
   @Concurrent
   async function query(context: Context): Promise<collections.Array<SharedValuesBucket | undefined>> {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
     console.info(`Get Store.db successfully!`);
   
     // Obtain the result set.
     let predicates: relationalStore.RdbPredicates = new relationalStore.RdbPredicates('test');
     let resultSet = await store.query(predicates); // Query all data.
     console.info(`Query data successfully! row count:${resultSet.rowCount}`);
   
     // Use collections.Array as a Sendable container to store the results.
     let index = 0;
     let result = collections.Array.create<SharedValuesBucket | undefined>(resultSet.rowCount, undefined);
     resultSet.goToFirstRow();
     do {
       // Read data from ResultSet field by field and wrap it as IValueBucket.
       let v: IValueBucket = {
         id: resultSet.getLong(resultSet.getColumnIndex('id')),
         name: resultSet.getString(resultSet.getColumnIndex('name')),
         age: resultSet.getLong(resultSet.getColumnIndex('age')),
         salary: resultSet.getDouble(resultSet.getColumnIndex('salary'))
       };
       // Wrap it as a @Sendable class instance to support cross-thread reference passing.
       result[index++] = new SharedValuesBucket(v);
     } while (resultSet.goToNextRow());
     resultSet.close();
     return result;
   }
   
   @Concurrent
   async function clear(context: Context) {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     await relationalStore.deleteRdbStore(context, CONFIG);
     console.info(`Delete Store.db successfully!`);
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
   
     build() {
       RelativeContainer() {
         Text(this.message)
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             let context: Context = this.getUIContext().getHostContext() as Context;
   
             // Prepare data.
             const count = 5;
             let valueBucketArray = collections.Array.create<SharedValuesBucket | undefined>(count, undefined);
             for (let i = 0; i < count; i++) {
               let v: IValueBucket = {
                 id: i,
                 name: 'zhangsan' + i,
                 age: 20,
                 salary: 5000 + 50 * i
               };
               valueBucketArray[i] = new SharedValuesBucket(v);
             }
             await taskpool.execute(create, context);
             await taskpool.execute(insert, context, valueBucketArray);
             let index = 0;
             let ret: collections.Array<SharedValuesBucket> =
               await taskpool.execute(query, context) as collections.Array<SharedValuesBucket>;
             for (let v of ret.values()) {
               console.info(`Row[${index}].id = ${v.id}`);
               console.info(`Row[${index}].name = ${v.name}`);
               console.info(`Row[${index}].age = ${v.age}`);
               console.info(`Row[${index}].salary = ${v.salary}`);
               index++;
             };
             await taskpool.execute(clear, context);
             this.message = 'success';
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```


## Using Sendable for Large-Scale Database Operations with Complex Class Instances

The properties of regular class instances can contain Sendable class instances.

For complex regular class instances, you can first wrap the relevant database data fields in Sendable class instances and then let the regular class instances hold these Sendable class instances. This can help lower the cost of cross-thread operations.

1. Define the data format in the database. Sendable can be used to minimize cross-thread latency.

   <!-- @[define_data_format](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/SharedValuesBucket.ets) -->
   
   ``` TypeScript
   export interface IValueBucket {
     id: number;
     name: string;
     age: number;
     salary: number;
   }
   
   @Sendable
   export class SharedValuesBucket implements IValueBucket {
     public id: number = 0;
     public name: string = '';
     public age: number = 0;
     public salary: number = 0;
   
     constructor(v: IValueBucket) {
       this.id = v.id;
       this.name = v.name;
       this.age = v.age;
       this.salary = v.salary;
     }
   }
   ```

2. Define a regular class instance to hold the Sendable class instance.

   <!-- @[define_normal_class_instance_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/Material.ets) -->
   
   ``` TypeScript
   import { SharedValuesBucket } from './SharedValuesBucket';
   import { collections } from '@kit.ArkTS';
   
   export class Material {
     public seq: number = 0;
     public materialName: string = '';
     //... Other properties are omitted.
     public buckets: collections.Array<SharedValuesBucket | undefined>;
   
     constructor(seq: number, materialName: string, buckets: collections.Array<SharedValuesBucket | undefined>) {
       this.seq = seq;
       this.materialName = materialName;
       this.buckets = buckets;
     }
   
     getBuckets() : collections.Array<SharedValuesBucket | undefined>{
       return this.buckets;
     }
   
     setBuckets(buckets: collections.Array<SharedValuesBucket | undefined>) {
       this.buckets = buckets;
     }
   }
   ```

3. The UI main thread initiates a database operation request and performs operations such as adding, deleting, modifying, and querying the data in the child thread.

   <!-- @[complex_class_instance_object_using_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/ComplexClassInstanceObjectUsingSendable.ets) -->
   
   ``` TypeScript
   import { relationalStore, ValuesBucket } from '@kit.ArkData';
   import { collections, taskpool } from '@kit.ArkTS';
   import { IValueBucket, SharedValuesBucket } from './SharedValuesBucket';
   import { Material } from './Material';
   
   @Concurrent
   async function create(context: Context): Promise<boolean> {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     try {
       // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
       let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
       console.info('Get Store.db successfully!');
   
       // Create a table.
       const CREATE_TABLE_SQL = 'CREATE TABLE IF NOT EXISTS test (' +
         'id INTEGER PRIMARY KEY AUTOINCREMENT, ' +
         'name TEXT NOT NULL, ' +
         'age INTEGER, ' +
         'salary REAL, ' +
         'blobType BLOB)';
       await store.executeSql(CREATE_TABLE_SQL);
       console.info('Create table test successfully!');
       return true;
     } catch (err) {
       console.error(`Create db failed, code: ${err.code}, message: ${err.message}`);
       return false;
     }
   }
   
   @Concurrent
   async function insert(context: Context, valueBucketArray: collections.Array<SharedValuesBucket | undefined>) {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
     console.info('Get Store.db successfully!');
   
     // Insert data.
     await store.batchInsert('test', valueBucketArray as Object as Array<ValuesBucket>);
   }
   
   @Concurrent
   async function query(context: Context): Promise<collections.Array<SharedValuesBucket | undefined>> {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     let store: relationalStore.RdbStore = await relationalStore.getRdbStore(context, CONFIG);
     console.info('Get Store.db successfully!');
   
     // Obtain the predicate used for query.
     let predicates: relationalStore.RdbPredicates = new relationalStore.RdbPredicates('test');
     // Query all data.
     let resultSet = await store.query(predicates);
     console.info(`Query data successfully! row count:${resultSet.rowCount}`);
     let index = 0;
     let result = collections.Array.create<SharedValuesBucket | undefined>(resultSet.rowCount, undefined);
     resultSet.goToFirstRow();
     do {
       let value: IValueBucket = {
         id: resultSet.getLong(resultSet.getColumnIndex('id')),
         name: resultSet.getString(resultSet.getColumnIndex('name')),
         age: resultSet.getLong(resultSet.getColumnIndex('age')),
         salary: resultSet.getDouble(resultSet.getColumnIndex('salary'))
       };
       result[index++] = new SharedValuesBucket(value);
     } while (resultSet.goToNextRow());
     resultSet.close();
     return result;
   }
   
   @Concurrent
   async function deleteStore(context: Context) {
     const CONFIG: relationalStore.StoreConfig = {
       name: 'Store.db',
       securityLevel: relationalStore.SecurityLevel.S1,
     };
   
     // The default database file path is context.databaseDir + "/rdb/" + StoreConfig.name.
     await relationalStore.deleteRdbStore(context, CONFIG);
     console.info('Delete Store.db successfully!');
   }
   
   function initMaterial(): Material {
     // Prepare data.
     const count = 5;
     let valueBucketArray = collections.Array.create<SharedValuesBucket | undefined>(count, undefined);
     for (let i = 0; i < count; i++) {
       let value: IValueBucket = {
         id: i,
         name: 'zhangsan' + i,
         age: 20,
         salary: 5000 + 50 * i
       };
       valueBucketArray[i] = new SharedValuesBucket(value);
     }
     let material = new Material(1, 'test', valueBucketArray);
     return material;
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
   
     build() {
       RelativeContainer() {
         Text(this.message)
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(async () => {
             let context: Context = this.getUIContext().getHostContext() as Context;
             let material = initMaterial();
             let ret = await taskpool.execute(create, context);
             if (!ret) {
               console.error('Create db failed.');
               return;
             }
             await taskpool.execute(insert, context, material.getBuckets());
             let index = 0;
             let resultSet: collections.Array<SharedValuesBucket> =
               await taskpool.execute(query, context) as collections.Array<SharedValuesBucket>;
             material.setBuckets(resultSet);
             for (let value of resultSet.values()) {
               console.info(`Row[${index}].id = ${value.id}`);
               console.info(`Row[${index}].name = ${value.name}`);
               console.info(`Row[${index}].age = ${value.age}`);
               console.info(`Row[${index}].salary = ${value.salary}`);
               index++;
             }
             await taskpool.execute(deleteStore, context);
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```