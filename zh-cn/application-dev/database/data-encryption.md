# 数据库加密 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997; @dboy190-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍

为了增强数据库的安全性，数据库提供了一个安全适用的数据库加密能力，从而对数据库存储的内容实施有效保护。通过数据库加密等安全方法实现了数据库数据存储的保密性和完整性要求，使得数据库以密文方式存储并在密态方式下工作，确保了数据安全。

加密后的数据库只能通过接口进行访问，无法通过其它方式打开数据库文件。数据库的加密属性在创建数据库时确认，无法变更。

键值型数据库和关系型数据库均支持数据库加密操作，其中关系型数据库支持自定义加密/解密的密钥和其他参数。


## 键值型数据库加密

键值型数据库，通过options中encrypt参数来设置是否加密，默认为false，表示不加密。encrypt参数为true时表示加密。

具体接口及功能，可见[分布式键值数据库](../reference/apis-arkdata/js-apis-distributedKVStore.md)。

   ```ts
   // 导入模块
   // 在pages目录下新建KvStoreInterface.ets
   import { distributedKVStore } from '@kit.ArkData';
   import { BusinessError } from '@kit.BasicServicesKit';
   import EntryAbility from '../entryability/EntryAbility';
   // Logger为hilog封装后实现的打印功能
   import Logger from '../common/Logger';

   let kvManager: distributedKVStore.KVManager | undefined = undefined;
   let kvStore: distributedKVStore.SingleKVStore | undefined = undefined;
   let appId: string = 'com.example.kvstoresamples';
   let storeId: string = 'storeId';
   const context = EntryAbility.getContext();

   // 下面所有接口的代码都实现在KvInterface中
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
         // 创建KVManager实例
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
       // 0表示COMPATIBLE模式，1表示STRICT模式。
       schema.mode = 1;
       // 支持在检查Value时，跳过skip指定的字节数，且取值范围为[0,4M-2]。
       schema.skip = 0;
   
       const options: distributedKVStore.Options = {
         createIfMissing: true,
         // 设置数据库加密
         encrypt: true,
         backup: false,
         autoSync: false,
         // kvStoreType不填时，默认创建多设备协同数据库
         kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
         // 多设备协同数据库：kvStoreType: distributedKVStore.KVStoreType.DEVICE_COLLABORATION,
         schema: schema,
         // schema未定义可以不填，定义方法请参考上方schema示例。
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
           // 请确保获取到键值数据库实例后，再进行相关数据操作
         });
     } catch (e) {
       let error = e as BusinessError;
       Logger.error(`An unexpected error occurred. Code:${error.code},message:${error.message}`);
     }
   })
   ```

## 关系型数据库加密

关系型数据库，通过[StoreConfig](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#storeconfig)中encrypt属性来设置是否加密。encrypt参数为true时表示加密；为false时表示不加密；默认值为false。

当encrypt为true时，支持开发者通过ArkTs API中的可选属性cryptoParam设置自定义的加密/解密密钥和算法等参数。

针对cryptoParam的配置与否，有如下两种场景：

场景1：不配置cryptoParam属性，此时会使用默认的加密配置进行数据库的加密/解密。


<!-- @[encryption_TS_IncludeSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

``` TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit'
```



<!-- @[defaultConfigRdbStoreTs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

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



场景2：配置cryptoParam属性，此时会使用开发者自定义的密钥和算法参数进行数据库的加密/解密。

<!-- @[customizedConfigRdbStoreTs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/ets/pages/encryption/Encryption.ets) -->

``` TypeScript
let store: relationalStore.RdbStore | undefined = undefined;
let context = getContext();
// 初始化需要使用的密钥，示例中使用硬编码密钥仅用于演示目的， 实际应用中应使用安全的密钥管理服务
let key = new Uint8Array(32);
for (let i = 0; i < 32; i++) {
  key[i] = i;
}

// 初始化加密算法
const CRYPTO_PARAM: relationalStore.CryptoParam = {
  encryptionKey: key, // 必选参数，使用指定的密钥打开加密数据库。为空则由数据库负责生成并保存密钥，并使用生成的密钥打开数据库文件。
  iterationCount: 25000, // 可选参数，迭代次数。迭代次数必须大于零。不指定或等于零则使用默认值10000和默认加密算法。
  encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_CBC, // 可选参数，加密/解密算法。如不指定，默认算法为AES_256_GCM。
  hmacAlgo: relationalStore.HmacAlgo.SHA256, // 可选参数，HMAC算法。如不指定，默认值为SHA256。
  kdfAlgo: relationalStore.KdfAlgo.KDF_SHA512, // 可选参数，KDF算法。如不指定，默认值和HMAC算法相等。
  cryptoPageSize: 2048 // 可选参数，加密/解密时使用的页大小。必须为1024到65536范围内的整数并且为2的幂。如不指定，默认值为1024。
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
  // 调用完后需要将密钥清零
  CRYPTO_PARAM.encryptionKey.fill(0);
  key.fill(0);
} catch (e) {
  const err = e as BusinessError;
  hilog.error(DOMAIN, 'Encryption', `Failed to get RdbStore. Code:${err.code}, message:${err.message}`);
}
```



如果开发者不关心加密使用的算法及参数，则无需配置cryptoParam属性，使用默认加密配置即可。当开发者需要自定义加密配置，或需要打开非默认配置的加密数据库时，则需要配置cryptoParam属性。
