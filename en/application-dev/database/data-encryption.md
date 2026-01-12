# Database Encryption (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997; @dboy190-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## When to Use

OpenHarmony provides the database encryption capability to effectively protect the data stored in a database. Database encryption allows data to be stored and used in ciphertext, ensuring data confidentiality and integrity.

The encrypted database can be accessed only using an API, and the database file cannot be opened in other ways. Whether a database is encrypted is set when the database is created, and the setting cannot be changed.

Both KV stores and RDB stores support database encryption. For RDB stores, you can customize the encryption/decryption keys and other parameters.


## Encrypting a KV Store

When a KV store is created, the **encrypt** parameter in **options** specifies whether to encrypt it. The value **true** means to encrypt the KV store, and the value **false** (default) means the opposite.

For details about the APIs, see [Distributed KV Store](../reference/apis-arkdata/js-apis-distributedKVStore.md).

   ```ts
   // Import modules.
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
   const context = EntryAbility.getContext();

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
         // kvStoreType is distributedKVStore.KVStoreType.DEVICE_COLLABORATION for a device KV store.
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

## Encrypting an RDB Store 

The **encrypt** property in [StoreConfig](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#storeconfig) specifies whether to encrypt the RDB store. The value **true** means to encrypt the RDB store, and **false** means the opposite.

If **encrypt** is **true**, you can set parameters such as the key and algorithm used for encryption/decryption in **cryptoParam** in ArkTS APIs.

The **cryptoParam** setting involves the following scenarios:

If **cryptoParam** is not set, the default configuration is used for database encryption and decryption.


<!-- @[encryption_TS_IncludeSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

``` TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit'
```



<!-- @[defaultConfigRdbStoreTs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

``` TypeScript
let store: relationalStore.RdbStore | undefined = undefined;
let context = getContext();

try {
  const STORE_CONFIG: relationalStore.StoreConfig = {
    name: 'RdbTest.db',
    securityLevel: relationalStore.SecurityLevel.S3,
    encrypt: true
  };
  store = await relationalStore.getRdbStore(context, STORE_CONFIG);
  hilog.info(DOMAIN, 'Encryption', 'Succeeded in getting RdbStore.');
} catch (e) {
  const err = e as BusinessError;
  hilog.error(DOMAIN, 'Encryption', `Failed to get RdbStore. Code:${err.code}, message:${err.message}`);
}
```



If **cryptoParam** is set, the specified key and algorithm are used for database encryption and decryption.

<!-- @[customizedConfigRdbStoreTs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

``` TypeScript
let store: relationalStore.RdbStore | undefined = undefined;
let context = getContext();
// Initialize the key to be used. Hard-coded keys are used as an example. You should use a secure key management service in actual development.
let key = new Uint8Array(32);
for (let i = 0; i < 32; i++) {
  key[i] = i;
}

// Initialize the encryption algorithm.
const CRYPTO_PARAM: relationalStore.CryptoParam = {
  encryptionKey: key, // (Mandatory) Key used to open the encrypted database. If this parameter is not specified, the database generates and saves the key and uses the generated key to open the database file.
  iterationCount: 25000, // (Optional) Number of iterations. The value must be greater than or equal to 0. If this parameter is not specified or is set to 0, the default value 10000 and the default encryption algorithm are used.
  encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_CBC, // (Optional) Encryption/Decryption algorithm. If this parameter is not specified, the default algorithm AES_256_GCM is used.
  hmacAlgo: relationalStore.HmacAlgo.SHA256, // (Optional) HMAC algorithm. If this parameter is not specified, the default value SHA256 is used.
  kdfAlgo: relationalStore.KdfAlgo.KDF_SHA512, // (Optional) KDF algorithm. If this parameter is not specified, the default value (same as the HMAC algorithm) is used.
  cryptoPageSize: 2048 // (Optional) Page size used for encryption/decryption. The value must be an integer within the range of 1024 to 65536 and a power of 2. The default value is 1024.
}

const STORE_CONFIG: relationalStore.StoreConfig = {
  name: 'encrypted.db',
  securityLevel: relationalStore.SecurityLevel.S3,
  encrypt: true,
  cryptoParam: CRYPTO_PARAM
}
try {
  store = await relationalStore.getRdbStore(context, STORE_CONFIG);
  if (store == null) {
    hilog.error(DOMAIN, 'Encryption', 'Failed to get RdbStore.');
  } else {
    hilog.info(DOMAIN, 'Encryption', 'Succeeded in getting RdbStore.');
  }
  // Clear the key.
  CRYPTO_PARAM.encryptionKey.fill(0);
  key.fill(0);
} catch (e) {
  const err = e as BusinessError;
  hilog.error(DOMAIN, 'Encryption', `Failed to get RdbStore. Code:${err.code}, message:${err.message}`);
}
```



If you do not care about the algorithm and other parameters used for encryption, leave **cryptoParam** unspecified. In this case, the default encryption configuration is used. If you want to customize the encryption configuration or open an encrypted database that is not configured by default, set **cryptoParam**.
