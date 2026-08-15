# Encryption and Decryption with a 3DES Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=9fdfc79fd811dbd3830944fd4ada4372911e5c41 translatedAt=2026-08-07T03:23:47.915Z pushedAt=2026-08-07T07:41:45.494Z -->

For the corresponding algorithm specifications, see [Symmetric Key Encryption/Decryption Algorithm Specifications: 3DES](crypto-encryption-decryption.md#3des).

## How to Develop

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a 192-bit 3DES symmetric key (**SymKey**).

To learn how to generate a 3DES symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: 3DES](crypto-key-generation-conversion.md#3des) and [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md). Note that the referenced documents may differ from the current example in input parameters. Pay attention to these differences when reading.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for encryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In **Cipher.init**, set **opMode** to **CryptoMode.ENCRYPT_MODE** (encryption) and **key** to **SymKey** (the key used for encryption).

   If ECB mode is used, pass **null**.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).

   - If a small amount of data is to be encrypted, you can use **Cipher.doFinal** immediately after **Cipher.init**.

   - If a large amount of data is to be encrypted, you can call **Cipher.update** multiple times to pass in the data by segment.

   - You can determine the data size. For example, call **Cipher.update** when the data size is greater than 20 bytes.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

   - If **Cipher.update** has been called, pass **null** for **data**.

   - The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for decryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In **Cipher.init**, set **opMode** to **CryptoMode.DECRYPT_MODE** (decryption) and **key** to **SymKey** (the key used for decryption). If ECB mode is used, pass **null**.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

If 3DES decryption fails with error code 17630001, see [Failed to Call doFinal During Decryption Using DES/3DES](../../reference/apis-crypto-architecture-kit/errorcode-crypto-framework.md#failed-to-call-dofinal-during-decryption-using-des3des).

## Example

If the cipher mode is ECB, you do not need to set IV parameter for encryption and decryption.

If the CBC, CTR, OFB, or CFB block mode is used, you need to set the IV. For details, see [Setting the IV](#setting-the-iv). Ensure that the related parameters are correctly set when the **Cipher** instance is generated and initialized.

- Example (using asynchronous APIs):

  <!-- @[async_symmetry_encrypt_decrypt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidance3DES/entry/src/main/ets/pages/3des_ecb_encryption_decryption_asynchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    let symKey = await symGenerator.convertKey(symKeyBlob);
    console.info('convertKey result: success.');
    return symKey;
  }
  
  async function main() {
    let keyData =
      new Uint8Array([238, 249, 61, 55, 128, 220, 183, 224, 139, 253, 248, 239, 239, 41, 71, 25, 235, 206, 230, 162, 249,
        27, 234, 114]);
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
  }
  ```

- Example (using synchronous APIs):

  <!-- @[sync_symmetry_encrypt_decrypt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidance3DES/entry/src/main/ets/pages/3des_ecb_encryption_decryption_synchronous.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    let symKey = symGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync result: success.');
    return symKey;
  }
  
  function main() {
    let keyData =
      new Uint8Array([238, 249, 61, 55, 128, 220, 183, 224, 139, 253, 248, 239, 239, 41, 71, 25, 235, 206, 230, 162, 249,
        27, 234, 114]);
    let symKey = genSymKeyByData(keyData);
    let message = 'This is a test';
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = encryptMessage(symKey, plainText);
    let decryptText = decryptMessage(symKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed');
    }
  }
  ```

### Setting the IV

The following example demonstrates how to set the IV when the CBC mode is used.

If CBC, CTR, OFB, or CFB mode is used, set the IV in the same way. If ECB mode is used, you do not need to set this parameter.

  ```ts
  function genIvParamsSpec() {
    let ivBlob = generateRandom(8); // The IV length for 3DES CBC, CFB, OFB, and CTR modes is 8 bytes.
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: "IvParamsSpec",
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  let iv = genIvParamsSpec();
  let cipher = cryptoFramework.createCipher('3DES192|CBC|PKCS7');
  cipher.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
  // This code snippet only demonstrates the differences between CBC, CTR, OFB, and CFB block cipher modes. For other processes, refer to the development example.
  ```

  <!--no_check-->