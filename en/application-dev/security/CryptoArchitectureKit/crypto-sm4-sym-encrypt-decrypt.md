# Encryption and Decryption with an SM4 Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=64044667f2ece520228c37a4e282d90b2e014ba4 translatedAt=2026-08-31T09:28:10.772Z pushedAt=2026-08-31T10:11:59.529Z -->

For the corresponding algorithm specifications, see [Symmetric Encryption and Decryption Algorithm Specifications: SM4](crypto-encryption-decryption.md#sm4).

## Encrypting and Decrypting with SM4 Symmetric Key (ECB Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a 128-bit SM4 symmetric key (**SymKey**).

   For details about how to generate an SM4 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: SM4](crypto-key-generation-conversion.md#sm4) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|ECB|PKCS7'** to create a **Cipher** instance for encryption. The key type is **SM4_128**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption) and key to **SymKey** (the key used for encryption).

   If ECB mode is used, pass in **null**.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

   - If a small amount of data is to be encrypted, you can use **Cipher.doFinal** immediately after **Cipher.init**.
   - If a large amount of data is to be encrypted, you can call **Cipher.update** multiple times to pass in the data by segment.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

   - If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
   - The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|ECB|PKCS7'** to create a **Cipher** instance for decryption. The key type is **SM4_128**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption) and key to **SymKey** (the key used for decryption). The ECB mode has no encryption parameters, so pass in **null**.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If SM4 (CBC mode) decryption fails with error code 17630001, see [Failed to Call doFinal During Decryption Using SM4-ECB/CBC](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-sm4-ecbcbc).

- Example (using asynchronous APIs):

  <!-- @[async_symmetry_encrypt_decrypt_sm4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_ecb_encryption_decryption/sm4_ecb_encryption_decryption_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('SM4_128|ECB|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|ECB|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = await symGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
    let keyData = new Uint8Array([7, 154, 52, 176, 4, 236, 150, 43, 237, 9, 145, 166, 141, 174, 224, 131]);
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

  <!-- @[sync_symmetry_encrypt_decrypt_sm4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_ecb_encryption_decryption/sm4_ecb_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('SM4_128|ECB|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|ECB|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = symGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    let keyData = new Uint8Array([7, 154, 52, 176, 4, 236, 150, 43, 237, 9, 145, 166, 141, 174, 224, 131]);
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

## Using an SM4 Symmetric Key (CBC Mode) for Encryption and Decryption

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a 128-bit SM4 symmetric key (**SymKey**).

   For details about how to generate an SM4 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: SM4](crypto-key-generation-conversion.md#sm4) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|CBC|PKCS7'** to create a **Cipher** instance with the symmetric key type of SM4_128, the block mode of CBC, and the padding mode of PKCS7, which is used to perform encryption.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey** (the key for encryption), and parameter to **IvParamsSpec** (the encryption parameters for CBC mode).

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

   - If a small amount of data is to be encrypted, you can use **Cipher.doFinal** immediately after **Cipher.init**.
   - If a large amount of data is to be encrypted, you can call **Cipher.update** multiple times to pass in the data by segment.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

   - If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
   - The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|CBC|PKCS7'** to create a **Cipher** instance with the symmetric key type of SM4_128, the block mode of CBC, and the padding mode of PKCS7, which is used to perform decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey** (the key for decryption), and parameter to **IvParamsSpec** corresponding to the CBC mode.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If SM4 (CBC mode) decryption fails with error code 17630001, see [Failed to Call doFinal During Decryption Using SM4-ECB/CBC](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-sm4-ecbcbc).

- Example (using asynchronous APIs):

  <!-- @[async_symmetry_encrypt_decrypt_sm4_cbc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_cbc_encryption_decryption/sm4_cbc_encryption_decryption_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16); // 16 bytes
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('SM4_128|CBC|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|CBC|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = await symGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
    try {
      let keyData = new Uint8Array([7, 154, 52, 176, 4, 236, 150, 43, 237, 9, 145, 166, 141, 174, 224, 131]);
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
      console.error(`SM4 failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```


- Example (using synchronous APIs):

  <!-- @[sync_symmetry_encrypt_decrypt_sm4_cbc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_cbc_encryption_decryption/sm4_cbc_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genIvParamsSpec() {
    let ivBlob = generateRandom(16); // 16 bytes
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: 'IvParamsSpec',
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  
  let iv = genIvParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('SM4_128|CBC|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, iv);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|CBC|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = symGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    try {
      let keyData = new Uint8Array([7, 154, 52, 176, 4, 236, 150, 43, 237, 9, 145, 166, 141, 174, 224, 131]);
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
      console.error(`SM4 failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```
## Encrypting and Decrypting with an SM4 Symmetric Key (GCM Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a 128-bit SM4 symmetric key (**SymKey**).

   For details about how to generate an SM4 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: SM4](crypto-key-generation-conversion.md#sm4) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|GCM'** to create a **Cipher** instance for encryption. The key type is SM4_128, and the block cipher mode is GCM.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey** (the key for encryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

   There is no limit on the length of a single `update` call. You can decide how to call `update` based on the amount of data.

   - If a small amount of data is to be encrypted, you can use **Cipher.doFinal** immediately after **Cipher.init**.
   - When the amount of data is large, you can call `update` multiple times, that is, [segmented encryption and decryption](crypto-sm4-sym-encrypt-decrypt.md#encrypting-and-decrypting-in-segments-with-an-sm4-symmetric-key-gcm-mode).

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.
   - If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
   - The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

6. Obtain [GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag as the authentication information for decryption.

   In GCM mode, take the last 16 bytes from the encrypted data as the authentication information used for initialization during decryption. In the example, `authTag` is exactly 16 bytes.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|GCM'** to create a **Cipher** instance for decryption. The key type is SM4_128, and the block cipher mode is GCM.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey** (the key for decryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If SM4 (GCM mode) decryption fails with error code 17630001, see [Failed to Call doFinal During Decryption Using SM4-GCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-sm4-gcm).

- Example (using asynchronous APIs):

  <!-- @[async_symmetry_encrypt_decrypt_sm4_gcm](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_encryption_decryption/sm4_gcm_encryption_decryption_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12); // 12 bytes
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // In GCM mode, obtain the authTag from the doFinal result during encryption, and pass it in the params parameter of the init function during decryption.
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
    let cipher = cryptoFramework.createCipher('SM4_128|GCM');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let encryptUpdate = await cipher.update(plainText);
    // In GCM mode, pass null to doFinal during encryption to obtain the tag data and update it to the gcmParams object.
    gcmParams.authTag = await cipher.doFinal(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|GCM');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let decryptUpdate = await decoder.update(cipherText);
    // In GCM mode, pass null to doFinal during decryption to verify the tag data passed to init. An exception is thrown if verification fails.
    let decryptData = await decoder.doFinal(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let sm4Generator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = await sm4Generator.convertKey(symKeyBlob);
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

- Example (using synchronous APIs):

  <!-- @[sync_symmetry_encrypt_decrypt_sm4_gcm](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_encryption_decryption/sm4_gcm_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12); // 12 bytes
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // In GCM mode, the authTag is obtained from the doFinal result during encryption and passed to the params parameter of the init function during decryption.
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
    let cipher = cryptoFramework.createCipher('SM4_128|GCM');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let encryptUpdate = cipher.updateSync(plainText);
    // In GCM mode, pass null to doFinal during encryption to obtain the tag data and update it to the gcmParams object.
    gcmParams.authTag = cipher.doFinalSync(null);
    return encryptUpdate;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('SM4_128|GCM');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let decryptUpdate = decoder.updateSync(cipherText);
    // In GCM mode, pass null to doFinal during decryption to verify the tag data passed to init. An exception is thrown if verification fails.
    let decryptData = decoder.doFinalSync(null);
    if (decryptData == null) {
      console.info('GCM decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let sm4Generator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = sm4Generator.convertKeySync(symKeyBlob);
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

## Encrypting and Decrypting in Segments with an SM4 Symmetric Key (GCM Mode)

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a 128-bit SM4 symmetric key (**SymKey**).

   For details about how to generate an SM4 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: SM4](crypto-key-generation-conversion.md#sm4) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). The referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|GCM'** to create a **Cipher** instance for encryption. The key type is SM4_128, and the block mode is GCM.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey** (the key for encryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

4. Set the amount of data passed in at a time to 20 bytes, and call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) multiple times to update the data (plaintext).

   - Currently, there is no limit on the length of a single update. You can decide how to call update based on the amount of data.
   - It is recommended that you check whether the result of each update is null, and when the result is not null, extract the data from it and concatenate it to form the complete ciphertext. This is because in different modes, the result of update may be affected differently.

      1) For example, in ECB and CBC modes, encryption is always performed in units of blocks, and the encrypted block result produced by this update is output. That is, when this update operation fills a complete block, the ciphertext is output; if it does not fill a block, this update outputs null, and the unencrypted data is concatenated with the data input next time to fill a block before output. At the final doFinal, the unencrypted data is padded according to the specified padding mode, and then the remaining encryption result is output. The same applies to update during decryption.

      2) For stream cipher modes (such as CTR and OFB), the ciphertext length is usually equal to the plaintext length.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

   - If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
   - The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

6. Obtain [GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag as the authentication information for decryption.

   In GCM mode, you need to extract the last 16 bytes from the encrypted data as the authentication information for initialization during decryption. In the example, authTag is exactly 16 bytes.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'SM4_128|GCM'** to create a **Cipher** instance for decryption. The key type is SM4_128, and the block mode is GCM.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey** (the key for decryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

3. Set the amount of data passed in at a time to 20 bytes, and call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) multiple times to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If SM4 (GCM mode) decryption fails with error code 17630001, see [Failed to Call doFinal During Decryption Using SM4-GCM](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-sm4-gcm).

- Example (using asynchronous APIs):

  <!-- @[async_symmetry_encrypt_decrypt_sm4_gcm_seg](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_seg_encryption_decryption/sm4_gcm_seg_encryption_decryption_asynchronous.ets) -->

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
    let cipher = cryptoFramework.createCipher('SM4_128|GCM');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume that each update processes 20 bytes. There is no actual requirement on the segment size.
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += updateLength) {
      let updateMessage = plainText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      let updateOutput = await cipher.update(updateMessageBlob);
      // Concatenate the update results to obtain the ciphertext. In some cases, the doFinal result also needs to be concatenated, depending on the block mode
      // and padding mode. In this example, the doFinal result of GCM mode contains only the authTag, not the ciphertext, so no concatenation is needed.
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
    let decoder = cryptoFramework.createCipher('SM4_128|GCM');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume that each update processes 20 bytes. There is no actual requirement on the segment size.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += updateLength) {
      let updateMessage = cipherText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
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
    let sm4Generator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = await sm4Generator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function sm4() {
    let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
    let symKey = await genSymKeyByData(keyData);
    let message = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee'; // Assume the message is 43 bytes in total, which is also 43 bytes after UTF-8 decoding.
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

- Example (using synchronous APIs):

  <!-- @[sync_symmetry_encrypt_decrypt_sm4_gcm_seg](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_seg_encryption_decryption/sm4_gcm_seg_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genGcmParamsSpec() {
    let ivBlob = generateRandom(12); // 12 bytes
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
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
    let cipher = cryptoFramework.createCipher('SM4_128|GCM');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume the update is performed in 20-byte segments; there is no actual requirement for this.
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += updateLength) {
      let updateMessage = plainText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
      let updateOutput = cipher.updateSync(updateMessageBlob);
      // Concatenate the update results to obtain the ciphertext (in some cases, the doFinal result also needs to be concatenated, depending on the block mode
      // and padding mode. In this example, the doFinal result in GCM mode contains only the authTag without the ciphertext, so no concatenation is needed).
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
    let decoder = cryptoFramework.createCipher('SM4_128|GCM');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
    let updateLength = 20; // Assume the update is performed in 20-byte segments; there is no actual requirement for this.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += updateLength) {
      let updateMessage = cipherText.data.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Update in segments.
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
    let sm4Generator = cryptoFramework.createSymKeyGenerator('SM4_128');
    let symKey = sm4Generator.convertKeySync(symKeyBlob);
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


