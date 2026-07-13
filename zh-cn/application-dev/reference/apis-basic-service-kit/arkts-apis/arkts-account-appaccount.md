# @ohos.account.appAccount

本模块提供应用账号信息的添加、删除、修改和查询基础能力，并支持应用间鉴权和分布式数据同步功能。

**起始版本：** 7

**系统能力：** SystemCapability.Account.AppAccount

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAppAccountManager](arkts-basicservices-createappaccountmanager-f.md#createappaccountmanager-1) | 创建应用账号管理器对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Authenticator](arkts-basicservices-authenticator-c.md) | 认证器基类。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AppAccountInfo](arkts-basicservices-appaccountinfo-i.md) | 表示应用账号信息。 |
| [AppAccountManager](arkts-basicservices-appaccountmanager-i.md) | 应用账号管理器，可用于管理应用自身的账号信息。 |
| [AuthCallback](arkts-basicservices-authcallback-i.md) | 认证器回调类。 |
| [AuthResult](arkts-basicservices-authresult-i.md) | 表示认证结果信息。 |
| [AuthTokenInfo](arkts-basicservices-authtokeninfo-i.md) | 表示Auth令牌信息。 |
| [AuthenticatorCallback](arkts-basicservices-authenticatorcallback-i.md) | OAuth认证器回调接口。@link appAccount.AuthCallback}替代。 |
| [AuthenticatorInfo](arkts-basicservices-authenticatorinfo-i.md) | 表示OAuth认证器信息。 |
| [CreateAccountImplicitlyOptions](arkts-basicservices-createaccountimplicitlyoptions-i.md) | 表示隐式创建账号的选项。 |
| [CreateAccountOptions](arkts-basicservices-createaccountoptions-i.md) | 表示创建账号的选项。 |
| [OAuthTokenInfo](arkts-basicservices-oauthtokeninfo-i.md) | 表示OAuth令牌信息。@link appAccount.AuthTokenInfo}替代。 |
| [SelectAccountsOptions](arkts-basicservices-selectaccountsoptions-i.md) | 表示用于选择账号的选项。 |
| [SetPropertiesOptions](arkts-basicservices-setpropertiesoptions-i.md) | 表示用于设置属性的选项。 |
| [VerifyCredentialOptions](arkts-basicservices-verifycredentialoptions-i.md) | 表示用于验证凭据的选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Constants](arkts-basicservices-constants-e.md) | 表示常量的枚举。 |
| [ResultCode](arkts-basicservices-resultcode-e.md) | 表示返回码的枚举。 |

