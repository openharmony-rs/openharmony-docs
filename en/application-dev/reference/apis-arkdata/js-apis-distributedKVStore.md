# @ohos.data.distributedKVStore (Distributed KV Store)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->

The **distributedKVStore** module implements collaboration between databases for different devices that form a Super Device. You can use the APIs provided by this module to save application data to a distributed key-value (KV) store and perform operations, such as adding, deleting, modifying, and querying data, and synchronizing data across devices.

The **distributedKVStore** module provides the following functionalities:

- [KVManager](#kvmanager): provides a **KVManager** instance to obtain KV store information.
- [KVStoreResultSet](#kvstoreresultset): provides APIs for accessing the results obtained from a KV store.
- [Query](#query): provides APIs for setting predicates for data query.
- [SingleKVStore](#singlekvstore): provides APIs for querying data in single KV stores and synchronizing data across devices. The single KV stores manage data without distinguishing devices.
- [DeviceKVStore](#devicekvstore): provides APIs for querying data in device KV stores and synchronizing data across devices. This class inherits from [SingleKVStore](#singlekvstore). The device KV stores manage data by device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { distributedKVStore } from '@kit.ArkData';
```

## KVManagerConfig

Provides the **KVManager** instance configuration, including the bundle name of the invoker and the application context.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name    | Type             | Read Only| Optional| Description                                                        |
| ---------- | ---------------|----- | ---- | ------------------------------------------------------------ |
| context    | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md)    | No  | No  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md).<br>Since API version 10, the parameter type of context is [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md).|
| bundleName | string          | No  | No  | Bundle name of the caller. The value cannot be empty and must be a string of 1 to 256 bytes.                                              |

## Constants

Provides constants of the distributed KV store.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name                 | Type  | Read Only| Optional| Description                                                      |
| --------------------- | ------ | ---- | ---- | ---------------------------------------------------------- |
| MAX_KEY_LENGTH        | number | Yes  | No  | Maximum length of a key in the database, which is 1024 bytes.       |
| MAX_VALUE_LENGTH      | number | Yes  | No  | Maximum length of a value in the database, which is 4194303 bytes.  |
| MAX_KEY_LENGTH_DEVICE | number | Yes  | No  | Maximum length of a key in a device KV store, which is 896 bytes.|
| MAX_STORE_ID_LENGTH   | number | Yes  | No  | Maximum length of a KV store ID, which is 128 bytes.       |
| MAX_QUERY_LENGTH      | number | Yes  | No  | Maximum query length, which is 512000 bytes.                  |
| MAX_BATCH_SIZE        | number | Yes  | No  | Maximum number of batch operations allowed, which is 128.                         |

## ValueType

Enumerates the types of the value in a KV pair.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name      | Value| Description                |
| ---------- | - | -------------------- |
| STRING     | 0 | String.  |
| INTEGER    | 1 | Integer.    |
| FLOAT      | 2 | Float (single-precision floating point).  |
| BYTE_ARRAY | 3 | Byte array.|
| BOOLEAN    | 4 | Boolean.  |
| DOUBLE     | 5 | Double (double-precision floating point).|

## Value

Defines the **value** object in a KV store.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name | Type  | Read Only| Optional| Description                                                              |
| ----- | -------|-----|-----|------------------------------------------------------------------|
| type | [ValueType](#valuetype) | No   | No  | Type of the value.                                                            |
| value | Uint8Array \| string \| number \| boolean| No   | No  | Value in a key-value pair. The length of the Uint8Array and string types ranges from 0 to [MAX_VALUE_LENGTH](#constants). The value range of the number and boolean types is determined by their own types.|

## Entry

Defines the KV pairs stored in a KV store.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name | Type       | Read Only| Optional| Description    |
| ----- | ---------- |-- | ---- | -------- |
| key   | string          | No   | No  | Key name. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).  |
| value | [Value](#value) | No   | No  | Value object of the KV pair.|

## ChangeNotification

Defines the content of a data change notification, including inserted data, updated data, deleted data, and device ID.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name         | Type         | Read Only| Optional      | Description                    |
| ------------- | ----------------- |---- | ---- | ------------------------ |
| insertEntries | [Entry](#entry)[] | No   | No  | Data inserted.          |
| updateEntries | [Entry](#entry)[] | No   | No  | Data updated.          |
| deleteEntries | [Entry](#entry)[] | No   | No   | Data deleted.          |
| deviceId      | string            | No   | No   | UUID of the device.|

## SyncMode

Enumerates the sync modes.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name     | Value| Description                                          |
| --------- | - | ---------------------------------------------- |
| PULL_ONLY | 0 | Pull data from the peer end to the local end only.                   |
| PUSH_ONLY | 1 | Push data from the local end to the peer end only.                   |
| PUSH_PULL | 2 | Push data from the local end to the peer end and then pull data from the peer end to the local end.|

## SubscribeType

Enumerates the subscription types.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name                 | Value| Description                        |
| --------------------- | - | ---------------------------- |
| SUBSCRIBE_TYPE_LOCAL  | 0 | Local data changes.        |
| SUBSCRIBE_TYPE_REMOTE | 1 | Remote data changes.        |
| SUBSCRIBE_TYPE_ALL    | 2 | Local and remote data changes.  |

## KVStoreType

Enumerates the distributed KV store types.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name                | Value| Description                                                        |
| -------------------- | - | ------------------------------------------------------------ |
| DEVICE_COLLABORATION | 0 | Device KV store.<br>The device KV store manages data by device, which eliminates conflicts. Data can be queried by device.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore|
| SINGLE_VERSION       | 1 | Single KV store.<br>The single KV store does not differentiate data by device. If entries with the same key are modified on different devices, the value will be overwritten.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|

## SecurityLevel

Enumerates the KV store security levels.

> **NOTE**
>
> For the scenarios involving a single device, you can upgrade the security level of a KV store by modifying the **securityLevel** parameter. When upgrading the database security level, observe the following:
> * This operation does not apply to the databases that require cross-device sync. Data cannot be synced between databases of different security levels. If you want to upgrade the security level of a database, you are advised to create a database of a higher security level.
> * After closing the current database, modify the **securityLevel** parameter to reset the database security level, and then call the [getKVStore](#getkvstore) API to open the database again.
> * You cannot downgrade the database security level. For example, you can change the database security level from S2 to S3, but cannot change it from S3 to S2.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name       | Value| Description                                                        |
| --------   | - | ------------------------------------------------------------ |
| S1        | 2 | Low security level. Disclosure, tampering, corruption, or loss of the data may cause minor impact on an individual or group.<br>Examples: gender and nationality information, and user application records|
| S2        | 3 | Medium security level. Disclosure, tampering, corruption, or loss of the data may cause major impact on an individual or group.<br>Examples: individual mailing addresses and nicknames|
| S3        | 5 | High security level. Disclosure, tampering, corruption, or loss of the data may cause critical impact on an individual or group.<br>Examples: real-time precise positioning information and movement trajectory |
| S4        | 6 | Critical security level for a KV store. Disclosure, tampering, corruption, or loss of the data may cause significant adverse impact on an individual or group.<br><br>Examples: political opinions, religion, philosophical belief, trade union membership, genetic data, biological information, health, sexual life status, sexual orientation, device authentication, and personal credit card information.|

## Options

Provides KV store configuration.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

| Name         | Type                       | Read Only| Optional| Description                                                        |
| --------------- | -------------- | ---- | ----| -------------------------|
| createIfMissing | boolean                         | No   | Yes | Whether to create a database when database files do not exist. The value **true** means to create a database, and the value **false** means the opposite. The default value is **true**.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|
| encrypt         | boolean                         | No   | Yes  | Whether to encrypt the database files. The value **true** means to encrypt the database files, and the value **false** means the opposite. The default value is **false**.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|
| backup          | boolean                         | No   | Yes  | Whether to back up the database files. The value **true** means to back up the database files, and the value **false** means the opposite. The default value is **true**.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|
| autoSync        | boolean                         | No   | Yes  | Whether to enable auto sync across devices. The default value is **false**, indicating that only manual sync is supported. If this parameter is set to **true**, <!--RP1-->it takes effect only in [device collaboration using cross-device calls](../../application-models/hop-multi-device-collaboration.md#using-cross-device-call).<!--RP1End--><br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core<br>**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC|
| kvStoreType     | [KVStoreType](#kvstoretype)     | No   | Yes  | Type of the KV store to create. The default value is **DEVICE_COLLABORATION**, which indicates a device KV store.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|
| securityLevel   | [SecurityLevel](#securitylevel) | No   | No  | Security level of the KV store.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.Core|
| schema          | [Schema](#schema)               | No   | Yes  | Schema that defines the values stored in the KV store. The default value is **undefined**, which means no schema is used.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore|
| rootDir<sup>24+</sup> | string                         | No   | Yes | Database file storage path. If it is not set, the default path (context.databaseDir) is used. It cannot be an empty string. When creating or deleting a database, the directory must have the access permission and exist. This parameter is not verified when the database is closed.<br>**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore|

## BackupConfig<sup>24+</sup>

Configures database backup.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

| Name         | Type                       | Read Only| Optional| Description                                                        |
| --------------| -------------- | ---- | ----| -------------------------|
| fileName      | string         | No| No| Name of the database to back up. There is no length limit, but the name cannot contain slashes (/).|
| filePath      | string         | No| No| Path of the database to back up. There is no length limit.|

## Schema

Defines the schema of a KV store. You can create a **Schema** object and pass it in [Options](#options) when creating or opening a KV store.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

| Name   | Type                   | Read Only| Optional| Description                      |
| ------- | ----------------------- | ---- | ---- | -------------------------- |
| root    | [FieldNode](#fieldnode) | No | No | Definitions of all the fields in **Value**.|
| indexes | Array\<string>          | No | No | Indexes of the fields in **Value**. Indexes are created only for **FieldNode** with this parameter specified. The format is **'$.field1'**, **'$.field2'**.|
| mode    | number                  | No | No | Schema mode, which can be **0** (compatible mode) or **1** (strict mode).|
| skip    | number                  | No | No | Number of bytes to be skipped during the value check. The value range is [0, 4 × 1024 × 1024 - 2].|

Strict mode: In this mode, the value to be inserted must strictly match the schema defined, and the number and format of fields must be consistent with that defined in the schema. Otherwise, an error will be returned.

Compatible mode: In this mode, the value check is successful as long as the value has the characteristics defined in the schema. Extra fields are allowed. For example, if **id** and **name** are defined, more fields such as **id**, **name**, and **age** can be inserted.

### constructor

constructor()

Defines a constructor used to create a **Schema** instance.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Example**

```ts

let child1 = new distributedKVStore.FieldNode('id');
child1.type = distributedKVStore.ValueType.INTEGER;
child1.nullable = false;
child1.default = '1';
let child2 = new distributedKVStore.FieldNode('name');
child2.type = distributedKVStore.ValueType.STRING;
child2.nullable = false;
child2.default = 'zhangsan';

let schema = new distributedKVStore.Schema();
schema.root.appendChild(child1);
schema.root.appendChild(child2);
schema.indexes = ['$.id', '$.name'];
schema.mode = 1;
schema.skip = 0;
```

## FieldNode

Represents a **Schema** instance, which provides the methods for defining the values stored in a KV store.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

| Name    | Type   | Read Only| Optional| Description                                                                                                    |
| -------- | ------- | ---- | ---- |--------------------------------------------------------------------------------------------------------|
| nullable | boolean | No  | No  | Whether the field can be null. The value **true** means the node field can be null; the value **false** means the opposite.                                                       |
| default  | string  | No  | No  | Default value of **FieldNode**. The value of **default** must be a string literal that can be parsed by the type. Ensure that the value type is the same as **type**.                                       |
| type     | number  | No  | No  | **FieldNode** data type, which is a value of [ValueType](#valuetype). Note: Currently, the **BYTE_ARRAY** type is not supported. Using this type may cause a failure in calling [getKVStore](#getkvstore). |

### constructor

constructor(name: string)

Defines a constructor used to create a **FieldNode** instance with a string field.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name| Type| Mandatory| Description           |
| ------ | -------- | ---- | --------------- |
| name   | string   | Yes  | Value of the **FieldNode**, which cannot be empty. The value contains 1 to 64 characters.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |

### appendChild

appendChild(child: FieldNode): boolean

Appends a child node to this **FieldNode**.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name| Type               | Mandatory| Description      |
| ------ | ----------------------- | ---- |----------|
| child  | [FieldNode](#fieldnode) | Yes  | Child node to append.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |

**Example**

```ts

try {
  let node: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('root');
  let child1: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child1');
  let child2: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child2');
  let child3: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child3');
  node.appendChild(child1);
  node.appendChild(child2);
  node.appendChild(child3);
  console.info('appendNode ' + JSON.stringify(node));
  child1 = null;
  child2 = null;
  child3 = null;
  node = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to append child. Code: ${error.code}, message: ${error.message}`);
}
```

## distributedKVStore.createKVManager

createKVManager(config: KVManagerConfig): KVManager

Creates a **KVManager** instance for KV store management.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type                     | Mandatory| Description                                                     |
| ------ | ----------------------------- | ---- | --------------------------------------------------------- |
| config | [KVManagerConfig](#kvmanagerconfig) | Yes  | Configuration of the **KVManager** instance , including the application context and the bundle name of the caller (cannot be empty).|

**Return value**

| Type                                  | Description                                      |
| -------------------------------------- | ------------------------------------------ |
| [KVManager](#kvmanager) | **KVManager** instance created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let kvManager: distributedKVStore.KVManager;
let appId: string = 'com.example.datamanagertest';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbilityStage onCreate');
    let context = this.context;
    const kvManagerConfig: distributedKVStore.KVManagerConfig = {
      context: context,
      bundleName: appId
    }
    try {
      kvManager = distributedKVStore.createKVManager(kvManagerConfig);
      console.info('Succeeded in creating KVManager');
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create KVManager. Code: ${error.code}, message: ${error.message}`);
    }
    if (kvManager !== undefined) {
      // Perform subsequent operations such as creating a KV store.
      // ...
    }
  }
}
```

FA model:

<!--code_no_check_fa-->
```ts
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let kvManager: distributedKVStore.KVManager;
let appId: string = 'com.example.datamanagertest';
let context = featureAbility.getContext();
const kvManagerConfig: distributedKVStore.KVManagerConfig = {
  context: context,
  bundleName: appId
}
try {
  kvManager = distributedKVStore.createKVManager(kvManagerConfig);
  console.info('Succeeded in creating KVManager');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create KVManager. Code: ${error.code}, message: ${error.message}`);
}
if (kvManager !== undefined) {
  kvManager = kvManager as distributedKVStore.KVManager;
  // Perform subsequent operations such as creating a KV store.
  // ...
}
```

## KVManager

Provides an instance to obtain information about a distributed KV store. Before calling any API in **KVManager**, you must use [createKVManager](#distributedkvstorecreatekvmanager) to create a **KVManager** instance.

### getKVStore

getKVStore&lt;T&gt;(storeId: string, options: Options, callback: AsyncCallback&lt;T&gt;): void

Creates and obtains a distributed KV store based on the specified **options** and **storeId**. This API uses an asynchronous callback to return the result. After using the obtained database, call [closeKVStore](#closekvstore) to close the database and release resources.

> **NOTE**
>
> If the database file cannot be opened (for example, the file header is damaged) when an existing distributed KV store is obtained, the automatic rebuild logic will be triggered to return a newly created distributed KV store instance. For important data that cannot be regenerated, you are advised to use the backup and restore feature to prevent data loss. For details, see [Database Backup and Restoration](../../database/data-backup-and-restore.md).

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type              | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| storeId  | string                 | Yes  | Unique identifier of the KV store. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| options  | [Options](#options)    | Yes  | Configuration of the KV store to create.                              |
| callback | AsyncCallback&lt;T&gt; | Yes  | Callback used to return the **SingleKVStore** or **DeviceKVStore** instance created.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100002     | Open existed database with changed options. |
| 15100003     | Database corrupted.                         |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
try {
  const options: distributedKVStore.Options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
    securityLevel: distributedKVStore.SecurityLevel.S3
  };
  kvManager.getKVStore('storeId', options, (err: BusinessError, store: distributedKVStore.SingleKVStore) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    if (kvStore !== null) {
       // Perform subsequent data operations, such as adding, deleting, modifying, and querying data, and subscribing to data changes.
       // ...
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getKVStore

getKVStore&lt;T&gt;(storeId: string, options: Options): Promise&lt;T&gt;

Creates and obtains a distributed KV store based on the specified **options** and **storeId**. This API uses a promise to return the result. After using the obtained database, call [closeKVStore](#closekvstore) to close the database and release resources.

> **NOTE**
>
> If the database file cannot be opened (for example, the file header is damaged) when an existing distributed KV store is obtained, the automatic rebuild logic will be triggered to return a newly created distributed KV store instance. For important data that cannot be regenerated, you are advised to use the backup and restore feature to prevent data loss. For details, see [Database Backup and Restoration](../../database/data-backup-and-restore.md).

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type           | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| storeId | string              | Yes  | Unique identifier of the KV store. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| options | [Options](#options) | Yes  | Configuration of the KV store to create.                              |

**Return value**

| Type            | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| Promise&lt;T&gt; | Promise used to return the **SingleKVStore** or **DeviceKVStore** instance created.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.|
| 15100002     | Open existed database with changed options. |
| 15100003     | Database corrupted.                         |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
try {
  const options: distributedKVStore.Options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
    securityLevel: distributedKVStore.SecurityLevel.S3,
    // From API version 24, you can use rootDir to specify the database storage path.
    rootDir: "/data/storage/el2/database/entry"
  };
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then((store: distributedKVStore.SingleKVStore) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### closeKVStore

closeKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void

Closes a distributed KV store. This API uses an asynchronous callback to return the result. This method is used together with the **getKVStore()** method. After the database is used, you can call this method to close it.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| appId    | string                    | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.                                     |
| storeId  | string                    | Yes  | Unique identifier of the KV store to close. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3
}
try {
  kvManager.getKVStore('storeId', options, async (err: BusinessError, store: distributedKVStore.SingleKVStore | null) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId is the one in createKVManager.
      kvManager.closeKVStore(appId, 'storeId', (err: BusinessError)=> {
        if (err) {
          console.error(`Failed to close KVStore. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing KVStore');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### closeKVStore

closeKVStore(appId: string, storeId: string, kvConfig?: Options): Promise&lt;void&gt;

Closes a distributed KV store. If the **kvConfig** parameter is used, the distributed KV store in the specified path is closed. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory| Description                                                        |
| ------- | -------- | ---- | ------------------------------------------------------------ |
| appId   | string   | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.                          |
| storeId | string   | Yes  | Unique identifier of the KV store to close. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| kvConfig<sup>24+</sup> | [Options](#options)  | No  | Configuration information of the KV store to close. Defaults to null.|

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3,
  // From API version 24, you can use rootDir to specify the database storage path.
  rootDir: "/data/storage/el2/database/entry"
}
try {
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then(async (store: distributedKVStore.SingleKVStore | null) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId refers to the appId in createKVManager. If rootDir is not configured in options, the closeKVStore does not require the options parameter.
      kvManager.closeKVStore(appId, 'storeId', options).then(() => {
        console.info('Succeeded in closing KVStore');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close KVStore. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to close KVStore. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteKVStore

deleteKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a distributed KV store. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| appId    | string                    | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.                                     |
| storeId  | string                    | Yes  | Unique identifier of the KV store to delete. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|
| 15100004     | Not found.   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3
}
try {
  kvManager.getKVStore('storeId', options, async (err: BusinessError, store: distributedKVStore.SingleKVStore | null) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId is the one in createKVManager.
      kvManager.deleteKVStore(appId, 'storeId', (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete KVStore. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in deleting KVStore`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to delete KVStore. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteKVStore

deleteKVStore(appId: string, storeId: string, kvConfig?: Options): Promise&lt;void&gt;

Deletes a distributed KV store. If the **kvConfig** parameter is used, the distributed KV store in the specified path is deleted. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory| Description                                                        |
| ------- | -------- | ---- | ------------------------------------------------------------ |
| appId   | string   | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.                          |
| storeId | string   | Yes  | Unique identifier of the KV store to delete. The KV store ID allows only letters, digits, and underscores (_), and its length ranges from 1 to [MAX_STORE_ID_LENGTH](#constants) in length.|
| kvConfig<sup>24+</sup> | [Options](#options)  | No  | Configuration information of the KV store to delete. Defaults to null.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|
| 15100004     | Not found.   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3,
  // From API version 24, you can use rootDir to specify the database storage path.
  rootDir: "/data/storage/el2/database/entry"
}
try {
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then(async (store: distributedKVStore.SingleKVStore | null) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId refers to the appId in createKVManager. If rootDir is not configured in options, the deleteKVStore does not require the options parameter.
      kvManager.deleteKVStore(appId, 'storeId', options).then(() => {
        console.info('Succeeded in deleting KVStore');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete KVStore. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to delete KVStore. Code: ${error.code}, message: ${error.message}`);
}
```

### getAllKVStoreId

getAllKVStoreId(appId: string, callback: AsyncCallback&lt;string[]&gt;): void

Obtains the IDs of all distributed KV stores that are created by [getKVStore](#getkvstore) and have not been deleted by [deleteKVStore](#deletekvstore). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                               |
| -------- | ----------------------------- | ---- | --------------------------------------------------- |
| appId    | string                        | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.                             |
| callback | AsyncCallback&lt;string[]&gt; | Yes  | Callback used to return the IDs of all the distributed KV stores created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // appId is the one in createKVManager.
  kvManager.getAllKVStoreId(appId, (err: BusinessError, data: string[]) => {
    if (err) {
      console.error(`Failed to get AllKVStoreId. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting AllKVStoreId');
    console.info(`GetAllKVStoreId size = ${data.length}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get AllKVStoreId. Code: ${error.code}, message: ${error.message}`);
}
```

### getAllKVStoreId

getAllKVStoreId(appId: string): Promise&lt;string[]&gt;

Obtains the IDs of all distributed KV stores that are created by [getKVStore](#getkvstore) and have not been deleted by [deleteKVStore](#deletekvstore). This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                  |
| ------ | -------- | ---- | ---------------------- |
| appId  | string   | Yes  | Bundle name of the application. The value cannot be empty and contains 1 to 256 bytes.|

**Return value**

| Type                   | Description                                                  |
| ----------------------- | ------------------------------------------------------ |
| Promise&lt;string[]&gt; | Promise used to return the IDs of all the distributed KV stores created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // appId is the one in createKVManager.
  console.info('GetAllKVStoreId');
  kvManager.getAllKVStoreId(appId).then((data: string[]) => {
    console.info('Succeeded in getting AllKVStoreId');
    console.info(`GetAllKVStoreId size = ${data.length}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get AllKVStoreId. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get AllKVStoreId. Code: ${error.code}, message: ${error.message}`);
}
```

### on('distributedDataServiceDie')

on(event: 'distributedDataServiceDie', deathCallback: Callback&lt;void&gt;): void

Subscribes to the service termination event. If the service is terminated, you need to call [on('dataChange')](#ondatachange) and [on('syncComplete')](#onsynccomplete) again to register the callbacks for data change notifications and cross-device sync completion notifications. In addition, an error will be returned for a sync operation. After calling **on** to subscribe to the event, you must call [off('distributedDataServiceDie')](#offdistributeddataservicedie) to cancel the subscription when it is no longer needed.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name       | Type            | Mandatory| Description                                                        |
| ------------- | -------------------- | ---- | ------------------------------------------------------------ |
| event         | string               | Yes  | Name of the event to subscribe to. The value is fixed to **distributedDataServiceDie**, indicating the service termination event.|
| deathCallback | Callback&lt;void&gt; | Yes  | Callback used to return the result. If the subscription is successful, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info('KVManagerOn');
  const deathCallback = () => {
    console.info('death callback call');
  }
  kvManager.on('distributedDataServiceDie', deathCallback);
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### off('distributedDataServiceDie')

off(event: 'distributedDataServiceDie', deathCallback?: Callback&lt;void&gt;): void

Unsubscribes from the termination (death) of the distributed data service. You must call [on('distributedDataServiceDie')](#ondistributeddataservicedie) to subscribe to the termination of the distributed data service before calling **off** to cancel the subscription. The **deathCallback** parameter must be a callback registered for subscribing to the termination of the distributed data service. Otherwise, the unsubscription will fail.

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name       | Type            | Mandatory| Description                                                        |
| ------------- | -------------------- | ---- | ------------------------------------------------------------ |
| event         | string               | Yes  | Event type. The value is **distributedDataServiceDie**, which indicates the termination of the distributed data service.|
| deathCallback | Callback&lt;void&gt; | No  | Callback function. If this parameter is not specified, this API unregisters all callbacks for the **distributedDataServiceDie** event.                                         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info('KVManagerOff');
  const deathCallback = () => {
    console.info('death callback call');
  }
  kvManager.off('distributedDataServiceDie', deathCallback);
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## KVStoreResultSet

Provides APIs for obtaining the distributed KV store result sets. A maximum of eight result sets can be opened at a time.

The **KVStoreResultSet** instance is not refreshed in real time. After using the result set, if the data in the database is changed (by being added, deleted, or modified), you need to query the result set again to obtain the latest data.

Before calling any API in **KVStoreResultSet**, you must use **[getKVStore](#getkvstore)** to construct a **SingleKVStore** or **DeviceKVStore** instance.

> **NOTE**
>
> The cursor start position of **KVStoreResultSet** is **-1**.

### getCount

getCount(): number

Obtains the total number of rows in the result set.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Total number of rows obtained.|

**Example**

```ts
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

### getPosition

getPosition(): number

Obtains the current data read position (position from which data is read) in the result set. The read position changes with the operations, such as [moveToFirst](#movetofirst) and [moveToLast](#movetolast).

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Current data read position obtained. The value must be greater than or equal to **-1**. The value **-1** means no data is read; the value **0** indicates the first row.|

**Example**

```ts
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

### moveToFirst

moveToFirst(): boolean

Moves the data read position to the first row. If the result set is empty, **false** will be returned.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
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

### moveToLast

moveToLast(): boolean

Moves the data read position to the last row. If the result set is empty, **false** will be returned.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
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

### moveToNext

moveToNext(): boolean

Moves the data read position to the next row. If the result set is empty, **false** will be returned. This API applies when the whole result set is obtained.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
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

### moveToPrevious

moveToPrevious(): boolean

Moves the data read position to the previous row. If the result set is empty, **false** will be returned. This API applies when the whole result set is obtained.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
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

### move

move(offset: number): boolean

Moves the data read position with the specified offset from the current position. That is, moves the number of rows specified by **offset** from the current position.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| offset | number   | Yes  | Offset to move the data read position. A positive value means to move towards the end of the result set (the row number increases); a negative value means to move towards the start of the result set (the row number decreases). If the cursor is beyond the start or end position of the result set, **false** is returned.|

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let moved: boolean;
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    moved = resultSet.move(2); // If the current position is 0, move the read position forward by two rows, that is, move to row 3.
    console.info(`Succeeded in moving.moved = ${moved}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to move. Code: ${error.code}, message: ${error.message}`);
}
```

### moveToPosition

moveToPosition(position: number): boolean

Moves the data read position from 0 to an absolute position.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type| Mandatory| Description          |
| -------- | -------- | ---- | -------------- |
| position | number   | Yes  | Absolute position to move to. If the absolute position exceeds the start or end position of the result set, **false** is returned.|

**Return value**

| Type   | Description                                           |
| ------- | ----------------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |

**Example**

```ts
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

### isFirst

isFirst(): boolean

Checks whether the data read position is the first row.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the first row is being read; returns **false** otherwise.|

**Example**

```ts
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

### isLast

isLast(): boolean

Checks whether the data read position is the last row.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the last row is being read; returns **false** otherwise.|

**Example**

```ts
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

### isBeforeFirst

isBeforeFirst(): boolean

Checks whether the data read position is before the first row.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the data read position is before the first row; returns **false** otherwise.|

**Example**

```ts
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

### isAfterLast

isAfterLast(): boolean

Checks whether the data read position is after the last row.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the data read position is after the last row; returns **false** otherwise.|

**Example**

```ts
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

### getEntry

getEntry(): Entry

Obtains the KV pair from the current position.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type           | Description        |
| --------------- | ------------ |
| [Entry](#entry) | KV pair obtained.|

**Example**

```ts
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

## Query

Provides methods to create a **Query** object, which defines different data query criteria. The predicate methods of a **Query** object return the object itself, allowing for chain calls. A **Query** object supports a maximum of 256 predicates.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

### constructor

constructor()

Defines a constructor used to create a **Query** instance.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

### reset

reset(): Query

Resets the **Query** object.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description                 |
| -------------- | --------------------- |
| [Query](#query) | **Query** object, which is reset and all added predicate conditions are cleared. It can be used to reconstruct query conditions.|

**Example**

```ts
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

### equalTo

equalTo(field: string, value: number | string | boolean): Query

Creates a **Query** object to match the specified field whose value is equal to the given value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| value  | number \| string \| boolean  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.equalTo('field', 'value');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### notEqualTo

notEqualTo(field: string, value: number | string | boolean): Query

Creates a **Query** object to match the specified field whose value is not equal to the specified value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value  | number \| string \| boolean  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.notEqualTo('field', 'value');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### greaterThan

greaterThan(field: string, value: number | string | boolean): Query

Creates a **Query** object to match the specified field whose value is greater than the specified value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**
| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value  | number \| string \| boolean  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.greaterThan('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### lessThan

lessThan(field: string, value: number | string): Query

Creates a **Query** object to match the specified field whose value is less than the specified value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**


| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value  | number \| string  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.lessThan('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### greaterThanOrEqualTo

greaterThanOrEqualTo(field: string, value: number | string): Query

Creates a **Query** object to match the specified field whose value is greater than or equal to the specified value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**


| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value  | number \| string  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.greaterThanOrEqualTo('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### lessThanOrEqualTo

lessThanOrEqualTo(field: string, value: number | string): Query

Creates a **Query** object to match the specified field whose value is less than or equal to the specified value.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**


| Name | Type| Mandatory | Description                   |
| -----  | ------  | ----  | ----------------------- |
| field  | string  | Yes   |Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value  | number \| string  | Yes   | Value for the field to match. The value type must be the same as the field type defined in **Schema**.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.lessThanOrEqualTo('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### isNull

isNull(field: string): Query

Creates a **Query** object to match the specified field whose value is **null**.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### inNumber

inNumber(field: string, valueList: number[]): Query

Creates a **Query** object to match the specified field whose value is within the specified list of numbers.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name   | Type| Mandatory| Description                         |
| --------- | -------- | ---- | ----------------------------- |
| field     | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| valueList | number[] | Yes  | List of numbers.           |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.inNumber('field', [0, 1]);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### inString

inString(field: string, valueList: string[]): Query

Creates a **Query** object to match the specified field whose value is within the specified list of strings.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name   | Type| Mandatory| Description                         |
| --------- | -------- | ---- | ----------------------------- |
| field     | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| valueList | string[] | Yes  | List of strings.     |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### notInNumber

notInNumber(field: string, valueList: number[]): Query

Creates a **Query** object to match the specified field whose value is not within the specified list of numbers.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name   | Type| Mandatory| Description                         |
| --------- | -------- | ---- | ----------------------------- |
| field     | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| valueList | number[] | Yes  | List of numbers.           |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notInNumber('field', [0, 1]);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### notInString

notInString(field: string, valueList: string[]): Query

Creates a **Query** object to match the specified field whose value is not within the specified list of strings.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name   | Type| Mandatory| Description                         |
| --------- | -------- | ---- | ----------------------------- |
| field     | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| valueList | string[] | Yes  | List of strings.     |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### like

like(field: string, value: string): Query

Creates a **Query** object to match the specified field whose value is similar to the specified string.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| value  | string   | Yes  | Value for the field to match, which is a string.         |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### unlike

unlike(field: string, value: string): Query

Creates a **Query** object to match the specified field whose value is not similar to the specified string.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|
| value  | string   | Yes  | Value for the field not to match, which is a string.      |

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### and

and(): Query

Creates a **Query** object with the AND condition. You need to add query conditions using predicate methods such as **equalTo** and **notEqualTo** before calling **and()** to combine multiple conditions. If there is no predicate method, calling **and()** will be invalid.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description          |
| -------------- | -------------- |
| [Query](#query) | **Query** object created.|

**Example**

```ts
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

### or

or(): Query

Creates a **Query** object with the OR condition. You need to add query conditions using predicate methods such as **equalTo** and **notEqualTo** before calling **or()** to combine multiple conditions. If there is no predicate method, calling **or()** will be invalid.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description          |
| -------------- | -------------- |
| [Query](#query) | **Query** object created.|

**Example**

```ts
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

### orderByAsc

orderByAsc(field: string): Query

Creates a **Query** object to sort the query results in ascending order.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### orderByDesc

orderByDesc(field: string): Query

Creates a **Query** object to sort the query results in descending order.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### limit

limit(total: number, offset: number): Query

Creates a **Query** object to specify the number of records of the query result and where to start. This API must be called after the invocation of the **orderByAsc()**, **orderByDesc()**, and the query APIs of the **Query** object.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description              |
| ------ | -------- | ---- |------------------|
| total  | number   | Yes  | Maximum number of data records.<br>If the value is a non-negative integer, it indicates the maximum number of records.<br>If the value is a negative number, the entire result set is queried.|
| offset | number   | Yes  | Start position of the query result. If the value is a non-negative integer, it indicates the specified start position. If the value is a negative number, the entire result set is queried. If **offset** exceeds the end of the result set, the query result is empty.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
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

### isNotNull

isNotNull(field: string): Query

Creates a **Query** object to match the specified field whose value is not **null**.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

> **NOTE**
>
> This API should be used together with [Schema](#schema).
>
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV store using the **getKVStore()** method in [Persisting KV Store Data](../../database/data-persistence-by-kv-store.md#how-to-develop).

**Parameters**

| Name| Type| Mandatory| Description                         |
| ------ | -------- | ---- | ----------------------------- |
| field  | string   | Yes  | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Example**

```ts
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

### beginGroup

beginGroup(): Query

Creates a **Query** object for a query condition group with a left parenthesis. It must be used in conjunction with [endGroup()](#endgroup) to form a complete query condition group.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Example**

```ts
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

### endGroup

endGroup(): Query

Creates a **Query** object for a query condition group with a right parenthesis. It must be used in conjunction with [beginGroup()](#begingroup) to form a complete query condition group.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Example**

```ts
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

### prefixKey

prefixKey(prefix: string): Query

Creates a **Query** object with a specified key prefix.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description              |
| ------ | -------- | ---- | ------------------ |
| prefix | string   | Yes  | Key prefix, which cannot contain '^'. The length range is 0-[MAX_KEY_LENGTH](#constants). If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Example**

```ts
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

### setSuggestIndex

setSuggestIndex(index: string): Query

Creates a **Query** object with an index preferentially used for query.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description              |
| ------ | -------- | ---- | ------------------ |
| index  | string   | Yes  | Index to set, which cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
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

### deviceId

deviceId(deviceId:string):Query

Creates a **Query** object with the device ID as the key prefix.
> **NOTE**
>
> **deviceId** is **networkId** in [DeviceBasicInfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo), which can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type| Mandatory| Description              |
| -------- | -------- | ---- | ------------------ |
| deviceId | string   | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|

**Return value**

| Type          | Description           |
| -------------- | --------------- |
| [Query](#query) | **Query** object created.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |

**Example**

```ts
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

### getSqlLike

getSqlLike():string

Obtains the query statement of the **Query** object.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type  | Description                                |
| ------ | ------------------------------------ |
| string | Query statement string constructed by the **Query** object, which can be used to view and debug the current query conditions.|

**Example**

```ts
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

## SingleKVStore

Provides APIs for data management in a single KV store, such as adding data, deleting data, and subscribing to data changes or across-device data sync completion events.

Before calling any method in **SingleKVStore**, you must use [getKVStore](#getkvstore) to obtain a **SingleKVStore** instance.

### put

put(key: string, value: Uint8Array | string | number | boolean, callback: AsyncCallback&lt;void&gt;): void

Adds a KV pair of the specified type to this KV store. This API uses an asynchronous callback to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory | Description                                                                                                    |
| -----  | ------  | ----  |--------------------------------------------------------------------------------------------------------|
| key    | string  | Yes   | Key of the data to add. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).                                                    |
| value  | Uint8Array \| string \| number \| boolean | Yes   | Value of the data to add. The value type can be Uint8Array, string, number, or boolean. The length range of the Uint8Array and string is 0-[MAX_VALUE_LENGTH](#constants).|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.                                                                    |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### put

put(key: string, value: Uint8Array | string | number | boolean): Promise&lt;void&gt;

Adds a KV pair of the specified type to this KV store. This API uses a promise to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory | Description                                                                                                    |
| -----  | ------  | ----  |--------------------------------------------------------------------------------------------------------|
| key    | string  | Yes   | Key of the data to add. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).                                                    |
| value  | Uint8Array \| string \| number \| boolean | Yes   | Value of the data to add. The value type can be Uint8Array, string, number, or boolean. The length range of the Uint8Array and string is 0-[MAX_VALUE_LENGTH](#constants).|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### putBatch

putBatch(entries: Entry[], callback: AsyncCallback&lt;void&gt;): void

Batch inserts KV pairs to this single KV store. This API uses an asynchronous callback to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                | Mandatory| Description                    |
| -------- | ------------------------ | ---- | ------------------------ |
| entries  | [Entry](#entry)[]        | Yes  | KV pairs to insert, which An **entries** object supports up to 512 MB of data.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.  |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    } else {
      console.error('KvStore is null'); // The subsequent sample code is the same as the code here.
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### putBatch

putBatch(entries: Entry[]): Promise&lt;void&gt;

Batch inserts KV pairs to this single KV store. This API uses a promise to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type         | Mandatory| Description                    |
| ------- | ----------------- | ---- | ------------------------ |
| entries | [Entry](#entry)[] | Yes  | KV pairs to insert, which An **entries** object supports up to 512 MB of data.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### delete

delete(key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a KV pair from this KV store. This API uses an asynchronous callback to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| key      | string                    | Yes  | Key of the data to delete. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.        |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100005    | Database or result set already closed. |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.delete(KEY_TEST_STRING_ELEMENT, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in deleting');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### delete

delete(key: string): Promise&lt;void&gt;

Deletes a KV pair from this KV store. This API uses a promise to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| key    | string   | Yes  | Key of the data to delete. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.delete(KEY_TEST_STRING_ELEMENT).then(() => {
        console.info('Succeeded in deleting');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteBatch

deleteBatch(keys: string[], callback: AsyncCallback&lt;void&gt;): void

Batch deletes KV pairs from this single KV store. This API uses an asynchronous callback to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                    |
| -------- | ------------------------- | ---- | ------------------------ |
| keys     | string[]                  | Yes  | List of keys to delete in batches. The value cannot be empty. The length of each element in the array ranges from 1 to [MAX_KEY_LENGTH](#constants).|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                          |
| ------------ |----------------------------------------------------|
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  let keys: string[] = [];
  for (let i = 0; i < 5; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
    keys.push(key + i);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.deleteBatch(keys, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete Batch. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in deleting Batch');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteBatch

deleteBatch(keys: string[]): Promise&lt;void&gt;

Batch deletes KV pairs from this single KV store. This API uses a promise to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                    |
| ------ | -------- | ---- | ------------------------ |
| keys   | string[] | Yes  | List of keys to delete in batches. The value cannot be empty. The length of each element in the array ranges from 1 to [MAX_KEY_LENGTH](#constants).|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                             |
| ------------ |-------------------------------------------------------|
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  let keys: string[] = [];
  for (let i = 0; i < 5; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
    keys.push(key + i);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.deleteBatch(keys).then(() => {
        console.info('Succeeded in deleting Batch');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete Batch. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### removeDeviceData

removeDeviceData(deviceId: string, callback: AsyncCallback&lt;void&gt;): void

Deletes data of a device. This API uses an asynchronous callback to return the result. After the data is deleted, all data of the device will be permanently removed from the local database and cannot be queried using methods such as **get**.
> **NOTE**
>
> **deviceId** is **networkId** in [DeviceBasicInfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo), which can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type                 | Mandatory| Description                  |
| -------- | ------------------------- | ---- | ---------------------- |
| deviceId | string                    | Yes  | Network ID of the device whose data is to be deleted. This parameter cannot be left empty.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put device data. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting data');
    const deviceId = 'no_exist_device_id';
    if (kvStore) {
      kvStore.removeDeviceData(deviceId, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to remove device data. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in removing device data');
          if (kvStore) {
            kvStore.get(KEY_TEST_STRING_ELEMENT, async (err: BusinessError, data: boolean | string | number | Uint8Array) => {
                if (err) {
                  console.error(`Failed to get data. Code: ${err.code}, message: ${err.message}`);
                  return;
                }
                console.info(`Succeeded in getting data.data=${data}`);
              });
          }
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### removeDeviceData

removeDeviceData(deviceId: string): Promise&lt;void&gt;

Deletes data of a device. This API uses a promise to return the result. After the data is deleted, all data of the device will be permanently removed from the local database and cannot be queried using methods such as **get**.
> **NOTE**
>
> **deviceId** is **networkId** in [DeviceBasicInfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo), which can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type| Mandatory| Description                  |
| -------- | -------- | ---- | ---------------------- |
| deviceId | string   | Yes  | Network ID of the device whose data is to be deleted. This parameter cannot be left empty.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
  kvStore!.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info('Succeeded in putting data');
    const deviceId = 'no_exist_device_id';
    kvStore!.removeDeviceData(deviceId).then(() => {
      console.info('succeeded in removing device data');
      kvStore!.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data. Data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get data. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to remove device data. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### get

get(key: string, callback: AsyncCallback&lt;boolean | string | number | Uint8Array&gt;): void

Obtains the value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory | Description                                             |
| -----  | ------  | ----  |-------------------------------------------------|
| key    |string   | Yes   | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|
| callback  |AsyncCallback&lt;boolean \| string \| number \| Uint8Array&gt; | Yes   | Callback used to return the obtained value. The value type depends on the data type when the value is stored. |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT, (err: BusinessError, data: boolean | string | number | Uint8Array) => {
        if (err) {
          console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in getting data.data=${data}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### get

get(key: string): Promise&lt;boolean | string | number | Uint8Array&gt;

Obtains the value of the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| key    | string   | Yes  | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|

**Return value**

| Type   | Description      |
| ------  | -------   |
|Promise&lt;boolean \| string \| number \| Uint8Array&gt; |Promise used to return the value corresponding to the specified key. The value type depends on the data type when the value is stored.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data.data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(keyPrefix: string, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains all KV pairs that match the specified key prefix. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                              | Mandatory| Description                                                                                 |
| --------- | -------------------------------------- | ---- |-------------------------------------------------------------------------------------|
| keyPrefix | string                                 | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs that match the specified prefix.                                                               |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(keyPrefix: string): Promise&lt;Entry[]&gt;

Obtains all KV pairs that match the specified key prefix. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type| Mandatory| Description                                                                                 |
| --------- | -------- | ---- |-------------------------------------------------------------------------------------|
| keyPrefix | string   | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                            | Description                                       |
| -------------------------------- | ------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return the KV pairs that match the specified prefix.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';


try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(query: Query, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains the KV pairs that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                              | Mandatory| Description                        |
| -------- | -------------------------------------- | ---- |----------------------------|
| query    | [Query](#query)                         | Yes  | Object to match.                 |
| callback | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs that match the specified **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(query: Query): Promise&lt;Entry[]&gt;

Obtains the KV pairs that match the specified **Query** object. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type      | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                            | Description                                              |
| -------------------------------- | -------------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return the KV pairs that match the specified **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting Entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(keyPrefix: string, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a result set with the specified prefix from this single KV store. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                                                  | Mandatory| Description                                                                                 |
| --------- | ---------------------------------------------------------- | ---- |-------------------------------------------------------------------------------------|
| keyPrefix | string                                 | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the result set with the specified prefix.                                                                 |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100001     | Over max limits.<br>Applicable versions: 10+                     |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err :BusinessError) => {
            if (err) {
              console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing result set');
          });
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(keyPrefix: string): Promise&lt;KVStoreResultSet&gt;

Obtains a result set with the specified prefix from this single KV store. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type| Mandatory| Description                                                                                 |
| --------- | -------- | ---- |-------------------------------------------------------------------------------------|
| keyPrefix | string   | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                                                | Description                                   |
| ---------------------------------------------------- | --------------------------------------- |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the result set with the specified prefix.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                     |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore!.putBatch(entries).then(() => {
    console.info('Succeeded in putting batch');
    kvStore!.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting result set');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing result set');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(query: Query, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a **KVStoreResultSet** object that matches the specified **Query** object. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                                  | Mandatory| Description                                                     |
| -------- | ---------------------------------------------------------- | ---- | --------------------------------------------------------- |
| query    | [Query](#query)                                                      | Yes  | **Query** object to match.                                           |
| callback | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                     |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet(query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(query: Query): Promise&lt;KVStoreResultSet&gt;

Obtains a **KVStoreResultSet** object that matches the specified **Query** object. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type      | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                     |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
    kvStore!.putBatch(entries).then(() => {
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    kvStore!.getResultSet(query).then((result: distributedKVStore.KVStoreResultSet) => {
      console.info(`Succeeded in getting result set size=${result.getCount()}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### closeResultSet

closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback&lt;void&gt;): void

Closes the **KVStoreResultSet** object returned by [SingleKVStore.getResultSet](#getresultset-1). This API uses an asynchronous callback to return the result. After the result set is closed, the result set object cannot be used anymore, and related database resources are released.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                             | Mandatory| Description                              |
| --------- | ------------------------------------- | ---- | ---------------------------------- |
| resultSet | [KVStoreResultSet](#kvstoreresultset) | Yes  | **KVStoreResultSet** object to close.|
| callback  | AsyncCallback&lt;void&gt;             | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let resultSet: distributedKVStore.KVStoreResultSet;
try {
  kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing result set');
      })
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

### closeResultSet

closeResultSet(resultSet: KVStoreResultSet): Promise&lt;void&gt;

Closes the **KVStoreResultSet** object returned by [SingleKVStore.getResultSet](#getresultset-1). This API uses a promise to return the result. After the result set is closed, the result set object cannot be used anymore, and related database resources are released.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                             | Mandatory| Description                              |
| --------- | ------------------------------------- | ---- | ---------------------------------- |
| resultSet | [KVStoreResultSet](#kvstoreresultset) | Yes  | **KVStoreResultSet** object to close.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let resultSet: distributedKVStore.KVStoreResultSet;
try {
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing result set');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });

} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(query: Query, callback: AsyncCallback&lt;number&gt;): void

Obtains the number of results that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                       |
| -------- | --------------------------- | ---- | ------------------------------------------- |
| query    | [Query](#query)              | Yes  | **Query** object to match.                             |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize(query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set size');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(query: Query): Promise&lt;number&gt;

Obtains the number of results that match the specified **Query** object. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type      | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                 | Description                                           |
| --------------------- | ----------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize(query).then((resultSize: number) => {
    console.info('Succeeded in getting result set size');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### backup

backup(file:string, callback: AsyncCallback&lt;void&gt;):void

Backs up a database with a specified name to the default path (**context.databaseDir**). This API uses an asynchronous callback to return the result. To back up the database to a custom path, use the [backupEx](#backupex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| file     | string                    | Yes  | Name of the database to back up. The value cannot be empty and cannot contain slashes (/). There is no length limit.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to backup. Code: ${err.code}, message: ${err.message} `);
    } else {
      console.info(`Succeeded in backupping data`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### backup

backup(file:string): Promise&lt;void&gt;

Backs up a database with a specified name to the default path (**context.databaseDir**). This API uses a promise to return the result. To back up the database to a custom path, use the [backupEx](#backupex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| file   | string   | Yes  | Name of the database to back up. The value cannot be empty and cannot contain slashes (/). There is no length limit.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile).then(() => {
    console.info(`Succeeded in backupping data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to backup. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### backupEx<sup>24+</sup>

backupEx(backupConfig:BackupConfig): Promise&lt;void&gt;

Backs up a database with a specified name and path. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| backupConfig   | [BackupConfig](#backupconfig24)  | Yes  | Information about the database to back up, including the name and path.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100000     | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.backupEx(backupConfig).then(() => {
    console.info(`Succeeded in backupping data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to backup. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```
### restore

restore(file:string, callback: AsyncCallback&lt;void&gt;):void

Restores a database from a specified backup file in the default database path (**context.databaseDir**). This API uses an asynchronous callback to return the result. If the restoration is successful, the data in the current database will be replaced by the data in the backup file, and the original data that is not backed up will be lost. To restore the database from a custom path, use the [restoreEx](#restoreex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| file     | string                    | Yes  | Name of the database file. The value cannot be empty and cannot contain slashes (/). There is no length limit.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.restore(backupFile, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in restoring data`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### restore

restore(file:string): Promise&lt;void&gt;

Restores a database from a specified backup file in the default database path (**context.databaseDir**). This API uses a promise to return the result. If the restoration is successful, the data in the current database will be replaced by the data in the backup file, and the original data that is not backed up will be lost. To restore the database from a custom path, use the [restoreEx](#restoreex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| file   | string   | Yes  | Name of the database file. The value cannot be empty and cannot contain slashes (/). There is no length limit.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.restore(backupFile).then(() => {
    console.info(`Succeeded in restoring data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### restoreEx<sup>24+</sup>

restoreEx(backupConfig:BackupConfig): Promise&lt;void&gt;

Restores a database from a backup file with the specified path and name. This API uses a promise to return the result. If the restoration is successful, the data in the current database will be replaced by that in the backup file, and the original data that is not backed up will be lost.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type| Mandatory| Description                                                        |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| backupConfig   | [BackupConfig](#backupconfig24)  | Yes  | Information about the database to back up, including the name and path.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100000     | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.restoreEx(backupConfig).then(() => {
    console.info(`Succeeded in restoring data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteBackup

deleteBackup(files:Array&lt;string&gt;, callback: AsyncCallback&lt;Array&lt;[string, number]&gt;&gt;):void

Deletes a backup file from the default path (**context.databaseDir**) based on the specified name. This API uses an asynchronous callback to return the result. After a backup file is deleted, the data in the backup file cannot be restored using the [restore](#restore-1) API. To delete a backup file from a custom path, use the [deleteBackupEx](#deletebackupex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                          | Mandatory| Description                                                        |
| -------- | -------------------------------------------------- | ---- | ------------------------------------------------------------ |
| files    | Array&lt;string&gt;                                | Yes  | Name of the backup file to delete. The value cannot be empty and cannot contain slashes (/). There is no length limit.|
| callback | AsyncCallback&lt;Array&lt;[string, number]&gt;&gt; | Yes  | Callback used to return the name of the backup file deleted and the operation result.                |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let files = ['BK001', 'BK002'];
try {
  kvStore.deleteBackup(files, (err: BusinessError, data: [string, number][]) => {
    if (err) {
      console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeed in deleting Backup.data=${data}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteBackup

deleteBackup(files:Array&lt;string&gt;): Promise&lt;Array&lt;[string, number]&gt;&gt;

Deletes a backup file from the default path (**context.databaseDir**) based on the specified name. This API uses a promise to return the result. After a backup file is deleted, the data in the backup file cannot be restored using the [restore](#restore) API. To delete a backup file from a custom path, use the [deleteBackupEx](#deletebackupex24) API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type           | Mandatory| Description                                                        |
| ------ | ------------------- | ---- | ------------------------------------------------------------ |
| files  | Array&lt;string&gt; | Yes  | Name of the backup file to delete. The value cannot be empty and cannot contain slashes (/). There is no length limit.|

**Return value**

| Type                                        | Description                                           |
| -------------------------------------------- | ----------------------------------------------- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise used to return the name of the backup file deleted and the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Parameter verification failed.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let files = ['BK001', 'BK002'];
try {
  kvStore.deleteBackup(files).then((data: [string, number][]) => {
    console.info(`Succeed in deleting Backup.data=${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### deleteBackupEx<sup>24+</sup>

deleteBackupEx(backupConfig:BackupConfig): Promise&lt;void&gt;

Deletes a backup file based on the specified name and path. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type           | Mandatory| Description                                                        |
| ------ | ------------------- | ---- | ------------------------------------------------------------ |
| backupConfig   | [BackupConfig](#backupconfig24)  | Yes  | Information about the database to back up, including the name and path.|

**Return value**

| Type                                        | Description                                           |
| -------------------------------------------- | ----------------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100000     | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.deleteBackupEx(backupConfig).then(() => {
    console.info(`Succeed in deleting Backup.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### startTransaction

startTransaction(callback: AsyncCallback&lt;void&gt;): void

Starts the transaction in this single KV store. This API uses an asynchronous callback to return the result. After a transaction is started, subsequent database operations are included in this transaction until [commit](#commit) or [rollback](#rollback) is called.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function putBatchString(len: number, prefix: string) {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < len; i++) {
    let entry: distributedKVStore.Entry = {
      key: prefix + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  return entries;
} // Custom function used outside the scope to prevent syntax check errors.

try {
  let count = 0;
  kvStore.on('dataChange', 0, (data: distributedKVStore.ChangeNotification) => {
    console.info(`startTransaction 0 ${data}`);
    count++;
  });
  kvStore.startTransaction(async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to start Transaction. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in starting Transaction');
    let entries = putBatchString(10, 'batch_test_string_key');
    console.info(`entries: ${entries}`);
    if (kvStore != null) {
      kvStore.putBatch(entries, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in putting Batch');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to start Transaction. Code: ${error.code}, message: ${error.message}`);
}
```

### startTransaction

startTransaction(): Promise&lt;void&gt;

Starts the transaction in this single KV store. This API uses a promise to return the result. After a transaction is started, subsequent database operations are included in this transaction until [commit](#commit) or [rollback](#rollback) is called.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit.<br>Applicable versions: 10+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_ALL, (data: distributedKVStore.ChangeNotification) => {
    console.info(`startTransaction 0 ${data}`);
  });
  kvStore.startTransaction().then(async () => {
    console.info('Succeeded in starting Transaction');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start Transaction. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to start Transaction. Code: ${error.code}, message: ${error.message}`);
}
```

### commit

commit(callback: AsyncCallback&lt;void&gt;): void

Commits the transaction in this single KV store. This API uses an asynchronous callback to return the result. You need to call [startTransaction](#starttransaction) to start a transaction before calling this API to commit the transaction. After the transaction is successfully committed, all data changes during the transaction will take effect permanently and be written into the database.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.commit((err: BusinessError) => {
    if (err) {
      console.error(`Failed to commit. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in committing');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### commit

commit(): Promise&lt;void&gt;

Commits the transaction in this single KV store. This API uses a promise to return the result. You need to call [startTransaction](#starttransaction) to start a transaction before calling this API to commit the transaction. After the transaction is successfully committed, all data changes during the transaction will take effect permanently and be written into the database.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.commit().then(async () => {
    console.info('Succeeded in committing');
  }).catch((err: BusinessError) => {
    console.error(`Failed to commit. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### rollback

rollback(callback: AsyncCallback&lt;void&gt;): void

Rolls back the transaction in this single KV store. This API uses an asynchronous callback to return the result. You need to call [startTransaction](#starttransaction) to start a transaction before calling this API to roll back the transaction. After the transaction is successfully rolled back, all data changes during the transaction will be discarded and will not be written into the database.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rollback((err: BusinessError) => {
    if (err) {
      console.error(`Failed to rollback. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in rolling back');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### rollback

rollback(): Promise&lt;void&gt;

Rolls back the transaction in this single KV store. This API uses a promise to return the result. You need to call [startTransaction](#starttransaction) to start a transaction before calling this API to roll back the transaction. After the transaction is successfully rolled back, all data changes during the transaction will be discarded and will not be written into the database.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rollback().then(async () => {
    console.info('Succeeded in rolling back');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rollback. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### enableSync

enableSync(enabled: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets cross-device data sync, which can be enabled or disabled. This API uses an asynchronous callback to return the result. After cross-device data sync is enabled, data in the database can be automatically synced across devices. After it is disabled, data will not be automatically synced. You need to manually call the [sync](#sync) API to trigger data sync.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                 | Mandatory| Description                                                     |
| -------- | ------------------------- | ---- | --------------------------------------------------------- |
| enabled  | boolean                   | Yes  | Whether to enable data sync across devices. The value **true** means to enable data sync across devices, and the value **false** means the opposite.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                                                                                                      |
| ------------ |----------------------------------------------------------------------------------------------------------------|
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.enableSync(true, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to enable sync. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in enabling sync');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### enableSync

enableSync(enabled: boolean): Promise&lt;void&gt;

Sets cross-device data sync, which can be enabled or disabled. This API uses a promise to return the result. After cross-device data sync is enabled, data in the database can be automatically synced across devices. After it is disabled, data will not be automatically synced. You need to manually call the [sync](#sync) API to trigger data sync.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name | Type| Mandatory| Description                                                     |
| ------- | -------- | ---- | --------------------------------------------------------- |
| enabled | boolean  | Yes  | Whether to enable data sync across devices. The value **true** means to enable data sync across devices, and the value **false** means the opposite.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.enableSync(true).then(() => {
    console.info('Succeeded in enabling sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to enable sync. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### setSyncRange

setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback&lt;void&gt;): void

Sets the data sync range. This API uses an asynchronous callback to return the result. You can set the sync tags for the local and remote devices to determine which devices can perform data sync. Data can be synced only when the tags of the local device overlap with those of the remote device.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name             | Type                 | Mandatory| Description                            |
| ------------------- | ------------------------- | ---- | -------------------------------- |
| localLabels         | string[]                  | Yes  | Sync labels set for the local devices, which are used to identify the range of local devices that can be synced.        |
| remoteSupportLabels | string[]                  | Yes  | Sync labels set for the remote devices that expect to sync data, which are used to identify the range of remote devices that are allowed to sync data. Data can be synced between devices only when the **remoteSupportLabels** of the local device overlap with the **localLabels** of the remote device.|
| callback            | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localLabels = ['A', 'B'];
  const remoteSupportLabels = ['C', 'D'];
  kvStore.setSyncRange(localLabels, remoteSupportLabels, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set syncRange. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting syncRange');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### setSyncRange

setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise&lt;void&gt;

Sets the data sync range. This API uses a promise to return the result. You can set the sync tags for the local and remote devices to determine which devices can perform data sync. Data can be synced only when the tags of the local device overlap with those of the remote device.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name             | Type| Mandatory| Description                            |
| ------------------- | -------- | ---- | -------------------------------- |
| localLabels         | string[] | Yes  | Sync labels set for the local devices, which are used to identify the range of local devices that can be synced.        |
| remoteSupportLabels | string[] | Yes  | Sync labels set for the remote devices that expect to sync data, which are used to identify the range of remote devices that are allowed to sync data. Data can be synced between devices only when the **remoteSupportLabels** of the local device overlap with the **localLabels** of the remote device.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localLabels = ['A', 'B'];
  const remoteSupportLabels = ['C', 'D'];
  kvStore.setSyncRange(localLabels, remoteSupportLabels).then(() => {
    console.info('Succeeded in setting syncRange');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set syncRange. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### setSyncParam

setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback&lt;void&gt;): void

Sets the default delay for cross-device data sync. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> After the default delay is set, calling [sync](#sync) will not trigger the cross-device data sync immediately. Instead, the data sync will be executed only after the specified delay duration.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name               | Type                 | Mandatory| Description                                        |
| --------------------- | ------------------------- | ---- | -------------------------------------------- |
| defaultAllowedDelayMs | number                    | Yes  | Delay time to set, in ms. The value can be **0** or ranges from 100 to 86400000.|
| callback              | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAllowedDelayMs = 500;
  kvStore.setSyncParam(defaultAllowedDelayMs, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set syncParam. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting syncParam');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### setSyncParam

setSyncParam(defaultAllowedDelayMs: number): Promise&lt;void&gt;

Sets the default delay for cross-device data sync. This API uses a promise to return the result.

> **NOTE**
>
> After the default delay is set, calling [sync](#sync) will not trigger the cross-device data sync immediately. Instead, the data sync will be executed only after the specified delay duration.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name               | Type| Mandatory| Description                                        |
| --------------------- | -------- | ---- | -------------------------------------------- |
| defaultAllowedDelayMs | number   | Yes  | Delay time to set, in ms. The value can be **0** or ranges from 100 to 86400000.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**|
| ------------ | ------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAllowedDelayMs = 500;
  kvStore.setSyncParam(defaultAllowedDelayMs).then(() => {
    console.info('Succeeded in setting syncParam');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set syncParam. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### sync

sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void

Starts cross-device data sync manually. The sync result can be obtained by subscribing to the [on('syncComplete')](#onsynccomplete) event. For details about the sync modes of KV stores, see [Cross-Device Synchronization of KV Stores](../../database/data-sync-of-kv-store.md).
> **NOTE**
>
> **deviceIds** is **networkId** in [DeviceBasicInfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo), which can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type             | Mandatory| Description                                          |
| --------- | --------------------- | ---- | ---------------------------------------------- |
| deviceIds | string[]              | Yes  | List of **networkId**s of the devices in the same networking environment to be synchronized.|
| mode      | [SyncMode](#syncmode) | Yes  | Sync mode.                                    |
| delayMs   | number                | No  | Delay time allowed, in ms. The default value is **0**. If **delayMs** is set, data sync will be executed **delayMs** after **sync()** is called. If **delayMs** is not set, the delay set in [setSyncParam](#setsyncparam) is used.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**       |
| ------------ | ------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted. |
| 15100004     | Not found.          |

**Example**

```ts
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let devManager: distributedDeviceManager.DeviceManager;
const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
// create deviceManager
export default class EntryAbility extends UIAbility {
  onCreate() {
    let context = this.context;
    try {
      devManager = distributedDeviceManager.createDeviceManager(context.applicationInfo.name);
      let deviceIds: string[] = [];
      if (devManager != null) {
        let devices = devManager.getAvailableDeviceListSync();
        for (let i = 0; i < devices.length; i++) {
          deviceIds[i] = devices[i].networkId as string;
        }
      }
      try {
        if (kvStore != null) {
          kvStore.on('syncComplete', (data: [string, number][]) => {
            console.info('Sync dataChange');
          });
          if (kvStore != null) {
            kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, (err: BusinessError) => {
              if (err) {
                console.error(`Failed to sync. Code: ${err.code}, message: ${err.message}`);
                return;
              }
              console.info('Succeeded in putting data');
              const mode = distributedKVStore.SyncMode.PULL_ONLY;
              if (kvStore != null) {
                kvStore.sync(deviceIds, mode, 1000);
              }
            });
          }
        }
      } catch (err) {
        let error = err as BusinessError;
        console.error(`Failed to sync. Code: ${error.code}, message: ${error.message}`);
      }

    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create device manager. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

### sync

sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: number): void

Starts cross-device data sync manually. Data can be filtered by query conditions. The sync result can be obtained by subscribing to the [on('syncComplete')](#onsynccomplete) event. For details about the sync modes of KV stores, see [Cross-Device Synchronization of KV Stores](../../database/data-sync-of-kv-store.md).
> **NOTE**
>
> **deviceIds** is **networkId** in [DeviceBasicInfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo), which can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type             | Mandatory| Description                                          |
| --------- | --------------------- | ---- | ---------------------------------------------- |
| deviceIds | string[]              | Yes  | List of **networkId**s of the devices in the same networking environment to be synchronized.|
| query     | [Query](#query)        | Yes  | **Query** object to match.                     |
| mode      | [SyncMode](#syncmode) | Yes  | Sync mode.                                    |
| delayMs   | number                | No  | Delay time allowed, in ms. The default value is **0**. If **delayMs** is set, data sync will be executed **delayMs** after **sync()** is called. If **delayMs** is not set, the delay set in [setSyncParam](#setsyncparam) is used.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**       |
| ------------ | ------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted. |
| 15100004     | Not found.          |

**Example**

```ts
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
// create deviceManager
export default class EntryAbility extends UIAbility {
  onCreate() {
    let context = this.context;
    try {
      let devManager = distributedDeviceManager.createDeviceManager(context.applicationInfo.name);
      let deviceIds: string[] = [];
      if (devManager != null) {
        let devices = devManager.getAvailableDeviceListSync();
        for (let i = 0; i < devices.length; i++) {
          deviceIds[i] = devices[i].networkId as string;
        }
      }
      try {
        if (kvStore != null) {
          kvStore.on('syncComplete', (data: [string, number][]) => {
            console.info('Sync dataChange');
          });
          if (kvStore != null) {
            kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, (err: BusinessError) => {
              if (err) {
                console.error(`Failed to sync. Code: ${err.code}, message: ${err.message}`);
                return;
              }
              console.info('Succeeded in putting data');
              const mode = distributedKVStore.SyncMode.PULL_ONLY;
              const query = new distributedKVStore.Query();
              query.prefixKey('batch_test');
              query.deviceId(devManager.getLocalDeviceNetworkId());
              if (kvStore != null) {
                kvStore.sync(deviceIds, query, mode, 1000);
              }
            });
          }
        }
      } catch (err) {
        let error = err as BusinessError;
        console.error(`Failed to sync. Code: ${error.code}, message: ${error.message}`);
      }

    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create device manager. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

### on('dataChange')

on(event: 'dataChange', type: SubscribeType, listener: Callback&lt;ChangeNotification&gt;): void

Subscribes to data changes of the specified type. After calling **on** to subscribe to data changes, call [off('dataChange')](#offdatachange) to cancel the subscription when it is no longer needed.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                |
| -------- | --------------------------------------------------------- | ---- | ---------------------------------------------------- |
| event    | string                                                    | Yes  | Event type. The value is **dataChange**, which indicates a data change event.|
| type     | [SubscribeType](#subscribetype)                           | Yes  | Type of data change.                                    |
| listener | Callback&lt;[ChangeNotification](#changenotification)&gt; | Yes  | Callback used to return the object to be notified when the data changes.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100001     | Over max limits.                      |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_LOCAL, (data: distributedKVStore.ChangeNotification) => {
    console.info(`dataChange callback call data: ${data}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### on('syncComplete')

on(event: 'syncComplete', syncCallback: Callback&lt;Array&lt;[string, number]&gt;&gt;): void

Subscribes to the cross-device data sync completion events. After calling **on** to subscribe to the events, call [off('syncComplete')](#offsynccomplete) to unsubscribe from the events when they are no longer needed.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name      | Type                                     | Mandatory| Description                                                  |
| ------------ | --------------------------------------------- | ---- | ------------------------------------------------------ |
| event        | string                                        | Yes  | Event type. The value is **syncComplete**, which indicates the sync completion event.|
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | Yes  | Callback used to return the sync completion event.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_FLOAT_ELEMENT = 'key_test_float';
const VALUE_TEST_FLOAT_ELEMENT = 321.12;
try {
  kvStore.on('syncComplete', (data: [string, number][]) => {
    console.info(`syncComplete ${data}`);
  });
  kvStore.put(KEY_TEST_FLOAT_ELEMENT, VALUE_TEST_FLOAT_ELEMENT).then(() => {
    console.info('succeeded in putting');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to subscribe syncComplete. Code: ${error.code}, message: ${error.message}`);
}
```

### off('dataChange')

off(event:'dataChange', listener?: Callback&lt;ChangeNotification&gt;): void

Unsubscribes from data changes. You must call [on('dataChange')](#ondatachange) to subscribe to data changes before calling **off** to cancel subscription.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                    |
| -------- | --------------------------------------------------------- | ---- | -------------------------------------------------------- |
| event    | string                                                    | Yes  | Event type. The value is **dataChange**, which indicates a data change event.|
| listener | Callback&lt;[ChangeNotification](#changenotification)&gt; | No  | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for data changes.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class KvstoreModel {
  call(data: distributedKVStore.ChangeNotification) {
    console.info(`dataChange : ${data}`);
  }

  subscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_REMOTE, this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to subscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }

  unsubscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.off('dataChange', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to unsubscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

### off('syncComplete')

off(event: 'syncComplete', syncCallback?: Callback&lt;Array&lt;[string, number]&gt;&gt;): void

Unsubscribes from the cross-device data sync completion events. You must call [on('syncComplete')](#onsynccomplete) to subscribe to the events before calling **off** to cancel subscription.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name      | Type                                     | Mandatory| Description                                                      |
| ------------ | --------------------------------------------- | ---- | ---------------------------------------------------------- |
| event        | string                                        | Yes  | Event type. The value is **syncComplete**, which indicates a sync completion event.|
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | No  | Callback to unregister. If this parameter is not set, all callbacks used to listen for the data sync completion event are unregistered. Note that if multiple ArkTS instances (obtained through the [getKVStore](#getkvstore) API) of the same database all register the callback used to listen for the sync completion event, and one of the instances calls **off('syncComplete')** without passing the **syncCallback** parameter (that is, all callbacks of this instance are unregistered), then the callbacks of the other instances are also unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

class KvstoreModel {
  call(data: [string, number][]) {
    console.info(`syncComplete : ${data}`);
  }

  subscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.on('syncComplete', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to subscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }

  unsubscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.off('syncComplete', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to unsubscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  } 
}
```

### getSecurityLevel

getSecurityLevel(callback: AsyncCallback&lt;SecurityLevel&gt;): void

Obtains the security level of this KV store. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                            |
| -------- | ---------------------------------------------------- | ---- | -------------------------------- |
| callback | AsyncCallback&lt;[SecurityLevel](#securitylevel)&gt; | Yes  | Callback used to return the security level of the KV store.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.getSecurityLevel((err: BusinessError, data: distributedKVStore.SecurityLevel) => {
    if (err) {
      console.error(`Failed to get SecurityLevel. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting securityLevel');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getSecurityLevel

getSecurityLevel(): Promise&lt;SecurityLevel&gt;

Obtains the security level of this KV store. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type                                          | Description                               |
| ---------------------------------------------- | ----------------------------------- |
| Promise&lt;[SecurityLevel](#securitylevel)&gt; | Promise used to return the security level of the KV store.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.getSecurityLevel().then((data: distributedKVStore.SecurityLevel) => {
    console.info('Succeeded in getting securityLevel');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get SecurityLevel. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### rekey

rekey(): Promise&lt;void&gt;

Updates the encryption key of a database. This API uses a promise to return the result.

> **NOTE**
>
> The **rekey** operation is valid only for databases for which encryption is enabled during creation. That is, the **encrypt** parameter in **Options** must be set to **true**. If this API is called for a non-encrypted database, an error will be returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 15100003     | Database corrupted. |
| 15100005     | Database or result set already closed. |
| 15100006     | Failed to update the key. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rekey().then(() => {
    console.info('Success');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to rekey. Code: ${error.code}, message: ${error.message}`);
}
```

## DeviceKVStore

Provides APIs for querying data in a device KV store and performing cross-device data sync. This class inherits from **SingleKVStore**. The **SingleKVStore** APIs such as **put** and **putBatch** can be used.

Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified.

For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted.

Before calling any method in **DeviceKVStore**, you must use [getKVStore](#getkvstore) to obtain a **DeviceKVStore** object.

### get

get(key: string, callback: AsyncCallback&lt;boolean | string | number | Uint8Array&gt;): void

Obtains the value of the specified key for this device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| key      | string                                                       | Yes  | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|
| callback | AsyncCallback&lt;boolean \| string \| number \| Uint8Array&gt; | Yes  | Callback used to return the value obtained.                                |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT, (err: BusinessError, data: boolean | string | number | Uint8Array) => {
        if (err) {
          console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in getting data. Data=${data}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### get

get(key: string): Promise&lt;boolean | string | number | Uint8Array&gt;

Obtains the value of the specified key for this device. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| key    | string | Yes  | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).|

**Return value**

| Type                                                    | Description                           |
| -------------------------------------------------------- | ------------------------------- |
| Promise&lt;boolean \| string \| number \| Uint8Array&gt; | Promise used to return the obtained value. The value type depends on the data type when the value is stored.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data.data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### get

get(deviceId: string, key: string, callback: AsyncCallback&lt;boolean | string | number | Uint8Array&gt;): void

Obtains a value that matches the specified device ID and key. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name | Type| Mandatory | Description                   |
| -----  | ------   | ----  | ----------------------- |
| deviceId  |string  | Yes   |Network ID of the device whose data is to be queried. This parameter cannot be left empty.   |
| key       |string  | Yes   |Key name of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](#constants).   |
| callback  |AsyncCallback&lt;boolean \| string \| number \| Uint8Array&gt;  | Yes   |Callback used to return the result. If the operation is successful, the value that matches the specified condition is returned. The value type depends on the data type when the value is stored. If the operation fails, an error object is returned.   |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT, (err: BusinessError, data: boolean | string | number | Uint8Array) => {
        if (err) {
          console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting');
      });
    }
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### get

get(deviceId: string, key: string): Promise&lt;boolean | string | number | Uint8Array&gt;

Obtains a value that matches the specified device ID and key. This API uses a promise to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type| Mandatory| Description                    |
| -------- | -------- | ---- | ------------------------ |
| deviceId | string   | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| key      | string   | Yes  | Key to obtain. The value cannot be empty and its length range is 1-[MAX_KEY_LENGTH](#constants).   |

**Return value**

| Type   | Description      |
| ------  | -------   |
|Promise&lt;boolean \| string \| number \| Uint8Array&gt; |Promise used to return the value that matches the conditions. The value type depends on the data type when the value is stored.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(async () => {
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info('Succeeded in getting');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to put. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(keyPrefix: string, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains all KV pairs that match the specified key prefix for this device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                                  | Mandatory| Description                                    |
| --------- | -------------------------------------- | ---- | ---------------------------------------- |
| keyPrefix | string                                 | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs that match the specified prefix.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(keyPrefix: string): Promise&lt;Entry[]&gt;

Obtains all KV pairs that match the specified key prefix for this device. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type  | Mandatory| Description                |
| --------- | ------ | ---- | -------------------- |
| keyPrefix | string | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                            | Description                                       |
| -------------------------------- | ------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return the KV pairs that match the specified prefix.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains all KV pairs that match the specified device ID and key prefix. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name   | Type                              | Mandatory| Description                                          |
| --------- | -------------------------------------- | ---- | ---------------------------------------------- |
| deviceId  | string                                 | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                      |
| keyPrefix | string                                 | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries : ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', 'batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to put batch. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(deviceId: string, keyPrefix: string): Promise&lt;Entry[]&gt;

Obtains all KV pairs that match the specified device ID and key prefix. This API uses a promise to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name   | Type| Mandatory| Description                    |
| --------- | -------- | ---- | ------------------------ |
| deviceId  | string   | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| keyPrefix | string   | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                            | Description                                             |
| -------------------------------- | ------------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return all the KV pairs that match the given condition.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', 'batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
        console.info(`entries[0].value: ${entries[0].value}`);
        console.info(`entries[0].value.value: ${entries[0].value.value}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to put batch. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(query: Query, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains all KV pairs that match the specified **Query** object for this device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description                           |
| -------- | -------------------------------------- | ---- |-------------------------------|
| query    | [Query](#query)                         | Yes  | Object to match.                    |
| callback | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs that match the specified **Query** object on the local device.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(query: Query): Promise&lt;Entry[]&gt;

Obtains all KV pairs that match the specified **Query** object for this device. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type          | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                            | Description                                                    |
| -------------------------------- | -------------------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return the KV pairs that match the specified **Query** object on the local device.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting Entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(deviceId: string, query: Query, callback: AsyncCallback&lt;Entry[]&gt;): void

Obtains the KV pairs that match the specified device ID and **Query** object. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type                              | Mandatory| Description                                                   |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------- |
| deviceId | string                                 | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                                   |
| query    | [Query](#query)                         | Yes  | **Query** object to match.                                         |
| callback | AsyncCallback&lt;[Entry](#entry)[]&gt; | Yes  | Callback used to return the KV pairs that match the specified device ID and **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    let query = new distributedKVStore.Query();
    query.deviceId('localDeviceId');
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      })
    }
  });
  console.info('Succeeded in getting entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getEntries

getEntries(deviceId: string, query: Query): Promise&lt;Entry[]&gt;

Obtains the KV pairs that match the specified device ID and **Query** object. This API uses a promise to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type      | Mandatory| Description                |
| -------- | -------------- | ---- | -------------------- |
| deviceId | string         | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| query    | [Query](#query) | Yes  | **Query** object to match.      |

**Return value**

| Type                            | Description                                                      |
| -------------------------------- | ---------------------------------------------------------- |
| Promise&lt;[Entry](#entry)[]&gt; | Promise used to return the KV pairs that match the specified device ID and **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    let query = new distributedKVStore.Query();
    query.deviceId('localDeviceId');
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries('localDeviceId', query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get entries. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(keyPrefix: string, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a result set with the specified prefix for this device. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type                                                      | Mandatory| Description                                                                                |
| --------- | ---------------------------------------------------------- | ---- |------------------------------------------------------------------------------------|
| keyPrefix | string   | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the result set with the specified prefix.                                                                |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                                                                                                    |
| ------------ |--------------------------------------------------------------------------------------------------------------|
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 15100001     | Over max limits.<br>Applicable versions: 10+                                                                               |
| 15100003     | Database corrupted.                                                                                          |
| 15100005     | Database or result set already closed.                                                                       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing result set');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(keyPrefix: string): Promise&lt;KVStoreResultSet&gt;

Obtains a result set with the specified prefix for this device. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name   | Type  | Mandatory| Description                |
| --------- | ------ | ---- | -------------------- |
| keyPrefix | string | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                                                | Description                                   |
| ---------------------------------------------------- | --------------------------------------- |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the result set with the specified prefix.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
    kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting result set');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing result set');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a **KVStoreResultSet** object that matches the specified device ID and key prefix. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name   | Type                                                    | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| deviceId  | string                                                       | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                                    |
| keyPrefix | string                                                       | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|
| callback  | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('localDeviceId', 'batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing resultSet');
      })
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, keyPrefix: string): Promise&lt;KVStoreResultSet&gt;

Obtains a **KVStoreResultSet** object that matches the specified device ID and key prefix. This API uses a promise to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name   | Type| Mandatory| Description                    |
| --------- | -------- | ---- | ------------------------ |
| deviceId  | string   | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| keyPrefix | string   | Yes  | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](#constants). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned.|

**Return value**

| Type                                                  | Description                                                        |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  kvStore.getResultSet('localDeviceId', 'batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting resultSet');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing resultSet');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, query: Query, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a **KVStoreResultSet** object that matches the specified device ID and **Query** object. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type                                                    | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| deviceId | string                                                       | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                   |
| query    | [Query](#query)                                               | Yes  | **Query** object to match.                                              |
| callback | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the **KVStoreResultSet** object that matches the specified device ID and **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet('localDeviceId', query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSet');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing resultSet');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, query: Query): Promise&lt;KVStoreResultSet&gt;

Obtains a **KVStoreResultSet** object that matches the specified device ID and **Query** object. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type      | Mandatory| Description                              |
| -------- | -------------- | ---- | ---------------------------------- |
| deviceId | string         | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| query    | [Query](#query) | Yes  | **Query** object to match.                    |

**Return value**

| Type                                                  | Description                                                        |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object that matches the specified device ID and **Query** object.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  if (kvStore != null) {
    kvStore.getResultSet('localDeviceId', query).then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting resultSet');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing resultSet');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
    });
  }
  query.deviceId('localDeviceId');
  console.info('GetResultSet ' + query.getSqlLike());

} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(query: Query): Promise&lt;KVStoreResultSet&gt;

Obtains a **KVStoreResultSet** object that matches the specified **Query** object for this device. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type          | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                                                | Description                                                        |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| Promise&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSet(query).then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(query: Query, callback:AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains a **KVStoreResultSet** object that matches the specified **Query** object for this device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type          | Mandatory| Description                              |
| -------- | -------------- | ---- | ---------------------------------- |
| query    | [Query](#query) | Yes  | **Query** object to match.                    |
| callback    | AsyncCallback&lt;[KVStoreResultSet](#kvstoreresultset)&gt; | Yes  | Callback used to return the result. If the operation is successful, the **KVStoreResultSet** object that matches the specified **Query** object is returned. If the operation fails, an error object is returned.        |


**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 15100001     | Over max limits.<br>Applicable versions: 10+                      |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet(query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultSet. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSet');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to close resultSet. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing resultSet');
          })
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSet. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(query: Query, callback: AsyncCallback&lt;number&gt;): void

Obtains the number of results that match the specified **Query** object for this device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                       | Mandatory| Description                                             |
| -------- | --------------------------- | ---- | ------------------------------------------------- |
| query    | [Query](#query)              | Yes  | **Query** object to match.                                   |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize(query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set size');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(query: Query): Promise&lt;number&gt;

Obtains the number of results that match the specified **Query** object for this device. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type          | Mandatory| Description          |
| ------ | -------------- | ---- | -------------- |
| query  | [Query](#query) | Yes  | **Query** object to match.|

**Return value**

| Type                 | Description                                                |
| --------------------- | ---------------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize(query).then((resultSize: number) => {
    console.info('Succeeded in getting result set size');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(deviceId: string, query: Query, callback: AsyncCallback&lt;number&gt;): void

Obtains the number of results that match the specified device ID and **Query** object. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type                   | Mandatory| Description                                               |
| -------- | --------------------------- | ---- | --------------------------------------------------- |
| deviceId | string                      | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                 |
| query    | [Query](#query)              | Yes  | **Query** object to match.                                     |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize('localDeviceId', query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get resultSize. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting resultSize');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSize. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSize

getResultSize(deviceId: string, query: Query): Promise&lt;number&gt;

Obtains the number of results that match the specified device ID and **Query** object. This API uses a promise to return the result.
> **NOTE**
>
> **deviceId** can be obtained by [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync()](#sync).

**System capability**: SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters**

| Name  | Type      | Mandatory| Description                              |
| -------- | -------------- | ---- | ---------------------------------- |
| deviceId | string         | Yes  | Network ID of the device whose data is to be queried. This parameter cannot be left empty.|
| query    | [Query](#query) | Yes  | **Query** object to match.                    |

**Return value**

| Type                 | Description                                                  |
| --------------------- | ------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the number of results obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 15100003     | Database corrupted.                    |
| 15100004     | Not found.                             |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  let query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize('localDeviceId', query).then((resultSize: number) => {
    console.info('Succeeded in getting resultSize');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultSize. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get resultSize. Code: ${error.code}, message: ${error.message}`);
}
```
