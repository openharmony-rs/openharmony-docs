# Signing and Signature Verification with an RSA Key Pair (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=e80025ed82ed281bac11c255d720292d542f564f translatedAt=2026-08-31T02:35:39.901Z pushedAt=2026-08-31T09:22:56.959Z -->

For the corresponding algorithm specifications, see [Signing and Signature Verification Algorithm Specifications: RSA](crypto-sign-sig-verify-overview.md#rsa).

## Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode)

**Signing**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair) with the RSA algorithm, a key length of 1024 bits, and two prime numbers. The KeyPair includes a public key (PubKey) and a private key (PriKey).

   To learn how to generate an RSA asymmetric key pair, refer to the following example together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters, so read them carefully to distinguish the differences.

2. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter `'RSA1024|PKCS1|SHA256'` to create a Sign instance with the asymmetric key type RSA1024, the padding mode PKCS1, and the digest algorithm SHA256 for signing.

3. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the Sign instance with the private key (PriKey).

4. Call [Sign.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-3) to pass in the data to be signed.

   There is no limit on the length of a single update. You can decide how to call update based on the amount of data.

   - When the data to be signed is short, you can call sign directly after init is complete.
   - When the amount of data is large, you can call update multiple times, that is, [Segmented Signing and Signature Verification](crypto-rsa-sign-sig-verify.md#signing-and-signature-verification-with-an-rsa-key-pair-pkcs1-mode-in-segments).

5. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate a data signature.

**Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify), specify the string parameter 'RSA1024|PKCS1|SHA256', which must be consistent with the Sign instance used for signing. Create a Verify instance to complete the verification operation.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the Verify instance with the public key (PubKey).

3. Call [Verify.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-5) to pass in the data to be verified.

   Currently, there is no limit on the length of a single update call. You can determine how to call update based on the data volume.

   - When the data to be signed is short, you can call verify directly after init is complete.
   - When the data volume is large, you can call update multiple times, that is, [segment signature verification](crypto-rsa-sign-sig-verify.md#signing-and-signature-verification-with-an-rsa-key-pair-pkcs1-mode-in-segments).

4. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the data.

- Asynchronous method example:

  <!-- @[pkcs1_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_validator/rsa_pkcs1_signature_validator_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // The complete plaintext is split into input1 and input2.
  let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  let input2: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan2', 'utf-8').buffer) };
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey) {
    let signAlg = 'RSA1024|PKCS1|SHA256';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    await signer.update(input1); // If the plaintext is short, call the sign API to pass it in at once.
    let signData = await signer.sign(input2);
    return signData;
  }
  
  async function verifyMessagePromise(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    await verifier.update(input1); // If the plaintext is short, call the verify API to pass it in at once.
    let res = await verifier.verify(input2, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function main() {
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = await generator.generateKeyPair();
    let signData = await signMessagePromise(keyPair.priKey);
    let verifyResult = await verifyMessagePromise(signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

- Synchronous method example:

  <!-- @[pkcs1_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_validator/rsa_pkcs1_signature_validator_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // The complete plaintext is split into input1 and input2.
  let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  let input2: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan2', 'utf-8').buffer) };
  
  function signMessageSync(priKey: cryptoFramework.PriKey) {
    let signAlg = 'RSA1024|PKCS1|SHA256';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    signer.updateSync(input1); // If the plaintext is short, call the sign API to pass it in at once.
    let signData = signer.signSync(input2);
    return signData;
  }
  
  function verifyMessageSync(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    verifier.updateSync(input1); // If the plaintext is short, call the verify API to pass it in at once.
    let res = verifier.verifySync(input2, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function main() {
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let signData = signMessageSync(keyPair.priKey);
    let verifyResult = verifyMessageSync(signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

## Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode) (OnlySign and OnlyVerify Modes)

Starting from API version 26.0.0, signing and signature verification support the OnlyVerify mode.

**Signing**

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) and specify the digest algorithm SHA256 to create a digest instance (Md).

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6) and pass in a custom message to update the digest calculation. There is no limit on the length of a single update.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest) to obtain the digest calculation result.

4. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair) with the RSA algorithm, a key length of 1024 bits, and two prime numbers, including a public key (PubKey) and a private key (PriKey).

   For details about how to generate an RSA asymmetric key, refer to the following example, together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the input parameters in the reference documents may differ from those in the current example.

5. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter 'RSA1024|PKCS1|SHA256|OnlySign' to create a Sign instance with the asymmetric key type RSA1024, the padding mode PKCS1, and the digest algorithm SHA256 for signing.

6. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the Sign instance with the private key (PriKey).

7. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate a signature for the digest data.

**Verify**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) and specify the string parameter 'RSA1024|PKCS1|SHA256|OnlyVerify', which must be consistent with the Sign instance used for signing. Create a Verify instance to complete the signature verification.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the Verify instance with the public key (PubKey).

3. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the digest data.

- Asynchronous method example:

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
    // First use Md to compute the SHA256 digest (32 bytes).
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

- Synchronous method example:

  <!-- @[rsa_pkcs1_onlysign_onlyverify_signature_validator_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/rsa_pkcs1_onlysign_onlyverify_signature_validator_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function signMessageSync(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'RSA1024|PKCS1|SHA256|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let signData = signer.signSync(digestBlob);
    return signData;
  }
  
  function verifyMessageSync(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
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
    // First use Md to compute the SHA256 digest (32 bytes).
    let md = cryptoFramework.createMd('SHA256');
    md.updateSync(messageData);
    let digestBlob = md.digestSync();
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let signData = signMessageSync(keyPair.priKey, digestBlob);
    let verifyResult = verifyMessageSync(digestBlob, signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

## Signing and Signature Recovery with an RSA Key Pair (PKCS1 Mode)

**Signing**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair) with the RSA algorithm, a key length of 1024 bits, and two prime numbers. The KeyPair includes a public key (PubKey) and a private key (PriKey).

   To generate an RSA asymmetric key pair, refer to the following example and understand it together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). The referenced documents may differ from the current example in input parameters, so pay attention to the differences when reading them.

2. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter 'RSA1024|PKCS1|NoHash|OnlySign' to create a Sign instance with the asymmetric key type RSA1024, the padding mode PKCS1, and the signing mode OnlySign, for performing sign-only operations.

3. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the Sign instance with the private key (PriKey).

4. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate the data signature.

**Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) and specify the string parameter 'RSA1024|PKCS1|NoHash|Recover', which must be consistent with the Sign instance used for signing. Create a Verify instance for performing verification operations.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the Verify instance with the public key (PubKey).

3. Call [Verify.recover](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#recover12) to recover the signature from the data.

- Asynchronous method example:

  <!-- @[pkcs1_recover_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_restoration/rsa_pkcs1_signature_restoration_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // The complete plaintext is split into input1 and input2.
  let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey) {
    let signAlg = 'RSA1024|PKCS1|NoHash|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    let signData = await signer.sign(input1);
    return signData;
  }
  
  async function verifyMessagePromise(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|NoHash|Recover';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    let rawSignData = await verifier.recover(signMessageBlob);
    return rawSignData;
  }
  
  async function main() {
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = await generator.generateKeyPair();
    let signData = await signMessagePromise(keyPair.priKey);
    let rawSignData = await verifyMessagePromise(signData, keyPair.pubKey);
    if (rawSignData != null) {
      console.info('recover result: ' + rawSignData.data);
    } else {
      console.error('get verify recover result: fail!');
    }
  }
  ```

- Synchronous method example:

  <!-- @[pkcs1_recover_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_restoration/rsa_pkcs1_signature_restoration_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // The complete plaintext is split into input1 and input2.
  let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  
  function signMessageSync(priKey: cryptoFramework.PriKey) {
    let signAlg = 'RSA1024|PKCS1|NoHash|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let signData = signer.signSync(input1);
    return signData;
  }
  
  function verifyMessageSync(signMessageBlob: cryptoFramework.DataBlob, pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA1024|PKCS1|NoHash|Recover';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    let rawSignData = verifier.recoverSync(signMessageBlob);
    return rawSignData;
  }
  
  function main() {
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let signData = signMessageSync(keyPair.priKey);
    let rawSignData = verifyMessageSync(signData, keyPair.pubKey);
    if (rawSignData != null) {
      console.info('recover result: ' + rawSignData.data);
    } else {
      console.error('get verify recover result: fail!');
    }
  }
  ```

## Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode) in Segments

**Signing**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair) with the RSA algorithm, a key length of 1024 bits, and two prime numbers. The KeyPair includes a public key (PubKey) and a private key (PriKey).

   For details about how to generate an RSA asymmetric key pair, refer to the following example, together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the input parameters in the reference documents may differ from those in this example.

2. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter 'RSA1024|PKCS1|SHA256' to create a Sign instance with the asymmetric key type RSA1024, the padding mode PKCS1, and the digest algorithm SHA256 for signing.

3. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the Sign instance with the private key (PriKey).

4. Set the amount of data passed at a time to 64 bytes, and call [Sign.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-3) multiple times to pass in the data to be signed. There is no limit on the length of a single update call. You can determine how to call update based on the data volume.

5. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate the data signature.

**Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) and specify the string parameter 'RSA1024|PKCS1|SHA256', which must be consistent with the Sign instance used for signing. This creates a Verify instance for signature verification.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the Verify instance with the public key (PubKey).

3. Call [Verify.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-5) to pass in the data to be verified. There is no limit on the length of a single update. You can determine how to call update based on the data volume.

4. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the signature of the data.

- Asynchronous method example:

  <!-- @[pkcs1_seg_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_segment_signature/rsa_pkcs1_segment_signature_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  async function signMessageBySegment(priKey: cryptoFramework.PriKey, plainText: Uint8Array) {
    let signAlg = 'RSA1024|PKCS1|SHA256';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    let textSplitLen = 64; // Custom data split length, set to 64 here.
    for (let i = 0; i < plainText.length; i += textSplitLen) {
      let updateMessage = plainText.subarray(i, i + textSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      await signer.update(updateMessageBlob);
    }
    // All plaintext has been passed in segments, so pass null to sign here.
    let signData = await signer.sign(null);
    return signData;
  }
  
  async function verifyMessageBySegment(pubKey: cryptoFramework.PubKey, plainText: Uint8Array,
    signMessageBlob: cryptoFramework.DataBlob) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    let textSplitLen = 64; // Custom data split length, set to 64 here.
    for (let i = 0; i < plainText.length; i += textSplitLen) {
      let updateMessage = plainText.subarray(i, i + textSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      await verifier.update(updateMessageBlob);
    }
    // All plaintext has been passed in segments, so pass null as the first parameter of verify here.
    let res = await verifier.verify(null, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function rsaSignatureBySegment() {
    let message = 'This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!';
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = await generator.generateKeyPair();
    let messageData = new Uint8Array(buffer.from(message, 'utf-8').buffer);
    let signData = await signMessageBySegment(keyPair.priKey, messageData);
    let verifyResult = await verifyMessageBySegment(keyPair.pubKey, messageData, signData);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

- Synchronous method example:

  <!-- @[pkcs1_seg_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_segment_signature/rsa_pkcs1_segment_signature_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function signMessageBySegment(priKey: cryptoFramework.PriKey, plainText: Uint8Array) {
    let signAlg = 'RSA1024|PKCS1|SHA256';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let textSplitLen = 64; // Custom data split length, set to 64 here.
    for (let i = 0; i < plainText.length; i += textSplitLen) {
      let updateMessage = plainText.subarray(i, i + textSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      signer.updateSync(updateMessageBlob);
    }
    // All plaintext has been passed in segments, so pass null to sign here.
    let signData = signer.signSync(null);
    return signData;
  }
  
  function verifyMessageBySegment(pubKey: cryptoFramework.PubKey, plainText: Uint8Array,
    signMessageBlob: cryptoFramework.DataBlob) {
    let verifyAlg = 'RSA1024|PKCS1|SHA256';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    let textSplitLen = 64; // Custom data split length, set to 64 here.
    for (let i = 0; i < plainText.length; i += textSplitLen) {
      let updateMessage = plainText.subarray(i, i + textSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      verifier.updateSync(updateMessageBlob);
    }
    // All plaintext has been passed in segments, so pass null as the first parameter of verify here.
    let res = verifier.verifySync(null, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function rsaSignatureBySegment() {
    let message = 'This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!';
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let messageData = new Uint8Array(buffer.from(message, 'utf-8').buffer);
    let signData = signMessageBySegment(keyPair.priKey, messageData);
    let verifyResult = verifyMessageBySegment(keyPair.pubKey, messageData, signData);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

## Signing and Signature Verification with an RSA Key Pair (PSS Mode)

**Signing**

1. Call [cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10) and [AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10), and specify the key parameters to generate an RSA asymmetric key pair (KeyPair).

   To generate an RSA asymmetric key, refer to the following example together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Generating an Asymmetric Key Pair from Key Specifications](crypto-generate-asym-key-pair-from-key-spec.md). Note that the input parameters in the reference documents may differ from those in the current example.

2. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter `'RSA|PSS|SHA256|MGF1_SHA256'` to create a `Sign` instance whose asymmetric key type is RSA without a length, padding mode is PSS, digest algorithm is SHA256, and mask algorithm is MGF1_SHA256, for signing.

3. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) to initialize the `Sign` instance with the private key (PriKey).

4. Call [Sign.setSignSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setsignspec10) to set the signing parameters. Here, set the salt length (`SignSpecItem.PSS_SALT_LEN_NUM`) to 32 bytes. This value is verified during signature verification.

5. Call [Sign.getSignSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getsignspec10) to obtain other signing parameters.

6. Call [Sign.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-3) to pass in the data to be signed. There is no limit on the length of a single `update` call. You can decide how to call `update` based on the data volume.

7. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate the data signature.

**Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) with the string parameter `'RSA2048|PSS|SHA256|MGF1_SHA256'` to create a `Verify` instance with the asymmetric key type `RSA2048`, padding mode `PSS`, digest algorithm `SHA256`, and mask algorithm `MGF1_SHA256` for the verification operation.

2. Call [Verify.setVerifySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setverifyspec10) to set the signing parameters. They must be consistent with those set during signing.

3. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the `Verify` instance with the public key (`PubKey`).

4. Call [Verify.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-5) to pass in the data to be verified. There is no limit on the length of a single `update` call. You can determine how to call `update` based on the data volume.

5. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the data.

- Asynchronous method example:

  <!-- @[pss_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pss_signature_verification/rsa_pss_signature_verification_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Construct RSA asymmetric key pair parameters based on the key parameter properties.
  function genRsaKeyPairSpec(nIn: bigint, eIn: bigint, dIn: bigint) {
    let rsaCommSpec: cryptoFramework.RSACommonParamsSpec = {
      n: nIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC
    };
    let rsaKeyPairSpec: cryptoFramework.RSAKeyPairSpec = {
      params: rsaCommSpec,
      sk: dIn,
      pk: eIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC
    };
    return rsaKeyPairSpec;
  }
  
  // Generate RSA2048 key pair parameters.
  function genRsa2048KeyPairSpec(): cryptoFramework.RSAKeyPairSpec {
    let nIn =
      BigInt('0x9260d0750ae117eee55c3f3deaba74917521a262ee76007cdf8a56755ad73a1598a1408410a01434c3f5bc54a88b57fa19fc432' +
        '8daea0750a4c44e88cff3b2382621b80f670464433e4336e6d003e8cd65bff211da144b88291c2259a00a72b711c116ef7686e8fee34e4' +
        'd933c868187bdc26f7be071493c86f7a5941c3510806ad67b0f94d88f5cf5c02a092821d8626e8932b65c5bd8c92049c210932b7afa7ac' +
        '59c0e886ae5c1edb00d8ce2c57633db26bd6639bff73cee82be9275c402b4cf2a4388da8cf8c64eefe1c5a0f5ab8057c39fa5c0589c3e2' +
        '53f0960332300f94bea44877b588e1edbde97cf2360727a09b775262d7ee552b3319b9266f05a25');
    let eIn = BigInt('0x010001');
    let dIn =
      BigInt('0x6a7df2ca63ead4dda191d614b6b385e0d9056a3d6d5cfe07db1daabee022db08212d97613d3328e0267c9dd23d787abde2afcb3' +
        '06aeb7dfce69246cc73f5c87fdf06030179a2114b767db1f083ff841c025d7dc00cd82435b9a90f695369e94df23d2ce458bc3b3283ad8' +
        'bba2b8fa1ba62e2dce9accff3799aae7c840016f3ba8e0048c0b6cc4339af7161003a5beb864a0164b2c1c9237b64bc87556994351b275' +
        '06c33d4bcdfce0f9c491a7d6b0628c7c852be4f0a9c3132b2ed3a2c8881e9aab07e20e17deb074691be677776a78b5c502e05d9bdde721' +
        '26b3738695e2dd1a0a98a14247c65d8a7ee79432a092cb0721a12df798e44f7cfce0c498147a9b1');
    return genRsaKeyPairSpec(nIn, eIn, dIn);
  }
  
  async function verifyMessagePSS() {
    // The complete plaintext is split into input1 and input2.
    let messagePart1 = 'This is Sign test plan1';
    let messagePart2 = 'This is Sign test plan2';
    let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(messagePart1, 'utf-8').buffer) };
    let input2: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(messagePart2, 'utf-8').buffer) };
    // Obtain the RSA key pair parameter object.
    let rsaKeyPairSpec = genRsa2048KeyPairSpec();
    // Create the RSA key pair generator.
    let rsaGeneratorSpec = cryptoFramework.createAsyKeyGeneratorBySpec(rsaKeyPairSpec);
    // Both sign and verify support RSA keys with or without a length.
    let signer = cryptoFramework.createSign('RSA|PSS|SHA256|MGF1_SHA256');
    let verifier = cryptoFramework.createVerify('RSA2048|PSS|SHA256|MGF1_SHA256');
    let keyPair = await rsaGeneratorSpec.generateKeyPair();
    await signer.init(keyPair.priKey);
    // After sign initialization, set and get the PSS parameters.
    let setN = 32;
    signer.setSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
    let saltLen = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
    console.info('SaltLen: ' + saltLen);
    let tf = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_TRAILER_FIELD_NUM);
    console.info('trailer field: ' + tf);
    let md = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MD_NAME_STR);
    console.info('md: ' + md);
    let mgf = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MGF_NAME_STR);
    console.info('mgf: ' + mgf);
    let mgf1Md = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MGF1_MD_STR);
    console.info('mgf1Md: ' + mgf1Md);
    await signer.update(input1);
    let signMessageBlob = await signer.sign(input2);
    // Before verify initialization, set and get the PSS parameters.
    verifier.setVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
    saltLen = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
    console.info('SaltLen: ' + saltLen);
    tf = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_TRAILER_FIELD_NUM);
    console.info('trailer field: ' + tf);
    md = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MD_NAME_STR);
    console.info('md: ' + md);
    mgf = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MGF_NAME_STR);
    console.info('mgf: ' + mgf);
    mgf1Md = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MGF1_MD_STR);
    await verifier.init(keyPair.pubKey);
    await verifier.update(input1);
    let verifyResult = await verifier.verify(input2, signMessageBlob);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

- Synchronous method example:

  <!-- @[pss_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pss_signature_verification/rsa_pss_signature_verification_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Construct RSA asymmetric key pair parameters based on the key parameter attributes.
  function genRsaKeyPairSpec(nIn: bigint, eIn: bigint, dIn: bigint) {
    let rsaCommSpec: cryptoFramework.RSACommonParamsSpec = {
      n: nIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC
    };
    let rsaKeyPairSpec: cryptoFramework.RSAKeyPairSpec = {
      params: rsaCommSpec,
      sk: dIn,
      pk: eIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC
    };
    return rsaKeyPairSpec;
  }
  
  // Generate RSA2048 key pair parameters.
  function genRsa2048KeyPairSpec(): cryptoFramework.RSAKeyPairSpec {
    let nIn =
      BigInt('0x9260d0750ae117eee55c3f3deaba74917521a262ee76007cdf8a56755ad73a1598a1408410a01434c3f5bc54a88b57fa19fc43' +
        '28daea0750a4c44e88cff3b2382621b80f670464433e4336e6d003e8cd65bff211da144b88291c2259a00a72b711c116ef7686e8fee34' +
        'e4d933c868187bdc26f7be071493c86f7a5941c3510806ad67b0f94d88f5cf5c02a092821d8626e8932b65c5bd8c92049c210932b7afa' +
        '7ac59c0e886ae5c1edb00d8ce2c57633db26bd6639bff73cee82be9275c402b4cf2a4388da8cf8c64eefe1c5a0f5ab8057c39fa5c0589' +
        'c3e253f0960332300f94bea44877b588e1edbde97cf2360727a09b775262d7ee552b3319b9266f05a25');
    let eIn = BigInt('0x010001');
    let dIn =
      BigInt('0x6a7df2ca63ead4dda191d614b6b385e0d9056a3d6d5cfe07db1daabee022db08212d97613d3328e0267c9dd23d787abde2afcb' +
        '306aeb7dfce69246cc73f5c87fdf06030179a2114b767db1f083ff841c025d7dc00cd82435b9a90f695369e94df23d2ce458bc3b3283a' +
        'd8bba2b8fa1ba62e2dce9accff3799aae7c840016f3ba8e0048c0b6cc4339af7161003a5beb864a0164b2c1c9237b64bc87556994351b' +
        '27506c33d4bcdfce0f9c491a7d6b0628c7c852be4f0a9c3132b2ed3a2c8881e9aab07e20e17deb074691be677776a78b5c502e05d9bdd' +
        'e72126b3738695e2dd1a0a98a14247c65d8a7ee79432a092cb0721a12df798e44f7cfce0c498147a9b1');
    return genRsaKeyPairSpec(nIn, eIn, dIn);
  }
  
  function verifyMessagePSSSync() {
    // The complete plaintext is split into input1 and input2.
    let messagePart1 = 'This is Sign test plan1';
    let messagePart2 = 'This is Sign test plan2';
    let input1: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(messagePart1, 'utf-8').buffer) };
    let input2: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(messagePart2, 'utf-8').buffer) };
    // Obtain the RSA key pair parameter object.
    let rsaKeyPairSpec = genRsa2048KeyPairSpec();
    // Construct the RSA key pair generator.
    let rsaGeneratorSpec = cryptoFramework.createAsyKeyGeneratorBySpec(rsaKeyPairSpec);
    // Both sign and verify support RSA keys with or without length.
    let signer = cryptoFramework.createSign('RSA|PSS|SHA256|MGF1_SHA256');
    let verifier = cryptoFramework.createVerify('RSA2048|PSS|SHA256|MGF1_SHA256');
    let keyPair = rsaGeneratorSpec.generateKeyPairSync();
    signer.initSync(keyPair.priKey);
    // After signature initialization, perform set and get operations on PSS parameters.
    let setN = 32;
    signer.setSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
    let saltLen = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
    console.info('SaltLen: ' + saltLen);
    let tf = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_TRAILER_FIELD_NUM);
    console.info('trailer field: ' + tf);
    let md = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MD_NAME_STR);
    console.info('md: ' + md);
    let mgf = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MGF_NAME_STR);
    console.info('mgf: ' + mgf);
    let mgf1Md = signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_MGF1_MD_STR);
    console.info('mgf1Md: ' + mgf1Md);
    signer.updateSync(input1);
    let signMessageBlob = signer.signSync(input2);
    // Before verification initialization, perform set and get operations on PSS parameters.
    verifier.setVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
    saltLen = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
    console.info('SaltLen: ' + saltLen);
    tf = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_TRAILER_FIELD_NUM);
    console.info('trailer field: ' + tf);
    md = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MD_NAME_STR);
    console.info('md: ' + md);
    mgf = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MGF_NAME_STR);
    console.info('mgf: ' + mgf);
    mgf1Md = verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_MGF1_MD_STR);
    verifier.initSync(keyPair.pubKey);
    verifier.updateSync(input1);
    let verifyResult = verifier.verifySync(input2, signMessageBlob);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```

## Signing and Signature Verification with an RSA Key Pair (PSS Mode) (OnlySign and OnlyVerify Modes)

Starting from API version 26.0.0, signing and signature verification support the OnlySign/OnlyVerify modes.

**Signing**

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) and specify the digest algorithm SHA256 to create a digest instance (Md).

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6) and pass in a custom message to update the digest calculation. There is no limit on the length of a single update.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest) to obtain the digest calculation result.

4. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key object (KeyPair) with the RSA key algorithm, a key length of 1024 bits, and two prime numbers, including a public key (PubKey) and a private key (PriKey).

   To generate an RSA asymmetric key pair, refer to the following example, and understand it together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). The referenced documents may differ from the current example in input parameters, so pay attention to the differences when reading them.

5. Call [cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign) and specify the string parameter 'RSA|PSS|SHA256|MGF1_SHA256|OnlySign' to create a Sign instance whose asymmetric key type is RSA without a length, padding mode is PSS, digest algorithm is SHA256, mask algorithm is MGF1_SHA256, and signing mode is OnlySign, for completing the signing operation.

6. Call [Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3) and use the private key (PriKey) to initialize the Sign instance.

7. Call [Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1) to generate a signature for the digest data.

**Verification**

1. Call [cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify) and specify the string parameter 'RSA|PSS|SHA256|MGF1_SHA256|OnlyVerify' to create a Verify instance with the asymmetric key type RSA, padding mode PSS, digest algorithm SHA256, mask algorithm MGF1_SHA256, and verification mode OnlyVerify, for completing the verification operation.

2. Call [Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5) to initialize the Verify instance with the public key (PubKey).

3. Call [Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1) to verify the digest data.

- Asynchronous method example:

  <!-- @[rsa_pss_onlysign_onlyverify_signature_verification_asynchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/rsa_pss_onlysign_onlyverify_signature_verification_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  async function signMessagePromise(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'RSA|PSS|SHA256|MGF1_SHA256|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    await signer.init(priKey);
    let signData = await signer.sign(digestBlob);
    return signData;
  }
  
  async function verifyMessagePromise(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA|PSS|SHA256|MGF1_SHA256|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    await verifier.init(pubKey);
    let res = await verifier.verify(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  async function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is rsa onlySign test', 'utf-8').buffer) };
    // First use Md to calculate the SHA256 digest (32 bytes).
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

- Synchronous method example:

  <!-- @[rsa_pss_onlysign_onlyverify_signature_verification_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/onlysign_onlyverify_signature_validator/rsa_pss_onlysign_onlyverify_signature_verification_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function signMessageSync(priKey: cryptoFramework.PriKey, digestBlob: cryptoFramework.DataBlob) {
    let signAlg = 'RSA|PSS|SHA256|MGF1_SHA256|OnlySign';
    let signer = cryptoFramework.createSign(signAlg);
    signer.initSync(priKey);
    let signData = signer.signSync(digestBlob);
    return signData;
  }
  
  function verifyMessageSync(digestBlob: cryptoFramework.DataBlob, signMessageBlob: cryptoFramework.DataBlob,
    pubKey: cryptoFramework.PubKey) {
    let verifyAlg = 'RSA|PSS|SHA256|MGF1_SHA256|OnlyVerify';
    let verifier = cryptoFramework.createVerify(verifyAlg);
    verifier.initSync(pubKey);
    let res = verifier.verifySync(digestBlob, signMessageBlob);
    console.info('verify result: ' + res);
    return res;
  }
  
  function main() {
    let messageData: cryptoFramework.DataBlob =
      { data: new Uint8Array(buffer.from('This is rsa onlySign test', 'utf-8').buffer) };
    // First use Md to calculate the SHA256 digest (32 bytes).
    let md = cryptoFramework.createMd('SHA256');
    md.updateSync(messageData);
    let digestBlob = md.digestSync();
    let keyGenAlg = 'RSA1024';
    let generator = cryptoFramework.createAsyKeyGenerator(keyGenAlg);
    let keyPair = generator.generateKeyPairSync();
    let signData = signMessageSync(keyPair.priKey, digestBlob);
    let verifyResult = verifyMessageSync(digestBlob, signData, keyPair.pubKey);
    if (verifyResult === true) {
      console.info('verify result: success.');
    } else {
      console.error('verify result: failed.');
    }
  }
  ```
