# @ohos.account.appAccount

本模块提供应用账号信息的添加、删除、修改和查询基础能力，并支持应用间鉴权和分布式数据同步功能。

**起始版本：** 7

**系统能力：** SystemCapability.Account.AppAccount

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAppAccountManager](arkts-basicservices-appaccount-createappaccountmanager-f.md#createAppAccountManager-1) | 创建应用账号管理器对象。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [Authenticator](arkts-basicservices-appaccount-authenticator-c.md) | 认证器基类。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md) | 表示应用账号信息。<br/> |
| [AppAccountManager](arkts-basicservices-appaccount-appaccountmanager-i.md) | 应用账号管理器，可用于管理应用自身的账号信息。<br/> |
| [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 认证器回调类。<br/> |
| [AuthResult](arkts-basicservices-appaccount-authresult-i.md) | 表示认证结果信息。<br/> |
| [AuthTokenInfo](arkts-basicservices-appaccount-authtokeninfo-i.md) | 表示Auth令牌信息。<br/> |
| [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | OAuth认证器回调接口。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃。建议使用[AuthCallback](arkts-basicservices-appaccount-authcallback-i.md#AuthCallback)替代。<br/> |
| [AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md) | 表示OAuth认证器信息。<br/> |
| [CreateAccountImplicitlyOptions](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | 表示隐式创建账号的选项。<br/> |
| [CreateAccountOptions](arkts-basicservices-appaccount-createaccountoptions-i.md) | 表示创建账号的选项。<br/> |
| [OAuthTokenInfo](arkts-basicservices-appaccount-oauthtokeninfo-i.md) | 表示OAuth令牌信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 8开始支持，从API version 9开始废弃。建议使用[AuthTokenInfo](arkts-basicservices-appaccount-authtokeninfo-i.md#AuthTokenInfo)替代。<br/> |
| [SelectAccountsOptions](arkts-basicservices-appaccount-selectaccountsoptions-i.md) | 表示用于选择账号的选项。<br/> |
| [SetPropertiesOptions](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | 表示用于设置属性的选项。<br/> |
| [VerifyCredentialOptions](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | 表示用于验证凭据的选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Constants](arkts-basicservices-appaccount-constants-e.md) | 表示常量的枚举。<br/> |
| [ResultCode](arkts-basicservices-appaccount-resultcode-e.md) | 表示返回码的枚举。<br/><br/>&gt; **说明：**&lt;br/&gt;<br/>&gt; &gt; 从API version 8开始支持，从API version 9开始废弃。相关信息建议查看<br/>&gt; [账号管理错误码](../../../../reference/apis-basic-services-kit/errorcode-account.md)替代。<br/> |

