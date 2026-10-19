# Key Agreement Using ECDH (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=7bf845a7c8933b8c5015a7da3dfa1923d0e9dc57 translatedAt=2026-08-07T03:30:24.814Z pushedAt=2026-08-10T09:20:21.800Z -->

For details about the algorithm specifications, see [ECDH](crypto-key-agreement-overview.md#ecdh).

## How to Develop

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator), [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1), and [AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3) to generate a 256-bit ECC key pair (**KeyPair**).

For guidance on generating an ECC asymmetric key, refer to the following example, together with [Asymmetric Key Generation and Conversion Specifications: ECC](crypto-key-generation-conversion.md#ecc) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). The referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createKeyAgreement](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekeyagreement) with the string parameter **'ECC256'** to create a 256-bit ECC key agreement (**KeyAgreement**) instance.

3. Call [KeyAgreement.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret-1) to perform key agreement with the specified private key (**KeyPair.priKey**) and public key (**KeyPair.pubKey**), and return the shared secret.

- Example: Perform key agreement using **await**.

  <!-- @[use_ecdh_for_key_negotiation_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyNegotiation/entry/src/main/ets/pages/ECDH/ECDHAsync.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  async function ecdhAwait() {
    // The public and private key pair data is transferred from an external system.
    let pubKeyArray =
      new Uint8Array([48, 89, 48, 19, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7, 3, 66, 0, 4,
        83, 96, 142, 9, 86, 214, 126, 106, 247, 233, 92, 125, 4, 128, 138, 105, 246, 162, 215, 71, 81, 58, 202, 121, 26,
        105, 211, 55, 130, 45, 236, 143, 55, 16, 248, 75, 167, 160, 167, 106, 2, 152, 243, 44, 68, 66, 0, 167, 99, 92,
        235, 215, 159, 239, 28, 106, 124, 171, 34, 145, 124, 174, 57, 92]);
    let priKeyArray =
      new Uint8Array([48, 49, 2, 1, 1, 4, 32, 115, 56, 137, 35, 207, 0, 60, 191, 90, 61, 136, 105, 210, 16, 27, 4, 171,
        57, 10, 61, 123, 40, 189, 28, 34, 207, 236, 22, 45, 223, 10, 189, 160, 10, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7]);
    let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
    // Key pair A passed from an external system.
    let keyPairA = await eccGen.convertKey({ data: pubKeyArray }, { data: priKeyArray });
    // Key pair B generated internally.
    let keyPairB = await eccGen.generateKeyPair();
    let eccKeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
    // Use the public key of A and the private key of B to perform key agreement.
    let secret1 = await eccKeyAgreement.generateSecret(keyPairB.priKey, keyPairA.pubKey);
    // Use the private key of A and the public key of B to perform key agreement.
    let secret2 = await eccKeyAgreement.generateSecret(keyPairA.priKey, keyPairB.pubKey);
    // The two key agreement results should be the same.
    if (secret1.data.toString() === secret2.data.toString()) {
      console.info('ecdh result: success.');
      console.info('ecdh output: ' + secret1.data);
    } else {
      console.error('ecdh result is not equal.');
    }
  }
  ```

- Example (using synchronous APIs):

  <!-- @[use_ecdh_for_key_negotiation_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyNegotiation/entry/src/main/ets/pages/ECDH/ECDHSync.ets) -->

  ``` TypeScript
  
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  function ecdhSync() {
    // The public and private key pair data is transferred from an external system.
    let pubKeyArray =
      new Uint8Array([48, 89, 48, 19, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7, 3, 66, 0, 4,
        83, 96, 142, 9, 86, 214, 126, 106, 247, 233, 92, 125, 4, 128, 138, 105, 246, 162, 215, 71, 81, 58, 202, 121, 26,
        105, 211, 55, 130, 45, 236, 143, 55, 16, 248, 75, 167, 160, 167, 106, 2, 152, 243, 44, 68, 66, 0, 167, 99, 92,
        235, 215, 159, 239, 28, 106, 124, 171, 34, 145, 124, 174, 57, 92]);
    let priKeyArray =
      new Uint8Array([48, 49, 2, 1, 1, 4, 32, 115, 56, 137, 35, 207, 0, 60, 191, 90, 61, 136, 105, 210, 16, 27, 4, 171,
        57, 10, 61, 123, 40, 189, 28, 34, 207, 236, 22, 45, 223, 10, 189, 160, 10, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7]);
    let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
    // Key pair A passed from an external system.
    let keyPairA = eccGen.convertKeySync({ data: pubKeyArray }, { data: priKeyArray });
    // Key pair B generated internally.
    let keyPairB = eccGen.generateKeyPairSync();
    let eccKeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
    // Use the public key of A and the private key of B to perform key agreement.
    let secret1 = eccKeyAgreement.generateSecretSync(keyPairB.priKey, keyPairA.pubKey);
    // Use the private key of A and the public key of B to perform key agreement.
    let secret2 = eccKeyAgreement.generateSecretSync(keyPairA.priKey, keyPairB.pubKey);
    // The two key agreement results should be the same.
    if (secret1.data.toString() === secret2.data.toString()) {
      console.info('ecdh result: success.');
      console.info('ecdh output: ' + secret1.data);
    } else {
      console.error('ecdh result is not equal.');
    }
  }
  ```

  <!--no_check-->