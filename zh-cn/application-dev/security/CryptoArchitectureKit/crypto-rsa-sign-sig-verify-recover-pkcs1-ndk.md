# 使用RSA密钥对（PKCS1模式）签名恢复(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[验签算法规格：RSA](crypto-sign-sig-verify-overview.md#rsa)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 开发步骤

1. 调用[OH_CryptoVerify_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_create)，指定字符串参数'RSA1024|PKCS1|SHA256|Recover'，与签名的Sign实例保持一致。创建Verify实例，用于完成验签操作。

2. 调用[OH_CryptoVerify_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_init)，使用公钥（OH_CryptoPubKey）初始化Verify实例。

3. 调用[OH_CryptoVerify_Recover](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_recover)，对数据进行签名恢复。

<!-- @[pkcs1_recover_rsa_keypair_sign](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/rsa_pkcs1_signature_restoration.cpp) -->

