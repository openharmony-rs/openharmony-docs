# Encryption and Decryption with an AES Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=77a430155612769c4e2c05b4dfd0b9a692e9b4ab translatedAt=2026-10-30T03:23:19.860Z pushedAt=2026-10-30T07:58:04.476Z nl=1 -->

For details about the algorithm specifications, see [Symmetric Key Encryption and Decryption Algorithm Specifications: AES](crypto-encryption-decryption.md#aes).

## Encrypting and Decrypting with an AES Symmetric Key (GCM Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) to create a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits. Then call [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate the symmetric key.
   
   To generate an AES symmetric key, you can refer to the following example and read it together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). Note that the reference documents may differ from the current example in input parameters.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter 'AES128|GCM' to create a Cipher instance with the symmetric key type AES128 and the block mode GCM, which is used to complete encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the encryption key (SymKey) and the encryption parameters corresponding to the GCM mode (GcmParamsSpec), and initialize the encryption Cipher instance.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to update the data (plaintext).
   
   A single update call has no length limit. You can call update based on the data volume.

   - When the data volume is small, you can call doFinal directly after init is complete.
   - When the data volume is large, you can call update multiple times for segmented encryption and decryption. For details, see [Encryption and Decryption Using an AES Symmetric Key (GCM Mode)](crypto-aes-sym-encrypt-decrypt.md#encrypting-and-decrypting-with-an-aes-symmetric-key-gcm-mode).

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data. Note that because the data has already been passed in through update, pass null for data here. The doFinal output may be null. Before accessing specific data, check whether the result is null to avoid exceptions.

6. Read [GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag as the authentication information for decryption.

   > **NOTE**
   In GCM mode, during a single encryption process, concatenating the result of each update and the final doFinal yields "ciphertext + authTag", where authTag is the last 16 bytes and the rest is ciphertext. If null is passed to the data parameter of doFinal, the doFinal result is the authTag.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter 'AES128|GCM' to create a Cipher instance with the symmetric key type AES128 and the block mode GCM, which is used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (cryptoFramework.CryptoMode.DECRYPT_MODE), specify the decryption key (SymKey) and the decryption parameters corresponding to the GCM mode (GcmParamsSpec), and initialize the decryption Cipher instance.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to update the data (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If AES (GCM mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-GCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-gcm).

- Asynchronous method example:

  <!-- @[gcm_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_encryption_decryption/aes_gcm_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12);
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // For GCM, the authTag is obtained from the doFinal result during encryption and passed in the params parameter of the init function during decryption.
    let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'GcmParamsSpec'
    };
    return gcmParamsSpec;
  }
  
  let gcmParams = genGcmParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|GCM');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let encryptUpdate = await cipher.update(plainText);
    // For GCM encryption, pass null to doFinal to obtain the tag data and update it to the gcmParams object.
    gcmParams.authTag = await cipher.doFinal(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|GCM');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let decryptUpdate = await decoder.update(cipherText);
    // For GCM decryption, pass null to doFinal to verify the tag data passed in during init. An exception is thrown if verification fails.
    let decryptData = await decoder.doFinal(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
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

- Synchronous method example:

  <!-- @[gcm_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_encryption_decryption/aes_gcm_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12);
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // For GCM, the authTag is obtained from the doFinal result during encryption and passed in the params parameter of the init function during decryption.
    let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'GcmParamsSpec'
    };
    return gcmParamsSpec;
  }
  
  let gcmParams = genGcmParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|GCM');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let encryptUpdate = cipher.updateSync(plainText);
    // For GCM encryption, pass null to doFinal to obtain the tag data and update it to the gcmParams object.
    gcmParams.authTag = cipher.doFinalSync(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|GCM');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let decryptUpdate = decoder.updateSync(cipherText);
    // In GCM mode, pass null to doFinal during decryption to verify the tag data passed in during init. An exception is thrown if verification fails.
    let decryptData = decoder.doFinalSync(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
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

## Encrypting and Decrypting with an AES Symmetric Key (CCM Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits.
   
   For details about how to generate an AES symmetric key, you can refer to the example below, together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The reference documents may have differences in input parameters compared with the current example.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the specified string parameter 'AES128|CCM' to create a Cipher instance with the symmetric key algorithm AES128 and the block mode CCM, used to complete encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the key (SymKey) and the encryption parameters (CcmParamsSpec) corresponding to the CCM mode, and initialize the encryption Cipher instance.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to update the data (plaintext).

   The current single update has no length limit. You can decide how to call update based on the data volume.
  
   > **NOTE**
   >
   > The CCM mode does not support segmented encryption and decryption.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to get the data after encryption.
   - Since data has been passed through update, pass null here.
   - The doFinal output may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

6. Read [CcmParamsSpec.authTag](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ccmparamsspec) as the authentication information for decryption.

   > **NOTE**
   >
   > In CCM mode, during a one-time encryption process, concatenate the result of each update and the final doFinal to obtain "ciphertext + authTag", where authTag is the 12 bytes at the end. The remaining part is all ciphertext. If the data parameter of doFinal is passed as null, the result of doFinal is authTag.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter 'AES128|CCM' to create a Cipher instance with AES128 symmetric key and CCM block mode, used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (cryptoFramework.CryptoMode.DECRYPT_MODE), specify the key (SymKey) and the decryption parameters corresponding to CCM mode (CcmParamsSpec), and initialize the decryption Cipher instance.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If AES (CCM mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-CCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-ccm).

- Asynchronous method example:
  <!-- @[ccm_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ccm_encryption_decryption/aes_ccm_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function genCcmParamsSpec() {
    let rand: cryptoFramework.Random = cryptoFramework.createRandom();
    let ivBlob: cryptoFramework.DataBlob = rand.generateRandomSync(7);
    let aadBlob: cryptoFramework.DataBlob = rand.generateRandomSync(8);
    let arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 12 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // For CCM, the authTag is obtained from the doFinal result during encryption and passed in the params parameter of init during decryption.
    let ccmParamsSpec: cryptoFramework.CcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'CcmParamsSpec'
    };
    return ccmParamsSpec;
  }
  
  let ccmParams = genCcmParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CCM');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, ccmParams);
    let encryptUpdate = await cipher.update(plainText);
    // In CCM mode, pass null to doFinal during encryption to obtain the tag data and update it to the ccmParams object.
    ccmParams.authTag = await cipher.doFinal(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CCM');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, ccmParams);
    let decryptUpdate = await decoder.doFinal(cipherText);
    return decryptUpdate;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
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

- Synchronous method example:
  <!-- @[ccm_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ccm_encryption_decryption/aes_ccm_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function genCcmParamsSpec() {
    let rand: cryptoFramework.Random = cryptoFramework.createRandom();
    let ivBlob: cryptoFramework.DataBlob = rand.generateRandomSync(7);
    let aadBlob: cryptoFramework.DataBlob = rand.generateRandomSync(8);
    let arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 12 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // For CCM, the authTag is obtained from the doFinal result during encryption and passed in the params parameter of init during decryption.
    let ccmParamsSpec: cryptoFramework.CcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'CcmParamsSpec'
    };
    return ccmParamsSpec;
  }
  
  let ccmParams = genCcmParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CCM');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, ccmParams);
    let encryptUpdate = cipher.updateSync(plainText);
    // In CCM mode, pass null to doFinal during encryption to obtain the tag data and update it to the ccmParams object.
    ccmParams.authTag = cipher.doFinalSync(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CCM');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, ccmParams);
    let decryptUpdate = decoder.doFinalSync(cipherText);
    return decryptUpdate;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
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

## Encryption and Decryption Using an AES Symmetric Key (CCM Mode) with AeadParamsSpec

Starting from API version 26.0.0, encryption and decryption with an [AES](crypto-encryption-decryption.md#aes) symmetric key (CCM mode) supports the `AeadParamsSpec` parameter.

Use the `AeadParamsSpec` parameter when you do not want to explicitly save the `authTag` or when you need to specify the length of the `authTag`.

**Key generation**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits.
   
   For details about how to generate an AES symmetric key, refer to the following example together with the symmetric key generation and conversion specifications: [AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). Note that the reference documents may differ from the current example in input parameters.


**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the specified string parameter 'AES128|CCM' to create a Cipher instance with the symmetric key algorithm AES128 and the block mode CCM, used to complete encryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (`cryptoFramework.CryptoMode.ENCRYPT_MODE`), specify the key (`SymKey`) and the encryption parameters corresponding to the CCM mode (`AeadParamsSpec`), and initialize the encryption `Cipher` instance.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to get the data after encryption.

   > **NOTE**
   >
   > When `AeadParamsSpec` is used, in CCM mode you can call only one of `update` and `doFinal` for encryption, and each method can be called only once.
   > 
   > When a Cipher instance is initialized with `AeadParamsSpec`, the authentication tag (`authTag`) is automatically appended to the end of the ciphertext and does not need to be saved separately.
   >
   > In CCM mode with the `AeadParamsSpec` structure, `tagLen` supports 4, 6, 8, 10, 12, 14, and 16. If it is not passed, the default value is 12. The unit is bytes.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter 'AES128|CCM' to create a Cipher instance with AES128 symmetric key and CCM block mode, used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (`cryptoFramework.CryptoMode.DECRYPT_MODE`), specify the key (`SymKey`) and the decryption parameters (`AeadParamsSpec`) corresponding to the CCM mode, and initialize the decryption Cipher instance.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If AES (CCM mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-CCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-ccm).

- Asynchronous method example:
  <!-- @[new_ccm_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ccm_encryption_decryption/aes_new_ccm_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function genCcmAeadParamsSpec() {
    let nonce = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]; // 12 bytes
    let nonceValue = new Uint8Array(nonce);
    let aad = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]; // 12 bytes
    let aadValue = new Uint8Array(aad);
    let aeadParamsSpec: cryptoFramework.AeadParamsSpec = {
        nonce: nonceValue,
        authenticatedData: aadValue,
        algName: 'AeadParamsSpec'
    };
    return aeadParamsSpec;
  }
  
    let aeadParams = genCcmAeadParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CCM');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, aeadParams);
    let encryptUpdate = await cipher.doFinal(plainText);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CCM');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, aeadParams);
    let decryptUpdate = await decoder.doFinal(cipherText);
    return decryptUpdate;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  export async function main() : Promise<string> {
    try {
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
      return 'success';
    } catch (error) {
      console.error('decrypt failed. error: ' + error);
      return 'fail';
    }
  }
  ```

- Synchronous method example:
  <!-- @[new_ccm_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ccm_encryption_decryption/aes_new_ccm_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function genCcmAeadParamsSpec() {
    let nonce = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]; // 12 bytes
    let nonceValue = new Uint8Array(nonce);
    let aad = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]; // 12 bytes
    let aadValue = new Uint8Array(aad);
    let aeadParamsSpec: cryptoFramework.AeadParamsSpec = {
        nonce: nonceValue,
        authenticatedData: aadValue,
        algName: 'AeadParamsSpec'
    };
    return aeadParamsSpec;
  }
  
    let aeadParams = genCcmAeadParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CCM');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, aeadParams);
    let encryptUpdate = cipher.doFinalSync(plainText);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CCM');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, aeadParams);
    let decryptUpdate = decoder.doFinalSync(cipherText);
    return decryptUpdate;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  export function main() : string {
    try {
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
      return 'success';
    } catch (error) {
      console.error('decrypt failed. error: ' + error);
      return 'fail';
    }
  }
  ```

## Encrypting and Decrypting with an AES Symmetric Key (CBC Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits.
   
   For how to generate an AES symmetric key, you can refer to the example below, and understand it together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The reference documents may differ from the current example in input parameters, so please note the differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher), specify the string parameter 'AES128|CBC|PKCS7', and create a Cipher instance with the symmetric key type AES128, block mode CBC, and padding mode PKCS7, used to complete encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1), set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the encryption key (SymKey) and the encryption parameters corresponding to CBC mode (IvParamsSpec), and initialize the encryption Cipher instance.

4. When the content to be encrypted is short, you can directly call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) without calling update to obtain the data after encryption.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher), specify the string parameter 'AES128|CBC|PKCS7', and create a Cipher instance with the symmetric key type AES128, block mode CBC, and padding mode PKCS7, used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1), set the mode to decryption (cryptoFramework.CryptoMode.DECRYPT_MODE), specify the decryption key (SymKey) and the decryption parameters corresponding to CBC mode (IvParamsSpec), and initialize the decryption Cipher instance.

3. When the decrypted content is short, you can skip calling `update` and directly call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the data after decryption.

If AES (CBC mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-CBC](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-cbc).

- Asynchronous method example:
  <!-- @[cbc_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_cbc_encryption_decryption/aes_cbc_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16);
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CBC|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let cipherData = await cipher.doFinal(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CBC|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function aesCBC() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
      let symKey = await genSymKeyByData(keyData);
      let message = 'This is a test';
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      let encryptText = await encryptMessagePromise(symKey, plainText);
      let decryptText = await decryptMessagePromise(symKey, encryptText);
      if (plainText.data.toString() === decryptText.data.toString()) {
        console.info('decrypt ok');
        console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
      } else {
        console.error('decrypt failed');
      }
    } catch (error) {
      console.error(`AES CBC failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

- Synchronous method example:
  <!-- @[cbc_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_cbc_encryption_decryption/aes_cbc_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16);
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|CBC|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let cipherData = cipher.doFinalSync(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|CBC|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    try {
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
    } catch (error) {
      console.error(`AES CBC failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

## Encrypting and Decrypting with an AES Symmetric Key (ECB Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits.
   
   To learn how to generate an AES symmetric key, refer to the following example together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The reference documents may differ from the current example in input parameters, so note the difference when reading them.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter `'AES128|ECB|PKCS7'` to create a `Cipher` instance with the symmetric key type AES128, block mode ECB, and padding mode PKCS7, which is used to complete encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (`cryptoFramework.CryptoMode.ENCRYPT_MODE`), specify the encryption key (`SymKey`), and leave the ECB mode `Params` empty to initialize the encryption `Cipher` instance.

4. When the content to encrypt is short, you can call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) directly without calling `update` to obtain the encrypted data.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter `'AES128|ECB|PKCS7'` to create a `Cipher` instance with the symmetric key type AES128, block mode ECB, and padding mode PKCS7, which is used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (`cryptoFramework.CryptoMode.DECRYPT_MODE`), specify the decryption key (`SymKey`), and leave the ECB mode `Params` empty to initialize the decryption `Cipher` instance.

3. If the content to decrypt is short, you can skip `update` and directly call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the data after decryption.

If AES (ECB mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-ECB](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-ecb).

- Asynchronous method example:

  <!-- @[ecb_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ecb_encryption_decryption/aes_ecb_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|ECB|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let cipherData = await cipher.doFinal(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|ECB|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function aesECB() {
    try {
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
    } catch (error) {
      console.error(`AES ECB failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

- Synchronous method example:

  <!-- @[ecb_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_ecb_encryption_decryption/aes_ecb_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|ECB|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let cipherData = cipher.doFinalSync(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|ECB|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function aesECBSync() {
    try {
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
    } catch (error) {
      console.error(`AES ECB failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

## Encrypting and Decrypting with an AES Symmetric Key (GCM Mode) in Segments

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 128 bits.
   
   For how to generate an AES symmetric key, you can refer to the example below along with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The reference documents may have differences in input parameters from the current example, so please note the difference when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with the symmetric key type AES128, block mode GCM, and padding mode PKCS7, used to complete encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the encryption key (SymKey) and the encryption parameters corresponding to the GCM mode (GcmParamsSpec), and initialize the encryption Cipher instance.

4. Set the amount of data passed in at a time to 20 bytes, and call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) multiple times to update the data (plaintext).
   
   - There is no limit on the length of a single update. You can determine how to call update based on the amount of data.
   - It is recommended that you check whether the result of each update is null, and when the result is not null, extract the data from it and concatenate it to form the complete ciphertext. This is because in different modes, the result of update may be affected differently.
      
      1) For example, in ECB and CBC modes, encryption is always performed with a block as the basic unit, and the encrypted block result generated by this update is output. That is, when the current update operation fills a complete block, the ciphertext is output; if it does not fill a block, this update outputs null, and the unencrypted data is concatenated with the data input next time before being grouped and output. Finally, in doFinal, the unencrypted data is padded according to the specified padding mode, and the remaining encryption result is output. The update operation in the decryption process follows the same principle.

      2) For stream cipher modes such as CTR and OFB, the ciphertext length equals the plaintext length.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.
   
   - Since data has been passed through update, pass null here.
   - Before accessing the doFinal output result, check whether the result is null to avoid exceptions.

6. Read [GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag as the decryption authentication information.

   > **NOTE**
   In GCM mode, during a single encryption process, concatenating the result of each update and the final doFinal yields "ciphertext + authTag", where authTag is the last 16 bytes and the rest is ciphertext. If null is passed to the data parameter of doFinal, the doFinal result is the authTag.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with the symmetric key type AES128, the block mode GCM, and the padding mode PKCS7, which is used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (cryptoFramework.CryptoMode.DECRYPT_MODE), specify the decryption key (SymKey) and the decryption parameters corresponding to the GCM mode (GcmParamsSpec), and initialize the decryption Cipher instance.

3. Set the amount of data passed in at a time to 20 bytes, and call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) multiple times to update the data (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If AES (GCM mode) decryption fails and returns error code 17630001, see [Failed to Call doFinal During Decryption Using AES-GCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-aes-gcm).

- Asynchronous method example:

  <!-- @[gcm_seg_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_seg_encryption_decryption/aes_gcm_seg_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12);
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    }; // For GCM, the authTag is obtained through doFinal() during encryption and passed in through the params of init() during decryption.
    let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'GcmParamsSpec'
    };
    return gcmParamsSpec;
  }
  
  let gcmParams = genGcmParamsSpec();
  
  // Encrypt the message in segments.
  async function encryptMessageUpdateBySegment(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|GCM|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume that update is performed in segments of 20 bytes. There is no actual requirement for this.
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += updateLength) {
      let updateMessage = plainText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      let updateOutput = await cipher.update(updateMessageBlob);
      // Concatenate the update results to obtain the ciphertext. In some cases, the doFinal result also needs to be concatenated, depending on the block mode
      // and padding mode. In this example, the doFinal result in GCM mode contains only authTag, not ciphertext, so no concatenation is needed.
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    gcmParams.authTag = await cipher.doFinal(null);
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message in segments.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|GCM|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume that update is performed in 20-byte segments. There is no actual requirement on the segment size.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += updateLength) {
      let updateMessage = cipherText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Perform segmented update.
      let updateOutput = await decoder.update(updateMessageBlob);
      // Concatenate the update results to obtain the plaintext.
      let mergeText = new Uint8Array(decryptText.length + updateOutput.data.length);
      mergeText.set(decryptText);
      mergeText.set(updateOutput.data, decryptText.length);
      decryptText = mergeText;
    }
    let decryptData = await decoder.doFinal(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    let decryptBlob: cryptoFramework.DataBlob = { data: decryptText };
    return decryptBlob;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function aes() {
    let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
    let symKey = await genSymKeyByData(keyData);
    let message = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee'; // Assume that the message is 43 bytes in total, which is also 43 bytes after UTF-8 decoding.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = await encryptMessageUpdateBySegment(symKey, plainText);
    let decryptText = await decryptMessagePromise(symKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```

- Synchronous method example:

  <!-- @[gcm_seg_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_seg_encryption_decryption/aes_gcm_seg_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12);
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    }; // In GCM mode, authTag is obtained through doFinal() during encryption and passed in through the params of init() during decryption.
    let gcmParamsSpec: cryptoFramework.GcmParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'GcmParamsSpec'
    };
    return gcmParamsSpec;
  }
  
  let gcmParams = genGcmParamsSpec();
  
  // Encrypt the message in segments.
  function encryptMessageUpdateBySegment(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|GCM|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume that update is performed in 20-byte segments. There is no actual requirement on the segment size.
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += updateLength) {
      let updateMessage = plainText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Perform segmented update.
      let updateOutput = cipher.updateSync(updateMessageBlob);
      // Concatenate the update results to obtain the ciphertext (in some cases, the doFinal result also needs to be concatenated, depending on the block mode
      // and padding mode. In this example, the doFinal result of GCM mode contains only authTag and no ciphertext, so no concatenation is needed).
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    gcmParams.authTag = cipher.doFinalSync(null);
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message in segments.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|GCM|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume segmented update is performed in units of 20 bytes. There is no actual requirement for this.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += updateLength) {
      let updateMessage = cipherText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Perform segmented update.
      let updateOutput = decoder.updateSync(updateMessageBlob);
      // Concatenate the update results to obtain the plaintext.
      let mergeText = new Uint8Array(decryptText.length + updateOutput.data.length);
      mergeText.set(decryptText);
      mergeText.set(updateOutput.data, decryptText.length);
      decryptText = mergeText;
    }
    let decryptData = decoder.doFinalSync(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    let decryptBlob: cryptoFramework.DataBlob = { data: decryptText };
    return decryptBlob;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
    let symKey = genSymKeyByData(keyData);
    let message = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee'; // Assume the message is 43 bytes in total, which is also 43 bytes after UTF-8 decoding.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = encryptMessageUpdateBySegment(symKey, plainText);
    let decryptText = decryptMessage(symKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```

## Encryption and Decryption Using an AES Symmetric Key (XTS Mode)

Starting from API version 26.0.0, [AES](crypto-encryption-decryption.md#aes) symmetric key encryption and decryption supports the XTS block mode.

**Key generation**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a symmetric key (SymKey) with the AES algorithm and a key length of 256 bits.
   
   To learn how to generate an AES symmetric key, refer to the example below and the symmetric key generation and conversion specifications: [AES](crypto-key-generation-conversion.md#aes) and [randomly generate symmetric key](crypto-generate-sym-key-randomly.md) for understanding. Note that the reference documents and the current example may differ in input parameters.

   > **NOTE**
   >
   > When encrypting and decrypting with an AES symmetric key (XTS mode), the symmetric key length must be twice that of a standard AES key. Only AES-128 and AES-256 cipher instances can be created for encryption and decryption.
   >
   > In the example code, an AES256 symmetric key is created, and an AES128 cipher instance is used for encryption and decryption.

**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter 'AES128|XTS' to create a Cipher instance with the symmetric key type AES128 and the block mode XTS, used to complete encryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the encryption key (SymKey) and the encryption parameters corresponding to the XTS mode (IvParamsSpec), and initialize the encryption Cipher instance.

3. When the content to be encrypted is short, you can directly call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) without calling update to obtain the data after encryption.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter `'AES128|XTS'` to create a Cipher instance with the symmetric key type AES128 and the block mode XTS, which is used to complete decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (`cryptoFramework.CryptoMode.DECRYPT_MODE`), specify the decryption key (`SymKey`) and the decryption parameters (`IvParamsSpec`) corresponding to the XTS mode, and initialize the decryption Cipher instance.

3. When the decrypted content is short, you can skip calling `update` and directly call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the data after decryption.

- Asynchronous method example:
  <!-- @[xts_encrypt_decrypt_aes_symkey_asynchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_xts_encryption_decryption/aes_xts_encryption_decryption_asynchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16);
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|XTS');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let cipherData = await cipher.doFinal(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|XTS');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  export async function aesXTS() : Promise<string> {
    try {
      let symGenerator = cryptoFramework.createSymKeyGenerator('AES256')
      let symKey = await symGenerator.generateSymKey()
      let message = 'This is a xts encrypt decrypt test';
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      let encryptText = await encryptMessagePromise(symKey, plainText);
      let decryptText = await decryptMessagePromise(symKey, encryptText);
      if (plainText.data.toString() === decryptText.data.toString()) {
        console.info('decrypt ok');
        console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
      } else {
        console.error('decrypt failed');
      }
      return 'success';
    } catch (error) {
      console.error('xts decrypt failed. error: ' + error);
      return 'fail';
    }
  }
  ```

- Synchronous method example:
  <!-- @[xts_encrypt_decrypt_aes_symkey_synchronous](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_xts_encryption_decryption/aes_xts_encryption_decryption_synchronous.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16);
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('AES128|XTS');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let cipherData = cipher.doFinalSync(plainText);
    return cipherData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('AES128|XTS');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  export function aesXTS() : string {
    try {
      let symGenerator = cryptoFramework.createSymKeyGenerator('AES256')
      let symKey = symGenerator.generateSymKeySync()
      let message = 'This is a xts encrypt decrypt test';
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      let encryptText = encryptMessage(symKey, plainText);
      let decryptText = decryptMessage(symKey, encryptText);
      if (plainText.data.toString() === decryptText.data.toString()) {
        console.info('decrypt ok.');
        console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
      } else {
        console.error('decrypt failed.');
      }
      return 'success';
    } catch (error) {
      console.error('xts decrypt failed. error: ' + error);
      return 'fail';
    }
  }
  ```






