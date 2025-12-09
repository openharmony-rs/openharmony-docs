# 细粒度用户身份认证访问控制开发指导

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

细粒度用户身份认证访问控制是基于已有用户身份认证访问控制的扩展，提供了基于生物特征和锁屏密码二次身份认证的细粒度访问控制能力，允许设置密钥在加密、解密、签名、验签、密钥协商、密钥派生的单个或多个场景时是否需要进行身份验证。

比如，业务需要使用HUKS密钥加密保存账号密码信息等数据，要求在加密的时候不进行指纹等身份认证，解密的时候需要进行指纹等身份认证，这时就需要依赖HUKS提供细粒度的二次身份认证访问控制机制。

使用该功能仅需在密钥生成阶段，通过额外指定用于细粒度用户身份认证访问控制的HuksTag：HUKS_TAG_KEY_AUTH_PURPOSE，来指定在某种算法用途的情况下需要使用用户身份认证访问控制能力。

> **说明：**
>
> 对于对称加解密场景，仅AES/CBC、AES/GCM、SM4/CBC模式支持细粒度访问控制。

## 开发步骤
### 密钥生成和数据加密
<!-- @[fingerprint_access_key_generation_and_encryption](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->

### 用户认证
<!-- @[fingerprint_access_user_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->

### 数据解密和验证
<!-- @[fingerprint_access_decryption_and_verification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->