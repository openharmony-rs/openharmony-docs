# Encryption and Decryption with a ChaCha20 Symmetric Key Pair (Poly1305) (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The Crypto framework supports this algorithm since API version 22.

For details about the algorithm specifications, see [ChaCha20](crypto-sym-encrypt-decrypt-spec.md#chacha20).

## How to Develop

**Creating an Object**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a symmetric key (**SymKey**) using ChaCha20.
   
   For details about how to generate a ChaCha20 symmetric key, see the following example. To learn more, see [Symmetric Key Generation and Conversion Specifications: ChaCha20](crypto-sym-key-generation-conversion-spec.md#chacha20) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md). There may be differences between the input parameters in the reference documents and those in the following example.

**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance for encryption. The key type is ChaCha20, and the mode is Poly1305.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In the **Cipher.init** API, set **opMode** to **CryptoMode.ENCRYPT_MODE** (encryption), **key** to **SymKey** (the key for encryption), and **params** to **Poly1305ParamsSpec** corresponding to the Poly1305 mode.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

    > **NOTE**
    >
    > If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
    >
    > The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

5. Obtain [Poly1305ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#poly1305paramsspec22).authTag as the authentication information for decryption.

   In Poly1305 mode, extract the last 16 bytes from the encrypted data as the authentication information for initializing the **Cipher** instance in decryption.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance for decryption. The key type is ChaCha20, and the mode is Poly1305.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In the **Cipher.init** API, set **opMode** to **CryptoMode.DECRYPT_MODE** (decryption), **key** to **SymKey** (the key for decryption), and **params** to **Poly1305ParamsSpec** corresponding to the Poly1305 mode.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

- Example (using asynchronous APIs):

  ```ts
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
    // Obtain the Poly1305 authTag from the Cipher.doFinal result in encryption and fill it in the params parameter of Cipher.init in decryption.
    let poly1305ParamsSpec: cryptoFramework.Poly1305ParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: "Poly1305ParamsSpec"
    };
    return poly1305ParamsSpec;
  }

  let poly1305Params = genPoly1305ParamsSpec();

  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20|Poly1305');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, poly1305Params);
    let encryptUpdate = await cipher.update(plainText);
    // In Poly1305 mode, pass in null in Cipher.doFinal in encryption. Obtain the tag data and fill it in the poly1305Params object.
    poly1305Params.authTag = await cipher.doFinal(null);
    return encryptUpdate;
  }
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20|Poly1305');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, poly1305Params);
    let decryptUpdata = await decoder.update(cipherText);
    // In Poly1305 mode, pass in null in Cipher.doFinal in decryption. Verify the tag data passed in Cipher.init. If the verification fails, an exception will be thrown.
    let decryptData = await decoder.doFinal(null);
    if (decryptData === null) {
      console.info('poly1305 decrypt success, decryptData is null');
    }
    return decryptUpdata;
  }
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = await chacha20Generator.convertKey(symKeyBlob);
    console.info('convertKey success');
    return symKey;
  }
  async function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159,
        83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
      let symKey = await genSymKeyByData(keyData);
      let message = "This is a test";
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      let encryptText = await encryptMessagePromise(symKey, plainText);
      let decryptText = await decryptMessagePromise(symKey, encryptText);
      if (plainText.data.toString() === decryptText.data.toString()) {
        console.info('decrypt ok');
        console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
      } else {
        console.error('decrypt failed.');
      }
    } catch (error) {
      console.error(`decrypt failed, error info is ${error}, error code: ${error.code}`);
    }
  }
  ```

- Example (using synchronous APIs):

  ```ts
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
    // Obtain the Poly1305 authTag from the Cipher.doFinal result in encryption and fill it in the params parameter of Cipher.init in decryption.
    let poly1305ParamsSpec: cryptoFramework.Poly1305ParamsSpec = {
      iv: ivBlob,
      aad: aadBlob,
      authTag: tagBlob,
      algName: "Poly1305ParamsSpec"
    };
    return poly1305ParamsSpec;
  }

  let poly1305Params = genPoly1305ParamsSpec();

  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('ChaCha20|Poly1305');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, poly1305Params);
    let encryptUpdate = cipher.updateSync(plainText);
    // In Poly1305 mode, pass in null in Cipher.doFinal in encryption. Obtain the tag data and fill it in the poly1305Params object.
    poly1305Params.authTag = cipher.doFinalSync(null);
    return encryptUpdate;
  }
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('ChaCha20|Poly1305');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, poly1305Params);
    let decryptUpdata = decoder.updateSync(cipherText);
    // In Poly1305 mode, pass in null in Cipher.doFinal in decryption. Verify the tag data passed in Cipher.init. If the verification fails, an exception will be thrown.
    let decryptData = decoder.doFinalSync(null);
    if (decryptData === null) {
      console.info('poly1305 decrypt success, decryptData is null');
    }
    return decryptUpdata;
  }
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let chacha20Generator = cryptoFramework.createSymKeyGenerator('ChaCha20');
    let symKey = chacha20Generator.convertKeySync(symKeyBlob);
    console.info('convertKeySync success');
    return symKey;
  }
  function main() {
    try {
      let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159,
        83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
      let symKey = genSymKeyByData(keyData);
      let message = "This is a test";
      let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
      let encryptText = encryptMessage(symKey, plainText);
      let decryptText = decryptMessage(symKey, encryptText);
      if (plainText.data.toString() === decryptText.data.toString()) {
        console.info('decrypt ok');
        console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
      } else {
        console.error('decrypt failed.');
      }
    } catch (error) {
      console.error(`decrypt failed, error info is ${error}, error code: ${error.code}`);
    }
  }
  ```
