# 用户身份认证访问控制开发指导

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

场景介绍及相关概念说明请参考[用户身份认证访问控制简介](huks-identity-authentication-overview.md)。

## 开发步骤

### 生成密钥

指定指纹访问控制类型及相关属性。

生成或导入密钥时，在密钥属性集中需指定三个参数：用户认证类型[HuksUserAuthType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksuserauthtype9)、授权访问类型[HuksAuthAccessType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksauthaccesstype9)、挑战值类型[HuksChallengeType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukschallengetype9)。

<!-- @[user_authentication_key_generation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->

### 通过PIN码认证获取授权令牌
<!-- @[user_authentication_pin_verification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->

### 使用认证令牌进行加密操作
<!-- @[user_authentication_data_encryption](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->