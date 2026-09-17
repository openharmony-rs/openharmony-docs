# Encryption and Decryption with an RSA Asymmetric Key Pair (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=64044667f2ece520228c37a4e282d90b2e014ba4 translatedAt=2026-09-03T11:13:07.879Z pushedAt=2026-09-03T11:28:25.099Z -->

For the corresponding algorithm specifications, see [Asymmetric Key Encryption and Decryption Algorithm Specifications: RSA](crypto-encryption-decryption.md#rsa).

## Using RSA Asymmetric Keys for Encryption and Decryption (PKCS1 Mode)

**Encryption**

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) and [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to generate an asymmetric key pair (**keyPair**) of the RSA1024 type with two prime numbers. The **keyPair** object includes a public key (**PubKey**) and a private key (**PriKey**).

   To understand how to generate an RSA asymmetric key pair, refer to the following example, along with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters.

2. Call [OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create) with the string parameter **'RSA1024|PKCS1'** to create a **Cipher** instance for encryption and decryption. The key type is **RSA1024**, and the padding mode is **PKCS1**.

3. Call [OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**keyPair**).

4. Call [OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) and pass the plaintext to obtain the encrypted data.

   - The output of **OH_CryptoAsymCipher_Final** may be **NULL**. To avoid exceptions, always check whether the result is **NULL** before accessing specific data.
   - When the amount of data is large, you can call OH_CryptoAsymCipher_Final multiple times, that is, [segmented encryption and decryption](crypto-rsa-asym-encrypt-decrypt-ndk.md#using-rsa-asymmetric-keys-for-segmented-encryption-and-decryption).

**Decryption**

1. Since the **Cipher** instance of the RSA algorithm does not support repeated initialization, call [OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create) to create a new **Cipher** instance.

2. Call [OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_DECRYPT_MODE**, and specify the key for decryption (**keyPair**).

3. Call [OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) and pass the ciphertext to obtain the decrypted data.

  <!-- @[rsa_pkcs1_encrypt_decrypt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceCpp/entry/src/main/cpp/types/project/rsa/PKCS1_RSA.cpp) -->

  ``` C++
  
  #include "CryptoArchitectureKit/crypto_architecture_kit.h"
  #include <cstring>
  
  static OH_Crypto_ErrCode doRsaEncrypt(const Crypto_DataBlob *plainData, OH_CryptoKeyPair **keyPair,
      OH_CryptoAsymKeyGenerator **keyGen, Crypto_DataBlob *encryptedData)
  {
      OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create("RSA1024", keyGen);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
  
      ret = OH_CryptoAsymKeyGenerator_Generate(*keyGen, keyPair);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoAsymKeyGenerator_Destroy(*keyGen);
          return ret;
      }
  
      OH_CryptoAsymCipher *cipher = nullptr;
      ret = OH_CryptoAsymCipher_Create("RSA1024|PKCS1", &cipher);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoKeyPair_Destroy(*keyPair);
          OH_CryptoAsymKeyGenerator_Destroy(*keyGen);
          return ret;
      }
  
      ret = OH_CryptoAsymCipher_Init(cipher, CRYPTO_ENCRYPT_MODE, *keyPair);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoAsymCipher_Destroy(cipher);
          OH_CryptoKeyPair_Destroy(*keyPair);
          OH_CryptoAsymKeyGenerator_Destroy(*keyGen);
          return ret;
      }
  
      ret = OH_CryptoAsymCipher_Final(cipher, plainData, encryptedData);
      OH_CryptoAsymCipher_Destroy(cipher);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoKeyPair_Destroy(*keyPair);
          OH_CryptoAsymKeyGenerator_Destroy(*keyGen);
          return ret;
      }
  
      return ret;
  }
  
  static OH_Crypto_ErrCode doRsaDecrypt(const Crypto_DataBlob *encryptedData, OH_CryptoKeyPair *keyPair,
      const Crypto_DataBlob *expectedPlainData)
  {
      OH_CryptoAsymCipher *cipher = nullptr;
      OH_Crypto_ErrCode ret = OH_CryptoAsymCipher_Create("RSA1024|PKCS1", &cipher);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
  
      ret = OH_CryptoAsymCipher_Init(cipher, CRYPTO_DECRYPT_MODE, keyPair);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoAsymCipher_Destroy(cipher);
          return ret;
      }
  
      Crypto_DataBlob decrypted = { 0 };
      ret = OH_CryptoAsymCipher_Final(cipher, encryptedData, &decrypted);
      OH_CryptoAsymCipher_Destroy(cipher);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
  
      if ((decrypted.len != expectedPlainData->len) ||
          (memcmp(decrypted.data, expectedPlainData->data, decrypted.len) != 0)) {
          OH_Crypto_FreeDataBlob(&decrypted);
          return CRYPTO_OPERTION_ERROR;
      }
  
      OH_Crypto_FreeDataBlob(&decrypted);
      return ret;
  }
  
  OH_Crypto_ErrCode doTestRsaEncDec()
  {
      const char *testData = "Hello, RSA!";
      Crypto_DataBlob plainData = {
          .data = (uint8_t *)testData,
          .len = strlen(testData)
      };
  
      OH_CryptoKeyPair *keyPair = nullptr;
      OH_CryptoAsymKeyGenerator *keyGen = nullptr;
      Crypto_DataBlob encryptedData = { 0 };
  
      OH_Crypto_ErrCode ret = doRsaEncrypt(&plainData, &keyPair, &keyGen, &encryptedData);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
  
      ret = doRsaDecrypt(&encryptedData, keyPair, &plainData);
      OH_Crypto_FreeDataBlob(&encryptedData);
      OH_CryptoKeyPair_Destroy(keyPair);
      OH_CryptoAsymKeyGenerator_Destroy(keyGen);
      return ret;
  }
  ```

## Using RSA Asymmetric Keys for Segmented Encryption and Decryption

**Encryption**

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) and [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to generate an asymmetric key pair (**keyPair**) of the RSA1024 type with two prime numbers. The **keyPair** object includes a public key (**PubKey**) and a private key (**PriKey**).

   To understand how to generate an RSA asymmetric key pair, refer to the following example, along with [Asymmetric Key Generation and Conversion Specifications: RSA](crypto-key-generation-conversion.md#rsa) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly.md). Note that the reference documents may differ from the current example in input parameters.

2. Call [OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create) with the string parameter **'RSA1024|PKCS1'** to create a **Cipher** instance for encryption and decryption. The key type is **RSA1024**, and the padding mode is **PKCS1**.

3. Call [OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**keyPair**).

4. Call [OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) multiple times and pass the plaintext to obtain the encrypted data.

   - The output of **OH_CryptoAsymCipher_Final** may be **NULL**. To avoid exceptions, always check whether the result is **NULL** before accessing specific data.

   - Here, the plaintext is split into 64-byte segments and encrypted multiple times. With a 1024-bit key, each encryption generates 128 bytes of ciphertext.
   > **NOTE**
   >
   > Segmented encryption and decryption with asymmetric keys means that when the plaintext exceeds the data length supported by a single encryption or decryption operation, the data to be encrypted or decrypted is split into segments of an appropriate length, and the encryption or decryption operation is performed on each segment. For details, see [Introduction to Asymmetric Segmented Encryption and Decryption](crypto-encryption-decryption.md#asymmetric-encryption-and-decryption).

**Decryption**

1. Because the **Cipher** instance of the RSA algorithm does not support repeated initialization, call [OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create) to create a new **Cipher** instance.

2. Call [OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_DECRYPT_MODE**, and specify the key for decryption (**keyPair**).

3. Call [OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) multiple times and pass the ciphertext to obtain the decrypted data.


<!-- @[rsa_encrypt_decrypt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceCpp/entry/src/main/cpp/types/project/rsa/RSAEncryptDecrypt.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <algorithm>
#include <vector>
#include <string>

static std::vector<uint8_t> doTestRsaEnc(OH_CryptoKeyPair *keyPair, std::vector<uint8_t> &plainText)
{
    std::vector<uint8_t> cipherText;
    OH_CryptoAsymCipher *cipher = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoAsymCipher_Create("RSA1024|PKCS1", &cipher);
    if (ret != CRYPTO_SUCCESS) {
        return std::vector<uint8_t>{};
    }

    ret = OH_CryptoAsymCipher_Init(cipher, CRYPTO_ENCRYPT_MODE, keyPair);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymCipher_Destroy(cipher);
        return std::vector<uint8_t>{};
    }

    size_t plainTextSplitLen = 64;
    for (size_t i = 0; i < plainText.size(); i += plainTextSplitLen) {
        Crypto_DataBlob in = {};
        in.data = plainText.data() + i;
        if (i + plainTextSplitLen > plainText.size()) {
            in.len = plainText.size() - i;
        } else {
            in.len = plainTextSplitLen;
        }
        Crypto_DataBlob out = {};
        ret = OH_CryptoAsymCipher_Final(cipher, &in, &out);
        if (ret != CRYPTO_SUCCESS) {
            OH_CryptoAsymCipher_Destroy(cipher);
            return std::vector<uint8_t>{};
        }
        cipherText.insert(cipherText.end(), out.data, out.data + out.len);
        OH_Crypto_FreeDataBlob(&out);
    }

    OH_CryptoAsymCipher_Destroy(cipher);
    return cipherText;
}

static std::vector<uint8_t> doTestRsaDec(OH_CryptoKeyPair *keyPair, std::vector<uint8_t> &encryptText)
{
    std::vector<uint8_t> decryptText;
    OH_CryptoAsymCipher *cipher = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoAsymCipher_Create("RSA1024|PKCS1", &cipher);
    if (ret != CRYPTO_SUCCESS) {
        return std::vector<uint8_t>{};
    }

    ret = OH_CryptoAsymCipher_Init(cipher, CRYPTO_DECRYPT_MODE, keyPair);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymCipher_Destroy(cipher);
        return std::vector<uint8_t>{};
    }

    size_t cipherTextSplitLen = 128; // The ciphertext byte length generated by each RSA key encryption is calculated as: key bits / 8.
    for (size_t i = 0; i < encryptText.size(); i += cipherTextSplitLen) {
        Crypto_DataBlob in = {};
        in.data = encryptText.data() + i;
        if (i + cipherTextSplitLen > encryptText.size()) {
            in.len = encryptText.size() - i;
        } else {
            in.len = cipherTextSplitLen;
        }
        Crypto_DataBlob out = {};
        ret = OH_CryptoAsymCipher_Final(cipher, &in, &out);
        if (ret != CRYPTO_SUCCESS) {
            OH_CryptoAsymCipher_Destroy(cipher);
            return std::vector<uint8_t>{};
        }
        decryptText.insert(decryptText.end(), out.data, out.data + out.len);
        OH_Crypto_FreeDataBlob(&out);
    }

    OH_CryptoAsymCipher_Destroy(cipher);
    return decryptText;
}

OH_Crypto_ErrCode doTestRsaEncLongMessage()
{
    OH_CryptoAsymKeyGenerator *keyGen = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create("RSA1024", &keyGen);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    OH_CryptoKeyPair *keyPair = nullptr;
    ret = OH_CryptoAsymKeyGenerator_Generate(keyGen, &keyPair);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(keyGen);
        return ret;
    }

    std::string message =
        "This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!"
        "This is a long plainText! This is a long plainText! This is a long plainText! This is a long plainText!";

    std::vector<uint8_t> plainText(message.begin(), message.end());
    std::vector<uint8_t> cipherText = doTestRsaEnc(keyPair, plainText);
    std::vector<uint8_t> decryptText = doTestRsaDec(keyPair, cipherText);

    if ((plainText.size() != decryptText.size()) ||
        (!std::equal(plainText.begin(), plainText.end(), decryptText.begin()))) {
        OH_CryptoKeyPair_Destroy(keyPair);
        OH_CryptoAsymKeyGenerator_Destroy(keyGen);
        return CRYPTO_OPERTION_ERROR;
    }

    OH_CryptoKeyPair_Destroy(keyPair);
    OH_CryptoAsymKeyGenerator_Destroy(keyGen);
    return CRYPTO_SUCCESS;
}
```
