# 使用ML-DSA密钥对签名验签(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，签名验签支持ML-DSA算法。对应的算法规格请查看[签名验签算法规格：ML-DSA](crypto-sign-sig-verify-overview.md#ml-dsa)。

**签名**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)、[AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1)，生成非对称密钥算法为ML-DSA的密钥对（KeyPair）。

2. 调用[cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign)，指定字符串参数'ML-DSA'，创建非对称密钥类型为ML-DSA的Sign实例，用于完成签名操作。

3. （可选）调用[Sign.setSignSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setsignspec)，设置ML-DSA签名参数，如确定性签名（ML_DSA_DETERMINISTIC_BOOL）、外部μ哈希模式（ML_DSA_MU_BOOL）或上下文字符串（ML_DSA_CONTEXT_UINT8ARR），当设置外部μ哈希模式（ML_DSA_MU_BOOL）为true时，上下文字符串（ML_DSA_CONTEXT_UINT8ARR）无效。

4. 调用[Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3)，使用私钥（PriKey）初始化Sign实例。

   ML-DSA签名算法不支持update接口。

5. 调用[Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1)，生成数据签名。

**验签**

1. 调用[cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify)，指定字符串参数'ML-DSA'，创建非对称密钥类型为ML-DSA的Verify实例，用于完成验签操作。

2. （可选）调用[Verify.setVerifySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setverifyspec)，设置ML-DSA验签参数，如外部μ哈希模式（ML_DSA_MU_BOOL）或上下文字符串（ML_DSA_CONTEXT_UINT8ARR）。验签的参数应当与签名的参数保持一致，验签时无需设置确定性签名（ML_DSA_DETERMINISTIC_BOOL）。

3. 调用[Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5)，使用公钥（PubKey）初始化Verify实例。

   ML-DSA验签算法不支持update接口。

4. 调用[Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1)，对数据进行验签。

- 异步方法示例：

  <!-- @[signature_verification_with_ml_dsa_key_pair_ark_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/ml_dsa_signature_verification/ml_dsa_signature_verification_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let input: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan', 'utf-8').buffer) };
  let context: Uint8Array = new Uint8Array(buffer.from('test', 'utf-8').buffer);
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey) {
    let signer = cryptoFramework.createSign('ML-DSA');
    signer.setSignSpec(cryptoFramework.SignSpecItem.ML_DSA_DETERMINISTIC_BOOL, true);
    signer.setSignSpec(cryptoFramework.SignSpecItem.ML_DSA_CONTEXT_UINT8ARR, context);
    await signer.init(priKey);
    let signData = await signer.sign(input);
    return signData;
  }
  
  async function verifyMessagePromise(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifier = cryptoFramework.createVerify('ML-DSA');
    verifier.setVerifySpec(cryptoFramework.SignSpecItem.ML_DSA_CONTEXT_UINT8ARR, context);
    await verifier.init(pubKey);
    let res = await verifier.verify(input, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function main() {
    try {
      let generator = cryptoFramework.createAsyKeyGenerator('ML-DSA-87');
      let keyPair = await generator.generateKeyPair();
      let signData = await signMessagePromise(keyPair.priKey);
      let verifyResult = await verifyMessagePromise(signData, keyPair.pubKey);
      if (verifyResult === true) {
        console.info('verify result: success.');
        return 'Success';
      } else {
        console.error('verify result: failed.');
        return 'Fail';
      }
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`verify failed: errCode: ${e.code}, errMessage: ${e.message}`);
      return 'Fail';
    }
  }
  ```

- 同步方法示例：

  <!-- @[signature_verification_with_ml_dsa_key_pair_ark_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/ml_dsa_signature_verification/ml_dsa_signature_verification_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let input: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan', 'utf-8').buffer) };
  let context: Uint8Array = new Uint8Array(buffer.from('test', 'utf-8').buffer);
  
  function signMessageSync(priKey: cryptoFramework.PriKey) {
    let signer = cryptoFramework.createSign('ML-DSA');
    signer.setSignSpec(cryptoFramework.SignSpecItem.ML_DSA_DETERMINISTIC_BOOL, true);
    signer.setSignSpec(cryptoFramework.SignSpecItem.ML_DSA_CONTEXT_UINT8ARR, context);
    signer.initSync(priKey);
    let signData = signer.signSync(input);
    return signData;
  }
  
  function verifyMessageSync(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifier = cryptoFramework.createVerify('ML-DSA');
    verifier.setVerifySpec(cryptoFramework.SignSpecItem.ML_DSA_CONTEXT_UINT8ARR, context);
    verifier.initSync(pubKey);
    let res = verifier.verifySync(input, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function main() {
    try {
      let generator = cryptoFramework.createAsyKeyGenerator('ML-DSA-87');
      let keyPair = generator.generateKeyPairSync();
      let signData = signMessageSync(keyPair.priKey);
      let verifyResult = verifyMessageSync(signData, keyPair.pubKey);
      if (verifyResult === true) {
        console.info('verify result: success.');
        return 'Success';
      } else {
        console.error('verify result: failed.');
        return 'Fail';
      }
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`verify failed: errCode: ${e.code}, errMessage: ${e.message}`);
      return 'Fail';
    }
  }
  ```
