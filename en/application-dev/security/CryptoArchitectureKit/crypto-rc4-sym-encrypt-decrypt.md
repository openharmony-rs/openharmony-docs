# Encryption and Decryption with an RC4 Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=7bf845a7c8933b8c5015a7da3dfa1923d0e9dc57 translatedAt=2026-08-07T03:32:16.004Z pushedAt=2026-08-10T09:35:48.174Z -->

The Crypto framework supports encryption and decryption with an RC4 symmetric key since API version 26.0.0.

For the corresponding algorithm specifications, see [Symmetric Key Encryption and Decryption Algorithm Specifications: RC4](crypto-encryption-decryption.md#rc4).

RC4 is a stream cipher algorithm and does not require a block cipher mode or padding.

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator), [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1), or [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the RC4 algorithm and a key length ranging from 8 bits to 4096 bits (for example, RC4_128).

   For details about how to generate an RC4 symmetric key, refer to the example below, together with [Symmetric Key Generation and Conversion Specifications: RC4](crypto-key-generation-conversion.md#rc4) and [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md). Note that the reference documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with a string parameter (for example, **'RC4'**) to create a **Cipher** instance of the RC4 symmetric key type for encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption) and key to **SymKey** (the key used for encryption). RC4 is a stream cipher. If there are no encryption/decryption parameters such as IV, **null** will be passed.

4. To encrypt a small amount of data, simply call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1).

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with a string parameter (for example, **'RC4'**) to create a **Cipher** instance of the RC4 symmetric key type for decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption) and key to **SymKey** (the key used for decryption). If there is no encryption or decryption parameter, **null** will be passed.

3. To decrypt a small amount of data, simply call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1).

- Example (using asynchronous APIs):

  <!-- @[encrypt_decrypt_rc4_asynchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceArkTs/entry/src/main/ets/pages/rc4_encryption_decryption/rc4_encryption_decryption_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RC4');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let cipherData = await cipher.doFinal(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RC4');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let rc4Generator = cryptoFramework.createSymKeyGenerator('RC4');
    let symKey = await rc4Generator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function rc4EncryptionDecryption() {
    let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
    let symKey = await genSymKeyByData(keyData);
    let message = 'This is a test';
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = await encryptMessagePromise(symKey, plainText);
    let decryptText = await decryptMessagePromise(symKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```

- Example (using synchronous APIs):

  <!-- @[encrypt_decrypt_rc4_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceArkTs/entry/src/main/ets/pages/rc4_encryption_decryption/rc4_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RC4');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let cipherData = cipher.doFinalSync(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RC4');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let rc4Generator = cryptoFramework.createSymKeyGenerator('RC4');
    let symKey = rc4Generator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function rc4EncryptionDecryption() {
    let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
    let symKey = genSymKeyByData(keyData);
    let message = 'This is a test';
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = encryptMessage(symKey, plainText);
    let decryptText = decryptMessage(symKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```

  <!--no_check-->