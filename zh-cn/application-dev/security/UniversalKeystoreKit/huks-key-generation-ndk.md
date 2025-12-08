# 生成密钥(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

以ECC算法为例，生成随机密钥。具体的场景介绍及支持的算法规格，请参考[密钥生成支持的算法](huks-key-generation-overview.md#支持的算法)。

> **注意：**
> 密钥别名中禁止包含个人数据等敏感信息。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。通过[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)、[OH_Huks_AddParams](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_addparams)、[OH_Huks_BuildParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_buildparamset)构造密钥属性集paramSet。
   密钥属性集中必须包含[OH_Huks_KeyAlg](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyalg)、[OH_Huks_KeySize](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keysize)、[OH_Huks_KeyPurpose](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keypurpose)属性。注：一个密钥只能有一类PURPOSE，并且，生成密钥时指定的用途要与使用时的方式一致，否则会导致异常。

3. 调用[OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem)，传入密钥别名和密钥属性集，生成密钥。

> **说明：**
>
> 如果业务再次使用相同别名调用HUKS生成密钥，HUKS将生成新密钥并直接覆盖历史的密钥文件。

<!-- @[generate_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/GenerateKey/entry/src/main/cpp/napi_init.cpp) -->
