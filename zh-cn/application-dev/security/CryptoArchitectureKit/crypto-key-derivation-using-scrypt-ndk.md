# 使用SCRYPT进行密钥派生(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[密钥派生算法规格：SCRYPT](crypto-key-derivation-overview.md#scrypt算法)。

## 开发步骤

1. 调用[OH_CryptoKdfParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_create)，指定字符串参数'SCRYPT'，创建密钥派生参数对象。

2. 调用[OH_CryptoKdfParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_setparam)，设置Scrypt所需的参数。

密钥派生失败原因：下列参数未设置。
   - CRYPTO_KDF_KEY_DATABLOB：用于生成派生密钥的原始密码。
   - CRYPTO_KDF_SALT_DATABLOB：盐值。
   - CRYPTO_KDF_SCRYPT_N_UINT64：CPU/内存开销参数，必须是2的幂次方。
   - CRYPTO_KDF_SCRYPT_R_UINT64：块大小参数，影响并行度。
   - CRYPTO_KDF_SCRYPT_P_UINT64：并行化参数。
   - CRYPTO_KDF_SCRYPT_MAX_MEM_UINT64：最大内存限制（字节）。

3. 调用[OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create)，指定字符串参数'SCRYPT'，创建密钥派生函数对象。

4. 调用[OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive)，指定目标密钥的字节长度，进行密钥派生。

<!-- @[scrypt_test_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyDerivation/SCRYPTDerivation/entry/src/main/cpp/types/project/scrypt_test.cpp) -->
