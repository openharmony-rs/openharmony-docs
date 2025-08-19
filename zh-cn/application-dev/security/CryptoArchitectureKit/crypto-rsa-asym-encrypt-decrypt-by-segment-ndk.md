# 使用RSA非对称密钥分段加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[非对称密钥加解密算法规格：RSA](crypto-asym-encrypt-decrypt-spec.md#rsa)。

**加密**

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)、[OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，生成RSA密钥类型为RSA1024、素数个数为2的非对称密钥对（keyPair）。keyPair对象中包括公钥PubKey、私钥PriKey。

   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[随机生成非对称密钥对](crypto-generate-asym-key-pair-randomly.md)理解。参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create)，指定字符串参数'RSA1024|PKCS1'，创建非对称密钥类型为RSA1024、填充模式为PKCS1的Cipher实例，用于完成加解密操作。

3. 调用[OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定加密密钥（keyPair），初始化加密Cipher实例。

4. 多次调用[OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final)，传入明文，获取加密后的数据。

   - OH_CryptoAsymCipher_Final输出结果可能为NULL，在访问具体数据前，需要先判断结果是否为NULL，避免产生异常。

   - 此处将明文按64个字节一组拆分，多次加密。使用1024位密钥，每次将生成128字节密文。
   > **说明：**
   > 非对称密钥的分段加解密是指当明文大于单次加解密支持的数据长度时，需要将待加解密数据分为合适长度的数据段，并对每个数据段执行加解密操作。详细介绍可见[非对称分段加解密介绍](crypto-encrypt-decrypt-by-segment.md#非对称加解密)。

**解密**

1. 由于RSA算法的Cipher实例不支持重复init操作，需要调用[OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create)，重新生成Cipher实例。

2. 调用[OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init)，设置模式为解密（CRYPTO_DECRYPT_MODE），指定解密密钥（keyPair）初始化解密Cipher实例。

3. 多次调用[OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final)，传入密文，获取解密后的数据。

- 异步方法示例：

```C++
#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <algorithm>
#include <vector>

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

    size_t cipherTextSplitLen = 128; // RSA密钥每次加密生成的密文字节长度计算方式：密钥位数/8。
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

static OH_Crypto_ErrCode doTestRsaEncLongMessage()
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
        "This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!"
        "This is a long plainTest! This is a long plainTest! This is a long plainTest! This is a long plainTest!";

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