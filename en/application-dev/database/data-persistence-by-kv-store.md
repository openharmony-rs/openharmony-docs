# Persisting KV Store Data (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->


## When to Use

The key-value (KV) database stores data in the form of KV pairs. You can use KV stores to store data organized in a simple model, for example, product names and prices or employee IDs and daily attendance. The simple data structure allows higher compatibility with different database versions and device types.


## Constraints

- For each record in a device KV store, the key cannot exceed 896 bytes and the value cannot exceed 4 MB.

- For each record in a single KV store, the key cannot exceed 1 KB and the value cannot exceed 4 MB.

- A maximum of 16 distributed KV stores can be opened simultaneously for an application.

- Blocking operations, for example, modifying UI components, are not allowed in the KV store event callbacks.


## Available APIs

The following table lists the APIs used for KV data persistence. Most of the APIs are executed asynchronously, using a callback or promise to return the result. The following table uses the callback-based APIs as an example. For more information about the APIs, see [Distributed KV Store](../reference/apis-arkdata/js-apis-distributedKVStore.md).

| API| Description| 
| -------- | -------- |
| createKVManager(config: KVManagerConfig): KVManager | Creates a **KvManager** instance to manage database objects.| 
| getKVStore&lt;T&gt;(storeId: string, options: Options, callback: AsyncCallback&lt;T&gt;): void | Obtains a KV store of the specified type.| 
| put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback&lt;void&gt;): void | Adds a KV pair of the specified type to this KV store.| 
| get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void | Obtains the value of the specified key.| 
| delete(key: string, callback: AsyncCallback&lt;void&gt;): void | Deletes a KV pair based on the specified key.| 
| closeKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void | Closes the distributed KV store of the given **storeId**.| 
| deleteKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void | Deletes the distributed KV store of the given **storeId**.| 


## How to Develop

1. Use the **createKVManager()** method to create a **KVManager** instance for managing database objects. <br>Example:

   ```ts
   // Import the module.
   // Create a KvStoreInterface.ets file in the pages directory.
   import { distributedKVStore } from '@kit.ArkData';
   import { BusinessError } from '@kit.BasicServicesKit';
   import EntryAbility from '../entryability/EntryAbility';
   // Logger implements the print feature after Hilog is encapsulated.
   import Logger from '../common/Logger';

   let kvManager: distributedKVStore.KVManager | undefined = undefined;
   let kvStore: distributedKVStore.SingleKVStore | undefined = undefined;
   let appId: string = 'com.example.kvstoresamples';
   let storeId: string = 'storeId';
   // Obtain the context of the stage model from EntryAbility.ets.
   const context = EntryAbility.getContext();

   // Obtain the context of the FA model.
   import { featureAbility } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let context = featureAbility.getContext();

   // The code of all the following APIs is implemented in KvInterface.
   export class KvInterface {
   }
   ```
   <!-- @[kv_store1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public CreateKvManager = (() => {
     Logger.info('CreateKvManager start');
     if (typeof (kvManager) === 'undefined') {
       const kvManagerConfig: distributedKVStore.KVManagerConfig = {
         bundleName: appId,
         context: context
       };
       try {
         // Create a KVManager instance.
         kvManager = distributedKVStore.createKVManager(kvManagerConfig);
         Logger.info('Succeeded in creating KVManager.');
       } catch (err) {
         Logger.error(`Failed to create KVManager. Code:${err.code},message:${err.message}`);
       }
     } else {
       Logger.info ('KVManager has created');
     }
   })
   ```

2. Use the **getKVStore()** method to create and obtain a KV store. <br>Example:

   <!-- @[kv_store3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public GetKvStore = (() => {
     Logger.info('GetKvStore start');
     if (kvManager === undefined) {
       Logger.info('KvManager not initialized');
       return;
     }
     try {
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
       // The value 0 indicates the compatible mode, and 1 indicates the strict mode.
       schema.mode = 1;
       // Set the number of bytes to be skipped during the value check. The value range is [0, 4M-2].
       schema.skip = 0;
   
       const options: distributedKVStore.Options = {
         createIfMissing: true,
         // Whether to encrypt the KV store.
         encrypt: true,
         backup: false,
         autoSync: false,
         // If kvStoreType is left empty, a device KV store is created by default.
         kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
         // Device KV store: kvStoreType: distributedKVStore.KVStoreType.DEVICE_COLLABORATION,
         schema: schema,
         // If the schema is not defined, you can leave it empty. For details about how to define the schema, see the example above.
         securityLevel: distributedKVStore.SecurityLevel.S3
       };
       kvManager.getKVStore<distributedKVStore.SingleKVStore>(storeId, options,
         (err, store: distributedKVStore.SingleKVStore) => {
           if (err) {
             Logger.error(`Failed to get KVStore: Code:${err.code},message:${err.message}`);
             return;
           }
           Logger.info('Succeeded in getting KVStore.');
           kvStore = store;
           // Before performing related data operations, obtain a KV store instance.
         });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
     }
   })
   ```

3. Use the **on()** method to subscribe to distributed data changes. To unsubscribe from the data changes, call [off('dataChange')](../reference/apis-arkdata/js-apis-distributedKVStore.md#offdatachange). <br>Example:

   <!-- @[kv_store12](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public On = (() =>{
     Logger.info('On start');
     if(kvStore === undefined) {
       Logger.info('On: kvStore not initialized');
       return;
     }
     try {
       kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_ALL, (data) => {
         Logger.info(`dataChange callback call data: ${data}`);
       });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`An unexpected error occurred. code:${error.code},message:${error.message}`);
     }
   })
   ```

4. Use **put()** to add data to the KV store. <br>Example:

   <!-- @[kv_store4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public Put = (() => {
     Logger.info('Put start');
     if (kvStore === undefined) {
       Logger.info('Put: kvStore not initialized');
       return;
     }
     const KEY_TEST_STRING_ELEMENT = 'key_test_string';
     // If schema is not defined, pass in other values that meet the requirements.
     const VALUE_TEST_STRING_ELEMENT = '{"id":0, "name":"lisi"}';
     try {
       kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err) => {
         if (err !== undefined) {
           Logger.error(`Failed to put data. Code:${err.code},message:${err.message}`);
           return;
         }
         Logger.info('Succeeded in putting data.');
       });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
     }
   })
   ```

   > **NOTE**
   >
   > The **put()** method adds a KV pair if the specified key does not exist and changes the value if the specified key already exists.

5. Use **get()** to obtain the value of a key. <br>Example:

   <!-- @[kv_store5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public Get = (() => {
     Logger.info('Get start');
     if (kvStore === undefined) {
       Logger.info('Get: kvStore not initialized');
       return;
     }
     const KEY_TEST_STRING_ELEMENT = 'key_test_string';
     try {
       kvStore.get(KEY_TEST_STRING_ELEMENT, (err, data) => {
         if (err != undefined) {
           Logger.error(`Failed to get data. Code:${err.code},message:${err.message}`);
           return;
         }
         Logger.info(`Succeeded in getting data. Data:${data}`);
       });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`Failed to get data. Code:${error.code},message:${error.message}`);
     }
   })
   ```

6. Use **delete()** to delete the data of the specified key. <br>Example:

   <!-- @[kv_store6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
   
   ``` TypeScript
   public Delete = (() => {
     Logger.info('DeleteData start');
     if (kvStore === undefined) {
       Logger.info('DeleteData: kvStore not initialized');
       return;
     }
     const KEY_TEST_STRING_ELEMENT = 'key_test_string';
     try {
       kvStore.delete(KEY_TEST_STRING_ELEMENT, (err) => {
         if (err !== undefined) {
           Logger.error(`Failed to delete data. Code:${err.code},message:${err.message}`);
           return;
         }
         Logger.info('Succeeded in deleting data.');
       });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
     }
   })
   ```

7. Use **closeKVStore()** to close the specified distributed KV store by **storeId**. <br>Example:

    <!-- @[kv_store10](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
    
    ``` TypeScript
    public CloseKVStore = (()=>{
      Logger.info('CloseKVStore start');
      if (kvManager === undefined) {
        Logger.info('KvManager not initialized');
        return;
      }
      try {
        // appId is the bundle name of the application.
        kvStore = undefined;
        kvManager.closeKVStore(appId, storeId, (err: BusinessError)=> {
          if (err) {
            Logger.error(`Failed to close KVStore.code is ${err.code},message is ${err.message}`);
            return;
          }
          Logger.info('Succeeded in closing KVStore');
        });
      } catch (e) {
        let error = e as BusinessError;
        Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    })
    ```

8. Use **deleteKVStore()** to delete the specified distributed KV store by **storeId**. <br>Example:

    <!-- @[kv_store11](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->
    
    ``` TypeScript
    public DeleteKvStore = (()=>{
      Logger.info('DeleteKvStore start');
      if (kvManager === undefined) {
        Logger.info('KvManager not initialized');
        return;
      }
      try {
        // appId is the bundle name of the application.
        kvStore = undefined;
        kvManager.deleteKVStore(appId, storeId, (err: BusinessError)=> {
          if (err) {
            Logger.error(`Failed to delete KVStore.code is ${err.code},message is ${err.message}`);
            return;
          }
          Logger.info('Succeeded in deleting KVStore');
        });
      } catch (e) {
        let error = e as BusinessError;
        Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
      }
    })
    ```

<!--RP1--><!--RP1End-->
