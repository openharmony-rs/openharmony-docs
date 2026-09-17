# Encryption and Decryption with a ChaCha20 Symmetric Key Pair (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=64044667f2ece520228c37a4e282d90b2e014ba4 translatedAt=2026-09-09T07:16:41.944Z pushedAt=2026-09-09T07:25:43.725Z -->

Starting from API version 22, the algorithm library supports this algorithm.

<!--Del-->For details about the algorithm specifications, see [ChaCha20](crypto-encryption-decryption.md#chacha20).<!--DelEnd-->

## Using a ChaCha20 Symmetric Key for Encryption and Decryption

**Creating an Object**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a symmetric key (**SymKey**) using ChaCha20.

   For details about how to generate a ChaCha20 symmetric key, refer to the example below, together with <!--Del-->[ChaCha20](crypto-key-generation-conversion.md#chacha20) and <!--DelEnd-->[Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). Note that the reference documents and the example may differ in input parameters. Pay attention to the differences.

**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter **'ChaCha20'** to create a **Cipher** instance of the symmetric key for encryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey** (the key for encryption), and parameter to **IvParamsSpec**.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

    > **NOTE**
    >
    > Since data has been passed in through **update()**, pass **null** for **data** here.
    >
    > The output of **doFinal()** may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter **'ChaCha20'** to create a **Cipher** instance of the symmetric key for decryption.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey** (the key for decryption), and parameter to **IvParamsSpec**.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

- Example (using asynchronous APIs):

  <!-- @[encrypt_decrypt_chacha20_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20EncryptionDecryptionAsync.ets) -->

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
  let ivSpec = genIvParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, ivSpec);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, ivSpec);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = await chacha20Generator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159, 83,
        217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
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
      console.error(`decrypt failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```


- Example (using synchronous APIs):

  <!-- @[encrypt_decrypt_chacha20_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20EncryptionDecryptionSync.ets) -->

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
  
  let ivSpec = genIvParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, ivSpec);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, ivSpec);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = chacha20Generator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159, 83,
        217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
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
      console.error(`decrypt failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

## Using a ChaCha20 Symmetric Key (Poly1305 Mode) for Encryption/Decryption

**Creating an Object**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a symmetric key (**SymKey**) using ChaCha20.

   For details about how to generate a ChaCha20 symmetric key, refer to the example below, together with <!--Del-->[ChaCha20](crypto-key-generation-conversion.md#chacha20) and <!--DelEnd-->[Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). Note that the reference documents and the example may differ in input parameters. Pay attention to the differences.

**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance with the ChaCha20 symmetric key type and Poly1305 mode, used to complete the encryption operation.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (**cryptoFramework.CryptoMode.ENCRYPT_MODE**), specify the encryption key (**SymKey**) and the encryption parameters (**Poly1305ParamsSpec**) for Poly1305 mode, and initialize the **Cipher** instance for encryption.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

    > **NOTE**
    >
    > Since data has been passed in through **update()**, pass **null** for **data** here.
    >
    > The output of **doFinal()** may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

5. Read [Poly1305ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#poly1305paramsspec22).authTag as the authentication information for decryption.

   In Poly1305 mode, extract the last 16 bytes from the encrypted data as the authentication information for decryption initialization.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance with the ChaCha20 symmetric key type and Poly1305 mode, used to complete the encryption operation.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (**cryptoFramework.CryptoMode.DECRYPT_MODE**), specify the decryption key (**SymKey**) and the decryption parameters (**Poly1305ParamsSpec**) for Poly1305 mode, and initialize the **Cipher** instance for decryption.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If ChaCha20 (Poly1305 mode) decryption fails with error code 17630001, see [doFinal Call Failure During ChaCha20-Poly1305 Decryption](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-chacha20-poly1305).

- Example (using asynchronous APIs):

  <!-- @[encrypt_decrypt_chacha20_poly1305_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20Poly1305EncryptionDecryptionAsync.ets) -->

  ``` TypeScript
  
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genPoly1305ParamsSpec() {
    let ivBlob = generateRandom(12); // 12 bytes
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // The Poly1305 authTag is obtained from the doFinal result during encryption and passed to the params parameter of the init function during decryption.
    let poly1305ParamsSpec: cryptoFramework.Poly1305ParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'Poly1305ParamsSpec'
    };
    return poly1305ParamsSpec;
  }
  
  let poly1305Params = genPoly1305ParamsSpec();
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20|Poly1305');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, poly1305Params);
    let encryptUpdate = await cipher.update(plainText);
    // In Poly1305 mode, pass null to doFinal during encryption to obtain the tag data and update it to the poly1305Params object.
    poly1305Params.authTag = await cipher.doFinal(null);
    return encryptUpdate;
  }
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20|Poly1305');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, poly1305Params);
    let decryptUpdate = await decoder.update(cipherText);
    // In Poly1305 mode, pass null to doFinal during decryption to verify the tag data passed to init; an exception is thrown if verification fails.
    let decryptData = await decoder.doFinal(null);
    if (decryptData === null) {
      console.info('poly1305 decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = await chacha20Generator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  async function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159,
        83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
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
      console.error(`decrypt failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```

- Example (using synchronous APIs):

  <!-- @[encrypt_decrypt_chacha20_poly1305_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20Poly1305EncryptionDecryptionSync.ets) -->

  ``` TypeScript
  
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  function generateRandom(len: number) {
    let rand = cryptoFramework.createRandom();
    let generateRandSync = rand.generateRandomSync(len);
    return generateRandSync;
  }
  
  function genPoly1305ParamsSpec() {
    let ivBlob = generateRandom(12); // 12 bytes
    let arr = [1, 2, 3, 4, 5, 6, 7, 8]; // 8 bytes
    let dataAad = new Uint8Array(arr);
    let aadBlob: cryptoFramework.DataBlob = { data: dataAad };
    arr = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]; // 16 bytes
    let dataTag = new Uint8Array(arr);
    let tagBlob: cryptoFramework.DataBlob = {
      data: dataTag
    };
    // For Poly1305, the authTag is obtained from the doFinal result during encryption and passed in the params parameter of the init function during decryption.
    let poly1305ParamsSpec: cryptoFramework.Poly1305ParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: 'Poly1305ParamsSpec'
    };
    return poly1305ParamsSpec;
  }
  
  let poly1305Params = genPoly1305ParamsSpec();
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20|Poly1305');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, poly1305Params);
    let encryptUpdate = cipher.updateSync(plainText);
    // In Poly1305 mode, pass an empty value to doFinal during encryption to obtain the tag data, and update it to the poly1305Params object.
    poly1305Params.authTag = cipher.doFinalSync(null);
    return encryptUpdate;
  }
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20|Poly1305');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, poly1305Params);
    let decryptUpdate = decoder.updateSync(cipherText);
    // In Poly1305 mode, pass an empty value to doFinal during decryption to verify the tag data passed to init. An exception is thrown if verification fails.
    let decryptData = decoder.doFinalSync(null);
    if (decryptData === null) {
      console.info('poly1305 decrypt result: success, decryptData is null.');
    }
    return decryptUpdate;
  }
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = chacha20Generator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159,
        83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
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
      console.error(`decrypt failed: errCode: ${error.code}, message: ${error.message}`);
    }
  }
  ```
