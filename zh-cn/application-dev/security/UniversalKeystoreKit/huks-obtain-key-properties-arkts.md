# 获取密钥属性(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供了接口供业务获取指定密钥的相关属性。在获取指定密钥属性前，需要确保已在HUKS中生成或导入持久化存储的密钥。
>**说明：**
>
> <!--RP1-->轻量级设备<!--RP1End-->不支持获取密钥属性功能。

从API 23开始支持[群组密钥](huks-group-key-overview.md)特性。

## 开发步骤

1. 指定待查询的密钥别名keyAlias，密钥别名最大长度为128字节。

2. 调用接口[getKeyItemProperties](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgetkeyitemproperties9)，传入参数keyAlias和options。options为预留参数，当前可传入空。

3. 返回值为[HuksReturnResult](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksreturnresult9)类型对象，获取的属性集在properties字段中。

<!-- @[obtaining_key_attribute_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OtherOperations/GetKeyAttributes/entry/src/main/ets/pages/GetKeyAttributes.ets) -->