# 使用HKDF进行密钥派生(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应算法规格请查看[密钥派生算法规格：HKDF](crypto-key-derivation-overview.md#hkdf算法)。

## 开发步骤

1. 调用[OH_CryptoKdfParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_create)，指定字符串参数'HKDF'，创建密钥派生参数对象。

2. 调用[OH_CryptoKdfParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_setparam)，设置HKDF所需的参数。示例如下：
   - CRYPTO_KDF_KEY_DATABLOB：用于生成派生密钥的原始密钥材料。
   - CRYPTO_KDF_SALT_DATABLOB：盐值。
   - CRYPTO_KDF_INFO_DATABLOB：应用程序特定的信息（可选）。

3. 调用[OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create)，指定字符串参数'HKDF|SHA256|EXTRACT_AND_EXPAND'，创建密钥派生函数对象。

4. 调用[OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive)，指定目标密钥的字节长度，进行密钥派生。

<!-- @[hkdf_test_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyDerivation/HKDFDerivation/entry/src/main/cpp/types/project/hkdf_test.cpp) -->
