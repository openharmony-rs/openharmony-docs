# 使用KEM进行密钥封装解封装(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，支持ML-KEM算法的密钥封装解封装，对应的算法规格请查看[密钥封装解封装算法规格](#算法规格)。

ML-KEM（Module-Lattice-Based Key-Encapsulation Mechanism）是一种基于格的后量子密钥封装机制，用于在不安全的通道上安全地协商共享密钥。封装方使用公钥生成共享密钥和封装密钥，解封装方使用私钥和封装密钥恢复出相同的共享密钥。

## 算法规格

| 算法   | 字符串参数   | API版本 |
| ------ | ------------ | ------- |
| ML-KEM | ML_KEM_512   | 26.0.0+ |
| ML-KEM | ML_KEM_768   | 26.0.0+ |
| ML-KEM | ML_KEM_1024  | 26.0.0+ |

## 开发步骤

**封装**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)和[AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1)，生成密钥算法为ML-KEM的非对称密钥（KeyPair）。

2. 调用[cryptoFramework.createKem](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekem)，指定算法参数为KemAlgNameId.ML_KEM_768，创建Kem实例。

3. 调用[Kem.encapsulate](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#encapsulate)，基于传入的公钥（KeyPair.pubKey）进行密钥封装，返回封装结果（[KemEncapResult](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#kemencapresult)）。

   [KemEncapResult](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#kemencapresult)包含sharedSecret（共享密钥）和wrappedKey（封装密钥）。封装方保留sharedSecret，将wrappedKey发送给解封装方。ikme参数传入null时，由算法库内部随机生成临时密钥。

**解封装**

1. 调用[cryptoFramework.createKem](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekem)，指定算法参数为KemAlgNameId.ML_KEM_768，创建Kem实例。

2. 调用[Kem.decapsulate](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#decapsulate)，基于传入的私钥（KeyPair.priKey）和封装密钥（wrappedKey）进行密钥解封装，返回共享密钥。

   解封装得到的共享密钥应与封装时生成的sharedSecret一致。

## 开发示例

- 异步方法示例：

  <!-- @[kem_encapsulate_decapsulate_await_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KemEncapsulateDecapsulate/entry/src/main/ets/pages/Await.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  namespace Kem {
    export async function kemDecapsulateAwait() {
      let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
      let keyPair = await asyKeyGenerator.generateKeyPair();
      let kem : cryptoFramework.Kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
      try {
        let encapResult : cryptoFramework.KemEncapResult = await kem.encapsulate(keyPair.pubKey, null);
        let sharedSecret : Uint8Array = await kem.decapsulate(keyPair.priKey, encapResult.wrappedKey);
        console.info('decapsulate success');
        console.info('sharedSecret length: ' + sharedSecret.length);
        return 'Success';
      } catch (err) {
        let e: BusinessError = err as BusinessError;
        console.error(`decapsulate failed: errCode: ${e.code}, errMsg: ${e.message}`);
        return 'Failed';
      }
    }
  }
  ```


- 同步方法示例：

  <!-- @[kem_encapsulate_decapsulate_sync_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KemEncapsulateDecapsulate/entry/src/main/ets/pages/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  namespace Kem {
    export function kemDecapsulateSync() {
      let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
      let keyPair = asyKeyGenerator.generateKeyPairSync();
      let kem : cryptoFramework.Kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
      try {
        let encapResult : cryptoFramework.KemEncapResult= kem.encapsulateSync(keyPair.pubKey, null);
        let sharedSecret : Uint8Array = kem.decapsulateSync(keyPair.priKey, encapResult.wrappedKey);
        console.info('decapsulateSync success');
        console.info('sharedSecret length: ' + sharedSecret.length);
        return 'Success';
      } catch (err) {
        let e: BusinessError = err as BusinessError;
        console.error(`decapsulateSync failed: errCode: ${e.code}, errMsg: ${e.message}`);
        return 'Failed';
      }
    }
  }
  ```
