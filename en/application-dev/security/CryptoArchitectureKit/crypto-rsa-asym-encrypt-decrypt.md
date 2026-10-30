# RSA Asymmetric Key Encryption and Decryption (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3aff3c192b61804c6eafd655527edff9eb980a translatedAt=2026-10-30T03:50:48.518Z pushedAt=2026-10-30T08:06:31.368Z nl=1 -->

For the corresponding algorithm specifications, see [Asymmetric Key Encryption and Decryption Algorithm Specifications: RSA](crypto-encryption-decryption.md#rsa).

## Using an RSA Asymmetric Key for Encryption and Decryption (PKCS1 Mode)

**Encryption**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key pair (KeyPair) with the RSA key type RSA1024 and two prime numbers. The KeyPair object includes a public key (PubKey) and a private key (PriKey).

   To learn how to generate an RSA asymmetric key pair, refer to the following example together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters, so read them carefully to distinguish the differences.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter 'RSA1024|PKCS1' to create a Cipher instance with the asymmetric key type RSA1024 and the padding mode PKCS1, used to complete encryption and decryption operations.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (`cryptoFramework.CryptoMode.ENCRYPT_MODE`), specify the encryption key (`KeyPair.PubKey`), and initialize the encryption Cipher instance.

   An asymmetric key has no encryption parameters, so pass null directly.

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1), pass the plaintext, and obtain the encrypted data.

   - The doFinal output result may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.
   - When the data volume is large, you can call doFinal multiple times, that is, [segmented encryption and decryption](crypto-rsa-asym-encrypt-decrypt.md#using-rsa-asymmetric-keys-for-segmented-encryption-and-decryption).

**Decryption**

1. Because the Cipher instance of the RSA algorithm does not support repeated init operations, call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) to regenerate a Cipher instance.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (`cryptoFramework.CryptoMode.DECRYPT_MODE`), specify the decryption key (`KeyPair.PriKey`), and initialize the decryption Cipher instance. The PKCS1 mode has no encryption parameters, so pass null directly.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1), pass the ciphertext, and obtain the decrypted data.

- Asynchronous method example:

  <!-- @[rsa_pkcs1_encrypt_decrypt_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1/RSAPKCS1Async.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  async function encryptMessagePromise(publicKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, publicKey, null);
    let encryptData = await cipher.doFinal(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  async function decryptMessagePromise(privateKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, privateKey, null);
    let decryptData = await decoder.doFinal(cipherText);
    return decryptData;
  }
  
  // Generate an RSA key pair.
  async function genKeyPairByData(pubKeyData: Uint8Array, priKeyData: Uint8Array) {
    let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyData };
    let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyData };
    let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
    let keyPair = await rsaGenerator.convertKey(pubKeyBlob, priKeyBlob);
    console.info('convertKey result: success.');
    return keyPair;
  }
  
  async function main() {
    let pkData =
      new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
        2, 129, 129, 0, 197, 64, 10, 198, 14, 110, 65, 92, 206, 35, 28, 123, 153, 24, 134, 255, 145, 74, 42, 173, 40, 215,
        146, 58, 143, 46, 10, 195, 154, 160, 69, 196, 220, 152, 179, 44, 111, 200, 84, 78, 215, 73, 210, 181, 12, 29, 70,
        68, 36, 135, 153, 89, 230, 202, 130, 212, 111, 243, 234, 92, 131, 62, 145, 50, 73, 48, 104, 245, 46, 70, 45, 157,
        147, 143, 140, 162, 156, 216, 220, 49, 121, 142, 194, 33, 223, 201, 0, 16, 163, 210, 240, 118, 92, 147, 121, 220,
        17, 114, 24, 52, 125, 135, 176, 88, 21, 83, 86, 17, 156, 88, 250, 48, 79, 86, 128, 248, 105, 208, 133, 140, 13,
        153, 164, 191, 136, 164, 44, 53, 2, 3, 1, 0, 1]);
    let skData =
      new Uint8Array([48, 130, 2, 119, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 97, 48,
        130, 2, 93, 2, 1, 0, 2, 129, 129, 0, 197, 64, 10, 198, 14, 110, 65, 92, 206, 35, 28, 123, 153, 24, 134, 255, 145,
        74, 42, 173, 40, 215, 146, 58, 143, 46, 10, 195, 154, 160, 69, 196, 220, 152, 179, 44, 111, 200, 84, 78, 215, 73,
        210, 181, 12, 29, 70, 68, 36, 135, 153, 89, 230, 202, 130, 212, 111, 243, 234, 92, 131, 62, 145, 50, 73, 48, 104,
        245, 46, 70, 45, 157, 147, 143, 140, 162, 156, 216, 220, 49, 121, 142, 194, 33, 223, 201, 0, 16, 163, 210, 240,
        118, 92, 147, 121, 220, 17, 114, 24, 52, 125, 135, 176, 88, 21, 83, 86, 17, 156, 88, 250, 48, 79, 86, 128, 248,
        105, 208, 133, 140, 13, 153, 164, 191, 136, 164, 44, 53, 2, 3, 1, 0, 1, 2, 129, 128, 70, 75, 184, 139, 53, 1, 94,
        17, 240, 244, 218, 101, 193, 253, 215, 190, 164, 204, 197, 192, 200, 89, 107, 39, 171, 119, 65, 38, 204, 168, 105,
        180, 234, 217, 16, 161, 185, 132, 175, 103, 25, 154, 153, 153, 36, 36, 26, 178, 150, 66, 45, 8, 185, 19, 90, 228,
        210, 177, 30, 200, 177, 141, 78, 184, 248, 59, 113, 154, 145, 73, 160, 24, 73, 157, 86, 207, 186, 32, 95, 200,
        106, 252, 107, 69, 170, 193, 216, 196, 181, 142, 74, 203, 15, 18, 89, 228, 152, 19, 239, 21, 233, 98, 121, 214,
        57, 187, 111, 239, 223, 248, 199, 70, 223, 108, 108, 113, 234, 144, 155, 95, 246, 144, 244, 122, 39, 55, 127, 81,
        2, 65, 0, 246, 96, 188, 0, 0, 104, 221, 105, 139, 144, 63, 175, 209, 87, 179, 162, 88, 192, 99, 82, 125, 53, 54,
        48, 70, 245, 239, 37, 15, 242, 247, 84, 115, 187, 196, 95, 156, 40, 165, 60, 64, 102, 13, 229, 243, 2, 149, 0,
        232, 226, 221, 192, 95, 11, 12, 208, 5, 181, 98, 62, 210, 190, 141, 235, 2, 65, 0, 204, 244, 34, 10, 105, 80, 76,
        116, 163, 35, 231, 168, 187, 206, 189, 101, 215, 103, 80, 115, 86, 11, 34, 127, 203, 114, 84, 188, 121, 174, 169,
        31, 142, 2, 182, 27, 140, 225, 157, 227, 71, 98, 15, 203, 187, 213, 5, 190, 20, 121, 8, 30, 193, 100, 232, 101,
        141, 8, 124, 20, 29, 78, 6, 95, 2, 65, 0, 204, 43, 225, 224, 6, 118, 224, 117, 100, 200, 199, 94, 70, 23, 109,
        175, 173, 232, 208, 230, 61, 8, 105, 189, 156, 48, 150, 91, 154, 89, 248, 136, 173, 215, 254, 166, 84, 220, 130,
        1, 234, 68, 40, 100, 84, 251, 224, 202, 254, 51, 115, 28, 198, 38, 124, 25, 175, 129, 94, 199, 61, 17, 216, 189,
        2, 64, 72, 230, 129, 129, 48, 138, 134, 87, 106, 123, 231, 247, 165, 173, 216, 194, 115, 198, 228, 223, 209, 120,
        46, 114, 68, 92, 75, 117, 170, 214, 140, 131, 147, 208, 181, 19, 193, 157, 178, 186, 87, 246, 178, 101, 166, 79,
        20, 54, 211, 51, 101, 199, 2, 197, 48, 192, 134, 84, 193, 69, 170, 82, 201, 131, 2, 65, 0, 213, 165, 55, 166, 131,
        210, 195, 56, 250, 147, 195, 61, 205, 208, 189, 185, 40, 52, 50, 119, 137, 23, 246, 46, 220, 108, 52, 23, 152,
        154, 94, 32, 144, 195, 184, 249, 21, 168, 12, 57, 222, 18, 60, 117, 81, 157, 72, 30, 155, 190, 165, 242, 228, 139,
        240, 184, 145, 170, 103, 210, 160, 161, 135, 13]);
    let keyPair = await genKeyPairByData(pkData, skData);
    let pubKey = keyPair.pubKey;
    let priKey = keyPair.priKey;
    let message = 'This is a test';
    // Decode the string into a Uint8Array using UTF-8.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = await encryptMessagePromise(pubKey, plainText);
    let decryptText = await decryptMessagePromise(priKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      // Encode the Uint8Array into a string using UTF-8.
      let messageDecrypted = buffer.from(decryptText.data).toString('utf-8');
      console.info('decrypted result string: ' + messageDecrypted);
    } else {
      console.error('decrypt failed.');
    }
  }
  ```


- Synchronous method example:

  <!-- @[rsa_pkcs1_encrypt_decrypt_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1/RSAPKCS1Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message.
  function encryptMessage(publicKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, publicKey, null);
    let encryptData = cipher.doFinalSync(plainText);
    return encryptData;
  }
  
  // Decrypt the message.
  function decryptMessage(privateKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, privateKey, null);
    let decryptData = decoder.doFinalSync(cipherText);
    return decryptData;
  }
  
  // Generate an RSA key pair.
  function genKeyPairByData(pubKeyData: Uint8Array, priKeyData: Uint8Array) {
    let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyData };
    let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyData };
    let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
    let keyPair = rsaGenerator.convertKeySync(pubKeyBlob, priKeyBlob);
    console.info('convertKeySync result: success.');
    return keyPair;
  }
  
  function main() {
    let pkData =
      new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
        2, 129, 129, 0, 197, 64, 10, 198, 14, 110, 65, 92, 206, 35, 28, 123, 153, 24, 134, 255, 145, 74, 42, 173, 40, 215,
        146, 58, 143, 46, 10, 195, 154, 160, 69, 196, 220, 152, 179, 44, 111, 200, 84, 78, 215, 73, 210, 181, 12, 29, 70,
        68, 36, 135, 153, 89, 230, 202, 130, 212, 111, 243, 234, 92, 131, 62, 145, 50, 73, 48, 104, 245, 46, 70, 45, 157,
        147, 143, 140, 162, 156, 216, 220, 49, 121, 142, 194, 33, 223, 201, 0, 16, 163, 210, 240, 118, 92, 147, 121, 220,
        17, 114, 24, 52, 125, 135, 176, 88, 21, 83, 86, 17, 156, 88, 250, 48, 79, 86, 128, 248, 105, 208, 133, 140, 13,
        153, 164, 191, 136, 164, 44, 53, 2, 3, 1, 0, 1]);
    let skData =
      new Uint8Array([48, 130, 2, 119, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 97, 48,
        130, 2, 93, 2, 1, 0, 2, 129, 129, 0, 197, 64, 10, 198, 14, 110, 65, 92, 206, 35, 28, 123, 153, 24, 134, 255, 145,
        74, 42, 173, 40, 215, 146, 58, 143, 46, 10, 195, 154, 160, 69, 196, 220, 152, 179, 44, 111, 200, 84, 78, 215, 73,
        210, 181, 12, 29, 70, 68, 36, 135, 153, 89, 230, 202, 130, 212, 111, 243, 234, 92, 131, 62, 145, 50, 73, 48, 104,
        245, 46, 70, 45, 157, 147, 143, 140, 162, 156, 216, 220, 49, 121, 142, 194, 33, 223, 201, 0, 16, 163, 210, 240,
        118, 92, 147, 121, 220, 17, 114, 24, 52, 125, 135, 176, 88, 21, 83, 86, 17, 156, 88, 250, 48, 79, 86, 128, 248,
        105, 208, 133, 140, 13, 153, 164, 191, 136, 164, 44, 53, 2, 3, 1, 0, 1, 2, 129, 128, 70, 75, 184, 139, 53, 1, 94,
        17, 240, 244, 218, 101, 193, 253, 215, 190, 164, 204, 197, 192, 200, 89, 107, 39, 171, 119, 65, 38, 204, 168, 105,
        180, 234, 217, 16, 161, 185, 132, 175, 103, 25, 154, 153, 153, 36, 36, 26, 178, 150, 66, 45, 8, 185, 19, 90, 228,
        210, 177, 30, 200, 177, 141, 78, 184, 248, 59, 113, 154, 145, 73, 160, 24, 73, 157, 86, 207, 186, 32, 95, 200,
        106, 252, 107, 69, 170, 193, 216, 196, 181, 142, 74, 203, 15, 18, 89, 228, 152, 19, 239, 21, 233, 98, 121, 214,
        57, 187, 111, 239, 223, 248, 199, 70, 223, 108, 108, 113, 234, 144, 155, 95, 246, 144, 244, 122, 39, 55, 127, 81,
        2, 65, 0, 246, 96, 188, 0, 0, 104, 221, 105, 139, 144, 63, 175, 209, 87, 179, 162, 88, 192, 99, 82, 125, 53, 54,
        48, 70, 245, 239, 37, 15, 242, 247, 84, 115, 187, 196, 95, 156, 40, 165, 60, 64, 102, 13, 229, 243, 2, 149, 0,
        232, 226, 221, 192, 95, 11, 12, 208, 5, 181, 98, 62, 210, 190, 141, 235, 2, 65, 0, 204, 244, 34, 10, 105, 80, 76,
        116, 163, 35, 231, 168, 187, 206, 189, 101, 215, 103, 80, 115, 86, 11, 34, 127, 203, 114, 84, 188, 121, 174, 169,
        31, 142, 2, 182, 27, 140, 225, 157, 227, 71, 98, 15, 203, 187, 213, 5, 190, 20, 121, 8, 30, 193, 100, 232, 101,
        141, 8, 124, 20, 29, 78, 6, 95, 2, 65, 0, 204, 43, 225, 224, 6, 118, 224, 117, 100, 200, 199, 94, 70, 23, 109,
        175, 173, 232, 208, 230, 61, 8, 105, 189, 156, 48, 150, 91, 154, 89, 248, 136, 173, 215, 254, 166, 84, 220, 130,
        1, 234, 68, 40, 100, 84, 251, 224, 202, 254, 51, 115, 28, 198, 38, 124, 25, 175, 129, 94, 199, 61, 17, 216, 189,
        2, 64, 72, 230, 129, 129, 48, 138, 134, 87, 106, 123, 231, 247, 165, 173, 216, 194, 115, 198, 228, 223, 209, 120,
        46, 114, 68, 92, 75, 117, 170, 214, 140, 131, 147, 208, 181, 19, 193, 157, 178, 186, 87, 246, 178, 101, 166, 79,
        20, 54, 211, 51, 101, 199, 2, 197, 48, 192, 134, 84, 193, 69, 170, 82, 201, 131, 2, 65, 0, 213, 165, 55, 166, 131,
        210, 195, 56, 250, 147, 195, 61, 205, 208, 189, 185, 40, 52, 50, 119, 137, 23, 246, 46, 220, 108, 52, 23, 152,
        154, 94, 32, 144, 195, 184, 249, 21, 168, 12, 57, 222, 18, 60, 117, 81, 157, 72, 30, 155, 190, 165, 242, 228, 139,
        240, 184, 145, 170, 103, 210, 160, 161, 135, 13]);
    let keyPair = genKeyPairByData(pkData, skData);
    let pubKey = keyPair.pubKey;
    let priKey = keyPair.priKey;
    let message = 'This is a test';
    // Decode the string into a Uint8Array using UTF-8.
    let plainText: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(message, 'utf-8').buffer) };
    let encryptText = encryptMessage(pubKey, plainText);
    let decryptText = decryptMessage(priKey, encryptText);
    if (plainText.data.toString() === decryptText.data.toString()) {
      console.info('decrypt ok.');
      // Encode the Uint8Array into a string using UTF-8.
      let messageDecrypted = buffer.from(decryptText.data).toString('utf-8');
      console.info('decrypted result string: ' + messageDecrypted);
    } else {
      console.error('decrypt failed.');
    }
  }
  ```


## Using RSA Asymmetric Keys for Segmented Encryption and Decryption

**Encryption**

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1) to generate an asymmetric key pair (KeyPair) with the RSA key type RSA1024 and two prime numbers (the default when not specified). The KeyPair object includes a public key (PubKey) and a private key (PriKey).

   To learn how to generate an RSA asymmetric key pair, refer to the following example together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters, so read them carefully to distinguish the differences.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) and specify the string parameter 'RSA1024|PKCS1' to create a Cipher instance with the asymmetric key type RSA1024 and the padding mode PKCS1, used to complete encryption and decryption operations.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (cryptoFramework.CryptoMode.ENCRYPT_MODE), specify the encryption key (KeyPair.PubKey), and initialize the encryption Cipher instance.

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) multiple times, passing the plaintext, to obtain the encrypted data.

   The doFinal output result may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

   Here, the plaintext is split into 64-byte groups and encrypted multiple times. With a 1024-bit key, each encryption produces 128 bytes of ciphertext.
   > **Note:**
   >
   > Segmented encryption and decryption with asymmetric keys means that when the plaintext exceeds the data length supported by a single encryption or decryption operation, the data to be encrypted or decrypted must be divided into data segments of appropriate length, and the encryption or decryption operation is performed on each segment. For details, see [Introduction to Asymmetric Segmented Encryption and Decryption](crypto-encryption-decryption.md#asymmetric-encryptiondecryption).

**Decryption**

1. Because the Cipher instance of the RSA algorithm does not support repeated init operations, call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) to regenerate a Cipher instance.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (cryptoFramework.CryptoMode.DECRYPT_MODE), specify the decryption key (KeyPair.PriKey), and initialize the decryption Cipher instance. The PKCS1 mode has no encryption parameters, so pass null directly.

3. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) multiple times, passing the ciphertext, to obtain the decrypted data.

- Asynchronous method example:

  <!-- @[rsa_segmentation_encrypt_decrypt_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_segmentation/RSASegmentationAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message in segments.
  async function rsaEncryptBySegment(pubKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, pubKey, null);
    let plainTextSplitLen = 64;
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += plainTextSplitLen) {
      let updateMessage = plainText.data.subarray(i, i + plainTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the plaintext into 64-byte segments and call doFinal in a loop for encryption. With a 1024-bit key, each encryption produces 128 bytes of ciphertext.
      let updateOutput = await cipher.doFinal(updateMessageBlob);
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message in segments.
  async function rsaDecryptBySegment(priKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, priKey, null);
    let cipherTextSplitLen = 128; // Ciphertext byte length produced per RSA encryption: key bits / 8.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += cipherTextSplitLen) {
      let updateMessage = cipherText.data.subarray(i, i + cipherTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the ciphertext into 128-byte segments for decryption, and concatenate the resulting plaintext.
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
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024'); // Create an asymmetric key generator object.
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


- Synchronous method example:

  <!-- @[rsa_segmentation_encrypt_decrypt_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_segmentation/RSASegmentationSync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Encrypt the message in segments.
  function rsaEncryptBySegment(pubKey: cryptoFramework.PubKey, plainText: cryptoFramework.DataBlob) {
    let cipher = cryptoFramework.createCipher('RSA1024|PKCS1');
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, pubKey, null);
    let plainTextSplitLen = 64;
    let cipherText = new Uint8Array();
    for (let i = 0; i < plainText.data.length; i += plainTextSplitLen) {
      let updateMessage = plainText.data.subarray(i, i + plainTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the plaintext into 64-byte segments and call doFinal in a loop for encryption. With a 1024-bit key, each encryption produces 128 bytes of ciphertext.
      let updateOutput = cipher.doFinalSync(updateMessageBlob);
      let mergeText = new Uint8Array(cipherText.length + updateOutput.data.length);
      mergeText.set(cipherText);
      mergeText.set(updateOutput.data, cipherText.length);
      cipherText = mergeText;
    }
    let cipherBlob: cryptoFramework.DataBlob = { data: cipherText };
    return cipherBlob;
  }
  
  // Decrypt the message in segments.
  function rsaDecryptBySegment(priKey: cryptoFramework.PriKey, cipherText: cryptoFramework.DataBlob) {
    let decoder = cryptoFramework.createCipher('RSA1024|PKCS1');
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, priKey, null);
    let cipherTextSplitLen = 128; // Method for calculating the ciphertext byte length generated by each RSA key encryption: key bits/8.
    let decryptText = new Uint8Array();
    for (let i = 0; i < cipherText.data.length; i += cipherTextSplitLen) {
      let updateMessage = cipherText.data.subarray(i, i + cipherTextSplitLen);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      // Split the ciphertext into 128-byte chunks for decryption, and concatenate the decrypted plaintext.
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
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024'); // Create an asymmetric key generator object.
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

## Encryption and Decryption Using an RSA Asymmetric Key (PKCS1_OAEP Mode)

**Encryption**

1. Call [cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10) and [AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10), and specify the key parameters to generate an RSA asymmetric key pair (KeyPair).
   
   To generate an RSA asymmetric key pair, refer to the following example together with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Generating an Asymmetric Key Pair from Key Specifications](crypto-generate-asym-key-pair-from-key-spec.md). Note that the input parameters in the reference documents may differ from those in the current example.

2. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter `'RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1'` to create a `Cipher` instance for the RSA key with the asymmetric key type `RSA2048`, padding mode `PKCS1_OAEP`, digest algorithm `SHA256`, and mask digest `MGF1_SHA1`, used to complete encryption and decryption operations.

3. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to encryption (`cryptoFramework.CryptoMode.ENCRYPT_MODE`), specify the encryption key (`KeyPair.PubKey`), and initialize the encryption `Cipher` instance.
   
   An asymmetric key has no encryption parameters, so pass `null` directly.

4. Before calling `Cipher.doFinal`, call [Cipher.setCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setcipherspec10) to set the PKCS1_OAEP padding parameter `pSource`. Call [Cipher.getCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getcipherspec10) to obtain the OAEP-related parameters.

5. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1), pass the plaintext, and obtain the encrypted data.

**Decryption**

1. Because the `Cipher` instance of the RSA algorithm does not support repeated `init` operations, call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) to regenerate the `Cipher` instance.

2. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to set the mode to decryption (`cryptoFramework.CryptoMode.DECRYPT_MODE`), specify the decryption key (`KeyPair.PriKey`), and initialize the decryption `Cipher` instance. The PKCS1_OAEP mode has no additional encryption parameters, so pass `null` directly.

3. Before calling `Cipher.doFinal`, call [Cipher.setCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setcipherspec10) to set the PKCS1_OAEP padding parameter `pSource`, which must be consistent with the value set during encryption. Call [Cipher.getCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getcipherspec10) to obtain the OAEP-related parameters.

4. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1), pass the ciphertext, and obtain the decrypted data.

- Asynchronous method example:

  <!-- @[pss_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1_oaep/RSAPKCS1OAEPAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  // Construct RSA asymmetric key pair parameters based on the key parameter attributes.
  function genRsaKeyPairSpec(nIn: bigint, eIn: bigint, dIn: bigint) {
    let rsaCommSpec: cryptoFramework.RSACommonParamsSpec = {
      n: nIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC
    };
    let rsaKeyPairSpec: cryptoFramework.RSAKeyPairSpec = {
      params: rsaCommSpec,
      sk: dIn,
      pk: eIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC
    };
    return rsaKeyPairSpec;
  }
  
  // Generate RSA2048 key pair parameters.
  function genRsa2048KeyPairSpec(): cryptoFramework.RSAKeyPairSpec {
    let nIn =
      BigInt('0x9260d0750ae117eee55c3f3deaba74917521a262ee76007cdf8a56755ad73a1598a1408410a01434c3f5bc54a88b57fa19fc4328daea0750a4c44e88cff3b2382621b80f670464433e4336e6d003e8cd65bff211da144b88291c2259a00a72b711c116ef7686e8fee34e4d933c868187bdc26f7be071493c86f7a5941c3510806ad67b0f94d88f5cf5c02a092821d8626e8932b65c5bd8c92049c210932b7afa7ac59c0e886ae5c1edb00d8ce2c57633db26bd6639bff73cee82be9275c402b4cf2a4388da8cf8c64eefe1c5a0f5ab8057c39fa5c0589c3e253f0960332300f94bea44877b588e1edbde97cf2360727a09b775262d7ee552b3319b9266f05a25');
    let eIn = BigInt('0x010001');
    let dIn =
      BigInt('0x6a7df2ca63ead4dda191d614b6b385e0d9056a3d6d5cfe07db1daabee022db08212d97613d3328e0267c9dd23d787abde2afcb306aeb7dfce69246cc73f5c87fdf06030179a2114b767db1f083ff841c025d7dc00cd82435b9a90f695369e94df23d2ce458bc3b3283ad8bba2b8fa1ba62e2dce9accff3799aae7c840016f3ba8e0048c0b6cc4339af7161003a5beb864a0164b2c1c9237b64bc87556994351b27506c33d4bcdfce0f9c491a7d6b0628c7c852be4f0a9c3132b2ed3a2c8881e9aab07e20e17deb074691be677776a78b5c502e05d9bdde72126b3738695e2dd1a0a98a14247c65d8a7ee79432a092cb0721a12df798e44f7cfce0c498147a9b1');
    return genRsaKeyPairSpec(nIn, eIn, dIn);
  }
  
  async function rsaUseSpecDecryptOAEPPromise() {
    let plan = 'This is a test';
    // Obtain the RSA key pair parameter object.
    let rsaKeyPairSpec = genRsa2048KeyPairSpec();
    // Generate an RSA key pair based on the RSA key pair parameters.
    let rsaGeneratorSpec = cryptoFramework.createAsyKeyGeneratorBySpec(rsaKeyPairSpec);
    let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
    let decoder = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
    // RSA encryption and decryption PKCS1-OAEP mode padding byte stream P.
    let pSource = new Uint8Array([1, 2, 3, 4]);
    let input: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(plan, 'utf-8').buffer) };
    // Generate a key pair.
    let keyPair = await rsaGeneratorSpec.generateKeyPair();
    // Initialize the encryption operation.
    await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, keyPair.pubKey, null);
    // The get and set operations can be placed after the Cipher object init. Perform set and get operations on the cipher here.
    cipher.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
    let retP = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR);
    // Compare whether the P byte stream obtained by get is consistent with the P byte stream set.
    if (retP.toString() != pSource.toString()) {
      console.error('error init pSource ' + retP);
    } else {
      console.info('pSource changed == ' + retP);
    }
    // Perform the get operation for other OAEP parameters.
    let md = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
    console.info('md == ' + md);
    let mgf = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF_NAME_STR);
    console.info('mgf == ' + mgf);
    let mgf1Md = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_MD_STR);
    console.info('mgf1Md == ' + mgf1Md);
    let cipherDataBlob = await cipher.doFinal(input);
    // The get and set operations can be placed before the init of the Cipher object and are equivalent to those after init. Here, set and get operations are performed on the decoder.
    decoder.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
    retP = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR);
    // Compare whether the P byte stream obtained by get is consistent with the P byte stream set.
    if (retP.toString() != pSource.toString()) {
      console.error('error init pSource ' + retP);
    } else {
      console.info('pSource changed == ' + retP);
    }
    // Perform the get operation for other OAEP parameters.
    md = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
    console.info('md == ' + md);
    mgf = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF_NAME_STR);
    console.info('mgf == ' + mgf);
    mgf1Md = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_MD_STR);
    console.info('mgf1Md == ' + mgf1Md);
    // Initialize the decryption operation.
    await decoder.init(cryptoFramework.CryptoMode.DECRYPT_MODE, keyPair.priKey, null);
    let decodeData = await decoder.doFinal(cipherDataBlob);
    // Decryption succeeded.
    if (decodeData.data.toString() === input.data.toString()) {
      console.info('oaep decrypt result: success.');
    } else {
      console.error('oaep decrypt result: fail.');
    }
  }
  ```

- Synchronous method example:

  <!-- @[pss_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1_oaep/RSAPKCS1OAEPSync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  // Construct RSA asymmetric key pair parameters based on the key parameter attributes.
  function genRsaKeyPairSpec(nIn: bigint, eIn: bigint, dIn: bigint) {
    let rsaCommSpec: cryptoFramework.RSACommonParamsSpec = {
      n: nIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC
    };
    let rsaKeyPairSpec: cryptoFramework.RSAKeyPairSpec = {
      params: rsaCommSpec,
      sk: dIn,
      pk: eIn,
      algName: 'RSA',
      specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC
    };
    return rsaKeyPairSpec;
  }
  // Generate RSA2048 key pair parameters.
  function genRsa2048KeyPairSpec(): cryptoFramework.RSAKeyPairSpec {
    let nIn = BigInt('0x9260d0750ae117eee55c3f3deaba74917521a262ee76007cdf8a56755ad73a1598a1408410a01434c3f5bc54a88b57fa19fc4328daea0750a4c44e88cff3b2382621b80f670464433e4336e6d003e8cd65bff211da144b88291c2259a00a72b711c116ef7686e8fee34e4d933c868187bdc26f7be071493c86f7a5941c3510806ad67b0f94d88f5cf5c02a092821d8626e8932b65c5bd8c92049c210932b7afa7ac59c0e886ae5c1edb00d8ce2c57633db26bd6639bff73cee82be9275c402b4cf2a4388da8cf8c64eefe1c5a0f5ab8057c39fa5c0589c3e253f0960332300f94bea44877b588e1edbde97cf2360727a09b775262d7ee552b3319b9266f05a25');
    let eIn = BigInt('0x010001');
    let dIn = BigInt('0x6a7df2ca63ead4dda191d614b6b385e0d9056a3d6d5cfe07db1daabee022db08212d97613d3328e0267c9dd23d787abde2afcb306aeb7dfce69246cc73f5c87fdf06030179a2114b767db1f083ff841c025d7dc00cd82435b9a90f695369e94df23d2ce458bc3b3283ad8bba2b8fa1ba62e2dce9accff3799aae7c840016f3ba8e0048c0b6cc4339af7161003a5beb864a0164b2c1c9237b64bc87556994351b27506c33d4bcdfce0f9c491a7d6b0628c7c852be4f0a9c3132b2ed3a2c8881e9aab07e20e17deb074691be677776a78b5c502e05d9bdde72126b3738695e2dd1a0a98a14247c65d8a7ee79432a092cb0721a12df798e44f7cfce0c498147a9b1');
    return genRsaKeyPairSpec(nIn, eIn, dIn);
  }
  function main() {
    let plan = 'This is a test';
    // Obtain the RSA key pair parameter object.
    let rsaKeyPairSpec = genRsa2048KeyPairSpec();
    // Generate an RSA key pair based on the RSA key pair parameters.
    let rsaGeneratorSpec = cryptoFramework.createAsyKeyGeneratorBySpec(rsaKeyPairSpec);
    let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
    let decoder = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
    // P byte stream for RSA encryption and decryption in PKCS1-OAEP padding mode.
    let pSource = new Uint8Array([1, 2, 3, 4]);
    let input: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from(plan, 'utf-8').buffer) };
    // Generate a key pair.
    let keyPair = rsaGeneratorSpec.generateKeyPairSync();
    // Initialize the encryption operation.
    cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, keyPair.pubKey, null);
    // The get and set operations can be placed after the Cipher object init. Here, perform set and get operations on cipher.
    cipher.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
    let retP = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR);
    // Compare whether the P byte stream obtained by get is consistent with the P byte stream set.
    if (retP.toString() != pSource.toString()) {
      console.error('error init pSource ' + retP);
    } else {
      console.info('pSource changed == ' + retP);
    }
    // Perform get operations on other OAEP parameters.
    let md = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
    console.info('md == ' + md);
    let mgf = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF_NAME_STR);
    console.info('mgf == ' + mgf);
    let mgf1Md = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_MD_STR);
    console.info('mgf1Md == ' + mgf1Md);
    let cipherDataBlob = cipher.doFinalSync(input);
    // The get and set operations can be placed before the Cipher object init and are equivalent to those after init. Here, perform set and get operations on decoder.
    decoder.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
    retP = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR);
    // Compare whether the P byte stream obtained by get is consistent with the P byte stream set.
    if (retP.toString() != pSource.toString()) {
      console.error('error init pSource ' + retP);
    } else {
      console.info('pSource changed == ' + retP);
    }
    // Perform get operations on other OAEP parameters.
    md = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
    console.info('md == ' + md);
    mgf = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF_NAME_STR);
    console.info('mgf == ' + mgf);
    mgf1Md = decoder.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_MD_STR);
    console.info('mgf1Md == ' + mgf1Md);
    // Initialize the decryption operation.
    decoder.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, keyPair.priKey, null);
    let decodeData = decoder.doFinalSync(cipherDataBlob);
    // Decryption succeeded.
    if (decodeData.data.toString() === input.data.toString()) {
      console.info('oaep decrypt result: success.');
    } else {
      console.error('oaep decrypt result: fail.');
    }
  }
  ```


