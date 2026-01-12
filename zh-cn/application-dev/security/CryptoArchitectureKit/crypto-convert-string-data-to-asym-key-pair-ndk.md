# 指定PEM格式字符串数据转换非对称密钥对(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以RSA为例，根据指定的非对称密钥字符串数据，生成非对称密钥对（OH_CryptoKeyPair）。

> **说明：**
>
> 针对非对称密钥的convertPemKey操作：
>
> - 公钥需满足X.509规范、PKCS\#1规范、PEM编码格式。
>
> - 私钥需满足PKCS\#8规范、PKCS\#1规范、PEM编码格式。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 指定PEM格式字符串数据转换RSA密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)，指定字符串参数'RSA1024'，创建RSA密钥类型为RSA1024、素数个数为2的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。

   生成RSA非对称密钥时，默认素数为2，此处省略了参数PRIMES_2。

2. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入二进制密钥数据，生成非对称密钥对象（OH_CryptoKeyPair）。
3. 调用[OH_CryptoPubKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptopubkey_encode)，将非对称密钥对象中的公钥转换成pkcs1或x509格式。

- 以下以生成RSA密钥对为例：
<!-- @[specify_pem_string_convert_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSpecifiedPEMAsymmetricKeyPair/entry/src/main/cpp/types/project/rsa.cpp) -->



