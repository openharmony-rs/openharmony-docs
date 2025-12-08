# 生成密钥(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

以DH算法为例，生成随机密钥。具体的场景介绍及支持的算法规格，请参考[密钥生成支持的算法](huks-key-generation-overview.md#支持的算法)。

> **注意：**
> 密钥别名中禁止包含个人数据等敏感信息。

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。
   - 通过[HuksParam](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam)封装密钥属性，搭配Array组成密钥属性集，并赋值给[HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions)中的properties字段。
   - 密钥属性集中必须包含[HuksKeyAlg](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyalg)、[HuksKeySize](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeysize)、[HuksKeyPurpose](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose)属性，即必传TAG：HUKS_TAG_ALGORITHM、HUKS_TAG_PURPOSE、HUKS_TAG_KEY_SIZE。
   
   > **注意：**
   >
   > 一个密钥只能有一类PURPOSE，并且生成密钥时指定的用途要与使用时的方式一致，否则会导致异常。

3. 调用[generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9)，传入密钥别名和密钥属性集，生成密钥。

> **说明：**
>
> 如果业务再次使用相同别名调用HUKS生成密钥，HUKS将生成新密钥并直接覆盖历史的密钥文件。

<!-- @[generate_key_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/GenerateKey/entry/src/main/ets/pages/Index.ets) -->