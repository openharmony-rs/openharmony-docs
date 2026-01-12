# 使用私钥对象获取公钥对象(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API version 23开始，算法库支持从私钥对象中获取公钥对象的操作。

以RSA为例，根据私钥对象获取公钥对象。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

对应的算法规格请查看[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

## 开发步骤

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)，指定字符串参数'RSA1024|PRIMES_2'，创建RSA密钥类型为RSA1024、素数个数为2的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。

2. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入私钥数据，生成非对称密钥对象（OH_CryptoKeyPair）。

3. 调用[OH_CryptoKeyPair_GetPubKey](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptokeypair_getpubkey)获取公钥对象 (OH_CryptoPubKey)。

4. 调用[OH_CryptoPubKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptopubkey_encode)获取公钥对象的二进制数据。

5. 比较公钥数据与期望值是否相等。

<!-- @[prikey_get_pubkey_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/cpp/types/project/prikey_get_pubkey.cpp) -->

