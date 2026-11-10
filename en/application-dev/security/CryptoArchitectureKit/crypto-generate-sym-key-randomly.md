# Randomly Generating a Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2abb6d40560bb8e1a9913751e42e44a0192e5f14 translatedAt=2026-11-10T01:07:43.180Z pushedAt=2026-11-10T02:43:58.323Z nl=1 -->

This topic uses AES and SM4 as an example to describe how to generate a symmetric key and obtain the binary data.

The symmetric key object may be used for subsequent encryption and decryption operations, and binary data may be used for storage or transmission.

## Randomly Generating an AES Key

For the corresponding algorithm specifications, see [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes).

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) with the string parameter **'AES256'** to create a symmetric key generator (**SymKeyGenerator**) object for a 256-bit AES key.

2. Call [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to randomly generate a symmetric key (**SymKey**) object.

3. Call [SymKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the key.

- Example: Randomly generate a 256-bit AES key (using promise-based APIs).

  <!-- @[generate_aes_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateSymmetricKeyArkTS/entry/src/main/ets/pages/aes/Promise.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function testGenerateAesKey() {
    // Create a SymKeyGenerator instance.
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
    // Use SymKeyGenerator to randomly generate a symmetric key.
    let promiseSymKey = symKeyGenerator.generateSymKey();
    promiseSymKey.then(key => {
      // Obtain the binary data of the symmetric key and output a 256-bit key, which is of 32 bytes.
      let encodedKey = key.getEncoded();
      console.info('key hex: ' + encodedKey.data);
    }).catch((error: BusinessError) => {
      console.error(`testGenerateAesKey failed: errCode: ${error.code}, message: ${error.message}`);
    });
  }
  ```


- Example using synchronous API [generateSymKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkeysync12):
  <!-- @[generate_aes_key_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateSymmetricKeyArkTS/entry/src/main/ets/pages/aes/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function testSyncGenerateAesKey() {
    try {
      // Create a SymKeyGenerator instance.
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
      // Use the key generator to randomly generate a symmetric key.
      let symKey = symKeyGenerator.generateSymKeySync();
      // Obtain the binary data of the symmetric key and output a 256-bit key. The length is 32 bytes.
      let encodedKey = symKey.getEncoded();
      console.info('key hex: ' + encodedKey.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`testSyncGenerateAesKey failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```


## Randomly Generating an SM4 Key

For the corresponding algorithm specifications, see [Symmetric Key Generation and Conversion Specifications: SM4](crypto-key-generation-conversion.md#sm4).

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) with the string parameter **'SM4_128'** to create a symmetric key generator (**SymKeyGenerator**) object for a 128-bit SM4 key.

   If you need to use other algorithms, modify the string parameter.

2. Call [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to randomly generate a symmetric key (**SymKey**) object.

3. Call [SymKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the key.

- Example: Randomly generate a 128-bit SM4 key (using promise-based APIs).

  <!-- @[generate_sm4_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateSymmetricKeyArkTS/entry/src/main/ets/pages/sm4/Promise.ets) --> 
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function testGenerateSM4Key() {
    // Create a SymKeyGenerator instance.
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
    // Use SymKeyGenerator to randomly generate a symmetric key.
    let promiseSymKey = symKeyGenerator.generateSymKey();
    promiseSymKey.then(key => {
      // Obtain the binary data of the symmetric key and output a 128-bit byte stream, which is of 16 bytes.
      let encodedKey = key.getEncoded();
      console.info('key hex: ' + encodedKey.data);
    }).catch((error: BusinessError) => {
      console.error(`testGenerateSM4Key failed: errCode: ${error.code}, message: ${error.message}`);
    });
  }
  ```


- Example using synchronous API [generateSymKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkeysync12):
  <!-- @[generate_sm4_key_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateSymmetricKeyArkTS/entry/src/main/ets/pages/sm4/Sync.ets) --> 
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function testSyncGenerateSm4Key() {
    try {
      // Create a SymKeyGenerator instance.
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
      // Use the key generator to randomly generate a symmetric key.
      let symKey = symKeyGenerator.generateSymKeySync();
      // Obtain the binary data of the symmetric key and output a 128-bit byte stream. The length is 16 bytes.
      let encodedKey = symKey.getEncoded();
      console.info('key hex: ' + encodedKey.data);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`testSyncGenerateSm4Key failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```

