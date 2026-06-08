# Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode) (OnlySign and OnlyVerify Modes) (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

Signature verification supports the OnlyVerify mode since API version 26.0.0. For details about the algorithm specifications, see [Signing and Signature Verification Overview and Algorithm Specifications: RSA](crypto-sign-sig-verify-overview.md#rsa).

**Signing**

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) with the MD algorithm **SHA256** to create a message digest (**Md**) instance.

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6) to pass a custom message to perform digest update calculation. There is not limit on the size of data to be passed in a single update.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest) to obtain the digest calcuation result.

4. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate a 1024-bit RSA key pair (**KeyPair**) with two primes. The **KeyPair** instance consists of a public key (**PubKey**) and a private key (**PriKey**).

   In addition to the example in this topic, [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-asym-key-generation-conversion-spec.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md) may help you better understand how to generate an RSA asymmetric key pair. Note that the input parameters in the reference documents may be different from those in the example below.

5. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) with the string parameter **'RSA1024|PKCS1|SHA256|OnlySign'** to create a **Sign** instance. The asymmetric key type is **RSA1024**, the padding mode is **PKCS1**, and the MD algorithm is **SHA256**.

6. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the **Sign** instance with the private key (**PriKey**).

7. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate a digest signature.

**Signature verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) with the string parameter **'RSA1024|PKCS1|SHA256|OnlyVerify'** to create a **Verify** instance. The key parameters must be the same as that used to create the **Sign** instance.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the **Verify** instance using the public key (**PubKey**).

3. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the digest signature.

- Example (using asynchronous APIs):

  <!-- @[rsa_pkcs1_onlysign_onlyverify_signature_validator_asynchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/rsa_pkcs1_onlysign_onlyverify_signature_validator_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'RSA1024|PKCS1|SHA256|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    let signData = await signer.sign(digestBlob);
    return signData;
  }
  
  async function verifyMessagePromise(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    let res = await verifier.verify(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is rsa onlySign test', 'utf-8').buffer) };
    // Use MD to calculate the SHA-256 digest (32 bytes) first.
    let md = cryptoFramework.createMd('SHA256');
    await md.update(messageData);
    let digestBlob = await md.digest();
    let keyGenAlg = 'RSA1024';
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

  <!-- @[rsa_pkcs1_onlysign_onlyverify_signature_validator_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/rsa_pkcs1_onlysign_onlyverify_signature_validator_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function signMessagePromise(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'RSA1024|PKCS1|SHA256|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let signData = signer.signSync(digestBlob);
    return signData;
  }
  
  function verifyMessagePromise(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    let res = verifier.verifySync(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is rsa onlySign test', 'utf-8').buffer) };
    // Use MD to calculate the SHA-256 digest (32 bytes) first.
    let md = cryptoFramework.createMd('SHA256');
    md.updateSync(messageData);
    let digestBlob = md.digestSync();
    let keyGenAlg = 'RSA1024';
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
