# Key Agreement Using DH (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ae6edf9e57a4f160cca98ef88ced0cd8e0518bb0 translatedAt=2026-11-04T08:20:35.511Z pushedAt=2026-11-04T08:25:33.024Z nl=1 -->

For details about the algorithm specifications, see [DH](crypto-key-agreement-overview.md#dh).

## How to Develop

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key pair (**KeyPair**) that uses the DH key algorithm and the well-known security prime group modp1536.

   To learn how to generate a DH asymmetric key, refer to the following example and also see [Asymmetric Key Generation and Conversion Specifications: DH](crypto-key-generation-conversion.md#dh) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the referenced documents may differ from the current example in input parameters.

2. Call [cryptoFramework.createKeyAgreement](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekeyagreement) with the string parameter **'DH_modp1536'** to create a key agreement (**KeyAgreement**) that uses the DH key algorithm and the well-known security prime group modp1536.

3. Call [KeyAgreement.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret-1) to perform key agreement with the specified private key (**KeyPair.priKey**) and public key (**KeyPair.pubKey**), and return the shared secret.

- Example (using asynchronous APIs):

  <!-- @[use_dh_for_key_negotiation_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyNegotiation/entry/src/main/ets/pages/DH/DHAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  async function dhAwait() {
    try {
      let keyGen = cryptoFramework.createAsyKeyGenerator('DH_modp1536');
      // Randomly generate key pair A.
      let keyPairA = await keyGen.generateKeyPair();
      // Randomly generate key pair B with the same specifications.
      let keyPairB = await keyGen.generateKeyPair();
      let keyAgreement = cryptoFramework.createKeyAgreement('DH_modp1536');
      // Perform key agreement using A's public key and B's private key.
      let secret1 = await keyAgreement.generateSecret(keyPairB.priKey, keyPairA.pubKey);
      // Perform key agreement using A's private key and B's public key.
      let secret2 = await keyAgreement.generateSecret(keyPairA.priKey, keyPairB.pubKey);
      // The results of the two key agreements should be the same.
      if (secret1.data.toString() === secret2.data.toString()) {
        console.info('DH result: success.');
        console.info('DH output: ' + secret1.data);
      } else {
        console.error('DH result is not equal.');
      }
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```


- Example (using synchronous APIs):

  <!-- @[use_dh_for_key_negotiation_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyNegotiation/entry/src/main/ets/pages/DH/DHSync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function dhSync() {
    try {
      let keyGen = cryptoFramework.createAsyKeyGenerator('DH_modp1536');
      // Randomly generate key pair A.
      let keyPairA = keyGen.generateKeyPairSync();
      // Randomly generate key pair B with the same specifications.
      let keyPairB = keyGen.generateKeyPairSync();
      let keyAgreement = cryptoFramework.createKeyAgreement('DH_modp1536');
      // Perform key agreement using A's public key and B's private key.
      let secret1 = keyAgreement.generateSecretSync(keyPairB.priKey, keyPairA.pubKey);
      // Perform key agreement using A's private key and B's public key.
      let secret2 = keyAgreement.generateSecretSync(keyPairA.priKey, keyPairB.pubKey);
      // The results of the two key agreements should be the same.
      if (secret1.data.toString() === secret2.data.toString()) {
        console.info('DH result: success.');
        console.info('DH output: ' + secret1.data);
      } else {
        console.error('DH result is not equal.');
      }
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```

