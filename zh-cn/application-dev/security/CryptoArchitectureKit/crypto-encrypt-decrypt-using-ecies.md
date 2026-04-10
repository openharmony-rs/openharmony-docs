# 使用ECIES混合加解密(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API版本23开始，支持ECIES算法，ECIES是一种基于椭圆曲线密码学的加密算法。

**约束条件：**

- 密钥协商算法支持ECC256、ECC384、ECC521。
- 密钥派生算法仅支持X963KDF，摘要算法支持SHA1、SHA256、SHA384、SHA512。
- 对称加密算法支持AES128、AES192、AES256。
- 分组模式仅支持GCM。

**加密**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)、[SymKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair)，使用ECC算法生成密钥对。

2. 调用[cryptoFramework.createKeyAgreement](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekeyagreement)、[KeyAgreement.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11)，基于传入的私钥（KeyPair.priKey）与公钥（KeyPair.pubKey）进行密钥协商，返回共享密钥。

3. X963KDF密钥派生，调用[cryptoFramework.createKdf](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekdf11)、[Kdf.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11)，基于传入的密钥协商结果（Secret）进行密钥派生，返回派生后的密钥。

4. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'AES128|GCM'，创建对称密钥类型为AES128、分组模式为GCM的Cipher实例，用于完成加密操作。

5. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为加密（CryptoMode.ENCRYPT_MODE），指定加密密钥（SymKey）和GCM模式对应的加密参数（GcmParamsSpec），初始化加密Cipher实例。

6. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（明文）。

7. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取加密后的数据。

8. 读取[GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag作为解密的认证信息。

**解密**

1. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'AES128|GCM'，创建对称密钥类型为AES128、分组模式为GCM的Cipher实例，用于完成解密操作。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为解密（CryptoMode.DECRYPT_MODE），指定解密密钥（SymKey）和GCM模式对应的解密参数（GcmParamsSpec），初始化解密Cipher实例。

3. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（密文）。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取解密后的数据。

- 异步方法示例：

  <!-- @[use_sample_await_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/ets/pages/Await.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  namespace ECIES {
    export async function genGcmParamsSpec() {
      let ivBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B]), // 12 bytes
      }
      let aadBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07]),
      }
      let tagBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([
          0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F
        ]), // 16 bytes
      }
      // GCM的authTag在加密时从doFinal结果中获取，在解密时填入init函数的params参数中
      let gcmParams: cryptoFramework.GcmParamsSpec = {
        iv: ivBlob,
        aad: aadBlob,
        authTag: tagBlob,
        algName: 'GcmParamsSpec',
      }
      return gcmParams;
    }
  
    export async function genSymKey() {
      // 生成EC密钥
      let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
      let keyPair: cryptoFramework.KeyPair = await asyKeyGenerator.generateKeyPair();
      // EC密钥协商
      let agreement: cryptoFramework.KeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
      let keyData: cryptoFramework.DataBlob = await agreement.generateSecret(keyPair.priKey, keyPair.pubKey);
  
      let infoData: Uint8Array = new Uint8Array(buffer.from('infostring', 'utf-8').buffer);
      let spec: cryptoFramework.X963KdfSpec = {
        algName: 'X963KDF',
        key: keyData.data,
        info: infoData,
        keySize: 16
      }
  
      // 使用X963KDF进行密钥派生
      let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
      let secret = await kdf.generateSecret(spec);
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
      let symKey: cryptoFramework.SymKey = symKeyGenerator.convertKeySync(secret);
      return symKey;
    }
  
    export async function encrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      plainText: cryptoFramework.DataBlob) {
      // AES-GCM对称加密
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
      let cipherText: cryptoFramework.DataBlob = await cipher.update(plainText);
      gcmParams.authTag = await cipher.doFinal(null);
      return cipherText;
    }
  
    export async function decrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      cipherText: cryptoFramework.DataBlob) {
      // AES-GCM对称解密
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      await cipher.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
      let plainText: cryptoFramework.DataBlob = await cipher.update(cipherText);
      return plainText;
    }
  }
  
  async function testEciesEncryptDecrypt() {
    let symKey: cryptoFramework.SymKey = await ECIES.genSymKey();
    let gcmParams: cryptoFramework.GcmParamsSpec = await ECIES.genGcmParamsSpec();
    let message: string = 'This is a test message!!!';
    let plainText: cryptoFramework.DataBlob = {
      data: new Uint8Array(buffer.from(message, 'utf-8').buffer),
    }
    let cipherData: cryptoFramework.DataBlob = await ECIES.encrypt(symKey, gcmParams, plainText);
    let plainData: cryptoFramework.DataBlob = await ECIES.decrypt(symKey, gcmParams, cipherData);
    console.info('message: ' + buffer.from(plainData.data).toString('utf-8'));
  }
  ```

- 同步方法示例：

  <!-- @[use_sample_sync_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/ets/pages/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  namespace ECIES {
    export function genGcmParamsSpec() {
      let ivBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B]), // 12 bytes
      }
      let aadBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07]),
      }
      let tagBlob: cryptoFramework.DataBlob = {
        data: new Uint8Array([
          0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F
        ]), // 16 bytes
      }
      // GCM的authTag在加密时从doFinal结果中获取，在解密时填入init函数的params参数中
      let gcmParams: cryptoFramework.GcmParamsSpec = {
        iv: ivBlob,
        aad: aadBlob,
        authTag: tagBlob,
        algName: 'GcmParamsSpec',
      }
      return gcmParams;
    }
  
    export function genSymKey() {
      // 生成EC密钥
      let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
      let keyPair: cryptoFramework.KeyPair = asyKeyGenerator.generateKeyPairSync();
      // EC密钥协商
      let agreement: cryptoFramework.KeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
      let keyData: cryptoFramework.DataBlob = agreement.generateSecretSync(keyPair.priKey, keyPair.pubKey);
  
      let infoData: Uint8Array = new Uint8Array(buffer.from('infostring', 'utf-8').buffer);
      let spec: cryptoFramework.X963KdfSpec = {
        algName: 'X963KDF',
        key: keyData.data,
        info: infoData,
        keySize: 16
      }
  
      // 使用X963KDF进行密钥派生
      let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
      let secret = kdf.generateSecretSync(spec);
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
      let symKey: cryptoFramework.SymKey = symKeyGenerator.convertKeySync(secret);
      return symKey;
    }
  
    export function encrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      plainText: cryptoFramework.DataBlob) {
      // AES-GCM对称加密
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
      let cipherText: cryptoFramework.DataBlob = cipher.updateSync(plainText);
      gcmParams.authTag = cipher.doFinalSync(null);
      return cipherText;
    }
  
    export function decrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      cipherText: cryptoFramework.DataBlob) {
      // AES-GCM对称解密
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      cipher.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
      let plainText: cryptoFramework.DataBlob = cipher.updateSync(cipherText);
      return plainText;
    }
  }
  
  function testEciesEncryptDecrypt() {
    let symKey: cryptoFramework.SymKey = ECIES.genSymKey();
    let gcmParams: cryptoFramework.GcmParamsSpec = ECIES.genGcmParamsSpec();
    let message: string = 'This is a test message!!!';
    let plainText: cryptoFramework.DataBlob = {
      data: new Uint8Array(buffer.from(message, 'utf-8').buffer),
    }
    let cipherData: cryptoFramework.DataBlob = ECIES.encrypt(symKey, gcmParams, plainText);
    let plainData: cryptoFramework.DataBlob = ECIES.decrypt(symKey, gcmParams, cipherData);
    console.info('message: ' + buffer.from(plainData.data).toString('utf-8'));
  }
  ```
