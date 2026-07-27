# Encryption and Decryption by Segment with an RSA Asymmetric Key Pair (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

For details about the algorithm specifications, see [RSA](crypto-asym-encrypt-decrypt-spec.md#rsa).

**Encryption**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate a 1024-bit RSA asymmetric key pair (**KeyPair**) with two primes. The number of primes is not specified by default. The **KeyPair** object includes a public key (**PubKey**) and a private key (**PriKey**).

   In addition to the example in this topic, [RSA](crypto-asym-key-generation-conversion-spec.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md) may help you better understand how to generate an RSA asymmetric key pair. Note that the input parameters in the reference documents may be different from those in the example below.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'RSA1024|PKCS1'** to create a **Cipher** instance for encryption. The key type is **RSA1024**, and the padding mode is **PKCS1**.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption) and key to **KeyPair.PubKey** (the key used for encryption).

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) multiple times to pass in the plaintext and encrypt it by segment.

   The output of **doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

   In this example, the plaintext is split by 64 bytes and encrypted multiple times by a 1024-bit key. A 128-byte ciphertext is generated each time.
   > **NOTE**
   > Segment-based encryption and decryption of asymmetric keys means that when the plaintext is longer than the data length supported by a single encryption or decryption operation, the data to be encrypted or decrypted needs to be divided into segments of proper length. For details, see [Asymmetric Encryption and Decryption](crypto-encrypt-decrypt-by-segment.md#asymmetric-encryption-and-decryption).

**Decryption**

1. If RSA is used, the **Cipher** instance cannot be initialized repeatedly. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) to create a new **Cipher** instance.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption) and key to **KeyPair.PriKey** (the key used for decryption). If PKCS1 is used, set **params** to **null**.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) multiple times to pass in the ciphertext and decrypt it by segment.

- Example (using asynchronous APIs):

  <!-- @[rsa_segmentation_encrypt_decrypt_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_segmentation/RSASegmentationAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message by segment.
  async function rsaEncryptBySegment(pubKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, pubKey, null);
    let plainTextSplitLen = 64;
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += plainTextSplitLen) {
      let updateMessage = plainText.data.subarray(i, i + plainTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the plaintext into 64-byte segments and repeatedly call doFinal for encryption. When using a 1024-bit key, each encryption produces a 128-byte ciphertext.
      let updateOutput = await cipher.doFinal(updateMessageBlob);
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message by segment.
  async function rsaDecryptBySegment(priKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, priKey, null);
    let cipherTextSplitLen = 128; // Length of ciphertext bytes generated per RSA encryption: Key size/8
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += cipherTextSplitLen) {
      let updateMessage = cipherText.data.subarray(i, i + cipherTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the ciphertext into 128-byte segments for decryption and then concatenate the resulting plaintext segments.
      let updateOutput = await decoder.doFinal(updateMessageBlob);
      let mergeText = new Uint8Array(decryptText.length + updateOutput.data.length);
      mergeText.set(decryptText);
      mergeText.set(updateOutput.data, decryptText.length);
      decryptText = mergeText;
    }
    let decryptBlob: cryptoFramework.DataBlob = { data: decryptText };
    return decryptBlob;
  }
  
  async function rsaEncryptLongMessage() {
    let message = 'This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!';
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024'); // Create an AsyKeyGenerator object.
    let keyPair = await asyKeyGenerator.generateKeyPair(); // Randomly generate an RSA key pair.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = await rsaEncryptBySegment(keyPair.pubKey, plainText);
    let decryptText = await rsaDecryptBySegment(keyPair.priKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```


- Example (using synchronous APIs):

  <!-- @[rsa_segmentation_encrypt_decrypt_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_segmentation/RSASegmentationSync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message by segment.
  function rsaEncryptBySegment(pubKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, pubKey, null);
    let plainTextSplitLen = 64;
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += plainTextSplitLen) {
      let updateMessage = plainText.data.subarray(i, i + plainTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the plaintext into 64-byte segments and repeatedly call doFinal for encryption. When using a 1024-bit key, each encryption produces a 128-byte ciphertext.
      let updateOutput = cipher.doFinalSync(updateMessageBlob);
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message by segment.
  function rsaDecryptBySegment(priKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, priKey, null);
    let cipherTextSplitLen = 128; // Length of ciphertext bytes generated per RSA encryption: Key size/8
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += cipherTextSplitLen) {
      let updateMessage = cipherText.data.subarray(i, i + cipherTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the ciphertext into 128-byte segments for decryption and then concatenate the resulting plaintext segments.
      let updateOutput = decoder.doFinalSync(updateMessageBlob);
      let mergeText = new Uint8Array(decryptText.length + updateOutput.data.length);
      mergeText.set(decryptText);
      mergeText.set(updateOutput.data, decryptText.length);
      decryptText = mergeText;
    }
    let decryptBlob: cryptoFramework.DataBlob = { data: decryptText };
    return decryptBlob;
  }
  
  function main() {
    let message = 'This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!' +
      'This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!';
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024'); // Create an AsyKeyGenerator object.
    let keyPair = asyKeyGenerator.generateKeyPairSync(); // Randomly generate an RSA key pair.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = rsaEncryptBySegment(keyPair.pubKey, plainText);
    let decryptText = rsaDecryptBySegment(keyPair.priKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      console.info('decrypt plainText: ' + buffer.from(decryptText.data).toString('utf-8'));
    } else {
      console.error('decrypt failed.');
    }
  }
  ```
