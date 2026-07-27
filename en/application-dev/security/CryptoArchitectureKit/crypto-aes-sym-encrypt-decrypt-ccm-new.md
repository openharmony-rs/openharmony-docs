# Encryption and Decryption Using an AES Symmetric Key (CCM Mode) with AeadParamsSpec (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

Since API version 26.0.0, the **AeadParamsSpec** parameter can be used for encryption and decryption of [AES](crypto-sym-encrypt-decrypt-spec.md#aes) symmetric keys (CCM mode).

**Key Generation**

Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1) to generate a 128-bit AES symmetric key (**SymKey**).
   
   In addition to the example in this topic, [AES](crypto-sym-key-generation-conversion-spec.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly.md) may help you better understand how to generate an AES symmetric key. Note that the input parameters in the reference documents may be different from those in the example below.


**Encryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'AES128|CCM'** to create a **Cipher** instance for encryption. The key type is AES-128, and the block cipher mode is CCM.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey**, and parameter to **AeadParamsSpec** corresponding to the CCM mode.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

   > **NOTE**
   >
   > Only one of **update** and **doFinal** can be called for encryption in CCM mode. Each method can be called only once.
   > 
   > When a **Cipher** instance is initialized with **AeadParamsSpec**, the authentication tag (**authTag**) is automatically appended to the ciphertext and does not need to be saved separately.
   >
   > In CCM mode using **AeadParamsSpec**, the algorithm library supports **tagLen** ranging from 4 to 16 bytes. If no tag length is specified, the default length of 12 bytes is used.

**Decryption**

1. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'AES128|CCM'** to create a **Cipher** instance for decryption. The key type is AES128, and the block cipher mode is CCM.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey**, and parameter to **AeadParamsSpec** corresponding to the CCM mode.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

## Example Code

- Example (using asynchronous APIs):
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



- Example (using synchronous APIs):
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
