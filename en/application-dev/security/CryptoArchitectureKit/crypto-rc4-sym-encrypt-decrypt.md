# Encryption and Decryption with an RC4 Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The Crypto framework supports encryption and decryption with an RC4 symmetric key since API version 26.0.0.

For details about the algorithm specifications, see [Symmetric Key Encryption and Decryption Algorithm Specifications: RC4](crypto-sym-encrypt-decrypt-spec.md#rc4).

RC4 is a stream cipher algorithm and does not require a block cipher mode or padding. The same cipher string parameter (RC4_8 to RC4_4096) is used for encryption and decryption.

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator), [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1), or [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the RC4 algorithm and a key length ranging from 8 bits to 4096 bits (for example, RC4_128).
   
   In addition to the example in this topic, [RC4](crypto-sym-key-generation-conversion-spec.md#rc4) and [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md) may help you better understand how to generate an RC4 symmetric key pair. Note that the input parameters in the reference documents may be different from those in the example below.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify a character string parameter (for example, **'RC4_128'**, which supports RC4_8 to RC4_4096) to create a **Cipher** instance whose symmetric key type is RC4 for encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption) and key to **SymKey** (the key used for encryption). RC4 is a stream cipher. If there are no encryption/decryption parameters such as IV, **null** will be passed.

4. To encrypt a small amount of data, simply call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1).

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify a character string parameter (for example, **'RC4_128'**, which supports RC4_8 to RC4_4096) to create a **Cipher** instance whose symmetric key type is RC4 for decryption.

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
