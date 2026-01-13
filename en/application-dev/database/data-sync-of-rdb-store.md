# Cross-Device Sync of RDB Stores (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->


## When to Use

You can sync the application data in a local RDB store on a device to other devices that form a Super Device.


## Basic Concepts

OpenHarmony supports sync of the relational data of an application across multiple devices.

- Distributed table: a database table that supports data sync across multiple devices in the network cluster. Data from other devices is synced to the local device and stored in the table name associated with the device ID.
- Data sync: Changes to distributed tables in the database on a device are synced to other devices in the network cluster. Data can be synced between devices in either of the following ways: pushing data from a local device to a remote device and pulling data from a remote device to a local device.
- Data change notification: When data changes on other devices in the network cluster are synced to the current device, the registered callback function is executed.

## Working Principles

After completing device discovery and authentication, the underlying communication component notifies the application that the device goes online. The **DatamgrService** then establishes an encrypted transmission channel to sync data between the two devices.


### Cross-Device Data Sync Mechanism

![relationalStore_sync](figures/relationalStore_sync.jpg)

After writing data to an RDB store, the service sends a sync request to the **DatamgrService**.

The **DatamgrService** reads the data to be synced from the application sandbox and sends the data to the **DatamgrService** of the target device based on the **deviceId** of the peer device. Then, the **DatamgrService** writes the data to the RDB of the same application.


### Data Change Notification Mechanism

When data is added, deleted, or modified, a notification is sent to the subscriber. The notifications can be classified into the following types:

- Local data change notification: subscription of the application data changes on the local device. When the data in the local KV store is added, deleted, or modified in the database, a notification is received.

- Distributed data change notification: subscription of the application data changes of other devices in the network. When the data in the local RDB store changes after being synced with data from another device in the same network, a notification is received.


## Constraints

- A maximum of 16 RDB stores can be opened simultaneously for an application.

- Each RDB store supports a maximum of eight callbacks for subscription of data change notifications.

- A table containing composite keys cannot be set as a distributed table.

## Available APIs

The following table lists the APIs for cross-device data sync of RDB stores. Most of the APIs are executed asynchronously, using a callback or promise to return the result. The following table uses the callback-based APIs as an example. For more information about the APIs, see [RDB Store](../reference/apis-arkdata/arkts-apis-data-relationalStore.md).

| API| Description|
| -------- | -------- |
| setDistributedTables(tables: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void | Sets the distributed tables to be synced.|
| sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback&lt;Array&lt;[string, number]&gt;&gt;): void | Synchronizes data across devices.|
| on(event: 'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void | Subscribes to changes in the distributed data.|
| off(event:'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void | Unsubscribe from changes in the distributed data.|
| obtainDistributedTableName(device: string, table: string, callback: AsyncCallback&lt;string&gt;): void | Obtains the table name on the specified device based on the local table name.|
| remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array&lt;string&gt; , callback: AsyncCallback&lt;ResultSet&gt;): void | Queries data from the RDB store of a remote device based on specified conditions.|


## How to Develop

> **NOTE**
>
> The security level of the destination device (to which data is synced) cannot be higher than that of the source device. For details, see [Access Control Mechanism in Cross-Device Sync](access-control-by-device-and-data-level.md#access-control-mechanism-in-cross-device-sync).

1. Import the related modules.
   <!--@[sync_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->
   
   ``` TypeScript
   import { relationalStore } from '@kit.ArkData'; // Import modules.
   import { BusinessError } from '@kit.BasicServicesKit';
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   const DOMAIN = 0x0000;
   ```

2. Request permissions.

   1. Declare the **ohos.permission.DISTRIBUTED_DATASYNC** permission. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).
   2. Display a dialog box to ask for authorization from the user when the application is started for the first time. For details, see [Requesting User Authorization](../security/AccessToken/request-user-authorization.md).

3. Create an RDB store and a data table, and set the data table that requires cross-device data sync as a distributed table.
   <!--@[setDistributedTables](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)--> 
   
   ``` TypeScript
   let store: relationalStore.RdbStore | undefined = undefined;
   // ...
     const STORE_CONFIG: relationalStore.StoreConfig = {
       name: 'RdbTest.db', // Database file name.
       securityLevel: relationalStore.SecurityLevel.S3 // Database security level.
     };
     // Open the database and set the distributed table.
     relationalStore.getRdbStore(context, STORE_CONFIG).then(async (rdbStore: relationalStore.RdbStore) => {
       store = rdbStore;
       await store.executeSql('CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)');
       // Set the created table as a distributed table.
       await store.setDistributedTables(['EMPLOYEE']);
     }).catch((err: BusinessError) => {
       hilog.error(DOMAIN, 'rdbDataSync', `Get RdbStore failed, code is ${err.code}, message is ${err.message}`);
     });
   ```

4. Subscribe to data changes of other devices in the network cluster.
   1. Call [on('dataChange')](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#ondatachange) to listen for data changes of other devices. This API is called when data changes and is synced to the current device. The input parameter is the list of device IDs whose data changes.
   2. Obtain the distributed table name corresponding to the device based on the device ID and query data in the distributed table.
   <!--@[on_data_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->
   
   ``` TypeScript
   // Subscribe to data changes of other devices in the network cluster.
   if (store) {
     try {
       // Query the device list in the network cluster.
       const deviceManager = distributedDeviceManager.createDeviceManager('com.example.rdbDataSync');
       const deviceList = deviceManager.getAvailableDeviceListSync();
       const devices: string[] = [];
       deviceList.forEach(item => {
         if (item.networkId) {
           devices.push(item.networkId);
         }
       });
       // Register an observer to listen for the changes of the distributed data.
       // When data in the RDB store changes, the registered callback will be invoked to return the data changes.
       store.on('dataChange', relationalStore.SubscribeType.SUBSCRIBE_TYPE_REMOTE, async (devices) => {
         for (let i = 0; i < devices.length; i++) {
           let device = devices[i];
           if (!store) {
             return;
           }
           hilog.info(DOMAIN, 'rdbDataSync', `The data of device:${device} has been changed.`);
           // Obtain the distributed table name.
           const distributedTableName = await store.obtainDistributedTableName(device, 'EMPLOYEE');
           // Create a query predicate to query data in the distributed table.
           const predicates = new relationalStore.RdbPredicates(distributedTableName);
           const resultSet = await store.query(predicates);
           hilog.info(DOMAIN, 'rdbDataSync', `device ${device}, table EMPLOYEE rowCount is: ${resultSet.rowCount}`);
         }
       });
     } catch (err) {
       hilog.error(DOMAIN, 'rdbDataSync', `Failed to register observer. Code:${err.code},message:${err.message}`);
     }
   }
   ```

5. Sync data changes of the current device to other devices in the network cluster.
   1. After the data in the distributed table of the current device changes, the [sync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#sync-1) API of **RdbStore** is called to pass the [SYNC_MODE_PUSH](../reference/apis-arkdata/arkts-apis-data-relationalStore-e.md#syncmode) parameter to push data changes to other devices.
   2. Use the [inDevices](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbPredicates.md#indevices) method of the predicate to specify the target device for receiving data changes.
  
   <!--@[data_sync_push](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->
   
   ``` TypeScript
   // Sync data changes of the current device to other devices in the network cluster.
   if (store) {
     // Insert new data into the distributed data table of the current device.
     const ret = store.insertSync('EMPLOYEE', {
       name: 'sync_me',
       age: 18,
       salary: 666
     });
     hilog.info(DOMAIN, 'rdbDataSync', 'Insert to distributed table EMPLOYEE, result: ' + ret);
     // Query the device list in the network cluster.
     const deviceManager = distributedDeviceManager.createDeviceManager('com.example.rdbDataSync');
     const deviceList = deviceManager.getAvailableDeviceListSync();
     const syncTarget: string[] = [];
     deviceList.forEach(item => {
       if (item.networkId) {
         syncTarget.push(item.networkId);
       }
     });
     if (syncTarget.length === 0) {
       hilog.error(DOMAIN, 'rdbDataSync', 'no device to sync');
     } else {
       // Construct the predicate object for synchronizing the distributed table.
       const predicates = new relationalStore.RdbPredicates('EMPLOYEE');
       // Specify devices to be synced.
       predicates.inDevices(syncTarget);
       try {
         // Call the sync API to push the data changes from the current device to other devices in the network cluster.
         const result = await store.sync(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates);
         hilog.info(DOMAIN, 'rdbDataSync', 'Push data success.');
         // Obtain the sync result.
         for (let i = 0; i < result.length; i++) {
           const deviceId = result[i][0];
           const syncResult = result[i][1];
           if (syncResult === 0) {
             hilog.info(DOMAIN, 'rdbDataSync', `device:${deviceId} sync success`);
           } else {
             hilog.error(DOMAIN, 'rdbDataSync', `device:${deviceId} sync failed, status:${syncResult}`);
           }
         }
       } catch (e) {
         hilog.error(DOMAIN, 'rdbDataSync', 'Push data failed, code: ' + e.code + ', message: ' + e.message);
       }
     }
   }
   ```

6. Obtain the data changes of other devices in the network cluster.
   1. The current device can call the [sync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#sync-1) API of **RdbStore** and pass the [SYNC_MODE_PULL](../reference/apis-arkdata/arkts-apis-data-relationalStore-e.md#syncmode) parameter to pull data changes from other devices in the network cluster.
   2. Use the [inDevices](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbPredicates.md#indevices) method of the predicate to specify the target device.
   
   <!--@[data_sync_pull](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->
   
   ``` TypeScript
   // Obtain the data changes of other devices in the network cluster.
   if (store) {
     // Query the device list in the network cluster.
     const deviceManager = distributedDeviceManager.createDeviceManager('com.example.rdbDataSync');
     const deviceList = deviceManager.getAvailableDeviceListSync();
     const syncTarget: string[] = [];
     deviceList.forEach(item => {
       if (item.networkId) {
         syncTarget.push(item.networkId);
       }
     });
     if (syncTarget.length === 0) {
       hilog.error(DOMAIN, 'rdbDataSync', 'no device to pull data');
     } else {
       // Construct the predicate object for synchronizing the distributed table.
       const predicates = new relationalStore.RdbPredicates('EMPLOYEE');
       // Specify devices to be synced.
       predicates.inDevices(syncTarget);
       try {
         // Call the sync API to pull data changes from other devices to the current device.
         const result = await store.sync(relationalStore.SyncMode.SYNC_MODE_PULL, predicates);
         hilog.info(DOMAIN, 'rdbDataSync', 'Pull data success.');
         // Obtain the sync result.
         for (let i = 0; i < result.length; i++) {
           const deviceId = result[i][0];
           const syncResult = result[i][1];
           if (syncResult === 0) {
             hilog.info(DOMAIN, 'rdbDataSync', `device:${deviceId} sync success`);
           } else {
             hilog.error(DOMAIN, 'rdbDataSync', `device:${deviceId} sync failed, status:${syncResult}`);
           }
         }
       } catch (e) {
         hilog.error(DOMAIN, 'rdbDataSync', 'Pull data failed, code: ' + e.code + ', message: ' + e.message);
       }
     }
   }
   ```

7. If data sync is not complete or not triggered, use the [remoteQuery](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#remotequery-1) method of **RdbStore** to query the data in the distributed table on a specified device in the network cluster.
   <!--@[data_remote_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->
   
   ``` TypeScript
   // Query data of the distributed table on a specified device in the network cluster.
   if (store) {
     // Query the device list in the network cluster.
     const deviceManager = distributedDeviceManager.createDeviceManager('com.example.rdbDataSync');
     const deviceList = deviceManager.getAvailableDeviceListSync();
     const devices: string[] = [];
     deviceList.forEach(item => {
       if (item.networkId) {
         devices.push(item.networkId);
       }
     });
     if (devices.length === 0) {
       hilog.error(DOMAIN, 'rdbDataSync', 'no device to query data');
       return;
     }
     // Construct a predicate object for querying the distributed table.
     const predicates = new relationalStore.RdbPredicates('EMPLOYEE');
     try {
       // Query the distributed table on a specified device in the network cluster.
       const resultSet = await store.remoteQuery(devices[0], 'EMPLOYEE', predicates, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
       hilog.info(DOMAIN, 'rdbDataSync', `ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
     } catch (e) {
       hilog.error(DOMAIN, 'rdbDataSync', 'Remote query failed, code: ' + e.code + ', message: ' + e.message);
     }
   }
   ```
