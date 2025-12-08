# 密钥导出(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

业务需要获取持久化存储的非对称密钥的公钥时使用，当前支持ECC/RSA/ED25519/X25519/SM2的公钥导出。
>**说明：**
>
> <!--RP1-->轻量级设备<!--RP1End-->仅支持RSA公钥导出。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 调用接口[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)，传入参数keyAlias和options。options为预留参数，当前可传入空。

3. 返回值为[HuksReturnResult](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksreturnresult9)类型对象，获取的公钥明文在outData字段中，以标准的X.509规范的DER格式封装，具体请参考[公钥材料格式](huks-concepts.md#公钥材料格式)。

<!-- @[fetch_persistent_security_public_keys_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/KeyExport/entry/src/main/ets/pages/KeyExport.ets) -->