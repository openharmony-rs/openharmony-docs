# Encryption and Decryption with a 3DES Symmetric Key (ECB Mode) (ArkTS)

For details about the algorithm specifications, see [3DES](crypto-sym-encrypt-decrypt-spec.md#3des).

## How to Develop

**Encryption**

1. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a 192-bit 3DES symmetric key (**SymKey**).
   
   In addition to the example in this topic, [3DES](crypto-sym-key-generation-conversion-spec.md#3des) and [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md) may help you better understand how to generate a 3DES symmetric key pair. Note that the input parameters in the reference documents may be different from those in the example below.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for encryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In **Cipher.init**, set **opMode** to **CryptoMode.ENCRYPT_MODE** (encryption) and **key** to **SymKey** (the key used for encryption).
   
   If the ECB mode is used, pass **null**.

4. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be encrypted (plaintext).
   
   - If the amount of data to be encrypted is less than 100 KB, you can use **Cipher.doFinal** immediately after **Cipher.init**.
   - If the data size exceeds a certain threshold, call **Cipher.update** for multiple times for segment-based encryption and decryption.
   - You can determine the data size. For example, call **Cipher.update** when the data size is greater than 20 bytes.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.
   
  - If **Cipher.update** has been called, set **data** is set to **null**.
  - Note that the **Cipher.doFinal** output may be **null**.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for decryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. In **Cipher.init**, set **opMode** to **CryptoMode.DECRYPT_MODE** (decryption) and **key** to **SymKey** (the key used for decryption). If ECB mode is used, pass **null**.

3. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass in the data to be decrypted (ciphertext).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

## Example

If the cipher mode is ECB, you do not need to set encryption and decryption parameters.

If the cipher mode is CBC, CTR, OFB, or CFB, you must set the IV and modify the parameters when the **Cipher** instance is generated and initialized during encryption and decryption. For details about how to set the IV, see [Setting the IV](#setting-the-iv).

- Example (using asynchronous APIs):

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  // Encrypt the message.
  async function encryptMessagePromise(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    // If CBC, CTR, OFB, or CFB is used, modify the cipher mode and set the IV.
    let cipher = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  // Decrypt the message.
  async function decryptMessagePromise(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    // If CBC, CTR, OFB, or CFB is used, modify the cipher mode and set the IV.
    let decoder = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    let symKey = await symGenerator.convertKey(symKeyBlob);
    console.info('convertKey success');
    return symKey;
  }
  async function main() {
    let keyData = new Uint8Array([238, 249, 61, 55, 128, 220, 183, 224, 139, 253, 248, 239, 239, 41, 71, 25, 235, 206, 230, 162, 249, 27, 234, 114]);
    let symKey = await genSymKeyByData(keyData);
    let message = "This is a test";
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

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  // Encrypt the message.
  function encryptMessage(symKey: cryptoFramework.SymKey, plainText: cryptoFramework.DataBlob) {
    // If CBC, CTR, OFB, or CFB is used, modify the cipher mode and set the IV.
    let cipher = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, null);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  // Decrypt the message.
  function decryptMessage(symKey: cryptoFramework.SymKey, cipherText: cryptoFramework.DataBlob) {
    // If CBC, CTR, OFB, or CFB is used, modify the cipher mode and set the IV.
    let decoder = cryptoFramework.createCipher('3DES192|ECB|PKCS7');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let symGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    let symKey = symGenerator.convertKeySync(symKeyBlob);
    console.info('convertKeySync success');
    return symKey;
  }
  function main() {
    let keyData = new Uint8Array([238, 249, 61, 55, 128, 220, 183, 224, 139, 253, 248, 239, 239, 41, 71, 25, 235, 206, 230, 162, 249, 27, 234, 114]);
    let symKey = genSymKeyByData(keyData);
    let message = "This is a test";
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

If CBC, CTR, OFB, or CFB mode is used, set the IV in the same way. If ECB mode is used, you do not need to set the decryption parameters.

  ```ts
  function genIvParamsSpec() {
    let ivBlob = generateRandom (8); // The IV for 3DES CBC, CFB, OFB, or CTR is of 8 bytes.
    let ivParamsSpec: cryptoFramework.IvParamsSpec = {
      algName: "IvParamsSpec",
      iv: ivBlob
    };
    return ivParamsSpec;
  }
  let iv = genIvParamsSpec();
  let cipher = cryptoFramework.createCipher('3DES192|CBC|PKCS7');
  cipher.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, iv);
  // This code snippet only shows the differences between CBC, CTR, OFB, and CFB modes. For details about other processes, see the related development examples.
  ```
