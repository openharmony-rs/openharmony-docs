# Signing and Verification with the ECC Key Pair (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=71a9c24c930904b17deb97103d1dfffd94b342e3 translatedAt=2026-08-07T03:27:28.414Z pushedAt=2026-08-10T08:16:26.338Z -->

## OnlySign and OnlyVerify Modes

Signing and signature verification supports the **OnlySign** and **OnlyVerify** mode since API version 26.0.0. For details about the algorithm specifications, see [ECDSA](crypto-sign-sig-verify-overview.md#ecdsa).

**Signing**

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) with the digest algorithm **SHA1** to create a message digest (**Md**) instance.

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6) to pass a custom message to perform digest update calculation. There is no limit on the size of data to be passed in a single update.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest) to obtain the digest calculation result.

4. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair), which includes a public key (**PubKey**) and a private key (**PriKey**). The key algorithm is **ECC** and curve type is **ECC224**.

To learn how to generate an ECC asymmetric key pair, refer to the following example and also see [Asymmetric Key Generation and Conversion Specifications: ECC](crypto-key-generation-conversion.md#ecc) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters.

5. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) with the string parameter **'ECC|SHA1|OnlySign'** to create a **Sign** instance. The asymmetric key type is **ECC**, digest algorithm is **SHA1**, and signature mode is **OnlySign**.

6. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the **Sign** instance with the private key (**PriKey**).

7. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate a digest signature.

**Signature Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) with the string parameter **'ECC|SHA1|OnlyVerify'** to create a **Verify** instance. The asymmetric key type is **ECC**, digest algorithm is **SHA1**, and signature verification mode is **OnlyVerify**.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the **Verify** instance using the public key (**PubKey**).

3. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the digest signature.

- Example (using asynchronous APIs):

  <!-- @[ecc_onlysign_onlyverify_signature_verification_asynchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/ecc_onlysign_onlyverify_signature_verification_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'ECC|SHA1|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    let signData = await signer.sign(digestBlob);
    return signData;
  }
  
  async function verifyMessagePromise(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'ECC|SHA1|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    let res = await verifier.verify(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is ecc onlySign test', 'utf-8').buffer) };
    // Use Md to compute the SHA1 digest (20 bytes).
    let md = cryptoFramework.createMd('SHA1');
    await md.update(messageData);
    let digestBlob = await md.digest();
    let keyGenAlg = 'ECC224';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = await generator.generateKeyPair();
    let signData = await signMessagePromise(keyPair.priKey, digestBlob);
    let verifyResult = await verifyMessagePromise(digestBlob, signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

- Example (using synchronous APIs):

  <!-- @[ecc_onlysign_onlyverify_signature_verification_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/ecc_onlysign_onlyverify_signature_verification_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function signMessagePromise(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'ECC|SHA1|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let signData = signer.signSync(digestBlob);
    return signData;
  }
  
  function verifyMessagePromise(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'ECC|SHA1|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    let res = verifier.verifySync(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is ecc onlySign test', 'utf-8').buffer) };
    let md = cryptoFramework.createMd('SHA1');
    md.updateSync(messageData);
    let digestBlob = md.digestSync();
    let keyGenAlg = 'ECC224';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let signData = signMessagePromise(keyPair.priKey, digestBlob);
    let verifyResult = verifyMessagePromise(digestBlob, signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```
  
  <!--no_check-->