# 指定二进制数据转换对称密钥(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以3DES和HMAC为例，根据指定的对称密钥二进制数据生成密钥（OH_CryptoSymKey），将外部或存储的二进制数据转换为算法库的密钥对象，该对象可用于后续的加解密操作。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 指定二进制数据转换3DES密钥

查看[对称密钥生成和转换规格：3DES](crypto-sym-key-generation-conversion-spec.md#3des)。

1. 获取3DES二进制密钥数据，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。

2. 调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)，指定字符串参数'3DES192'，创建密钥算法为3DES、密钥长度为192位的对称密钥生成器（OH_CryptoSymKeyGenerator）。

3. 调用[OH_CryptoSymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert)，根据指定的对称密钥二进制数据生成对称密钥对象（OH_CryptoSymKey）。

4. 调用[OH_CryptoSymKey_GetKeyData](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_getkeydata)，获取密钥对象的二进制数据。

以下以生成3DES密钥为例：

<!-- @[generate_3des_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormat/entry/src/main/cpp/types/project/3des.cpp) -->


## 指定二进制数据转换HMAC密钥

查看[对称密钥生成和转换规格：HMAC](crypto-sym-key-generation-conversion-spec.md#hmac)。

1. 获取HMAC二进制密钥，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。

2. 调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)，指定字符串参数'HMAC'，创建密钥算法为HMAC、密钥长度为[1, 32768]位的对称密钥生成器（OH_CryptoSymKeyGenerator）。

3. 调用[OH_CryptoSymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert)，根据指定的对称密钥二进制数据生成对称密钥对象（OH_CryptoSymKey）。

4. 调用[OH_CryptoSymKey_GetKeyData](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_getkeydata)，获取密钥对象的二进制数据。

以下以生成HMAC密钥为例：

<!-- @[generate_hmac_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormat/entry/src/main/cpp/types/project/hmac.cpp) -->

