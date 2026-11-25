# Randomly Generating an Asymmetric Key Pair (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=9fca4748e6758305b5cd265dfe627a1972198ec1 translatedAt=2026-11-20T09:26:35.391Z pushedAt=2026-11-23T08:03:14.430Z nl=1 -->

This topic uses RSA and SM2 as an example to describe how to generate an asymmetric key pair (**KeyPair**) and obtain the binary data.

The asymmetric key pair may be used for subsequent operations such as encryption and decryption, and binary data may be used for storage or transmission.

## Randomly Generating an RSA Key Pair

For details about the algorithm specifications, see [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa).

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) with the string parameter **'RSA1024|PRIMES_2'** to create an asymmetric key generator (**AsyKeyGenerator**) object for a 1024-bit RSA key with two primes.

2. Call [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to randomly generate an asymmetric key pair (**KeyPair**).
   
   The **KeyPair** object includes a public key (**PubKey**) and a private key (**PriKey**).

3. Call [PubKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the public key, and call [PriKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the private key.

- Example: Randomly generate an RSA key pair (using promise-based APIs).

  <!-- @[generate_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPairArkTS/entry/src/main/ets/pages/rsa/Promise.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  async function generateAsyKey() {
    try {
      // Create an AsyKeyGenerator instance.
      let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_2');
      // Use the key generator to randomly generate an asymmetric key pair.
      let keyPair = await rsaGenerator.generateKeyPair();
      let pubKey = keyPair.pubKey;
      let priKey = keyPair.priKey;
      // Obtain the binary data of the asymmetric key pair.
      let pkBlob = pubKey.getEncoded();
      let skBlob = priKey.getEncoded();
      console.info('pk bin data: ' + pkBlob.data);
      console.info('sk bin data: ' + skBlob.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`generateAsyKey failed: errCode: ${e.code}, message: ${e.message}`);
      // ...
    }
  }
  ```


- Example: Randomly generate an RSA key pair (using the synchronous API [generateKeyPairSync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypairsync12)).

  <!-- @[generate_rsa_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPairArkTS/entry/src/main/ets/pages/rsa/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  function generateAsyKeySync() {
    // Create an AsyKeyGenerator instance.
    let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024|PRIMES_2');
    // Use AsyKeyGenerator to randomly generate an asymmetric key pair.
    try {
      let keyPair = rsaGenerator.generateKeyPairSync();
      if (keyPair != null) {
        let pubKey = keyPair.pubKey;
        let priKey = keyPair.priKey;
        // Obtain the binary data of the asymmetric key pair.
        let pkBlob = pubKey.getEncoded();
        let skBlob = priKey.getEncoded();
        console.info('pk bin data: ' + pkBlob.data);
        console.info('sk bin data: ' + skBlob.data);
      } else {
        console.error('[Sync]: get key pair result: fail!');
        // ...
      }
    } catch (e) {
      console.error(`get key pair failed: errCode: ${e.code}, message: ${e.message}`);
      // ...
    }
  }
  ```


## Randomly Generating an SM2 Key Pair

For details about the algorithm specifications, see [Asymmetric Key Generation and Conversion Specifications: SM2](crypto-key-generation-conversion.md#sm2).

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) with the string parameter **'SM2_256'** to create an asymmetric key generator (**AsyKeyGenerator**) object for a 256-bit SM2 key pair.

2. Call [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to randomly generate an asymmetric key pair (**KeyPair**).
   
   The **KeyPair** object includes a public key (**PubKey**) and a private key (**PriKey**).

3. Call [PubKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the public key, and call [PriKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the private key.

- Example: Randomly generate an SM2 key pair (using promise-based APIs).

  <!-- @[generate_sm2_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPairArkTS/entry/src/main/ets/pages/sm2/Promise.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  async function generateSM2Key() {
    try {
      // Create an AsyKeyGenerator instance.
      let sm2Generator = cryptoFramework.createAsyKeyGenerator('SM2_256');
      // Use the key generator to randomly generate an asymmetric key pair.
      let keyPair = await sm2Generator.generateKeyPair();
      let pubKey = keyPair.pubKey;
      let priKey = keyPair.priKey;
      // Obtain the binary data of the asymmetric key pair.
      let pkBlob = pubKey.getEncoded();
      let skBlob = priKey.getEncoded();
      console.info('pk bin data: ' + pkBlob.data);
      console.info('sk bin data: ' + skBlob.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`generateSM2Key failed: errCode: ${e.code}, message: ${e.message}`);
      // ...
    }
  }
  ```


- Return the result synchronously (using the synchronous API [generateKeyPairSync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypairsync12)).
  <!-- @[generate_sm2_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPairArkTS/entry/src/main/ets/pages/sm2/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  
  function generateSM2KeySync() {
    // Create an AsyKeyGenerator instance.
    let sm2Generator = cryptoFramework.createAsyKeyGenerator('SM2_256');
    // Use AsyKeyGenerator to randomly generate an asymmetric key pair.
    try {
      let keyPair = sm2Generator.generateKeyPairSync();
      if (keyPair != null) {
        let pubKey = keyPair.pubKey;
        let priKey = keyPair.priKey;
        // Obtain the binary data of the asymmetric key pair.
        let pkBlob = pubKey.getEncoded();
        let skBlob = priKey.getEncoded();
        console.info('pk bin data: ' + pkBlob.data);
        console.info('sk bin data: ' + skBlob.data);
      } else {
        console.error('[Sync]: get key pair result: fail!');
        // ...
      }
    } catch (e) {
      console.error(`get key pair failed: errCode: ${e.code}, message: ${e.message}`);
      // ...
    }
  }
  ```

