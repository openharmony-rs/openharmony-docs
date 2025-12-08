# 签名/验签(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

当前指导提供以下示例，供开发者参考完成签名、验签开发：

- [密钥算法为ECC256、摘要算法为SHA256](#ecc256sha256)
- [密钥算法为SM2、摘要算法为SM3](#sm2sm3)
- [密钥算法为SM2、摘要算法为NoDigest](#sm2nodigest)
- [密钥算法为RSA、摘要算法为SHA256、填充模式为PSS](#rsasha256pss)
- [密钥算法为RSA、摘要算法为SHA256、填充模式为PKCS1_V1_5](#rsasha256pkcs1_v1_5)
- [密钥算法为RSA、摘要算法为SHA384、填充模式为PSS](#rsa2048sha384pss)
<!--RP1--><!--RP1End-->

具体的场景介绍及支持的算法规格，请参考[签名/验签支持的算法](huks-signing-signature-verification-overview.md#支持的算法)。


## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

**生成密钥**
1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。

3. 调用[OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem)生成密钥，具体请参考[密钥生成](huks-key-generation-overview.md)。

除此之外，开发者也可以参考[密钥导入](huks-key-import-overview.md)，导入已有的密钥。

**签名**

1. 获取密钥别名。

2. 指定待签名的明文数据。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定算法参数配置。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，获取签名signature。

**验签**

1. 获取密钥别名。

2. 获取待验证的签名signature。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定[算法参数配置](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession)更新密钥会话。

6. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，验证签名。

**删除密钥**

当密钥废弃不用时，需要调用[OH_Huks_DeleteKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_deletekeyitem)删除密钥，具体请参考[密钥删除](huks-delete-key-ndk.md)。

## 开发案例

### ECC256/SHA256
<!-- @[key_algorithm_ecc_sha256_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/ecc_sha256_sign_verify.cpp) -->
### SM2/SM3
<!-- @[key_algorithm_sm2_sm3_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_sm3_sign_verify.cpp) -->
### SM2/NoDigest
<!-- @[key_algorithm_sm2_nodigest_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_nodigest_sign_verify.cpp) -->
### RSA/SHA256/PSS
<!-- @[key_algorithm_rsa_sha256_pss_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha256_pss_sign_verify.cpp) -->
### RSA/SHA256/PKCS1_V1_5
<!-- @[key_algorithm_rsa_sha256_pkcs1_v1_5_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha256_pkcs1_v1_5_sign_verify.cpp) -->
### RSA2048/SHA384/PSS
<!-- @[key_algorithm_rsa_sha384_pss_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha384_pss_sign_verify.cpp) -->